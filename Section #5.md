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
    num_of_acc = 0
    def __init__(self, name: str):
        self.name = name
        self.email = self.set_email()
        self.__password = self.set_password()
        Facebook.num_of_acc += 1
    
    def is_email_valid(self, email: str):
        cnt_at=0
        cnt_dot=0
        for char in email:
            if char == '@':
                cnt_at += 1
            elif char == '.':
                cnt_dot += 1
        return cnt_at == 1 and cnt_dot == 1

    def set_email(self):
        temp_email = input("Please Enter A Valid Email\n")
        while not self.is_email_valid(temp_email):
            print("This Email Is Not Valid")
            temp_email = input("Please Enter Another Valid Email\n")
        return temp_email
        
    def is_password_valid(self,password: str):
        if len(password) < 8 :
            return False
        
        cnt_digit=0
        cnt_upper=0
        cnt_char=0

        for char in password:
            if char == '@' or char == '#':
                cnt_char += 1
            elif char >= '0' and char <= '9':
                cnt_digit += 1
            elif char >= 'A' and char <= 'Z':
                cnt_upper += 1

        return cnt_digit > 0 and cnt_char > 0 and cnt_upper > 0

    def set_password(self):
        temp_password = input("Please Enter A Valid Password\n")
        while not self.is_password_valid(temp_password):
            print("This Password Is Not Valid")
            temp_password = input("Please Enter Another Valid Password\n")

        cipher_text = self.encrypt(temp_password)
        return cipher_text    
    
    def encrypt(self,password: str):
        cipher_text = ""
        for char in password:
            if char >= 'a' and char <= 'z':
                num_of_moves = (ord(char) - ord('a') + 3) % 26
                cipher_text += chr(ord('a') + num_of_moves)
            elif char >= 'A' and char <= 'Z':
                num_of_moves = (ord(char) - ord('A') + 3) % 26
                cipher_text += chr(ord('A') + num_of_moves)
            else:
                cipher_text += char

        return cipher_text
        
    def get_password(self):
        return self.__password
    
    def login(self,email:str, password:str):
        cipher_password = self.encrypt(password)
        if self.email == email and self.get_password() == cipher_password:
            print("Welcome Back", self.name)
        else:
            print("Not Authorized, Please Try Again")


# Ahmed1234@
name = input("Please Enter Your Name\n")
arafat = Facebook(name)

print(f'Your Encrypted Password Is {arafat.get_password()}')
print(f'Your Email is {arafat.email}')
email = input("Please Enter Your Email To Login\n")
password = input("Please Enter Your Password To Login\n")
arafat.login(email,password)

print(f'Number Of Created Accounts {Facebook.num_of_acc}')
````
