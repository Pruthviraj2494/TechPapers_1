# SOA: Performance and Scalability Challenges and Solutions


## Service-Oriented Architecture (SOA)
   Service-Oriented Architecture is a style of software design where services are provided to the other components by application components, through a communication protocol over a network. Its principles are independent of vendors and other technologies. In service oriented architecture, a number of services communicate with each other, in one of two ways: through passing data or through two or more services coordinating an activity. This is just one definition of Service-Oriented Architecture. The challenge in delivering SOA-based applications lies in identifying where potential problems will arise and addressing them as early in the deployment cycle as possible. Application delivery controllers are well suited to addressing both the wellunderstood and unanticipated issues associated with delivering SOA-based applications. Incorporating an application delivery controller into the deployment plans for your SOA can prevent unnecessary delays and even the need to re-architect portions of your SOA infrastructure—saving man hours, expense,
and headaches.

<img style="width:400px; height:400px" src="https://www.einfochips.com/blog/wp-content/uploads/2017/oldblog-images/service-oriented-architecture-soa.png"/>

### Performance Challenges and Solutions

> **Overview:** *In the service-oriented architecture (SOA) concepts such as loose coupling may have negative impact on the overall execution performance of a single request. There are ways to facilitate high performance applications which benefit from this kind of architectural style compensating the caused overhead significantly. This report gives an overview on high level strategies to improve the performance of SOAs with a central service bus and presents how to apply them to build high performance service-oriented applications without corrupting the SOA paradigm and concepts on the technical level.*


#### Introduction
   The key concepts of service-oriented architectures (SOAs) such as loose coupling, interoperability, or abstraction may have negative impact on the overall performance of applications. The reasons are additional costs for time-consuming operations such as message format transformations, dynamic service discovery, etc.
   
   
#### Related Work
  This report I will try show how a set of high level strategies can be applied to improve the performance of a SOA application without corrupting the underlying SOA concepts. Other work in the area of SOA performance improvements are focusing on the technical level. One example for technical improvements are performance best practices considering optimization strategies focusing on message processing, message structure, and message design of XML based protocols.

#### High Performance Strategies
  In this section I present six strategies which enable high performance service oriented applications without corrupting the underlying SOA concepts namely ``` Parallel Processing, Caching, Dynamic Service Discovery, Dynamic Service Migration, Multiple Service Instantiation, and Multiple Service Invocation ```. Each strategy targets performance issues on an architectural level. 

* ##### Parallel Processing

  This strategy is implimented to increasing the internal throughput of requests in the application to improve the overall application performance.
Assuming that each service is hosted on its own physical environment and therefore isolated from each other regarding performance. Thus, multiple concurrent service executions do not influence the performance of each other. An application implemented as SOA consists of different services orchestrated together to provide new functionality: The application receives a request, invokes several services and thereby delegates tasks to them needed to provide the overall application functionality. This concept is called ```Programming in the large```. If the invocations are independent from each other they can be done in parallel at the same time which increases throughput and therefore the overall processing performance. The distributed computing paradigm of service-oriented architectures enables this feature. The strategy has to be implemented in clients.

* ##### Caching
  This strategy is used to avoid multiple processing of identical requests to speed up the application’s performance.The requests have to be comparable in a way that identical requests can be recognized. One opportunity to improve the performance of an application’s request processing is to avoid the actual request processing at all by exploiting caching. The service bus is the central component which is responsible for any primary service request message consumption: Clients send request messages to the bus which routes the messages to selected services and the responses back to the corresponding requestors. For certain requests the responses are always the same, e.g. a matrix equation solving service returns always the same solution for the same requested equation. These requests can be cached by the service bus to decrease the response time.

* ##### Dynamic Service Discovery
  This strategy is to choose the fastest service for a certain request at runtime to decrease the response time.To select the fastest service, all available suitable services have to be comparable in their performance for processing a certain request. This performance values have to be predictable automatically (either by the service bus or by the respective services). One can distinguish between two different binding techniques: Static
binding and dynamic binding. The first one enables the client to explicitly define which service should be used while the latter one sends the request to the service bus which discovers a service matching the functional requirements of the request and then sends the request to this selected service. This service discovery can be enriched by taking non-functional requirements expressing capabilities into account, too. If there are functionally equivalent services, non-functional capabilities of the service are analyzed to select the service guaranteeing the fastest response time. This enables optimized load balancing, too. The Dynamic Service migration strategy may be applied to optimize the services before comparing them. The strategy has to be implemented in the service bus to enrich the service discovery.

* ##### Dynamic Service Migration
   This strategy is to achieve the fastest response time for processing a request regarding the environment and location conditions a service is hosted on. To apply this strategy, the migration of services has to be feasible. There are services whose response time to process a request depends on
the power of the environment they are hosted on. The Dynamic Service Migration strategy moves services from less powerful machines to more powerful ones to scale up. Other scenarios increasing the performance are the migration of one service collocated to another service to cut down network costs or the migration of other services hosted on the same environment to other environments to free resources. This component-based migration is possible because of the loose coupling concept of SOA. The strategy may be implemented in the service bus which triggers and manages the migration.

* ##### Multiple Service Invocation
  this strategy is to choose the fastest service for a certain request at runtime to decrease the response time. It is assumed that the multiple service invocations have no negative impact on the performance of other request processing services. The selection of the fastest service can be difficult, especially if there are completely different ways to process a single request. There are situations where the Dynamic Service Discovery strategy cannot be applied to discover the fastest service because the required values to compare the different services are not calculable. SOA offers a solution to achieve maximum request processing performance by sending the request to all available appropriate services concurrently and taking the
response returned by the first responding service. This decreases the response time to an ideal value as the fastest available service is implicitly chosen. To make this work, the different services have to be isolated in a way that they do not affect each other’s response time. The strategy has to be implemented in the service bus.

* ##### Multiple Service Instantiation
   This strategy is to increase the performance by invoking only services having free capacity. The current workload and utilization of a service has to be visible to the service bus to enable the selection of appropriate services and there have to be free resources for hosting the new instantiated services isolated in a way that the concurrent executions do not decrease the performance of each other. The performance of the overall system decreases if services cannot process a large number of requests any more. If there is no possibility to balance the outstanding workload differently, this strategy solves the problem by instantiating more services functionally equivalent to the overloaded ones. The new instantiated services can be invoked in parallel and hence scale out. The distribution of the workload discharges overloaded services and thus increases the throughput. The strategy
may be implemented in the service bus.


### Scalability Challenges and Solutions

  > **Overview:** *Making solutions scale is nothing new. However, the SOA technology and approaches recently employed are largely untested with higher application and information and service management traffic loads. SOA implementers were happy to get their solutions up-and-running, however in many cases scalability is simply not a consideration within the SOA, nor was load testing, or other performance fundamentals. We are seeing*


***Scalability*** refers to the number of users, sessions, transactions, and operations that can be accommodated by the entire system. Simply put, scalability is about doing what you do in a bigger way: Scaling a Web application means allowing more people to use the application by growing it to meet growing demand, without changing the code or sacrificing the data affinity and service levels your users demand. Why is scalability important? Because, in the end, you ideally want to build an application that can serve millions of users with zero downtime. Several organizations build a jumble of applications that don’t conform to set standards and don’t share a cohesive deployment pattern. This reduces their ability to iterate on product development and thereby creates a lag in business. Adopting a scalable platform architecture that covers all applications is a way to solve this problem.

   The core issue is that many SOA technology vendors have not focused on scalability within their solutions. Instead, feature/function enhancements are the rule of the day. It's more important to add orchestration features and more adapters to your solution than to figure out how to pump more information, and manage more services. Thus, these single threaded solutions, on top of the issues around Web services in general, make for solution that are more about integration than true business transaction loads.

   Dependence on the traditional architectures is the core problem of scaling SOA solutions. The most popular SOA technologies require that all information and services under management do so within a single server domain (in most cases). This processing is a mixture of service abstraction, service management, schema and content transformation, rules processing, message splitting and combining, as well as message routing (ESBs). This is despite the fact that Web services, at their essence, are more about distributed service invocation model that is not as well followed.

   Software Pipelines, the approach and the instance of technology (Hydra), increases scalability by providing concurrent computing of business services within, and across servers, while preserving business rules. For those of use who've been in the business for a while, this is really common sense scalability, meaning that the processing is distributed across more than one processing entity, and thus the throughput increases using this parallel processing model. As long as this distribution is managed well…it's very effective.


## Way forward
 Many of the challenges associated with SOA deployments are the same challenges we've encountered when deploying traditional web-based applications. The
underlying causes of these challenges may differ in a SOA, but the solutions to address those challenges remain the same. The key to addressing SOA-related challenges is to identify them as early as possible and include the appropriate solution in the architecture to reduce the possibility of re-architecture being required in a post-deployment environment.
