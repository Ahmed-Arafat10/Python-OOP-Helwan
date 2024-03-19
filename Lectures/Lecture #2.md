- Example #1

````python
class Addition:
    def __init__(self,num1,num2):
        self.num1 = num1
        self.num2 = num2

    def add(self):
        return self.num1 + self.num2
    
obj = Addition(1,2)
print(obj.add())
````

- Example #2

````python
class Car:
    wheels = 4
    engine = "electric"
    def __init__(self,maker,model,year,color):
        self.maker = maker
        self.model = model
        self.year = year
        self.color = color

obj = Car("BMW","X6","2020","Black")
````



- Example #3

````python
class Dog:
    def __init__(self,name,age):
        self.name = name
        self.age = age

myDog = Dog("Willie",6)
print(f"My dog's name is {myDog.name}.")
print(f"My dog's name is {myDog.age} years old.")
````




- Example #4

````python
class Dog:
    def __init__(self,name,age):
        self.name = name
        self.age = age

    def sit(self):
        print(f"{self.name} is now sitting.")
    
    def roll_over(self):
        print(f"{self.name} is rolled over.")

myDog = Dog("Willie",6)
print(f"My dog's name is {myDog.name}.")
print(f"My dog's name is {myDog.age} years old.")
print(myDog.sit())
print(myDog.roll_over())
````




- Example #5

````python
class MainClass:

    def first(self):
        print("first() function call")
    
    def second(self):
        self.first()
        print("second() function call")

class_instance = MainClass()
class_instance.second()
````




- Example #6

````python
class Person:
    def __init__(self,name,id):
        self.name = name
        self.id = id

    def sayHello(self):
        print("Hello! my name is " + self.name)

p1 = Person("Dan",1234)
p1.sayHello()
````



- Example #7

````python
class Person:
    def __init__(self,name,age):
        self.name = name
        self.age = age

p1 = Person("Dan",1234)
print(p1) # <__main__.Person object at 0x000001D9C2CA5DF0>   
````



- Example #8

````python
class Person:
    def __init__(self,name,age):
        self.name = name
        self.age = age

    def __str__(self):
        return f"{self.name} ({self.age})";

p1 = Person("Dan",1234)
print(p1) # Dan (1234)
````



- Example #9

````python
class Employee:
    def __init__(self,name,age):
        self.name = name
        self.age = age

    def myFunc(self):
        print("Hello my name is" + self.name);

emp1 = Employee("Jack",31)

print(emp1.age)
emp1.age = 40
print(emp1.age)
````

- Example #10

````python
class Car:
    def __init__(self,maker,model,year):
        self.maker = maker
        self.model = model
        self.year = year

    def get_descriptive_name(self):
        long_name = f"{self.maker}-{self.model}-{self.year}"
        return long_name.title() # capitalize first character of each word
    
my_new_car = Car('bmw','a4',2019)

print(my_new_car.get_descriptive_name())

my_new_car.maker = 'skoda'
my_new_car.model = 'octavia a8'
my_new_car.year = 2022

print(my_new_car.get_descriptive_name())
````
