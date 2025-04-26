
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
- `dog1 = `