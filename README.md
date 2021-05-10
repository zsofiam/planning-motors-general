# Planning motors

## Story

Your boss, Melon Usk, wants to jump into the electric car business.
Whoa, bold plan, as usual. He is really into sketches and diagrams,
and keeps sending you blurred pictures of his whiteboard with some
scribbles on it and asks you to implement it. And at the end it
always turns out that he'd thought of something completely different.
Super annoying. It's time to show him how it is done in the industry:
draw proper UML diagrams from the plans, and ask for a review _before_
the implementation.

## What are you going to learn?

- design an application using class diagram
- get to know how `draw.io` works
- think in OOP way

## Tasks

1. Melon says electric cars are a subtype of cars, the only difference is that instead of an engine they have electric motors. You translate it like this: - `ElectricCar` is a subclass of `Car` - `ElectricMotor` is a subclass of `Engine` - a `Car` has an `Engine` and an `ElectricCar` has an `ElectricMotor`. Draw this, and the result has to be exported and uploaded to the project as `motors-v1.png`.
    - The diagram shows 4 class blocks - `Car`, `ElectricCar`, `Engine`, and `ElectricMotor`
    - Class `ElectricCar` is a subclass of `Car`. Proper arrow between classes is visible
    - Class `ElectricMotor` is a subclass of `Engine`. Proper arrow between classes is visible
    - Class `Car` has an `Engine`, and the latter can exist in itself. Proper arrow between classes is visible
    - Class `ElectricCar` has an `ElectricMotor`, and the latter can exist in itself. Proper arrow between classes is visible

2. Looking at the first version, Melon starts shouting. He says that an electric motor is not an engine because it is not driven (by heat)[https://english.stackexchange.com/questions/42027/semantic-difference-between-engine-and-motor]. Cars with engines are just regular cars, while cars with electric motors are called _electric_ cars because of the motor. "And don't forget to include the batteries, we will be focusing on batteries!" - you hear the last instruction. You translate it like this: - `Motor` is abstract, and `Engine` and `ElectricMotor` are subclasses of it - every `Car` has a `Motor` - a `Battery` class has to be added to `Car`s as every car has a battery inside. - no need to introduce a new class for `ElectricCar` since the motor type will decide about its type Draw this, and the result has to be exported and uploaded to the project as `motors-v2.png`.
    - The diagram shows 5 class blocks - `Car`, `Motor`, `Engine`, `ElectricMotor`, and `Battery`
    - Class `Motor` is abstract
    - Classes `Engine` and `ElectricMotor` are subclasses of `Motor`. Proper arrow between classes is visible
    - Class `Car` has a `Motor` and a `Battery`, and the latter two can exist without the `Car`. Proper arrow between classes is visible

3. "Do not forget that electric cars in fact can be charged!" - yells Melon as you design the architecture. "Kevin, who works on SpaceY project, has already created `Rechargeable` interface with a method `charge`, please reuse it for our electric cars". All electric cars must implement `Rechargeable` interface. It seems we've deleted `ElectricCar` class too soon. Happens to the best ones, too. Draw this, and the result has to be exported and uploaded to the project as `motors-v3.png`.
    - The diagram shows 7 class blocks - `Car`, `ElectricCar`, `Motor`, `Engine`, `ElectricMotor`, `Battery`, and `Rechargeable`
    - Class `Motor` is abstract
    - Classes `Engine` and `ElectricMotor` are subclasses of `Motor`. Proper arrow between classes is visible
    - Class `Car` has a `Motor` and a `Battery`, and the latter two can exist without the `Car`. Proper arrow between classes is visible
    - Class `ElectricCar` has an `ElectricMotor`, and the latter can exist in itself. Proper arrow between classes is visible
    - Interface `Rechargeable` is visibe
    - Class `ElectricCar` extends `Car` and implements `Rechargeable`

4. Melon says that it looks cool, but `Car` is too generic. He asks you to create distinction between `ElectricCars` and `CombustionCars`. "Our customers can not think that electric cars are in any way extension of combustion ones!". Makes sense. Create a class `CombustionCar` that was derived from a `Car` class. At this point `Car` can be marked as abstract. `CombustionCars` can only have regular `Engines`. Draw this, and the result has to be exported and uploaded to the project as `motors-v4.png`.
    - The diagram shows 8 class blocks - `Car`, `ElectricCar`, `CombustionCar`, `Motor`, `Engine`, `ElectricMotor`, `Battery`, and `Rechargeable`
    - Classes `Motor` and `Car` are abstract
    - Classes `Engine` and `ElectricMotor` are subclasses of `Motor`. Proper arrows between classes are visible
    - Classes `ElectricCar` and `CombustionCar` are subclasses of `Car`. Proper arrows between classes are visible
    - Class `Car` has a `Motor` and a `Battery`, and the latter two can exist without the `Car`. Proper arrows between classes are visible
    - Class `CombustionCar` has an `Engine`, and the latter can exist in itself. Proper arrow between classes is visible
    - Class `ElectricCar` has an `ElectricMotor`, and the latter can exist in itself. Proper arrow between classes is visible
    - Interface `Rechargeable` is visible, and class `ElectricCar` implements it

5. "Hey, you cannot put _my_ battery to a combustion car!" - rages Melon. It seems that you have to differentiate two types of batteries: _automotive batteries_ that are included in all types of cars (even in electric ones) for providing power to standard automotive accessories. And there is the so-called "electric vehicle battery" which is the main source of energy for the traction of electric cars. Finally, it's clear what the boss wants: - `Battery` is abstract, and `AutomotiveBattery` and `ElectricVehicleBattery` are subclasses of it - Cars have an `AutomotiveBattery` in general - Electric cars have an additional `ElectricVehicleBattery` Draw this, and the result has to be exported and uploaded to the project as `motors-v5.png`.
    - The diagram shows 10 class blocks - `Car`, `ElectricCar`, `CombustionCar`, `Motor`, `Engine`, `ElectricMotor`, `Battery`, `AutomotiveBattery`, `ElectricVehicleBattery`, and `Rechargeable`
    - Classes `Motor`, `Car`, and `Battery` are abstract
    - Classes `Engine` and `ElectricMotor` are subclasses of `Motor`. Proper arrows between classes are visible
    - Classes `ElectricCar` and `CombustionCar` are subclasses of `Car`. Proper arrows between classes are visible
    - Class `Car` has a `Motor` and a `AutomotiveBattery`, and the latter two can exist without the `Car`. Proper arrow between classes is visible
    - Class `CombustionCar` has an `Engine`, and the latter can exist in itself. Proper arrow between classes is visible
    - Class `ElectricCar` has an `ElectricMotor` and an `ElectricVehicleBattery`, and the latter two can exist without the `ElectricCar`. Proper arrows between classes are visible
    - Interface `Rechargeable` is visible, and class `ElectricCar` implements it

## General requirements

None

## Hints

- Visit `draw.io` and create new class diagram. On left side menu find
  `UML` section and browse positions available there. Locate all
  building blocks needed in this project.

## Background materials

- <i class="far fa-exclamation"></i> [Class diagram basics](https://medium.com/@smagid_allThings/uml-class-diagrams-tutorial-step-by-step-520fd83b300b)
- <i class="far fa-exclamation"></i> [Class diagram explained](https://medium.com/@smagid_allThings/uml-class-diagram-example-fab6197200e6)
- <i class="far fa-exclamation"></i> [Class diagram in depth](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-class-diagram-tutorial/)
