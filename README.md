# Java-program-OOP-concepts-and-ArrayList-and-HashMap.
import java.util.*;

// Abstract class (Abstraction)
abstract class Person {
    private String name;   // Encapsulation
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Getters
    public String getName() { return name; }
    public int getAge() { return age; }

    // Abstract method
    public abstract void displayRole();
}

// Subclass: Student (Inheritance + Polymorphism)
class Student extends Person {
    private String course;

    public Student(String name, int age, String course) {
        super(name, age);
        this.course = course;
    }

    @Override
    public void displayRole() {
        System.out.println(getName() + " is a student of " + course);
    }
}

// Subclass: Teacher (Inheritance + Polymorphism)
class Teacher extends Person {
    private String subject;

    public Teacher(String name, int age, String subject) {
        super(name, age);
        this.subject = subject;
    }

    @Override
    public void displayRole() {
        System.out.println(getName() + " teaches " + subject);
    }
}

// Main Program
public class Main {
    public static void main(String[] args) {
        // ArrayList of Persons
        ArrayList<Person> people = new ArrayList<>();
        people.add(new Student("Janani", 22, "IT"));
        people.add(new Teacher("Blue", 30, "Java"));

        // HashMap for quick lookup
        HashMap<String, Person> personMap = new HashMap<>();
        for (Person p : people) {
            personMap.put(p.getName(), p);
        }

        // Display roles (Polymorphism in action)
        System.out.println("Roles:");
        for (Person p : people) {
            p.displayRole();
        }

        // Lookup by name using HashMap
        System.out.println("\nLookup:");
        Person found = personMap.get("Janani");
        if (found != null) {
            found.displayRole();
        }
    }
}



