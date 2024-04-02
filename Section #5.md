- Practice Example #1

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
