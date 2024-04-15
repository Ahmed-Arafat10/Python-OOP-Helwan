- Practice Example #1

````python
class Animal:
        # user-defined constructor
    def __init__(self,name :str):
        self.name = name
    
    def sound(self):
        print("Animal Sound")
    
    def printName(self):
        print("Animal Name " + self.name)


class Dog(Animal):
   
    def __init__(self, name: str,age :int):
        super().__init__(name) # calling super class constructor 
        self.age = age

    def printText(self):
        super().printName()
        print("Hello")



dog = Dog("lolo",3);
dog.printText()
dog.printName()
````

- Practice Example #2

````python
class Human:
def __init__(self, name, email):
print("Human Constructor")
self.name = name
self._email = email

    def sleeping(self):
        print("I am sleeping now")


class Employee(Human):
def __init__(self, name, personal_email, work_email, department, salary):
super().__init__(name, personal_email)
print("Employee Constructor")
self.work_email = work_email
self.department = department
self.salary = salary

    def print_personal_email(self):
        print("My Personal Email is:", self._email)

    def print_formal_email(self):
        print("My Formal Email is:", self.work_email)


class Manager(Employee):
def __init__(self, name, personal_email, work_email, department, salary):
super().__init__(name, personal_email, work_email, department, salary)
print("Manager Constructor")
self.managing_team = None

    def get_managing_team(self):
        return self.managing_team

    def set_managing_team(self, managing_team):
        self.managing_team = managing_team

    def get_salary(self):
        return self.salary


arafat = Manager(
"ahmed arafat",
"ahmed@gmail.com",
"ahmed@cic-cairo.com",
"IT",
1000
)
arafat.set_managing_team("Back-End")
arafat.print_personal_email()
arafat.print_formal_email()
print(arafat.get_salary())
print(arafat.get_managing_team())
print(arafat.name)
print(arafat._email)
````