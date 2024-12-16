<h1>
  <span class="headline">Factory Design Patterns in Java</span>
  <span class="subhead">Factory Method Pattern in Action</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to practice applying the Factory pattern to promote loose coupling and maintainability in an application.

## Use the Factory pattern to create a car factory

Let's consider an example scenario where we have a software application for a car manufacturing company. The application needs to create different types of cars, such as sedans, SUVs, and trucks. Instead of directly instantiating these types of cars in the client code, we can use the Factory Method pattern to create them.

First, we define an interface or an abstract base class `Car` that represents the common behavior of all cars:

```java
public interface Car {
    void drive();
}

```

Next, we create concrete implementations for each type of car, implementing the `Car` interface:

```java
public class Sedan implements Car {
    @Override
    public void drive() {
        System.out.println("Driving a sedan");
    }
}

```

```java
public class SUV implements Car {
    @Override
    public void drive() {
        System.out.println("Driving a SUV");
    }
}

```

```java
public class Truck implements Car {
    @Override
    public void drive() {
        System.out.println("Driving a Truck");
    }
}

```

Now, we define the Factory Method interface or abstract class, which provides a method for creating cars:

```java
public interface CarFactory {
    Car createCar();
}

```

We can then implement the Factory Method for each type of car:

```java
public class SedanFactory implements CarFactory {
    @Override
    public Car createCar() {
        return new Sedan();
    }
}

```

```java
public class SUVFactory implements CarFactory {
    @Override
    public Car createCar() {
        return new SUV();
    }
}

```

```java
public class TruckFactory implements CarFactory {
    @Override
    public Car createCar() {
        return new Truck();
    }
}
```

Finally, in the client code, we can use these factory classes to create cars without knowing the specific types:

```java
public class Client {
    public static void main(String[] args) {
        CarFactory sedanFactory = new SedanFactory();
        Car sedan = sedanFactory.createCar();
        sedan.drive();

        CarFactory suvFactory = new SUVFactory();
        Car suv = suvFactory.createCar();
        suv.drive();

        CarFactory truckFactory = new TruckFactory();
        Car truck = truckFactory.createCar();
        truck.drive();
    }
}
```

In this example, the Factory Method pattern allows us to create different types of cars (sedans, SUVs, and trucks) without explicitly specifying their concrete classes in the client code. Instead, the creation logic is encapsulated within the respective factory classes, promoting loose coupling and maintainability in the software application.
