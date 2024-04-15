### Practice Example #1

*Facebook Account Creation System*

*Objective*:  
Develop a Python program to manage the creation of Facebook accounts.

*Requirements*:

1. *Class Definition*:  
   - Create a class named Facebook to handle Facebook account operations.

2. *Initialization*:
   - Implement an __init__ method to initialize each account with a name, email, and password.
   - Increment the class variable numOfAcc to track the total number of accounts created.

3. *Email Validation*:
   - Implement the method is_email_valid to validate email addresses.
   - Ensure that the email contains exactly one '@' and one '.' character.

4. *Password Validation*:
   - Implement the method is_password_valid to validate passwords.
   - Passwords must meet the following criteria:
     - Minimum length of 8 characters.
     - At least one special character ('@' or '#').
     - At least one digit.
     - At least one uppercase letter.

5. *Password Encryption*:
   - Implement the encrypt method to encrypt passwords using a simple encryption algorithm.
     - Use the Caesar cipher algorithm, shifting each character by 3 positions.
   
6. *Set Email and Password*:
   - Implement the method set_email to set a valid email address for the account.
     - Continue prompting the user for input until a valid email is provided.
   - Implement the method set_password to set a valid password for the account, using the is_password_valid method for validation.
     - Continue prompting the user for input until a valid password is provided.

7. *Get Password*:
   - Implement the method get_password to retrieve the encrypted password.

8. *Login Authentication*:
   - Implement the method login to authenticate users based on their email and password.
   - Decrypt the provided password using the encrypt method and compare it with the stored encrypted password.
   - If authentication is successful, print a welcome message with the user's name. Otherwise, print a failure message.

9. *Sample Usage*:
   - Provide a sample usage demonstrating how to create an account, retrieve email and password, and authenticate using the login method.

10. *Code Quality*:
    - Ensure that the code is well-commented to explain the functionality of each method.
    - Adhere to proper coding conventions and style guidelines.

*Note*: Students are expected to implement the methods according to the provided requirements, ensuring correctness, efficiency, and clarity of the code. Additionally, passwords should be encrypted using the Caesar cipher algorithm, shifting each character by 3 positions

- Solution:

````python
class Facebook:
class Facebook:
    numOfAcc = 0
    def __init__(self, name):
        self.name = name
        self.set_email()
        self.set_password()
        Facebook.numOfAcc = Facebook.numOfAcc + 1

    def is_email_valid(self, email):
        cnt_at = 0
        cnt_dot = 0
        for char in email:
            if char == '@':
                cnt_at  += 1 
            if char == '.':
                cnt_dot  += 1
        return cnt_at == 1 and cnt_dot == 1
    
    def set_email(self):
        temp_email = input('Please Enter a valid email\n')
        while not self.is_email_valid(temp_email):
            print("This email is not valid. Please enter another email:")
            temp_email = input()
        self.email = temp_email

    def is_password_valid(self, password):
        if len(password) < 8:
            return False;
        cnt_char = 0
        cnt_num = 0
        cnt_upper = 0
        for char in password:
            if char == '@' or char == '#':
                cnt_char  += 1 
            if char >= '0' and char <= '9':
                cnt_num  += 1
            if char >= 'A' and char <= 'Z':
                cnt_upper  += 1
        return cnt_char and cnt_num and cnt_upper

    def set_password(self):
        temp_pass = input('Please Enter a valid Pasword\n')
        while not self.is_password_valid(temp_pass):
            print("This password is not valid. Please enter another password:\n")
            temp_pass = input()
        cipherText = self.encrypt(temp_pass)
        self.__password = cipherText

    def encrypt(self, password):
        cipher_text = ""
        for char in password:
            if char >= 'a' and char <= 'z':
                num_of_shift = ((ord(char) - ord('a')) + 3) % 26
                cipher_text += chr(ord('a') + num_of_shift)
            else:
                cipher_text += char    
        
        return cipher_text;
    
    def get_password(self):
        return self.__password
    
    def login(self,email,password):
        cipherPassword = self.encrypt(password)
        if cipherPassword == self.__password and email == self.email:
            print("welcome Back", self.name)
        else:
            print("Not Authorized, Please Try Again")


name = input("Please enter your name\n")
ahmed_arafat = Facebook(name)

print(f'Your email is {ahmed_arafat.email}')

print(ahmed_arafat.get_password())

ahmed_arafat.login("ahmed@gmail.com","Ahmed123@")
````
