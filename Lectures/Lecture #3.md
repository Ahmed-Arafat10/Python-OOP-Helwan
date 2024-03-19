- Example #1

````python
class Car:
    year = 2016
    mpg = 20
    speed = 100
    def accelerate(self):
        return Car.speed + 20
    
    def brake(self):
        return Car.speed - 50
    
car1 = Car()
print(car1.accelerate())
print(car1.brake())
print(car1.year())
print(car1.mpg())
print(car1.speed())
````


- Example #2

````python
class Company:
    name = "CIB"
    turnover = 5000
    revenue = 1000
    no_of_employees = 100
    def productivity(self):
        return Company.revenue / Company.no_of_employees
    
    def brake(self):
        return Car.speed - 50

print(Company.name)
print(Company.turnover)
print(Company.revenue )
print(Company().productivity()) # anonymous object. 
````

- Example #3

````python
class Dog:
    def __init__(self, name: str, age: float , breed: str, weight: int):
        self.name = name
        self.age = age
        self.breed = breed
        self.weight = weight
    
    def bark(self):
        return f'{self.name} goes bark!'
    
    def isPupy(self):
        if self.age <= 1:
            return f'{self.name} is a puppy!'
        else:
            return f'{self.name} is not puppy!'
        
    def size(self):
        if self.weight <= 30:
            return f'{self.name} is a small dog!'
        
        elif self.weight > 30 and self.weight <= 60:
            return f'{self.name} is a medium dog!'
        
        else:
            return f'{self.name} is a big dog!'
        
charlie = Dog('Charlie',1,'Golden',30)

print(charlie.bark())
print(charlie.isPupy())
print(charlie.size())
````