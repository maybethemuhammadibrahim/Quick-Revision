### **Notes on Object-Oriented Programming (OOP) Concepts**

---

#### 1. **Instantiating Classes** (r)

- **Explanation**: Creating an object of a class to use its members (attributes and methods).
- **Syntax**:
    
    ```cpp
    ClassName objectName;
    ```
    
- **Example**:
    
    ```cpp
    class Car {
    public:
        void start() {
            cout << "Car started!" << endl;
        }
    };
    
    int main() {
        Car myCar;       // Instantiating the class
        myCar.start();   // Accessing a class method
        return 0;
    }
    ```
    

---

#### 2. **Setters and Getters** (r)

- **Explanation**: Methods used to update (set) and retrieve (get) private data members safely.
- **Syntax**:
    
    ```cpp
    void setVariable(DataType value);
    DataType getVariable();
    ```
    
- **Example**:
    
    ```cpp
    class Person {
    private:
        string name;
    public:
        void setName(string n) {
            name = n;
        }
        string getName() {
            return name;
        }
    };
    
    int main() {
        Person p;
        p.setName("John");          // Set value
        cout << p.getName();        // Get value
        return 0;
    }
    ```
    

---

#### 3. **Inline Functions** (r)

- **Explanation**: Small functions defined inside the class, replacing function calls to save overhead.
- **Syntax**:
    
    ```cpp
    inline returnType functionName() { ... }
    ```
    
- **Example**:
    
    ```cpp
    class Calculator {
    public:
        inline int add(int a, int b) {
            return a + b;
        }
    };
    
    int main() {
        Calculator calc;
        cout << calc.add(3, 4); // Output: 7
        return 0;
    }
    ```
    

---

#### 4. **Encapsulation** (r)

- **Explanation**: Bundling data (attributes) and methods into a class and controlling access via access specifiers.
- **Syntax**:
    
    ```cpp
    private:
        // Private data
    public:
        // Public methods
    ```
    
- **Example**:
    
    ```cpp
    class Box {
    private:
        int length;
    public:
        void setLength(int l) { length = l; }
        int getLength() { return length; }
    };
    
    int main() {
        Box b;
        b.setLength(10);
        cout << b.getLength(); // Output: 10
        return 0;
    }
    ```
    

---

#### 5. **Constructors**

- **Explanation**: Special methods used to initialize objects automatically when created.
- **Syntax**:
    
    ```cpp
    ClassName(parameters) { ... }
    ```
    
- **Example**:
    
    ```cpp
    class Car {
    public:
        string brand;
    
        // Constructor
        Car(string b) {
            brand = b;
        }
    };
    
    int main() {
        Car myCar("Toyota");
        cout << myCar.brand; // Output: Toyota
        return 0;
    }
    ```
    

---

#### 6. **Inheritance**

- **Explanation**: A class (child) inherits properties and methods of another class (parent).
- **Syntax**:
    
    ```cpp
    class Child : accessSpecifier Parent { ... };
    ```
    
- **Example**:
    
    ```cpp
    class Animal {
    public:
        void eat() { cout << "This animal eats food." << endl; }
    };
    
    class Dog : public Animal {
    public:
        void bark() { cout << "Dog barks!" << endl; }
    };
    
    int main() {
        Dog d;
        d.eat();  // Inherited method
        d.bark(); // Child-specific method
        return 0;
    }
    ```
    

---

#### 7. **Accessing Private Data Members of Parent from Child**

- **Explanation**: Private members can’t be accessed directly in the child but can be indirectly accessed through public or `protected` members of the parent class.
- **Syntax**:
    
    ```cpp
    class Parent {
    protected:
        int data;
    };
    ```
    
- **Example**:
    
    ```cpp
    class Parent {
    protected:
        int value;
    public:
        Parent() : value(100) {}
    };
    
    class Child : public Parent {
    public:
        void showValue() {
            cout << "Value: " << value << endl; // Accessing protected member
        }
    };
    
    int main() {
        Child c;
        c.showValue(); // Output: Value: 100
        return 0;
    }
    ```
    

---

#### 8. **Polymorphism**

- **Explanation**: Using a parent class pointer to call child class methods at runtime (dynamic binding).
- **Syntax**:
    
    ```cpp
    class Parent { virtual void func() { ... } };
    ```
    
- **Example**:
    
    ```cpp
    class Parent {
    public:
        virtual void display() {
            cout << "Parent display" << endl;
        }
    };
    
    class Child : public Parent {
    public:
        void display() override {
            cout << "Child display" << endl;
        }
    };
    
    int main() {
        Parent* ptr;
        Child c;
        ptr = &c;
        ptr->display(); // Output: Child display
        return 0;
    }
    ```
    

---

#### 9. **Abstraction**

- **Explanation**: Hiding implementation details and showing only essential features to the user. Achieved using **abstract classes** with pure virtual functions.
- **Syntax**:
    
    ```cpp
    class AbstractClass {
        virtual void func() = 0; // Pure virtual function
    };
    ```
    
- **Example**:
    
    ```cpp
    class Shape {
    public:
        virtual void draw() = 0; // Pure virtual function
    };
    
    class Circle : public Shape {
    public:
        void draw() {
            cout << "Drawing Circle" << endl;
        }
    };
    
    int main() {
        Shape* shape = new Circle();
        shape->draw(); // Output: Drawing Circle
        delete shape;
        return 0;
    }
    ```