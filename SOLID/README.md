# SOLID Principles
SOLID is an acronym for five object-oriented design principles that help create maintainable, scalable, and flexible software.

## Single Responsibility Principle
A class should have only one reason or purpose to serve. It means the class should have only one responsibility. For Example:
User class should not send email :x:
```
class User {
    private $name;
    public function sendWelcomeEmail();
}
```
We will have to create separate class to have single responsibility :white_check_mark:
```
class User {
    private $name;
}
class EmailService {
    public function sendWelcomeEmail(User $user) {
        echo "Sending welcome email to {$user->getEmail()}\n";
    }
}
```

## Open-Close Principle
Instances should be open for extension but closed for modification. This mean instances (classes,functions,modules or etc.,) can be extendable by another instance but shouldn't allow direct modification to them. For Example:
Adding new shape here will require modification in the function :x:
```
class AreaCalculator {
    public function calculate($shape) {
        if ($shape['type'] == 'rectangle') {
            return $shape['width'] * $shape['height'];
        } elseif ($shape['type'] == 'circle') {
            return pi() * pow($shape['radius'], 2);
        }
        // Adding a new shape requires modifying this class
    }
}
```
We will create interface for area calculation and classes for shapes. Now to add shape we will create new shape and we dont have to change area calculator :white_check_mark:
```
interface Shape {
    public function area();
}

class Rectangle implements Shape {
    public function area();
}

class Circle implements Shape {
    public function area();
}

class Triangle implements Shape {
    public function area();
}

class AreaCalculator {
    public function calculate(Shape $shape) {
        return $shape->area();
    }
}

// Usage
$calculator = new AreaCalculator();
$rectangle = new Rectangle();
$circle = new Circle();
echo $calculator->calculate($rectangle);
echo $calculator->calculate($circle);
```

## Liskov Substitution Principle
This mean that objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program. For Example:
Penguin can't fly so `makeBirdFly()` will not work for it :x:
```
class Bird {
    public function fly();
}
class Penguin extends Bird {
    // Can't fly so no fly method
}
function makeBirdFly(Bird $bird) {
    return $bird->fly(); // This will break with Penguin
}
```
We will create new classes and create abstract class for bird to fix this issue :white_check_mark:
```
abstract class Bird {
    abstract public function move();
}
class FlyingBird extends Bird {
    public function move();
}
class Sparrow extends FlyingBird {
    // Can use parent's move() method
}
class NonFlyingBird extends Bird {
    public function move();
}
class Penguin extends NonFlyingBird {
    public function move();
}
function makeBirdMove(Bird $bird) {
    return $bird->move(); // Works for all birds
}

// Usage
$sparrow = new Sparrow();
$penguin = new Penguin();
echo makeBirdMove($sparrow);
echo makeBirdMove($penguin);
```

## Interface Segregation Principle
We shouldn't force the instances to implement the interfaces that they don't use. We should make the interface flexible for most cases. For Example:
Robots should not have `eat` or `sleep` function :x:
```
interface Worker {
    public function work();
    public function eat();
}

class HumanWorker implements Worker {
    public function work() { /* ... */ }
    public function eat() { /* ... */ }
}

class RobotWorker implements Worker {
    public function work() { /* ... */ }
    public function eat(); // Robots don't eat
}
```
Create separate interfaces so child is not forced to implement a function which child dont need :white_check_mark:
```
interface Workable {
    public function work();
}

interface Eatable {
    public function eat();
}

class HumanWorker implements Workable, Eatable {
    public function work() { 
        echo "Human working\n";
    }
    public function eat() { 
        echo "Human eating\n";
    }
}

class RobotWorker implements Workable {
    public function work() { 
        echo "Robot working\n";
    }
}

// Usage
function manageWork(Workable $worker) {
    $worker->work();
}
function manageBreak(Eatable $eater) {
    $eater->eat();
}
$human = new HumanWorker();
$robot = new RobotWorker();
manageWork($human);  // "Human working"
manageWork($robot);  // "Robot working"
manageBreak($human); // "Human eating"
// manageBreak($robot); // Error: Robot doesn't implement Eatable
```

## Dependency Inversion Principle
This principle aims to decouple high-level modules (which provide complex functionality) from low-level modules (which provide basic functionality) by introducing an abstraction layer between them. This allows both high-level and low-level modules to depend on abstractions rather than on solid implementations, making the system more flexible, extensible, and maintainable. For Example:
UserService directly depends on MySQLDatabase class :x:
```
class MySQLDatabase {
    public function connect();
    public function query($sql);
}

class UserService {
    private $database;
    
    public function __construct() {
        $this->database = new MySQLDatabase(); // Tight coupling
    }
    public function getUsers();
}
```
We should have an interface of Database connection instead so Service depends on abstract class = :white_check_mark:
```
interface DatabaseConnection {
    public function connect();
    public function query($sql);
}

class MySQLDatabase implements DatabaseConnection {
    public function connect();
    public function query($sql);
}

class PostgreSQLDatabase implements DatabaseConnection {
    public function connect();
    public function query($sql);
}

class UserService {
    private $database;
    
    public function __construct(DatabaseConnection $database) {
        $this->database = $database; // Dependency injection
    }
    
    public function getUsers() {
        $this->database->connect();
        return $this->database->query("SELECT * FROM users");
    }
}

// Usage with dependency injection
$mysql = new MySQLDatabase();
$postgres = new PostgreSQLDatabase();

$userService1 = new UserService($mysql);
$userService2 = new UserService($postgres);

echo $userService1->getUsers(); // Uses MySQL
echo $userService2->getUsers(); // Uses PostgreSQL
```

## Benefits of SOLID Principles in PHP
* **Maintainability**: Easier to understand and modify code
* **Testability**: Classes are loosely coupled, easier to unit test
* **Flexibility**: Easy to extend functionality without breaking existing code
* **Reusability**: Components can be reused in different contexts
* **Reduced Complexity**: Each class has a single, well-defined responsibility
