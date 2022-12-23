import re
global email
global password
global c
c=0
def check(us1):#chceking email id present in file or not
    db = open("register.txt", "r")
    d = []
    f = []
    for i in db:
        a, b = i.split(",")
        b = b.strip()
        d.append(a)
        f.append(b)
        data = dict(zip(d,f))
    if us1 not in data:
        return 1

global x
global y
global pw
def login():
    maill=input("Enter your mail id to login")
    pwl=input("enter your password to login")
    if check2(maill,pwl)==1:
        print("login success")
def forgetpw():
    mailf=input("enter your mail id")
    if check(mailf)==1:
        print("no username found do you wanna signup(Y/N)")
        r=input()
        if r=='Y' or r=='y':
            register()
    else:
        print("user name exist")
        print("try again")
        mail()
        print("1.Retrieve password\n2.Replace password")
        rp=int(input())
        if rp==1:
            retrive(mailf)
        elif rp==2:
            print("replace password will update soon......")
            #rplc()#mailf

def p_word():#passsword validation
    def up(s):
        for i in range(len(s)):
            if s[i].isalpha():
                if s[i].isupper():
                    return 1
def rplc(s,pw2):
    mails=[]
    pws=[]
    d = open("register.txt", "r")

    def low(s):
        for i in range(len(s)):
            if s[i].isalpha():
                if s[i].islower():
                    return 1
    for i in d:
        x,y=i.split(",")
        y=y.strip()
        mails.append(x)
        pws.append(y)
    if s in mails:
        idx2=(mails.index(s))
        rpl=pws[idx2]
        print(rpl)
        pws.insert(idx2,pw2)
    else:
        print("username not found press 1 to resgister")
        pn=input()
        if pn=='1':
            register()

    def digit(s):
        for i in range(len(s)):
            if s[i].isdigit():
                return 1

    def run(s):
        regex = re.compile('[@_!#$%^&*()<>?/{}~:;`\.,]')
        if (regex.search(s) == None):
            return 0
def register():
    global mail
    mail=input("Enter your Mail id")
    cout=0
    if "@" in mail:
        cout+=1
        idx = mail.index("@")
        if "." in mail:
            cout+=1
            if mail[idx+1]!=".":
                cout+=1
                if mail[0].islower():
                    cout+=1
                else:
                    print("first letter should in alphabetic try again!!!")
                    register()
            else:
                print("dont put . immediate to @ try again!!!")
                register()
        else:
            return 1

    password = input("Enter your password")
    password2=input("confirm your password")
    lenghtpw = len(password)
    if lenghtpw > 5 and lenghtpw < 16:
        if up(password) == 1:
            if low(password) == 1:
                if run(password) == 1:
                    if digit(password) == 1:
                        if password==password2:
                            print("password created successfully")
                            return password
                        else:
                            print("password mismatch")
                            p_word()
            print("mail id shoud have . try again!!!")
            register()
    else:
        print("mail id should have @ try again!!!")
    if cout==4:
        print("valid mail")
        password()
def password():
    def splchr(s):
        for i in s:
            if i in "~!@`#$%^&*()_-=+><.,/?\|" :
                return 1
                break
    def upper1(s):
        for i in s:
            if i.isupper():
                return 1
                break
    def lower1(s):
        for i in s:
            if i.islower():
                return 1
                break
    def digit1(s):
        for i in s:
            if i.isdigit():
                return 1
                break
    pw=input("Enter Your PassWord")
    cout1=0
    lenght=len(pw)
    #specialchr=
    if lenght > 5 and lenght< 16:
        if splchr(pw)==1:
            if upper1(pw)==1:
                if lower1(pw)==1:
                    if digit1(pw)==1:
                        cout1+=1
                    else:
                        print("minimum one digit required,try again")
                        p_word()
                        print("password must have a digit")
                        password()
                else:
                    print("minimum one special character required,try again")
                    p_word()
                    print("password must have a lowercase try again !!!")
                    password()
            else:
                print("minimum one lowercase required,try again")
                p_word()
                print("password must have a uppercase try again !!!")
                password()
        else:
            print("minimum one uppercase Required,try again")
            p_word()
            print("password must have a special character try again !!!")
            password()
    else:
        print("password should have minimum 5 to 16")
        password()
    if cout1==1:
        try :
            storedata(mail,pw)
        except NameError:
            return pw
def retrive(s):
    mails=[]
    pws=[]
    d = open("register.txt", "r")
    for i in d:
        x,y=i.split(",")
        y=y.strip()
        mails.append(x)
        pws.append(y)
    idx2=mails.index(s)
    pws1=pws[idx2]
    print("your password is :",pws1)

def check(s):
    mails=[]
    pws=[]
    d = open("register.txt", "r")
    for i in d:
        x,y=i.split(",")
        y=y.strip()
        mails.append(x)
        pws.append(y)
    if s  not in mails or len(mails)==0:
        return 1
    else:
        print("password must 5 to 16 lenght,try again")
        p_word()
def spw(p,u):#append mail id and password to file
    f = open("register.txt", "a")
    f.writelines(p+","+u+"\n")
    f.close()
def mail():#email validation
    email = input("Enter Email Id")
    if '@' and '.' in email:
        index1 = (email.index('@'))  # 8
        if email[index1 + 1] != '.':
            if email[0].islower():
                if email[0].isalpha():
                    if check(email)==1:
                        return email
                        print("set mail id successfully")
                        #global s_id
                        #s_id=email
        return 0
    d.close()
def check2(s,d1):
    mails=[]
    pws=[]
    d = open("register.txt", "r")
    for i in d:
        x,y=i.split(",")
        y=y.strip()
        mails.append(x)
        pws.append(y)
    if s in mails:
        if (pws[mails.index(s)])==d1:
            return 1
        else:
            print("missmatching password press 3 to forget password ")
            a=input()
            if a=='3':
                forgetpw()
                """mailp=input("enter your mail id")
                if check(mailp)==0:
                    print("your password is:",pws[mails.index(mailp)])
                else:
                    print("Invalid Username\tTry again")
                    mail()
                    print("no user found press 1 to registration")
                    ma1=input()
                    if ma1=='1':
                         register()
            elif a=='2':
                print("enter your mail id")
                ma3=input()
                print("enter your new password")
                po=password()
                rplc(ma3,po)"""

            else:
                print("Invalid Username\tTry again")
                mail()
        else:
            print("Invalid Username\tTry again")
            mail()
                print("thankyou")
    else:
        print("Invalid Username\tTry again")
        mail()
def register():#registertaion process
    print("register")
    email1 = mail()
    password1 = p_word()
    spw(email1,password1)
    print("successfully registered")
def d(s):#chcek mail id in file
    db=open("register.txt","r")
    d=[]
    f=[]
    for i in db:
        a,b=i.split(",")
        b=b.strip()
        d.append(a)
        f.append(b)
        data=dict(zip(d,f))
    if s not in data:
        print("username not found press 1 to register")
        r1=int(input())
        if r1==1:
        print("no user found press 1  to registration!!!")
        b=input()
        if b=='1':
            register()
    d.close()
def storedata(mail1,pword):
    if check(mail1)==1:
        d=open("register.txt","a")
        d.writelines(mail1+","+pword+"\n")
        print("Registration successfull")
        d.close()
    else:
        n=1
        while n<4:
            passcode=input("enter your password")
            if passcode==data[s]:
                print("login successfully")
                break
            else:
                print("try again",n)
                n+=1
        if n==4:
            print("failed 3 times press 1 to retrieve your password")
            fpw=int(input())
            if fpw==1:
                checkmail=input("enter your mail and get your password")
                if checkmail==s:
                    print("your password=",data[s])
        print("user id exists please try different name")
        register()

#driver code
print("1.Register\n2.Login")
a = int(input())
if a == 1:
print("1.Register\n2.login\n3.Forget Password")
userinput=int(input())
if userinput==1:
    register()
elif a == 2:
    print("Login")
    lin=input("Enter mail id")
    d(lin)





elif userinput==2:
    login()
elif userinput==3:
    print("forget password")
    forgetpw()
else:
    print("please select valid option")
