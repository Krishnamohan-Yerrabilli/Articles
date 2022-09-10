## What Serverless is all about?

😃 First of all thanks for checking out this article, By reading this article I'm pretty sure 
you will get a good understanding of What Serverless is all about, enough talk, Let's go 🚀 
 
### What is Serverless?

#### Definition

In simple terms, it means you just want to write the code of your application 
and deploy in the cloud, now the whole server part of your application is managed 
by you're cloud provider, as simple as that in a high-level context.

To understand things better, it's important to know some of the core functionality 
terminologies, let's see what are those one by one.

### Terminologies

#### FaaS

(Function as a service) is one of the Important concepts of serverless, it simply means 
your application only responds when the user requests any information regarding your
the site it's based on event-driven architecture.

You have more control over logic, this is executed on-demand when no one uses your app
guess what, you will not be charged, you only pay when you got a request and the CPU processing time of your request. 

These requests are handled by the cloud providers using a service called API gateway.

#### BaaS

(Backend as a service) It is a cloud service where a web application or mobile application user can easily access the back-end cloud storage is so helpful because now the developers will only concentrate 
on the front-end code.

Typically users want to access some back-end services, baas acts like a bridge

These services are handled by using a different set of services such as APIs(Application 
program interface), and SDKs(Software development Kits).

#### Containers

Containers are the instance of an image, containers are handled by shim, and containers are also called lightweight VMs

containers provide a high level of security because it does not talk to the host operating system and a container does not know what happens outside of the container 

Containers have their own operating system to run 

### Before Serverless

#### Monolothic

![Created a YAML config file and integrated it with AWS CloudFormation (3).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657549134463/t9GN-lmDj.png align="left")

In this architecture, all the components of the applications are bundled in one set 
of the package 

This application architecture is not a good choice for the cloud, 
because of its design

When any one of the services is down, there is a possibility that the whole application 
will get the effect

It takes a long time to come back to its normal state and it is a
time-consuming task for the developers. and It also has scalability issues.

#### Microservices

![Created a YAML config file and integrated it with AWS CloudFormation (5).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657550177039/WFAimsg_a.png align="center")

Microservices architecture is where the whole application is divided into smaller 
components

Individual components can work on their own without depending on
other parts of the applications 

By adopting this architecture, organizations can scale their applications easily, where
a single application is deployed to perform a specific task
 
#### Serverless

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657536542126/R63J_H3t7.png align="center")

It is purely evolved by the cloud, here serverless utilizes FaaS and BaaS instead of Iaas or Paas,
here application is deployed when it is requested along with specified resources, this FaaS is 
achieved by the user's request.

Here you don't have to manage the servers and the underlying resources used by them, you only
pay for the compute time and request count.

### Why Serverless?

Because now it's one of the emerging technologies in software development,
organizations don't want to manage the infrastructure so the better leverage 
the power of serverless

- Developers can fastly deploy the application.

- They simply build cloud-based apps and also for the easy migration of the cloud. 

- Organisations don't pay when their applications are ideal, ( pay only when you invoke the functions )

### Characteristics of Serverless

- No server management is needed from the customers.

- When the request is invoked a new environment will be created until its executions 
is done.

- Serverless is the cheapest way to deploy back-end applications.

- It can scale up and scale down easily.

- Where the requests continue to execute you can scale infinitely depending on the env. 

- The application only runs on-demand.

### How does it work?

![Created a YAML config file and integrated it with AWS CloudFormation (2).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657548091790/l-2hT7iui.png align="center")

The serverless architecture combines two phases one function as a service and another
one is a backend as a service, instead of BaaS, Serverless mainly focuses on the FaaS, 
because it doesn't need to provision resources.

Most of the software dev teams and organizations adopting this nature, here is how it works 
software developers write a code that triggers an event 

The event invokes the function, and the function is the service after the execution is done, 
it simply comes into a normal state. 

### Use-Cases

#### Parrallel-computing

Serverless is an efficient option for parallel computing because it can easily scale up the
resources so high load tasks can be easily distributed and can fastly be done to complete 
the operation.

#### Api-Backends

Any function can be turned into an HTTP endpoint, that is ready to serve to the clients,
These actions are known as web actions when it is enabled on the web

If this all goes correctly Integrating the function into a Full-fledged API becomes easy.

#### Batch process

You can easily launch extremely fast process streaming apps, you can create 
Pipelines with FaaS, and a database for Apache Kafka, and not only that we can
also, initiate and use IoT sensors fast transfers.

#### Data-processing

Serverless is a great use-case for data processing, such as (OCR) optical character 
recognization ), and also for video transcoding, pdf processing, data generation, data
validation, transformation, enriching (data enhancement method), 
and many use cases.   

### Pros

#### Faster Deployment

While developers don't write code for backend configuration and they also don't create
config for new app versions, so developers can easily deploy the product in a bit of 
seconds

With this type of serverless advantage, we can say it is also environment friendly,
green-computing, reduced costs, on-demand purposes, and the list goes on.

#### Scalability

Serverless handles Scalability, based on the demand it scales up easily
and scale down whenever the application is needed, for this reason
people often say "Elastic".

Developers are not config auto-scaling for their application after they don't 
need to tune with policies, and for juniors devs 

It's quite easy just to deploy the application code and no need for expertise, 
just release the code, everything else is managed by the application provider.

#### Cost-effective

Customers don't need to buy or rent servers based on their usage, it's just scales
when they needed

They don't pay when they not running the application, it is based on the "pay as you go"
model so you only pay what you use.

CSP only charges for certain use cases like the memory you used, the processing power, 
you don't pay when they're idle. 

#### Productivity

Developers don't need to handle server management, instead, they can think
about code and application improvement, Serverless simplifies the back-end 
development

They don't need to think about managing HTTP requests and handling 
multi-threading.

#### Latency

While the application is region-oriented, users in the region can easily and 
fastly access the application because the end-users are near and the request 
and response time is fast, tho it is on low latency. 

### Cons

#### Security 

Security is not compromised in the cloud, everyday cybersecurity attacks are
increasing, transferring sensitive data between the network is risky, because even
we can't say 100% sure that full security is provided.

#### Performance

The initial request takes time if no other servers running behind, this extra latency 
is also called a cold start

These latency requests are exhibited with less frequency even more than less latency, 
then the virtual machines, software containers, dedicated servers

### Which CSP's offering Serverless  

![Created a YAML config file and integrated it with AWS CloudFormation.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1657547914815/Zqq8c4IQh.jpg align="center")

### References

[Building Microservices: Designing Fine-Grained Systems](https://www.google.com/search?rlz=1C1PRFI_enIN981IN997&sxsrf=ALiCzsYU17pxjJcCd5KIki6-DCa9K6s4RA:1657550308471&q=Building+Microservices:+Designing+Fine-Grained+Systems&stick=H4sIAAAAAAAAAFWUzYvUSBjGO71Mb09GZ7t7XNA5tSPCMCCdyne8jOjoXhyEcQQPYph8VDofVUmqYpLq0-JZUAQHwYOy7MGDl716UPGmBw8KihcRb4J_gLsX7VG6snP85am36nmftyrduZWDo2AEgKNLsHYkJg9R6JKU-qQMXZ8Od4g7DgvfLa4Rf-ikaUxfCvsrZgwBiSWYTWbsalY8plnO9YgyrJo216mkJmVJuJ6bY5gncMbIxkGWWQZfD2oEI2DNOCrjSgU64PVqVkNJl2bseVUlJyrf3zFyS47y5vwsqjUNcL9jW7ENUpecFZhjUsW8voIFmti832CMM0mReX8kALDQXY3Xg8SkmDjcn8bUyoV8fRSAkgGSzDg3mQJN6vL1BTJA5DT-K1Zit-D148jRLTWXXwriCI0k3dNKqszEJKgLvfSa8PRp2IxOwz2wx7IMjNLI-SwhzhXmILmZnTIOIANNrzY2kRI0upNLnoG4HlixAsyGY0ePjbrgbMWSljfZevZEr3Fjd3p3Mg0pPKtMmpS2SZtZIc0lNuLZT--OTE27uWtUc2VkKE22Ji7UIOOz8dQAlTJp_NsAVY3fXFZilJkq5yyCoM721RsV1ho2pYJNPM7E0FS9yYcwS41U5n4SHrQXep-_flha3m3ffvTirXCzLfbOp9P3lbAtP9kpfG87HYzEzllchAUb_LZ8UFzYGycANJtIsXxI_LljrMfu2DOz3v2Pu8Lgkrhw0S-2083UCyEbnBtsiPObPnJ8Qi_AwTFRPJMmyfTRhike_L68JPZHLv8w-vGKVxa35vfOcQrbVZ4J7ZPt1fZKLl99_Hr3Vedy_8vdb9_uDbZOLa-u9cXORop2Qty_febUnbl_36-vLYnd7Z06xSli_cW__zn0qndlfeXo_P271p_Hqy_r_RvXhda7xSPPDv8ybK22wJu3v37s2P89XWtND7r-5OHzTrcr9Fpyu9uatA78NaefvhYmXoiD4eb__z0nhxs-DQO8J5wLsX_iDzJ14XvDi4wWPqK3OsJ3ZoRvr78EAAA&sa=X&ved=2ahUKEwjWptWKiPH4AhXB6jgGHdUEC2YQ-BZ6BAgQEAY&biw=1366&bih=638&dpr=1)
 
[Designing Distributed Systems: Patterns and Paradigms for Scalable, Reliable Services
](https://g.co/kgs/x9zGcA)
                            
[Hands-On Serverless Computing: Build, run and orchestrate serverless applications using AWS Lambda, Microsoft Azure Functions, and Google Cloud](https://www.amazon.in/Hands-Serverless-Computing-orchestrate-applications/dp/1788836650/ref=asc_df_1788836650/?tag=googleshopdes-21&linkCode=df0&hvadid=397009864213&hvpos=&hvnetw=g&hvrand=12927248821976648502&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=20453&hvtargid=pla-493342846784&psc=1&ext_vrnc=hi)

[AWS Lambda](https://aws.amazon.com/lambda/)

[Cloud Computing](https://g.co/kgs/zYu1bG)


<p>


Thank you for reading my blog. If you like my work feel free to connect -> <a target = "_blank" href= "https://www.linkedin.com/in/krishnamohanyerrabilli"> LinkedIn </a> or <a target = "_blank" href= "https://www.twitter.com/K_Mohan_">Twitter</a>, see you with another one guys.  😀 
