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
gmail_password = 'i_swear_this_is_not_my_password'

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

Basically I used the principle seen in this snippet to implement the email sending on the backend of our project.

***
### PayPal Sandbox
Another important aspect of what I learned this week was the implementation of PayPal. In theory it's really easy because paypal already provides everything for an easy integration. This is a code snippet written in JS that displays the paypal buttons:

``` HTML
<!DOCTYPE html>

<head>
  <meta name="viewport" content="width=device-width, initial-scale=1"> <!-- Ensures optimal rendering on mobile devices. -->
  <meta http-equiv="X-UA-Compatible" content="IE=edge" /> <!-- Optimal Internet Explorer compatibility -->
</head>

<body>
  <script
    src="https://www.paypal.com/sdk/js?client-id=GET_YOUR_OWN_KEY_FOOL"> // Required. Replace GET_YOUR_OWN_KEY_FOOL with your sandbox client ID.
  </script>
    <div id="paypal-button-container"></div>



<script>
  paypal.Buttons({
    createOrder: function(data, actions) {
      // This function sets up the details of the transaction, including the amount and line item details.
      return actions.order.create({
        purchase_units: [{
          amount: {
            value: '0.01'
          }
        }]
      });
    },
    onApprove: function(data, actions) {
      // This function captures the funds from the transaction.
      return actions.order.capture().then(function(details) {
        // This function shows a transaction success message to your buyer.
        alert('Transaction completed by ' + details.payer.name.given_name);
      });
    }
  }).render('#paypal-button-container');
  //This function displays Smart Payment Buttons on your web page.
  </script>
</body>
```

I think there are 2 main things to consider in this snpippet:
1. We include an URL with a src property in our tag that allow us to use all of the code that paypal already provides for us.
2. We have the funcion createOrder that allows us to set up the transaction that we want to achieve.

***
### Double Entry Account
I remember that I had to take an obligatory subject during my early university years about accounting. I'm not going to lie, at that time I thought that the class was pretty much useless to me, but this week I was proven wrong.
When designing our entities model for handling different transactions we implemented in our design what is called [double entry accounting](https://en.wikipedia.org/wiki/Double-entry_bookkeeping). It basically consists in the idea that for every transaction in the system there is a counterpart that is the negative for that.
For example, when we start our system we would have some initial data like this: 

```
  2020-11-05  initial balance of coins in our system    
        root-magic-account            -1,000,000 COINS
        for-selling-account            1,000,000 COINS          
```

You see what we did? We just started 2 initial accounts to be able to sell coins to our users.
For example:

```
 2020-11-06  buy coins
        luis-account             5 COINS
        for-selling-account       -5 COINS
```

This way we have an error to identify if at some point there is a mistake with our transactions data. Because in order to validate the previous we just have to make sure that all of our transactions are equal to 0.

***
### How to face an important presentation
This week I had to present my first demo to a client. It was the first time that I faced this situation, so naturally I was very nervous. I just applied two simple concepts to face my fears about this presentation.
**First,**
I discovered that I was afraid that I was going to be judged as a mediocre developer, so to face this insecurity I wrote down what it actually means to be a good developer, and this is what I wrote down.
```
Good developer traits:
- Is always learning
- Has good communication skills
- Problem solving hablities
- Knows how to be organized
```
So I started judging myself with my own standards, and I discovered that
1. This past two months I have been learning something new everyday.
2. I have improved my communication skills a lot by working in this internship.
3. Now I try to face every problem with the approaches of learning how to learn for better results.
4. I'm builiding the habit of writting down what I'm going to do the next day one day before.

I know I have a lot to learn yet, but I guess I'm not that bad after all (according to my own standards), so not today imposter syndrome.

**And second**
I got a tip from Dayra, and it's pretty straight forward. See "the figures of authority" as an equal. In this case it was the Product Owner who I was presenting my demo. I just had to acknowledge that he was just experienced in some field and I was more or less experienced in another field, that doesn't make him better than me and viceversa. At the moment this helped me a lot be less anxious.
