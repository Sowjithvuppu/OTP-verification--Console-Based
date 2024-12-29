# OTP-verification--Console-Based
import random
import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
otp = random.randint(1111,9999)
months={1:"Jan", 2:"Feb", 3:"Mar", 4:"Apr", 5:"May", 6:"Jun", 7:"Jul", 8:"Aug", 9:"Sep", 10:"Oct", 11:"Nov", 12:"Dec"}
name=input("Enter your name: ")
date = int(input("Enter your Data of Birth: "))
month = int(input("Enter your Month of Birth: "))

tomail = input("Enter Mail id: ")
subject = "OTP For Verifivation"
body = f"Hope you are doing well {name} !!\nDate of Birth : {date}- {months[month]}\nYour Secret OTP  codefor Verification is { otp }"

msg = MIMEMultipart()
msg['From'] = "vsowjith2024@gmail.com"
msg['To'] = tomail
msg['Subject'] = subject
msg.attach(MIMEText (body,'plain'))

server = smtplib.SMTP("smtp.gmail.com",587)
server.starttls()
server.login("vsowjith2024@gmail.com","jrxu mtpd dhdv wmic")
server.send_message(msg)
server.quit()

userinput = input("Enter OTP received to your mail: ")
if userinput == str(otp):
	print("OTP Validation Successful!")
else:
	print("Wrong OTP entered!")
