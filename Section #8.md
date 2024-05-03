Task: Write a Python script to model a simple zoo system using object-oriented programming concepts.
 
Step 1: Define Custom Exception Class
1. Begin by defining a custom exception class named AnimalNotFoundError.
2. Implement the __init__ method to initialize the exception with the name of the animal not found.
3. Override the __str__ method to return a formatted error message.
 
Step 2: Define Animal Classes
1. Create a base class named Animal.
2. Implement the __init__ method to initialize each animal with a name and age.
3. Define getter methods get_name() and get_age() to retrieve the name and age of an animal.
4. Define the make_sound() method as a placeholder method for producing animal sounds.
5. Implement the info() method to return information about the animal (name and age).
 
Step 3: Define Subclasses
1. Create subclasses Dog and Cat inheriting from the Animal class.
2. Implement the __init__ method for each subclass to initialize additional attributes (breed for Dog and color for Cat).
3. Define getter methods get_breed() for Dog and get_color() for Cat to retrieve specific attributes.
4. Override the make_sound() method in each subclass to produce the appropriate sound for the animal.
5. Override the info() method in each subclass to include additional information specific to the animal type.
 
Step 4: Define Zoo Class
1. Create a class named Zoo to manage the animals in the zoo.
2. Implement the __init__ method to initialize an empty list to store animals.
3. Define an add_animal() method to add an animal to the zoo.
4. Implement two overloaded get_animal_by_name() methods using the multipledispatch decorator:
   - One method takes a string parameter to search for an animal by name.
   - Another method takes an object parameter to search for an animal by object reference.
5. Implement make_sound_generic() and print_info_generic() methods to iterate over all animals and print their sounds and information.
 
Step 5: Define Duck Typing Function
1. Define a function named print_obj_data() to demonstrate duck typing.
2. This function takes an object as a parameter and calls the make_sound() and info() methods of the object.
 
Step 6: Main Execution
1. Inside the if __name__ == "__main__": block:
   - Create instances of Dog and Cat.
   - Create a Zoo instance and add the animals to the zoo.
   - Call the make_sound_generic() and print_info_generic() methods of the zoo.
   - Demonstrate polymorphism by using the get_animal_by_name() method to retrieve animals by name and object reference.
   - Print the sound and information of the retrieved animals using the print_obj_data() function.
   - Handle AnimalNotFoundError exceptions if an animal is not found in the zoo.
 
> Note: By following these steps, students can create a Python script that models a simple zoo system using object-oriented programming principles and demonstrate their understanding of concepts such as inheritance, polymorphism, dynamic binding, and exception handling.


- Solution:

````python
from multipledispatch import dispatch


class AnimalNotFoundError(Exception):
    def init(self, name):
        self.name = name

    def str(self):
        return f"Animal '{self.name}' not found in the zoo."

class Animal:
    def init(self, name, age):
        self._name = name
        self._age = age

    def get_name(self):
        return self._name

    def get_age(self):
        return self._age

    def make_sound(self):
        pass

    def info(self):
        return f"{self._name} is {self._age} years old."

class Dog(Animal):
    def init(self, name, age, breed):
        super().init(name, age)
        self._breed = breed

    def get_breed(self):
        return str.upper(self._breed)

    def make_sound(self):
        return "Woof!"

    def info(self):
        return f"{super().info()} He is a {self._breed}."

class Cat(Animal):
    def init(self, name, age, color):
        super().init(name, age)
        self._color = color

    def get_color(self):
        return self._color

    def make_sound(self):
        return "Meow!"

    def info(self):
        return f"{super().info()} She has {self._color} fur."

class Zoo:
    def init(self):
        self._animals = []

    def add_animal(self, animal):
        self._animals.append(animal)

    @dispatch(str)
    def get_animal_by_name(self, name):
        for animal in self._animals:
            if animal.get_name() == name:
                return animal
        return None

    @dispatch(object)
    def get_animal_by_name(self, animal_obj):
        return self.get_animal_by_name(animal_obj.get_name())

    def make_sound_generic(self):
        for animal in self._animals:
            print(animal.make_sound())

    def print_info_generic(self):
        for animal in self._animals:
            print(animal.info())


def print_obj_data(obj):
    print("duck typing function start")
    print(obj.make_sound())
    print(obj.info())
    print("duck typing function end")

if name == "main":
    dog = Dog("Buddy", 5, "Labrador")
    cat = Cat("Whiskers", 3, "White")

    zoo = Zoo()
    zoo.add_animal(dog)
    zoo.add_animal(cat)

    zoo.make_sound_generic();

    zoo.print_info_generic();

    print(zoo.get_animal_by_name("Buddy")) # address of object, first overloaded method

    print(zoo.get_animal_by_name(dog)) # address of object, second overloaded method



    print(zoo.get_animal_by_name("Buddy").get_age()) # 5 , as it returns object (dog) then call get_age() method inside it

    print(zoo.get_animal_by_name("Buddy123")) # None

    # note: we have passed an anonymous object (refer polymorphism section)
    print(zoo.get_animal_by_name(Cat("Whiskers12345", 3, "White"))) # None, as 'Whiskers12345' name is not found

    # Polymorphism with string parameter
    animal_object_copy = zoo.get_animal_by_name("Buddy")
    if animal_object_copy:
        print_obj_data(animal_object_copy)
    else:
        raise AnimalNotFoundError("Object Not Found 1")

    # Polymorphism with object parameter
    animal_obj = zoo.get_animal_by_name(cat)
    if animal_obj:
        print_obj_data(animal_obj)
    else:
        raise AnimalNotFoundError("Object Not Found 2")
````
