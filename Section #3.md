- class variable vs instance variable
- add default value to a parameter
- add data type for parameter
- print(Company().productivity()) # anonymous object. 

````python
class Animal:
    count = 0 # class variable
    
    def __init__(self,name):
        self.name = name # instance variable
        Animal.count = Animal.count + 1;
    
    def printAnimalName(self):
        return self.name


# obejct 1
dog = Animal("loka")

print(dog.count) # 1
print(Animal.count) # 1

dog.count = 10;

# print(dog.count) # 10
# print(Animal.count) # 1

bird = Animal("Lolo")

# print(Animal.count) # 2
# print(bird.count) # 2

print(dog.printAnimalName())

print(bird.age) # 'Animal' object has no attribute 'age'
````

- Practice Example #1

````python
class Rectangle:
    count = 0
    def __init__(self,w,l):
        self.width = w
        self.length = l
        Rectangle.count = Rectangle.count + 1;

    def getArea(self):
        return self.width * self.length
    
    def getPerimeter(self):
        return 2 * (self.width + self.length)
    

R1 = Rectangle(5,5)

R2 = Rectangle(225,225)

print(R1.getArea())
print(R1.getPerimeter())

print(R2.getArea())
print(R2.getPerimeter())

print(Rectangle.count)
````


- Practice Example #2

````python
class Circle:
    count = 0
    PI = 3.14
    def __init__(self,r):
        self.radius = r
        Circle.count = Circle.count + 1;

    def getArea(self):
        return Circle.PI * self.radius * self.radius
    
    def getCircumference (self):
        return 2 * Circle.PI * self.radius
    

circle1 = Circle(55)

circle2 = Circle(99)

print(circle1.getArea())


print(circle2.getCircumference())
````


- Practice Example #3

````python
class Calculator:
    count = 0
    def __init__(self,n1,n2,sign):
        self.n1 = n1
        self.n2 = n2
        self.sign = sign 
        Calculator.count = Calculator.count + 1;

    def calculate(self):
        if self.sign == "+":
            return self.sum()
        
        elif self.sign == "-":
            return self.sub()
        
        elif self.sign == "*":
            return self.multi()
        
        elif self.sign == "/":
            return self.div()

        else:
            return "Operator is not valid"


    def sum(self):
        return self.n1 + self.n2
    

    def sub(self):
        return self.n1 - self.n2
    

    def div(self):
        if self.n2 == 0:
            return "Cannot devided by 0"
        
        return self.n1 / self.n2
    

    def multi(self):
        return self.n1 * self.n2
    

n1 = int(input("Please Enter First Number \n"))
n2 = int(input("Please Enter Second Number \n"))
operator = input("Please Enter Operator \n")


myCalc = Calculator(n1,n2,operator)

print(myCalc.calculate())

print(Calculator.count)
````