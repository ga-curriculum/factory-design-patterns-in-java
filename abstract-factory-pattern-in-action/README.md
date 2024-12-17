<h1>
  <span class="headline">Factory Design Patterns in Java</span>
  <span class="subhead">Abstract Factory Pattern in Action</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to apply the abstract factory design pattern to enhance a software's flexibility and maintainability.

### Abstract factory design pattern in action

This program serves as a demonstration of the abstract factory design pattern applied in a fictional game development scenario. The purpose of the program is to illustrate how the abstract factory pattern can be used to create families of related objects, such as characters and weapons, without specifying their concrete classes directly. By employing this design pattern, the program promotes flexibility and maintainability in game development by allowing for the creation of interchangeable families of objects, facilitating easy adaptation to changing game requirements and the addition of new types of characters and weapons in the future.

First, we define the abstract factory interface for creating characters and weapons:

```java
package org.example.codealong.abstractfactory;

// Abstract factory interface for creating characters
interface CharacterFactory {
    Character createCharacter();

    Weapon createWeapon();
}

// Abstract product interface for characters
interface Character {
    void display();
}

// Abstract product interface for weapons
interface Weapon {
    void attack();
}

```

Next, we create concrete implementations for different families of characters and weapons:

```java
// Concrete factory for creating elf characters and weapons
class ElfFactory implements CharacterFactory {
    @Override
    public Character createCharacter() {
        return new ElfCharacter();
    }

    @Override
    public Weapon createWeapon() {
        return new Bow();
    }
}

// Concrete factory for creating orc characters and weapons
class OrcFactory implements CharacterFactory {
    @Override
    public Character createCharacter() {
        return new OrcCharacter();
    }

    @Override
    public Weapon createWeapon() {
        return new Axe();
    }
}

// Concrete product for elf character
class ElfCharacter implements Character {
    @Override
    public void display() {
        System.out.println("Creating an Elf character.");
    }
}

// Concrete product for orc character
class OrcCharacter implements Character {
    @Override
    public void display() {
        System.out.println("Creating an Orc character.");
    }
}

// Concrete product for bow weapon
class Bow implements Weapon {
    @Override
    public void attack() {
        System.out.println("Attacking with a bow.");
    }
}

// Concrete product for axe weapon
class Axe implements Weapon {
    @Override
    public void attack() {
        System.out.println("Attacking with an axe.");
    }
}

```

Finally, we use the abstract factory to create characters and weapons without knowing their specific types:

```java
public class AbstractFactoryGameDemo {
    public static void main(String[] args) {
        // Create elf character and weapon
        CharacterFactory elfFactory = new ElfFactory();
        Character elfCharacter = elfFactory.createCharacter();
        Weapon elfWeapon = elfFactory.createWeapon();
        elfCharacter.display();
        elfWeapon.attack();

        // Create orc character and weapon
        CharacterFactory orcFactory = new OrcFactory();
        Character orcCharacter = orcFactory.createCharacter();
        Weapon orcWeapon = orcFactory.createWeapon();
        orcCharacter.display();
        orcWeapon.attack();
    }
}
```

In this example, the abstract factory pattern allows us to create families of related objects (characters and weapons) without knowing their specific types. Instead, we use the abstract factory interface to create concrete instances of characters and weapons, promoting loose coupling and flexibility in the game's design.
