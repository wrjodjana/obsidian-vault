
**Definition**: a way of organizing code that uses objects and classes to represent real-world entities and their behavior

### Classes

**Definition**: a collection of objects, sometimes known as blueprints of objects. It defines a set of attributes and methods that created objects (instances) have

**Example:**
```Python
class Dog:
	species = "Canine"
	
	def __init__(self, name, age):
		self.name = name
		self.age = age
```

**Explanation:**
- `class Dog`: defines a class named dog
- `species:` class attribute
- `__init__ method`: initializes the name and age attributes when a new object is created

### Objects

**Definition:** an object is an instance of a class and represents an implementation of that class and hold its own data

**Example:**
```Python
dog1 = Dog("Buddy", 3)
print(dog1.name) # prints "Buddy"
print(dog1.species) # prints "Canine"
```

**Explanation:**
- `dog1 = Dog("Buddy", 3)`: creates an object of the Dog class with name as "Buddy" and age 3
- `dog1.name`: accesses the instance attribute name of the `dog1` object
- `dog1.species`: accesses the class attribute species of the `dog1` object

#### Self Parameter: 
- reference to the current instance of the class, allowing us to access the attributes and methods of the object
- `self.name`: refers to the name attribute of the object (dog1) calling the method

#### Constructor
- `__init__` method is also the constructor, where a new object is created
- `self.name` and `self.age` are instance attributes initialized in the constructor

#### Class and Instance Variables
- **Class variables:** shared by all instances of the class. If you change `Dog.species` it affects all objects, as it's a property of the class.
- **Instance variables**: defined by the constructor which is unique to each instance meaning that `dog1.name` and `dog2.name` is different
- **Accessing variables**: can be accessed via class name, `Dog.species`, or an object, `dog1.species`. Instance variables are acce