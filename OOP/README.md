# Object Oriented Programming Notes

## Class
Blueprint of an object. Have **properties** (attributes) and **methods** (functions).
```
class Car {
    // Properties
    public $brand;
    
    // Method
    public function startEngine();
}
```

## Object
Instance of a Class. Have **properties** (attributes) and **methods** (functions).
```
$car1 = new Car();
$car1->brand = "Toyota";
```

## Constructor
`__construct()`: Method called when object is created.

## Destructor
`__destruct`: Method called when object is destroyed or script ends.

## Access Modifiers
* `public`: can be accessed from anywhere.
* `protected`: can be accessed within the class and the child classes.
* `private`: can only be accessed within the class.

## Inheritance
`extends`: When a class derives from another class
    
## Multiple Inheritance
Can be done by using 2 methods:
* traits
```
trait Logger {}

trait Notifier {}

class User {
    use Logger, Notifier;
}
```
* composition (Having class objects as properties but ensure dependency injection to fix tight coupling).
```
class LoggerService {}

class NotifierService {}

class Product {
    private LoggerService $logger;
    private NotifierService $notifier;

    public function __construct(LoggerService $logger, NotifierService $notifier) {
        $this->logger = $logger;
        $this->notifier = $notifier;
    }

    public function create(string $productName) {
        $this->logger->log("Product " . $productName . " created.");
        $this->notifier->sendNotification("New product: " . $productName);
    }
}
```

## Abstract Class
An abstract class is a class that contains at least one abstract method. An abstract method is a method that is declared, but not implemented in the code. Method can be protected or public.
```
abstract class Shape { 
    abstract public function calculateArea();
    abstract protected function calculatePerimeter();
    
    public function describe() {
        return "This is a shape";
    }
}
```
* The child class method must be defined with the same name and it redeclares the parent abstract method
* The child class method must be defined with the same or a less restricted access modifier like parent public should be public in chlid and parent protected can be protected or public in child.
* The number of required arguments must be the same. However, the child class may have optional arguments in addition

## Interfaces
Interfaces allow you to specify what methods a class should implement.
```
interface Loggable {
    public function log($message);
}
```
## Polymorphism
When one or more classes use the same interface. Having same method name with different functionalities.
```
<?php
interface PaymentMethod {
    public function processPayment($amount);
}

class CreditCardPayment implements PaymentMethod {
    public function processPayment($amount);
}

class PayPalPayment implements PaymentMethod {
    public function processPayment($amount);
}

class BankTransferPayment implements PaymentMethod {
    public function processPayment($amount);
}

class PaymentProcessor {
    public function handlePayment(PaymentMethod $paymentMethod, $amount) {
        return $paymentMethod->processPayment($amount);
    }
}
```

## Static Methods
* `static` Static methods can be called directly - without creating an instance of the class first.
* `self` To access static method in the same class.
* `parent` To access protected static method from child.
```
class MathOperations {
    public static $operationCount = 10;
    
    public static function add($a, $b) {
        self::$operationCount++;
        return $a + $b;
    }
}
```

## Abstraction
Showing only important details and hiding unnecessary things from user.

## Trait:
Traits are used to declare methods and/or properties that can be used in multiple classes. Traits can have methods and abstract methods that can be used in multiple classes, and the methods can have any access modifier.
```
trait LoggerTrait {
    protected $logs = [];
    
    public function log($message, $level = 'INFO');
}

```

## Final
The `final` keyword can be used to prevent class inheritance or prevent function overide.
```
final class Configuration
{
    final public function getConfiguration();
}
```

## Method Overriding
Inherited methods can be overridden by redefining the methods (use the same name) in the child class.

## Encapsulation:
Exposing only necessary information using public access modifier. Hiding sensitive details using protected and private access modifier.
