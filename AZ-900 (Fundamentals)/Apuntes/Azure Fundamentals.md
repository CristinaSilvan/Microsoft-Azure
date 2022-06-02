# Azure Fundamentals AZ-900
---
---
>[Link to the exam](https://docs.microsoft.com/en-us/learn/certifications/exams/az-900)

>[Learning Path by Microsoft](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-cloud-concepts/?ns-enrollment-type=exam&ns-enrollment-id=exam.az-900)
-----
-----
# Cloud Computing and Vocabulary
## Cloud Computing

It's a delivery model for services like:
- **Storage**: like files and/or databases
- **Compute Power**: meaning servers such as windows, linux, hosting environments, etc.
- **Networking**: in azure but also outside when connecting to your company network
- **Analytics**: services for visualization and telemetry data

There are more services, but those are the four main (all of this delivered by the **internet**)

![2.png](img/2.png)

The Cloud Computing also has some characteristics which make them so useful:
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

![3.png](img/3.png)

Elasticity is the ability to scale dynamically

(If that scale is automatically, we're talking about automatic scaling which is elasticity)

-----
## Agility

![4.png](img/4.png)

Agility is the ability to react quickly, specifically abut allocating and deallocating resources

> **On-premise** means hardware in the area of the company (the opposite of cloud)

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

The way we measure it: **availability = uptime/(uptime + downtime)**

**High availability** is the ability to keep services running for extended periods of time with very little downtime (the downtime refers to the maintenance which needs to turn off the services while the course)

- Each company decide how many 9's the availability need to have in order to consider the service **High**

- They also decide to express the availability in terms of year, month or day

- Depending of the criticaly of your system, you need to choose whenever this system should be highly available or not (in Azure, many services has high availability by default)

-----
-----
-----
# Principle of economies of Scale
## Economies of Scale

![8.png](img/8.png)

![9](img/9.png)

The principle of economies of scale states that as the companies grow they become **more effective** at managing shared operations. Be that HR and hiring, taxes, accounting, internal operations, marketing, big purchases via contracts meaning better discounts, etc

Because of those, companies can save/earn more which in return allows for **reduction in cost** of their services to their customers. This is so called **price per unit**

It’s not possible to go to 0 because in the end some underlying infrastructure needs to run to provide the services. But the larger the scale the **more benefits can be passed to customers**

In fact, in the current scale, Microsoft can already offer multiple services for free due to how small a fraction of the cost it is for them

---
---
---
# CapEx vs OpEx and their differences
## Capital Expenditure (CapEx)

![10](img/10.png)

- Basically means, buying your **own infrastructure** and maintain it

- It requires a **big initial investment**

## Operational Expenditure (OpEx)

![11](img/11.png)

- It is about **renting infrastructure**

- There is no **initial investment** since you pay for **what you use**, scaling the services when need it

- The **maintenance** is up to you, which means it depends on what kind of renting are you in (but in general, the rent of the infrastructures came with services to maintain themself and working staff who manage it without you to hire no one)

## Differences

![12](img/12.png)

To sum up, **CapEx** is related to **On-premise** infrastructures, while **OpEx** is related to the **Cloud**