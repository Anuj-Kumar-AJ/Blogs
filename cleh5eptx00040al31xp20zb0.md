# Modernizing Monolithic Applications: From Virtual Machines to Containers

# Introduction

There are so many different terms and software for deploying our software, but it is confusing for beginners to understand it, the content is spread on the internet but I wish I had a story where it explains how and why different types of technology evolved with time.

So in this blog post, I have shared the evolution of technology in a story form, So it will be easier for folks to understand.

# Monolithic Architecture

### Dawn of the internet

Let's not get too much technical from start, Let's understand it like an interesting story.

Revenue generated in business is all about the interaction of people and organizations and how well the organization can show its product to customers. Before the internet organizations can only target a few customers, who they know can be potential buyers. This means organizations can't target customers they don't know, or customers have to go personally to organizations to know more about their products. Which can be a tedious task.

So what happened in the beginning years of the internet is, organizations got a hint about how to connect or broadcast their product to a large group of people, all over the world, Who can see their product just by visiting their website. This year is known as ***WEB 1.0***

This was better than before but there is a huge drawback in this strategy, can you guess? well, the feedback and review of that product. Well you know there are 100s different brand of the same stuff in the market, But you ask your friend who has used the product when you buy any goods, right? this strategy was nice when there were localised customers for the product. But the internet has made it global. Which makes it hard to connect with people who have used this product. So basically people can only see what organizations put it on their website (in view-only mode). But can't interact with it, meaning cant provide their feedback or review.

Well, this problem causes a new revolution in www or world wide web. which is ***WEB 2.0***. In this evolution of the internet, customers can interact with websites and provide their input. This means people can give a review of the product and when another customer needs that product, they can check the review before buying. This technology has powered social media. Or we can say the rise of social media was started due to this technology (like Facebook one of the initial players in social media).

### What is monolithic architecture

Monolithic architecture is a software development approach, Where all three components like user interface (frontend), business logic ( backend ) and database, were built as a single unit. Which are tightly coupled meaning all components are coupled as a single unit, which is not separated. And it is deployed as a single unit on any server

![Monolithic & Microservices Architecture | by Henrique Siebert Domareski |  Medium](https://miro.medium.com/max/714/1*F6y9GeBZwaOzNYnToahfQw.png align="left")

### Advantages of monolithic architecture

1. Easy to develop and deploy: Monolithic architecture is simple and straightforward, making it easy to develop, test, and deploy an application.
    
2. Efficient resource utilization: In a monolithic architecture, all the components are tightly integrated, allowing for efficient resource utilization and reduced overhead.
    
3. Improved performance: Because all the components are integrated into a single unit, there is less overhead, resulting in improved performance.
    
4. Easier to understand: The simplicity of the monolithic architecture makes it easier for developers to understand the application and the relationships between its components.
    
5. Faster time-to-market: Monolithic architecture allows for faster development and deployment times, enabling organizations to bring products to market more quickly.
    

Wow, there is soo many features, easy to implement. why is the need to develop any other architecture?

![Frustrating Frustrated GIF - Frustrating Frustrated Kid GIFs](https://media.tenor.com/aIVC4JjqorYAAAAM/frustrating-frustrated.gif align="center")

## Shortcomings of monolithic architecture

Well worry not this is true when the user base is less than the capacity of the server to serve the load of traffic. but when the traffic load gets more than the server capacity then, the response time will increase and the user feels lag and bad experience,

or this may happen **😜**

![Sparks Electrical Electricity Equipment Radio Amateur Fire GIF - Sparks Electrical Electricity Equipment Radio Amateur Fire GIFs](https://media.tenor.com/uDgrVufjT78AAAAC/sparks-electrical-electricity-equipment-radio-amateur-fire.gif align="left")

anyways, to get a server with more users than the capacity is not possible so the application needs to scale up. Welcome to a nightmare.

![Welcome To My Nightmare Desantis2024 GIF - Welcome To My Nightmare Desantis2024 Desantis GIFs](https://media.tenor.com/BjPtUeOBaMMAAAAM/welcome-to-my-nightmare-desantis2024.gif align="left")

But why is that? 🤔 let's understand it.

1. cost:- you see when you buy a server you are paying for real estate where the server will install, and physical protection of that server, and will be paying for a whole lot of waste resources on the server as not all resources (CPU, RAM, GPU, etc) will be used.
    
2. load balancing:- you have to hire a network engineer every time you add a new server, as load balancing is needed to implement to send excess traffic to the newly installed server.
    
3. Software installation on server:- It is also one of the main challenges to spin up a new server with all the dependencies installed and start the software on the new machine. As we know the term " **It works on my system** " ( for some who don't know this phrase, it means that particular software run on one machine by won't on another, due to some dependencies issues ), we don't want that to happen in the server right.
    

and much more.

So how do we solve this issue, well the virtual machine comes to the rescue

# Rise of Virtual machines

Let's first understand what virtual machines are, virtual machines are virtualizing system resources

![Virtual Machine or Physical Server - Actus Digital](https://actusdigital.com/wp-content/uploads/2021/05/virtual-machine-chart.jpeg align="left")

As this image shows, let's say you have 48GB RAM, 10 cores CPU, and 12TB Storage. So you can assume your physical machine gets broken down into 3 separate virtual machines, with resources of

1. the first Virtual machine resource :( vRAM 12GB, vCPU 2cores, vStorage 2TB )
    
2. second Virtual machine resource :( vRAM 16GB , vCPU 1cores, vStorage 3TB )
    
3. third Virtual machine resource :( vRAM 18GB , vCPU 4cores, vStorage 5TB )
    

It's upto you how you want to break ( in terms of capacity ), your physical resources (CPU, RAM, Storage) into virtual resources (vCPU, vRAM, vStorage )

Let's talk a bit more about the virtual machine, both diagrams below are two different types of virtualization.

well check the below pic, can you guess the difference

![Virtualisation and Hypervisor-based concepts | Xantaro](https://www.xantaro.net/wp-content/uploads/2019/01/Xantaro_Hypervisors.png align="left")

you must be very confused by this hypervisor thing, you must be thinking

![Meme What The Hell Is This GIF - Meme What The Hell Is This Elephant GIFs](https://media.tenor.com/BvNT-VXurjEAAAAM/meme-what-the-hell-is-this.gif align="left")

let's worry not I will share detailed explanations in another blog post, because it's a big topic and so are much interesting. but for now, think of hypervisor as a software layer that helps manage different virtual machines, or we can say guest host OS.

So with the help of a virtual machine you can run multiple OS at the same time using single physical hardware, isn't that cool.

you can assume these host OS as they run on different physical machines I am saying this becase you can't see data of another virtual machine meaning, although they share the same physical machine they are separated and can't access another OS virtual machine data. So if you want to share data then you have to make your hands dirty a bit, some way to do so is

1. to use the shared folder feature these virtual machine software like VMware, VirtualBox, etc
    
2. you can communicate over the network, by creating a communication channel between both or use VPN tunneling
    

Okay now you get the guest of the virtual machine, so then we reach the pinnacle of technology right? we can use multiple OS on a single physical machine, So we can use all the wasted resources which were common in a single OS on a physical machine.

Nope, there are a few more problems with VMs. let's understand a few of them

1. It's slow:- As a new virtual machine needed to boot the OS, it takes lots of time which some use-cases (needs) can't afford to spend. Time is money in current times, you don't want to lose customers due to your VM reaching its limit and you need to create a new Virtual machine but it takes time to boot up
    
2. Networking limitation:- well is complex, the network connection between different VMs is complex and it's not as fast as that of physical machines.
    
3. Resource overhead:- As OS has many processes running it consumes resources, which can't be utilized by us
    
4. and many more limitations are there for VMs
    

now that you know about VMs. Let's get back to the story. There are legacy applications that builds long before this cloud was feasible. But they also have seen the advantages of the cloud and want to migrate towards it.

You must have heard about Cloud applications or cloud-based software. Now let's understand the term cloud-based application

### Cloud Application

Cloud applications are software that was built for monolithic architecture but we are deploying it to the cloud after seeing the advantages of it.

In this type of software, whole coupled software is deployed on cloud VMs. And when there is a need to scale the system as the traffic increases. New VMs get spun up with the whole software again.

There is a big issue with this, Let's understand it with an example, let's say you have 3 components in your software (which is video streaming)

1. FrontEnd
    
2. BackEnd
    
3. Database
    
4. Content delivery network (CDN) --&gt; which catches the frequently use content to speed up the user experience.
    
    [To know more about these different component](https://hashnode.com/post/claun099m000008js0at93wrg)
    

and a new movie is uploaded to it, then traffic increases and our server reaches its limit. Now when we spin up new instances of our software then we are basically creating FrontEnd, Backend, and Database. again we will just waste our resources because we only need frontend to scale up. but think about it what if there are different VM that host frontend, backend and database . when we need to scale up our server we just scale up what is needed like in this example FrontEnd and CDN. So there will be resources saved.

Well, this is the concept of microservice, and we will deploy and run this component in containers, not VMs.

Are you excited to learn about it, because I am, while sharing about it

# Microservice Architecture

![What is Microservices? Microservices Definition and Related FAQs | Avi  Networks](https://avinetworks.com/wp-content/uploads/2018/06/Microservices-vs-monolithic-architecture-diagram.png align="left")

the basic overview of microservice architecture is, in this architecture, we try to break the different components which have different functions as much as we can and that components will run in an isolated containers( will learn in a bit) and communicate with each other over APIs

### Cloud-Native Applications

So this software which follows the microservice architecture and deploys on the cloud is called cloud Native applications, But why?

think about it, As in the cloud there are big data centers with thousands of servers connected, but they are shared by many of different users. So if the size of your software component is smaller, then it is easier for it to scale up and down, as this component can be deployed on servers that have fewer resources left. or else if the software of ours is big then it takes much larger resourceful server to run, and maybe that server may not easily be available.

That's why this architecture is called cloud-native ( meaning they are built for the cloud )

### Containers

Okay, we got the overview of the microservice architecture. But where do the different components run? well, the answer is on containers.

But the question arrises why don't we run it on VMs, why there is a need to create a new infrastructure component, that is containers? What do they do? well, that is a lot to ask, but due to keep this blog short I will just introduce the containers and will make a new blog to deep dive into containers, for now, i will brief you about containers.

you can understand containers as a box inside of which we just run our software with dependencies, which will be separated from the rest of the world outside containers.

the container will talk to the OS to provide resources to run our containers. You must have heard or experienced the term "**It works on my system**". when you try to send your code to your friend and due to dependency clash (let's say you have built your ass to use node with version 14 but your friend has version 16. and try to run your code then sometimes your code will break or not run on his system, and if your friend says this code is broken you say to him **IT works ON MY SYSTEM.**

let's understand how the container works, unlike VMs containers don't have its own OS, it utilizes the host OS kernel to provision resources ( like CPU, Memory, etc) so that containers can run applications inside of it.

So the container can use the

#### Kernel

for those who don't know about the kernel, It is the software structure that can talk to the hardware and give the application access to use system hardware to run. to see for yourself the code for [Linux kernel](https://github.com/torvalds/linux/tree/master/kernel) code. So container runs the application which is inside of it as a separate unit and it does not share any process with other containers on the host operating system or the host itself.

![Docker container architecture. | Download Scientific Diagram](https://www.researchgate.net/publication/333235708/figure/fig1/AS:760874507722754@1558418027301/Docker-container-architecture.ppm align="left")

The popular container software is docker

![10 things you should know about Docker | TechRepublic](https://www.techrepublic.com/wp-content/uploads/2015/02/docker-logo.png align="left")

Now let's get back to the story. Everyone is happy as the container was introduced. So now the company started to use containers at a drastic pace. and the company started to use containers for separate processes, as there is a need to scale up, the company can spin up more containers, easily. But the problem arises when the number of containers goes to more than the company can handle manually. So now to tackle this problem the concept of container orchestration was introduced.

Let's see what container orchestration is, and how can it solves our problem.

### Management of containers - container orchestration

![The Conductor' Review: Seizing the Baton - The New York Times](https://static01.nyt.com/images/2022/01/28/arts/conductor1/merlin_200685000_4948616b-2ad8-4564-9c1c-e0a3c850af33-superJumbo.jpg align="left")

In the pic above there is an orchestrator who orchestrates a band of a musician so that they produce rhythmic music combined. Similarly, there is the concept of container orchestration.

container orchestrator is a software structure that helps us manage thousands of containers automatically. there are many popular orchestrators but the most popular one is **Kubernetes (K8s)**. K8s is getting toward becoming an important part of cloud-native so it's best to learn k8s, I will share detailed working of k8s in upcoming blogs. I can't brief you about its architecture because it is much more complicated and needs a separate blog, but let's understand what this container orchestration really means

Till now we got to understand that all the workloads (tasks like running software) will run inside containers, but we are managing containers ourselves, with container orchestrators like k8s this management can be automated. let's say you have to host a website for your product. So you can give k8s access to all the hardware servers across geographic locations. Now as the demand or traffic to your website is dynamic there is a need to scale up or increase the number of containers and scale down or reduce the number of containers, So with k8s you just have to tell the k8s how many containers you want to keep running (using CLI (command line interface) or you can provide this information to k8s by creating a YAML (it is a type of language like JSON) file )and it will automatically increase and decrease the number of containers and while doing so k8s will automatically. Well, there is soo much more to k8s like load balancing, running data workload on Kubernetes, and much more which will be coverer in upcoming blogs.

there are also many orchestrators such as **Docker Swarm and Apache Mesos.**

# Conclusion

In this post, we have seen how and why our computing system is going through the transformation from a monolithic architecture to containers. We have also seen how VMs work. I have tried to make it a story so that folks can understand the journey. In upcoming blogs, I will dwell in depth on the cloud-native world. So stay tuned. And do share the feedback did you enjoy this content.