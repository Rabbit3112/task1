# task1
import re
import csv

email_regex = re.compile(r'([A-Za-z0-9]+[.-_])*[A-Za-z0-9]+@[A-Za-z0-9-]+(\.[A-Z|a-z]{2,})+')
pwd_regex = re.compile(r'^(?=.*?[A-Z])(?=.*?[a-z])(?=.*?[0-9])(?=.*?[#?!@$%^&*-]).{5,}$')


def checkid(email):
    if re.fullmatch(email_regex, email):
      return True
    else:
      return False

def checkpwd(pwd):
    if len(pwd) < 16 and len(pwd) > 5 and re.fullmatch(pwd_regex, pwd):
      return True
    else:
      return False

def register():
    print('\nRegister New User\n')
    email = input('email id: ')
    if checkid(email):
        password = input('password: ')
        if checkpwd(password):
            write_file(email, password)
            print('\nUser Registered Successfully')
        else:
            print('\nInvalid Password, Please Try Again...')
    else:
        print('\nInvalid Username, Please Try Again...')

    

def login():
    email = input('email id: ')
    auth  = False
    if checkid(email):
        password = input('password: ')
        if checkPwd(password):
            if search_file(email, password):
                print ('\n Log in Successfully...')
            else:
                print('\nUser not found,try again')
                register()
        else:
            print('\nInvalid Password, Please Try again')
    else:
        print('\nInvalid Username, Please Try again')

def forget_pwd():
    email = input('email id: ')
    if checkid(email):
        if search_pwd(email):
            print ('\n Log in successfully')
        else:
            print('\nUser not found,try again')
            register()
    else:
        print('\nInvalid Username, Please Try Again...')



if __name__ == "__main__":
   
        while True:
            print(''' \nSelect any one option below: \n
                1. Press '1' to Register 
                2. If you have an Account already,Press '2' to login:
                3. Forget Password, press 3''')
            option = int(input())
            if option == 1:
                register()
            elif option == 2:
                login()
            elif option == 3:
                forget_pwd()
            else:
                print("Invalid Option")
    except:
        print("Please try again later")
