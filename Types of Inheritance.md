# Types Of Inheritance - JAVA

This repository demonstrates **all major types of inheritance in Java** using **simple, real‑world–like examples** (Employee, Developer, Tester, TechLead, etc.).

---

## What is Inheritance?

**Inheritance** allows one class to **reuse properties and methods of another class**.

* Parent class → **Superclass**
* Child class → **Subclass**
* Java uses the keyword **`extends`** for classes
* Java uses **`implements`** for interfaces

👉 *Why we use inheritance?*

* Code reusability
* Logical relationship between classes
* Easier maintenance

---

## Base Class Used in Examples

```java
class Employee {
    int id;
    String name;

    Employee(int id, String name) {
        this.id = id;
        this.name = name;
        System.out.println("Employee is Created");
    }

    void displayDetails() {
        System.out.println("Name : " + name);
        System.out.println("ID : " + id);
    }
}
```

This class acts as the **parent class** for most inheritance examples.

---

## 1️⃣ Single Inheritance

### Definition

A class inherits from **exactly one parent class**.

### Structure

```
Parent
  ↑
Child
```

### Example

```java
class Developer extends Employee {
    String programmingLanguage;

    Developer(int id, String name, String programmingLanguage) {
        super(id, name);
        this.programmingLanguage = programmingLanguage;
    }

    void writeCode() {
        System.out.println(name + " is coding in " + programmingLanguage);
    }
}
```

```java
public class SingleInheritance {
    public static void main(String[] args) {
        Developer d = new Developer(101, "Arush", "Java");
        d.displayDetails(); // from Employee
        d.writeCode();      // from Developer
    }
}
```

### Key Points

* Most common and easiest type
* Uses `extends`
* Child can access **public & protected** members of parent

---

## 2️⃣ Hierarchical Inheritance

### Definition

**Multiple child classes inherit from the same parent class**.

### Structure

```
        Parent
       /      \
   Child1   Child2
```

### Example

```java
class Tester extends Employee {
    String testingTool;

    Tester(int id, String name, String testingTool) {
        super(id, name);
        this.testingTool = testingTool;
    }

    void testSoftware() {
        System.out.println(name + " is testing using " + testingTool);
    }
}
```

```java
public class HierarchicalInheritance {
    public static void main(String[] args) {
        Developer d = new Developer(51, "Arush", "Java");
        Tester t = new Tester(46, "Mohit", "Selenium");

        d.displayDetails();
        t.displayDetails();
    }
}
```

### Key Points

* One parent, many children
* Very common in real projects
* Promotes reusability

---

## 3️⃣ Multilevel Inheritance

### Definition

A class is derived from another **derived class**.

### Structure

```
Grandparent → Parent → Child
```

### Example

```java
class SeniorDeveloper extends Developer {
    int experience;

    SeniorDeveloper(int id, String name, String lang, int exp) {
        super(id, name, lang);
        this.experience = exp;
    }

    void designSystem() {
        System.out.println(name + " is designing system");
    }
}
```

```java
public class MultiLevelInheritance {
    public static void main(String[] args) {
        SeniorDeveloper sd = new SeniorDeveloper(121, "Ravindra", "Java", 4);
        sd.displayDetails();
        sd.writeCode();
        sd.designSystem();
    }
}
```

### Key Points

* Chain of inheritance
* `super()` is very important
* Overuse can make code complex

---

## 4️⃣ Multiple Inheritance (Using Interfaces)

### ❌ Why Java Does NOT Support Multiple Inheritance with Classes?

To avoid the **Diamond Problem**:

```
      A
     / \
    B   C
     \ /
      D
```

👉 Ambiguity: Which method should D inherit?

### ✅ Solution: Interfaces

### Interfaces Used

```java
interface CodeReview {
    int REVIEW_SCORE = 10;
    void review();
    void refactorCode();
}

interface TestReview {
    String TOOL = "Selenium";
    void review();
    void automateTesting();
}
```

### Example

```java
class QualityEngineer implements CodeReview, TestReview {
    String name;

    QualityEngineer(String name) {
        this.name = name;
    }

    public void review() {
        System.out.println("Reviewing code and tests");
    }

    public void refactorCode() {
        System.out.println("Refactoring code");
    }

    public void automateTesting() {
        System.out.println("Automating tests using " + TOOL);
    }
}
```

```java
public class MultipleInheritance {
    public static void main(String[] args) {
        QualityEngineer qe = new QualityEngineer("Rupak");
        qe.review();
        qe.refactorCode();
        qe.automateTesting();
    }
}
```

### Key Points (Very Important ⭐)

* Java supports **multiple inheritance ONLY via interfaces**
* Methods must be implemented
* Constants are `public static final` by default

---

## 5️⃣ Hybrid Inheritance

### Definition

A **combination of multiple inheritance types**.

> Java supports hybrid inheritance **using interfaces only**.

### Example

```java
class TechLead extends SeniorDeveloper implements TestReview, CodeReview {

    TechLead(int id, String name, String lang, int exp) {
        super(id, name, lang, exp);
    }

    public void review() {
        System.out.println(name + " is reviewing...");
    }

    public void automateTesting() {
        System.out.println(name + " is automating tests using " + TOOL);
    }

    public void refactorCode() {
        System.out.println(name + " is refactoring...");
    }
}
```

```java
public class HybridInheritance {
    public static void main(String[] args) {
        TechLead tl = new TechLead(58, "Amit", "Java", 10);
        tl.writeCode();
        tl.review();
        tl.automateTesting();
    }
}
```

### Key Points

* Class + multiple interfaces
* Very powerful design
* Common in enterprise applications

---

## 🔥 Most Confusing Points (Exam & Interview Focus)

✔ `extends` → class to class
✔ `implements` → class to interface
✔ Interfaces can have **same method names**
✔ Class constructor is called **top → bottom**
✔ Java avoids ambiguity using interfaces

---

## ✅ Summary Table

| Type         | Supported in Java | How                       |
| ------------ | ----------------- | ------------------------- |
| Single       | ✅                 | Class → Class             |
| Multilevel   | ✅                 | Class chain               |
| Hierarchical | ✅                 | One parent, many children |
| Multiple     | ❌ (classes)       | ✅ via interfaces          |
| Hybrid       | ❌ (classes)       | ✅ via interfaces          |

---

