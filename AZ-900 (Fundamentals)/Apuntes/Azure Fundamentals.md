# Azure Fundamentals AZ-900
-----
## Cloud Computing

It's a delivery model for services like:
    - **Storage** (Data, Tools, ...)
    - **Compute Power** (Virtual Machines, Dockers, Functions, Applications, ...)
    - **Networking**
    - **Analytics**

There are more services, but those are the four main (all of this delivered by the **internet**)

![2.png](img/2.png)

The Cloud Computing also has some characteristics:
    - Scalability
    - Elasticity
    - Agility
    - Fault Tolerance
    - High Availability
-----
## Scalability

![1.png](img/1.png)

Scalability is the ability to scale

Scaling is a process of:
    - **Allocating** (adding) resources
    - **Deallocating** (removing) resources

-----
## Elasticity

![3.png](3.png)

Elasticity is the ability to scale dynamically

(If that scale is automatically, we're talking about automatic scaling which is elasticity)

-----
## Agility

![4.png](img/4.png)

Agility is the ability to react quickly, specifically abut allocating and deallocating resources


> **On-premise** means hardware in the area of the company

----
## Fault Tolerance

![5.png](img/5.png)

Fault tolerance is the ability to remain up and running during component and service failures


Disaster is a serious disruption of services caused by natural or human-induced causes (they can affect entires Azure's regions) and **Disaster Recovery** is the ability to recover from that event by replication of the data in different regions for example

![6.png](img/6.png)

-----

## High Availability

![7](img/7.png)

Availability is a measure of system uptime for users/services which is measured by porcentage

**High availability** is the ability to keep services running for extended periods of time with very little downtime (the downtime refers to the maintenance which needs to turn off the services while the course)

- Each company decide how many 9's the availability need to have in order to consider the service **High**

- They also decide to express the availability in terms of year, month or day

- Depending of the criticaly of your system, you need to choose whenever this system should be highly available or not (in Azure, many services has high availability by default)