
**Definition**: a way of organizing code that uses objects and classes to represent real-world entities and their behavior.

### Classes

**Definition**: a collection of objects, sometimes known as blueprints of objects. It defines a set of attributes and methods that created objects (instances) have.

**Example:**
```Python
class Dog:
	species = "Canine"
	
	def __init__(self, name, age):
		self.name = name
		self.age = age
```

**Explanation:**
- `class Dog`: defines a class named dog.
- `species:` class attribute.
- `__init__ method`: initializes the name and age attributes when a new object is created.

### Objects

**Definition:** an object is an instance of a class and represents an implementation of that class and hold its own data.

**Example:**
```Python
dog1 = Dog("Buddy", 3)
print(dog1.name) # prints "Buddy"
print(dog1.species) # prints "Canine"
```

**Explanation:**
- `dog1 = Dog("Buddy", 3)`: creates an object of the Dog class with name as "Buddy" and age 3.
- `dog1.name`: accesses the instance attribute name of the `dog1` object.
- `dog1.species`: accesses the class attribute species of the `dog1` object.

#### Self Parameter: 
- reference to the current instance of the class, allowing us to access the attributes and methods of the object.
- `self.name`: refers to the name attribute of the object (dog1) calling the method.

#### Constructor
- `__init__` method is also the constructor, where a new object is created.
- `self.name` and `self.age` are instance attributes initialized in the constructor.

#### Class and Instance Variables
- **Class variables:** shared by all instances of the class. If you change `Dog.species` it affects all objects, as it's a property of the class.
- **Instance variables**: defined by the constructor which is unique to each instance meaning that `dog1.name` and `dog2.name` is different.
- **Accessing variables**: can be accessed via class name, `Dog.species`,or an object, `dog1.species`. Instance variables are accessed by objects, `dog1.name`.

### Inheritance

**Definition:** allows a child class to acquire the properties and methods of a parent class, supporting hierarchical classification and promotes code reusing

#### Single Inheritance

**Definition:** A child class inherits from a single parent class. `Labrador` inherits `Dog`'s attributes and methods.

**Example:**
```Python
class Dog:
	def __init__(self, name):
		self.name = name
	def display_name(self):
		print(f"Dog's name: {self.name}")

class Labrador(Dog):
	def sound(self):
		print("Labrador woofs")

lab = Labrador("Buddy")
lab.display_name() # prints Dog's name: Buddy
lab.sound() # prints Labrador woofs
```

#### Multilevel Inheritance

**Definition:** A child class inherits from a parent class, which inherits from another class. `GuideDog` extends `Labrador`, inheriting both `Dog` and `Labrador` functionalities

**Example:**
```Python
class GuideDog(Labrador):
	def guide(self):
		print(f"{self.name} guides the way!")

guide_dog = GuideDog("Max")
guide_dog.display_name() # prints Dog's name: Max
guide_dog.guide() # prints Max guides the way!
```


#### Multiple Inheritance

**Definition:** A child class inherits from more than one parent class. `GoldenRetriever` inherits from both `Dog` and `Friendly`.

**Example:**
```Python
class Friendly:
	def greet(self):
		print("Friendly")

class GoldenRetriever(Dog, Friendly):
	def sound(self):
		print("Golden Retriever Barks!")

retriever = GoldenRetriever("Charlie")
retriever.display_name() # prints Dog's name: Charlie
retriever.greet() # prints Friendly
retriever.sound() # prints Golden Retriever Barks!
```

### Polymorphism

**Definition:** allows methods to have the same name but behave differently based on the object's context. Achieved through method overriding or overloading.

**Default Implementation:**
```Python
class Dog:
	def sound(self):
		print("dog sound")
```
#### Run-time Polymorphism (Method overriding)

**Definition:** determined during the execution of the program. Occurs when a subclass provides a specific implementation for a method already defined in its parent class.

**Example:**
```Python
class Labrador(Dog):
	def sound(self):
		print("Labrador woofs")

class Beagle(Dog):
	def sound(self):
		print("Beagle barks")

dogs = [Dog(), Labrador(), Beagle()]
for dog in dogs:
	dog.sound() # Prints dog sound, Labrador woofs, Beagle barks
```

**Notes:**
- Using method overriding in the `Dog` class and its subclasses (`Labrador` and `Beagle`)
- Correct sound method is invoked at runtime based on the actual type of the object in the list
#### Compile-time Polymorphism (Method overloading)

**Definition:** determined during the compilation of the program. Allows methods or operators with the same name to behave differently based on their input parameters.

**Example:**
```Python
class Calculator:
	def add(self, a, b=0, c=0):
		return a + b + c

calc = Calculator()
print(calc.add(5, 10)) # prints 15
print(calc.add(5, 10, 15)) # prints 30
```

**Notes:**
- Python doesn't support method overloading. Instead use single method with default arguments to handle varying number of parameters
- Different behaviors are achieved based on how method is called

### Encapsulation

**Definition:** bundling of attributes and methods within a class, restricting access to some components to control interactions.

**Default Implementation:**
```Python
class Dog:
	def __init__(self, name):
		self.name = name
		self._breed = breed
		self.__age = age
	
	def get_info(self):
		return f"Name: {self.name}, Breed: {self._breed}, Age: {self.__age}"
```

#### Public Members

**Definition:** easily accessible, such as name.

**Example:**
```Python
dog = Dog("Buddy", "Labrador", 3)
print(dog.name) # prints "Buddy"
```

#### Protected Members

**Definition:** Used with a single `_`, such as `_breed`. Access is discouraged by allowed in subclasses

**Example:**
```Python
print(dog._breed) # prints "Labrador"
```

#### Private Members

**Definition:** Used with `__`, such as `__age`. Access requires setter and getter methods. Accessible only within the class.

**Example:**
```Python
class Dog:
	def get_age(self):
		return self.__age

	def set_age(self, age):
		if age > 0:
			self.__age = age
		else:
			print("Invalid age!")

print(dog.get_age()) # prints 3
dog.set_age(5) # age = 5
```

### Abstraction

**Definition:** hides the internal implementation details while exposing only the necessary functionality. Helps focus on "what to do" rather than "how to do it". Ensures consistency in derived classes by enforcing the implementation of abstract methods.


#### Full Abstraction

**Definition:** abstract class contains only abstract methods (like interfaces)

**Example:**
```Python
from abc import ABC, abstractmethod

class Dog(ABC):
	def __init__(self, name):
		self.name = name
	
	@abstractmethod
	def sound(self):
		pass
	
	@abstractmethod
	def display_name(self):
		pass
```

#### Partial Abstraction

**Definition:** abstract class contains both abstract and concrete methods. `Dog` class has both abstract (`sound`) and concrete (`display_name`) methods

**Example:**

```Python
from abc import ABC, abstractmethod

class Dog(ABC):
	def __init__(self, name):
		self.name = name

	@abstractmethod
	def sound(self):
		pass

	def display_name(self):
		print(f"Dog's name: {self.name}")
```

### Iterators

**Definition:** an object that holds a sequence of values and provide sequential traversal through a collection of items such as lists, dictionaries and tuples.

**Implementation:**
- initialized using the `iter()` method and uses the `next()` method for iteration

#### Iterator vs Iterable
- **Iterables:** objects that can return iterators, an iterable implements the`__iter__()` method, which expects to return an iterator object
- **Iterators:** objects that actually perform the iteration. They implement `__iter__()` and `__next__()` method. The `__iter()__` method returns the iterator object itself.

**Example:**
```Python
word = 'HEL'
it = iter(word)

print(next(it)) # H
print(next(it)) # E
print(next(it)) # L
```

#### Creating the iterator class

**Definition:**
1. Define the class: start by defining the class that will act as the iterator
2. Initialize attributes: initialize any attributes used in the iteration process in `__init__()`
3. Implement `__iter__()`: returns the iterator object itself, usually returning self
4. Implement `__next__()`: provides the next item in the sequence

**Example:** custom class `EvenNumbers`, iterates even numbers starting from 2

```Python
class EvenNumbers:
	def __iter__(self):
		self.n = 2
		return self

	def __next__(self):
		x = self.n
		self.n += 2
		return x
```

**Notes:**
- `__iter__()`: starts from the first even number, 2
- `__next__()`: increments by 2 to get the next even number

**Usage:**
```Python
even = EvenNumbers()
it = iter(even)

print(next(it)) # 2
print(next(it)) # 4
print(next(it)) # 6
print(next(it)) # 8
print(next(it)) # 10
``` 

#### `StopIteration` Exception

**Definition:** signals the iterator has no more items to return. Once exception is raised, further calls to `next()` on the same iterator will continue raising `StopIteration`.

**Example:**
```Python
li = [100, 200, 300]
it = iter(li)

while True:
	try:
		print(next(it)) # 100, 200, 300, End of Iteration
	except StopIteration:
		print("End of Iteration")
		break
```