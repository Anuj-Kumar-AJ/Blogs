# How Single Server Architecture Works

# Introduction

A journey of thousand miles begins with a single step. Or in our cases, we can say the same about systems: building complex systems begins with understanding the fundamentals of single-system design. You guys must have heard about system design, in this series we are going to learn about why we need system design, and what are the different components we need to design it. and how those components are going to interact with each other. We will also learn about when to use some components and its trade-off with our use cases. This all sounds interesting, right? So without further, a do let's get started.

# Few Terminologies

let's first get familiar with a few terminologies

1.  **Web serve**r: As its name suggests, that which serves. but in computer networking term it is the computer program or device which provide service to another computer program. But definition asides the first thing that comes to our mind when we hear the word server is 👇
    

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669621847248/3jdfaDzN3.png align="left")

But the server is not always about big houses full of strange and cool boxed devices connected with wires and placed in a cool environment. Your computer can also become a server, must have heard of nodeJS, apache web server, etc . with the help of those, you can also use a web server. You must have doubts that why need that big warehouse full of machines when we can use this small pc to act as one right. I have explained it in detail The History of Web- Journey from designing the interface to designing Systems check it out.

2.  **Client**: Yes, these are computer programs or devices that request some information from the server through any medium. like internet, LAN, WAN, etc. so when you use internet service from your pc, mobile, or tablet. You are acting as a client.
    

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669622518134/gYUGk6dTx.png align="left")

3.  **Database or database-server**: So databases are the heart of the internet, what I mean is that the internet is a basic medium to connect many devices, but why would a device what to connect, off-course to share information right? So this database is where all the information is stored.
    

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669622822040/6Av6UIKt0.png align="left")

But why do we need a separate database 🤔

With the growth of the user base, one server is not enough, and we need multiple servers: one for web/mobile traffic, and one for the database traffic. Separating both will lead us to scale independently. Again fancy terms(scale) I have explained in The History of Web- Journey from designing the interface to designing Systems check it out.

4.  **DNS**: It is a Domain Name System, now what is this DNS thing? well, it's a system that helps us to use the custom name of our servers rather than some numbers. To elaborate on it more, to understand it more check my How internet work blog. But the gist of it is, every device has a particular IP address on the internet, which is ipv4 or ipv6. which is in numeric form, but to go to let's say YouTube you type, www.youtube.com rather than the IP address of the youtube server. So basically DNS converts your given string literally to the IP address of that server.
    

# How these systems communicate with each other

So let's get to the interesting part. How all these weird devices communicate with each other behind the scene gives us this awesome experience. well if you haven't paid attention we have come a long way, from using a house size computer that works many times slower than your phone, to your phone which can use resource which is more than a MacBook pro, or any high-performance gaming laptop or desktop that can provide using the cloud.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1669889332062/by4-sJ7KZ.png align="left")

Above is the general basic infrastructural working of network communication.

Let's understand with an example

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1669889413115/MgnJoLAXB.png align="left")

1.  user will send a request to DNS, Usually, this DNS service is provided by a third-party provider, not hosted by our server itself.
    
2.  Then the DNS gives us the IP address of the user's device.
    
3.  This IP address will be used to get to our requested web server.
    
4.  This web server will provide us response as per our request. The response will be an HTML page or JSON which will be rendered by our device ( browser, mobile app).
    

Let's add our database server to this infrastructure too

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1669890628061/SC7sCxzbu.png align="left")

Let's first understand the difference between a Web server and the Database server.

As Both of them are servers it does not mean that their resource (CPU, Memory, Disk, etc..) is also the same.

So as the work demand the web server needed more computing resources like CPU, GPU, TPU, etc.

And as for the database server, its work is for storage of our data, hence it needed more disk space, with high read and write speed.

So when the user request the web server communicates with the database server and sends the required data to the user.

## Conclusion

In this blog of the series Dimension of System design, we have learned about Different components and their working, of the Single server Architecture like Web server, Database Server, and DNS.

But you guys must be thinking about when there are soo many users who access data from the server. and for all request servers needed to request data from the database, It will be too costly in terms of time and resources ( of the web server which will be consumed by the database to request and receive the same data for different users all the time). So there has to be a way to reduce this, Well there is a way. But that is a talk for next time.

Thanks For reading