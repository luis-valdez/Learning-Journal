### [Go back to index](https://luis-valdez.github.io/Learning-Journal/)

## Week 7 - 02/11/2020 to 06/11/2020
This week we're working in the phase of bulinding something from scratch and i'm learning a lot from this experience. The reason of this is because we're a team of 7 people were everyone needs to be involved in a little bit of everything. So basically in our team we're trying to avoid specialists to keep a low [bus factor]
(https://en.wikipedia.org/wiki/Bus_factor).
The overview represents the things that sticked with me throughout the week.

### Overview
- SMTP implementation
- PayPal sandbox
- Double Entry Account
- How to face an important presentation


### SMTP implementation
This week I had the chance to use gmail SMTP service for automatically sending emails when a user is registered.
To learn how to do this I first did it in a python script that looks like this:

``` python3
import smtplib

gmail_user = 'projectbetencoraacademy@gmail.com'
gmail_password = 'Happy!1234'

sent_from = gmail_user
to = ['luiscarlosvaldezr@gmail.com', 'luiscvr15@gmail.com']
subject = 'OMG Super Important Message'
body = 'Hey, whats up?\n\n- You'

email_text = """\
From: %s
To: %s
Subject: %s

%s
""" % (sent_from, ", ".join(to), subject, body)

try:
    server = smtplib.SMTP_SSL('smtp.gmail.com', 465)
    server.ehlo()
    server.login(gmail_user, gmail_password)
    server.sendmail(sent_from, to, email_text)
    server.close()
    print('Email sent!')
    
except:
    print('Something went wrong...')
```
