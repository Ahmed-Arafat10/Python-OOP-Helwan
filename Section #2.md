- Example #1

````python
class Human:
    # Default Constructor
    def __init__(self):
        self.name = "Ahmed Arafat";
        self.age = 24;
        self.gender = "Male";
    
    def myName(self):
        return "My Name is " + self.name
    

arafat = Human();
print(arafat.name) # Ahmed Arafat
print(arafat.age) # 24
print(arafat.gender) # Male
print(arafat.myName()) # My Name is Ahmed Arafat
print(arafat.myName) # <bound method Human.myName of <__main__.Human object at 0x000001F675B361B0>>
````


- Example #2:

````python
class Human:
    # Parameterized constructor
    def __init__(self,name,age,gender):
        self.name = name;
        self.age = age;
        self.gender = gender;
    
    def myName(self):
        return "My Name is " + self.name
    
    def myAge(self):
        return "My Age is " + str(self.age) # str() to convert age into string
    
    def myGender(self):
        return "My Gender is " + self.gender
    

# ahmed = Human("Ahmed") # Error: TypeError: Human.__init__() missing 2 required positional arguments: 'age', and 'gender'


ahmed = Human("Ahmed",24,"Male") # Correct

print(ahmed.myName()) # My Name is Ahmed
print(ahmed.myAge()) # My Age is 24
print(ahmed.myGender()) # My Gender is Male

salma = Human("Salma",22,"Female")

print(salma.myName()) # My Name is Salma
print(salma.myAge()) # My Age is 22
print(salma.myGender()) # My Gender is Female
````


Example #3

````python
class Dog:
    # Parameterized constructor
    def __init__(self,name):
        self.name = name;
    
    def myName(self): # void method (not returning a value)
        print("My Name is " + self.name) 
    

myDog = Dog("Golden")

print(myDog.myName()) # My Name is Golden    then prints   None
````


> Note: Be careful while writing in python, lines should be correctly intended (use tab button)