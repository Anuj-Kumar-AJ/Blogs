# Email Sending  using NodeJS and Express

# Introduction

### About Email
Email or Electronic mail now becomes a significant method of sending messages between two people or two devices.  The email was thus conceived as the electronic (digital) version of, or counterpart to, mail, at a time when "mail" meant only physical mail (hence e- + mail).
### Email in the current world
 An email later became a ubiquitous (very widely used) communication medium, to the point that in current use, an email address is often treated as a basic and necessary part of many processes in business, commerce, government, education, entertainment, and other spheres of daily life in most countries. 

### How the email server works
Today's email systems are based on a store-and-forward model (Store and forward is a telecommunications technique in which information is sent to an intermediate station where it is kept and sent at a later time to the final destination or to another intermediate station. The intermediate station, or node in a networking context, verifies the integrity of the message before forwarding it). Email servers accept, forward, deliver, and store messages. Neither the users nor their computers are required to be online simultaneously; they need to connect, typically to a mail server or a webmail interface to send or receive messages or download them.

# Why do we need to send an email over NodeJS? 

Let's take a scenario where you have to send an email to a large group and you have to send an structured message like lets say in `html` , to do so you cant use your gmail service provider api like google gmail , Microsoft outlook etc. 
because you can only use the services provided by these API . But if you have to make your custom functionality , Say you have to schedule your message when to send it. or you have made an app and for particular event you want to get notified over your email. and much more. You yourself can think many more utilities where Email can be your life Saver.

# Prerequisite

1. NodeJS installed [You can install it from here](https://nodejs.org/en/download/)
2. nodemailer installed 
3. Express installed


We have done So much talking. Without further a do let's get stated with coding


# Lets get our hand dirty

So here we talk about email , which is in crude term 2 devices talking right. one device send message to other and vice versa
and if they are taking . then it must be over some protocol which is in this case `http` .
And in nodeJS there is a `http` module. This module is fantastic but we are going to use `express` in our project which is build on top of `http`. So what i mean when i say it is build on top of `http` is, it have abstract away many complex code of `http` , and made user friendly code for our use with enhanced functionality.
Express is a minimal and flexible `Node.js` web application framework that provides a robust set of features for web and mobile applications. 


### creating nodemailer directory for our application

go to the terminal for Linux or Unix(mac) users or 
open  command prompt(cmd) or Power Shell  for windows user

``` 
mkdir nodemailer
cd nodemailer

```

### installing dependencies (Express and nodemailer) 

```
npm install express --save
npm install nodemailer --save

```
your package.json will look like this
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668934174111/K-5LYcsps.png align="left")

Note here --save flag is used so that the package.json will get updated with these dependencies automatically

For those who don't know what package.json is , in short it contain all the modules which our app can use.

if you want to know more about package.json check  


[More info about Packages and Modules or package.json](https://docs.npmjs.com/about-packages-and-modules)



### Let get to coding 

Create a file called `index.js`, and open it in your favorite IDE(integrated development environment).

add the following line of code

 ```javascript
// importing express 
express = require('express');
//importing nodemailer
nodemailer = require('nodemailer');

// creating an instance of express
app = express();
```
 here we have importing express and nodemailer in our `index.js` file. and  creating instance of express of app,
creating of instance means just like in object oriented programming , we declared class and create an instance of that class. Here also `express = require('express');` if class and `app = express();` is instance of that class

Next comes using nodemailer transporter object creation. 

```
let transporter = nodemailer.createTransport({
    host: "smtp.gmail.com",
    port: 587,
    secure: false, // true for 465, false for other ports
    auth: {
      user: //"User_ID", 
      pass: //"User_Password", 
    },
  });
```

SMTP is the main transport in Nodemailer for delivering messages. SMTP is also the protocol used between different email hosts, so its truly universal. Almost every email delivery provider supports SMTP based sending, even if they mainly push their API based sending. APIs might have more features but using these also means vendor lock-in while in case of SMTP you only need to change the configuration options to replace one provider with another and you’re good to go.

Note that in this example i have used gmail host, if you have different host please change it accordingly their SMTP configuration.

In place of `User_ID ` place your email address, and in Place of your User_password place your account `password`. 


```
const message = await transporter.sendMail({
    from: '"Anuj " <Anujkumar.sk639@gmail.com>', // sender address
    to: "user, <anujkumaraj639@gmail.com>", // list of receivers
    subject: "Email from nodeJS server", // Subject line
    text: "Hi from nodeJS server", // plain text body
    html: "<b>Hi from nodeJS server</b>", // html body
  });

```

we have use `await ` here, which is asynchronous or `async `function ,  which will stop the further execution and execute the `transporter.sendMail`, which will send the email 

Lets see what  `transporter.sendMail` contain. It have 
1. `from` contain  sender_name , and sender_address under arrow bracket
2. `to` contain receiver_name and receiver_address under arrow bracket  
It's important to note that we can add as many address as we want ( which ois less then what our host email provider support at a time) by saperated by space 
eg user1@host.com user2@host.com user3@host.com .......

3. `subject` to have subject of the email
4. `text` it contain plane text which you will send , suppose if recever device cant read html format then it will read plant text content present in text
5. `html` we can  add our html content which will rendered by receiver device

```
console.log("Message sent: %s", message.messageId);

```

It will print the conformation if the message was sent in terminal. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668939160642/hVhCEfZ28.png align="left")

# Challenges You may Face

The main challange i have face is with authorization of my email id , as i have used 2 factor authentication in gmail account, I was not able to connect with my email host to send messages while creating** transport Object** , So i have to create app password in my gmail account and used it as my user_password in transport object
You can check solution for this [problem here](https://community.nodemailer.com/using-gmail/)

# Conclusion

In this blog we have learn to send email using nodeJS, you can experement as many functionality as you want, using [nodemailer documentations ](https://nodemailer.com/about/). This is basic nodeJS email sender. 

you can check my [github reposotory](https://github.com/Anuj-Kumar-AJ/Sending-Email-using-nodeJS-and-Express/blob/main/index.js). I have used version control git in this project so you can check how this project build step by step. If this repo updated in future, I will keep git file for you to build project step by step by reading `README.md` file for that commit.