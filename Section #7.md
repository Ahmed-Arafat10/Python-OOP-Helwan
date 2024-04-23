## Topics 
- Method Overloading (two ways)
- Method Overriding (Shape/Circle/Rectangle Example)
- Dynamic Binding
- Duck Typing
- Anonymous Object
- Is-A vs Has-A Relationship
- Intro To Abstraction

### Method Overloading 
- Method #1 (Not Recommended)
````python
class Calculator:
    def sum(self,a = None,b = None,c = None):
        if a != None and b != None and c == None:
            return a + b
        elif a != None and b != None and c != None:
            return a + b + c

cal = Calculator() 
print(cal.sum(1,2,3))
print(cal.sum(1,2))
````

- Method #2
````python
#pip install multipledispatch
from multipledispatch import dispatch
class Calculator:
    @dispatch(int,float)
    def sum(self,a,b):
            print("@dispatch(int,float)")
            return a + b
    
    @dispatch(float,int)
    def sum(self,a,b):
            print("@dispatch(float,int)")
            return a + b



cal = Calculator() 
print(cal.sum(1.1,1))
````
> Dont forget to install multipledispatch `pip install multipledispatch`



### Method Overriding
````python
class Shape:
    def area(self):
        print('area() method from Shape Class')
    
    def perimeter(self):
        print('perimeter() method from Shape Class')

class Circle(Shape):
    PI = 3.14
    def __init__(self,radius):
        super().__init__()
        self.radius = radius

    def area(self):
        print(Circle.PI * self.radius * self.radius)

    def perimeter(self):
        print(Circle.PI * self.radius * 2)


class Rectangle(Shape):

    def __init__(self,length,width):
        super().__init__()
        self.length = length
        self.width = width

    def area(self):
        print(self.width * self.length)

    def perimeter(self):
        print(2 * (self.width + self.length))


myCir = Circle(5);
myRec = Rectangle(5,5);

myCir.area()
myCir.perimeter()

myRec.area()
myRec.perimeter()

````

### Dynamic Binding
````python
shapes = [Circle(5),Rectangle(5,5)]

for shape in shapes:
    shape.area() # dynamic binding
````


### Duck Typing
````python
def print_area(obj):  # duck typing
    obj.area()
    
shapes = [Circle(5),Rectangle(5,5)]

for shape in shapes:
    shape.area() # dynamic binding
````


### Anonymous Object
````python
def print_area(obj):  # duck typing
    obj.area()

print_area(Circle(5)) # anonymous object
````
