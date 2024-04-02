- Practice Example #1

**Bank Account Management System**
You are tasked with creating a simple bank account management system. Below are the requirements:

1. Create a class named `BankAccount`.
2. The class should have a constructor (`__init__`) method that accepts a string parameter representing the account holder's name (`n`). Initialize the account balance (`__balance`) to 0.
3. Implement a method named `setBalance()` to set the balance of the account. If the provided balance is negative, print a message indicating that the balance cannot be less than 0.
4. Implement a method named `deposit()` to deposit an amount (`b`) into the account. If the deposited amount is greater than or equal to 10,000, print a message indicating that the balance cannot exceed 10,000 LE. If the amount is negative or zero, print a corresponding message.
5. Implement a method named `withdraw()` to withdraw an amount (`b`) from the account. If the account balance is less than the withdrawal amount, print a message indicating that the withdrawal cannot be completed due to insufficient funds. If the withdrawal amount is greater than or equal to 5,000, print a message indicating that such large withdrawals are not allowed. If the amount is negative or zero, print a corresponding message.
6. Implement a method named `getBalance()` to return the current balance of the account after deducting 10% as taxes.
7. Implement a method named `getUsername()` to return a string consisting of the account holder's name followed by '@' and their current balance.

Ensure that the account balance and the account holder's name are private attributes (using double underscores `__`).


- Solution:
````python
class BankAccount:
    def __init__(self,n: str):
        self.__name = n
        self.__balance = 0
    
    def setBalance(self,b):
        if b < 0:
            print('Balance cannot be less than 0')
        else:
            self.__balance = b

    def deposite(self,b):
        if b >= 10000:    
            print('Balance cannot be more than 10,000 LE')
        elif b <= 0:
            print('Balance cannot be less than or equal 0')
        else:
            self.__balance = self.__balance + b
            print(f'your Balance now after depositing {b}LE is {self.__balance}LE')

    def withdraw(self,b):
        if self.__balance < b:
            print(f'You cannot withdraw {b}LE as you only have {self.__balance}LE in your account')
        elif b >= 5000:
            print(f'You are not allowed to withdraw {b}LE')
        elif b <= 0:
            print('Balance cannot be less than or equal 0')
        else:
            self.__balance = self.__balance - b
            print(f'your Balance now after withdrawing {b}LE is {self.__balance}LE')

    def getBalance(self):
        return f'your balance after 10% taxes is {self.__balance - (self.__balance * 0.1)}LE'
    
    def getUsername(self):
        return self.__name + '@' + str(self.__balance)


arafat = BankAccount("Ahmed")

arafat.setBalance(-100)

arafat.setBalance(1000)

arafat.withdraw(9000)

arafat.withdraw(1000)


arafat.deposite(100000)
arafat.deposite(0)

arafat.deposite(5000)

arafat.withdraw(1000)
print(arafat.getBalance())
print(arafat.getUsername())
````
