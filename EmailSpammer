import sys
import yagmail
import time
from smtplib import SMTPServerDisconnected

def main():

    presetEmail = ""
    presetPassword = ""
    presetReciever = ""

    print("Welcome to shitscript bot spammerr.")

    parametersSet = False

    while(parametersSet == False):
        preset = input("Use preset parameters or enter your own?(Y/N): ")
        if(preset=='Y'):
            senderEmail = presetEmail
            senderPassword = presetPassword
            recieverEmail = presetReciever
            parametersSet = True
        elif(preset=='N'):
            senderEmail = input("Enter your email: ")
            senderPassword = input("Enter your password: ")
            recieverEmail = input("Enter target email: ")
            parametersSet = True
        else:
            print("You did not enter valid input (Y/N)")

    subject = input("Enter your subject header for email: ")
    body = input("Enter your body header for email: ")

    y = 0
    
    yag = yagmail.SMTP(user=senderEmail, password=senderPassword)

    with open(subject + '.txt', 'w') as f:  
        sys.stdout = f
        while(y < 100):
            print(body)
            y+=1
    
    sys.stdout = sys.__stdout__
    print("Email file compiled.")
    
    y = 0

    while(True):
        try:
            yag.send(to=recieverEmail, subject=subject + str(y) , contents=body, attachments=subject+".txt")
            print("email sent")
            y+=1
            pass
        except SMTPServerDisconnected as e:
            print("Spammer reached limit. Refreshing Connection.")
            time.sleep(10)
            yag.close()
            yag = yagmail.SMTP(user=senderEmail, password=senderPassword)   
            pass
            

if __name__ == "__main__":
    main()
