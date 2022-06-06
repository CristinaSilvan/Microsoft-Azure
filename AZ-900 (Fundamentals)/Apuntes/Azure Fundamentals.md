# Azure Fundamentals AZ-900
---
---
>[Link to the exam](https://docs.microsoft.com/en-us/learn/certifications/exams/az-900)

>[Learning Path by Microsoft](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-cloud-concepts/?ns-enrollment-type=exam&ns-enrollment-id=exam.az-900)
-----
-----
# Cloud Computing and Vocabulary
## Cloud Computing

**Cloud Computing** is the renting of resources in the **data center** of other company

It's a delivery model for services like:
- **Storage**: like files and/or databases
- **Compute Power**: meaning servers such as windows, linux, hosting environments, virtual machines, containers, serverless, etc.
- **Networking**: in azure but also outside when connecting to your company network
- **Administration and Analytics**: services for visualization and telemetry data

There are more services depending on **which Cloud Provider**, but this are the main four in common (all of this delivered by the **internet**)

Some of the main **Cloud Providers** are:
- Microsoft
- Google
- Amazon

![2.png](img/2.png)

The Cloud Computing also has some characteristics which make them so useful:
- Scalability
- Elasticity
- Agility
- Fault Tolerance
- High Availability

Other benefits are:
- Geo-distribution
- Consumption-based model
-----
## Scalability

![1.png](img/1.png)

Scalability is the ability to scale

Scaling is a process of:
- **Allocating** (adding) resources
- **Deallocating** (removing) resources

Apps in the cloud can scale vertically and horizontally:
- **Scale vertically** to increase compute capacity by adding RAM or CPUs to a virtual machine
- **Scaling horizontally** increases compute capacity by adding instances of resources, such as adding VMs to the configuration

-----
## Elasticity

![3.png](img/3.png)

Elasticity is the ability to scale dynamically

(If that scale is automatically, we're talking about automatic scaling which is elasticity)

-----
## Agility

![4.png](img/4.png)

Agility is the ability to react quickly, specifically abut allocating and deallocating resources

> **On-premise** means hardware in the area of the company (may refers to opposite of cloud, but also private cloud)

----
## Fault Tolerance

![5.png](img/5.png)

Fault tolerance is the ability to remain up and running during component and service failures


Disaster is a serious disruption of services caused by natural or human-induced causes (they can affect entires Azure's regions) and **Disaster Recovery** is the ability to recover from that event

By taking advantage of cloud-based backup services, data replication, and geo-distribution, you can deploy your apps with the confidence that comes from knowing that your data is safe in the event of disaster

![6.png](img/6.png)

-----

## High Availability

![7](img/7.png)

Availability is a measure of system uptime for users/services which is measured by porcentage

The way we measure it: **availability = uptime/(uptime + downtime)**

**High availability** is the ability to keep services running for extended periods of time with very little downtime (the downtime refers to the maintenance which needs to turn off the services while the course)

Depending on the service-level agreement (SLA) that you choose, your cloud-based apps can provide a continuous user experience with no apparent downtime, even when things go wrong

- Each company decide how many 9's the availability need to have in order to consider the service **High**

- They also decide to express the availability in terms of year, month or day

- Depending of the criticaly of your system, you need to choose whenever this system should be highly available or not (in Azure, many services has high availability by default)

## Geo-distribution

You can deploy apps and data to regional datacenters around the globe, thereby ensuring that your customers always have the best performance in their region

## Consumption-based model

Cloud service providers operate on a consumption-based model, which means that **end users only pay for the resources that they use**

- No upfront costs.
- No need to purchase and manage costly infrastructure that users might not use to its fullest.
- The ability to pay for additional resources when they are needed.
- The ability to stop paying for resources that are no longer needed.

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

---
---
---
# Consumption-based Model

![13](img/13.png)

The consumption-based model is a **pricing model** used in the cloud so that customers are only charged **based on their resource usage**

This model is characterized by:
- No associated upfront cost

- No wasted resources as such no charges are incurred for unused resources. Unused in this case is different per service. For instance, blob storage that stores any data is considered to be used, as it consumes the storage space. Virtual Machines that are running consume CPU, memory and other resources even if there isn’t any traffic. Hence they are considered to be used and will incur charges

- Pay for what you need

- Stop paying when you don’t

![14](img/14.png)

**Consumption is the virtual metric** used to calculate how much each resource (service) in Azure was used. Each service has many smaller metrics that track its consumption to offer best possible pricing model. Those metrics are tracked on very granular level

---
---
---
# Cloud Service Models responsibilities

![15](img/15.png)

**As a service** means which party will manage the particular layer and all the layers below

- **Software layer** consists the application (application code and set) & the application data

- **Platform layer** means all the supporting software and the operating system required to host the application

- **Infrastructure layer** consists hardware the infrastructure and virtualization required to host the platform

> If the customer owns the physical severs, that means they have their own data centers/server rooms. This is so-called **On-Premise Enviroment**

## Infrastructure as a Service (IaaS)

![16](img/16.png)

![18](img/18.png)

Use common cases:
- **Migration of workloads**
- **Test and development**
- **Storage, backups and recovery**

## Platform as a Service (PaaS)

![17](img/17.png)

![19](img/19.png)

Use common cases:
- **Development framework**
- **Analytics and business intelligence**

## Software as a Service (SaaS)

![20](img/20.png)

![21](img/21.png)

Use common cases:
- **Buying of-the-shell (license) applications**

## Comparation

![22](img/22.png)

**Responsibility Matrix:**

![23](img/23.png)

---
---
---
# Public, Private and Hybrid Cloud

**Cloud Deployment Model** is simple a separation which describes where are the company resources deployed. Whenever this is in public cloud provider environment or private datacenter

There are so many reason why this three models exists, in which are include **politics, security, cost and options about recovery**

## Public Cloud

![24](img/24.png)

![25](img/25.png)

## Private Cloud

![26](img/26.png)

![27](img/27.png)

## Hybrid Cloud

![28](img/28.png)

![29](img/29.png)

---
---
---
# Azure Infrastructure

## Data Center

Data Centers are **building blocks of global azure infractucture** which contain servers with **power electricity, cooling and networking by their own**

![30](img/30.png)

## Region

**A group of data centers that are connected with each other** with high throughput internet connectivity with **low latency network** (under 2 miliseconds latency)

They can be on **different sizes**, as small as a single data center or they can contain multiple ones

![31](img/31.png)

Regions are simply a geographical area on the planet and there are **more than 50**

There are special regions, like **government regions** (or government regulations) and **partner regions**

![32](img/32.png)

They are globally distributed for instances but **some services are available only in certain regions**, while others are considered globals services with are not assigned/deployed in an specific region

![33](img/33.png)

We choose the **region closest as possible to our client** for their services location (the closer it is, the lower the delay it is **between the servers and the client**)

## Availability Zones

An Availability Zone is a **Data Center in the same region** with reduncance or other way of protectiong from **data center's failures**

They're prepared to **redirect** the client workflow to other Data Center is something goes wrong so the client **doesn't even realize it**

![34](img/34.png)

- **Not all regions** are supported since not all regions has multiple data centers or those are not necesarely created for availability

- Supported regions has **three or more zones** at least (and they can be as the same time multiple **data centers**)

## Zones Categories

- **Zonal Services**: which allow us to **choose the availability zones** we are doing the deployment to

- **Zone-redundant**: replicate data through multiple availability zones and will work **in a redundant way** (the cloud provider decided where to allocate the replication)

![35](img/35.png)


## Region Pairs
 
If there is a Region Level Failure (the entire region goes down), the use of **Availability Zones doesn't matter becuase it only affect inside of the region**

That's why Microsoft also created **Regions Pairs**, in a enough distantce to cover **natural disasters** (**Physical isolation** with at least 300 miles distance (when possible))

This way, they create another level of security for your data, allowing you to replicate the data **in the region pairs** of the one you deployed your data

**Every region** is paired exactly with **one other region** (no more than one)

The **ragion pairs** are always in the same **geography** so customers can **maintain their data residency**

![36](img/36.png)
![37](img/37.png)
![38](img/38.png)

The plan updates will rollout **first in one pair region**, and when everything is working correctly, they'll proceed to update the **second pair region** so they avoid disasters to happen to the same paired regions

Making sure that even the **platform update** won't affect our applications

Some of them are not in the **same country**, but they have to be **close enough to maintain high speed connectivity**

They can also replicate into others regions, but **paired regions are preffered**

## Geographies

Everything before, is **grouped into geographies**

It's porpuse is that **all data leverl requirements are met**, like residency, sovereignty, resiliency and compliance

![39](img/39.png)
![40](img/40.png)

---
---
---
# Resources management

## What Resources Are
Resources is the **representation of our services** in Azure, like objects

Objects **used to manage services** in Azure

Azure use the resources to **save all the configuration** we make for our services

It also represent **the service lifecycle** of the recourse, so not only save configuration but **state** (such us the time used, the recoursed associated and if it's still renting or going to be delete)

All of this as the **properties of the object**

![41](img/41.png)

Every resource in Azure can be **represented as a Json template** that describe all this properties and values

![42](img/42.png)

There are **four common properties** in this Json formats across all resources:
- **Type**
- **Api Version**
- **Name**
- **Location**

## Resource Group

Everything created in Azure, **belongs to something called resource group** and **only belongs to that group**

A **resource group** is a **logical container** for resources related

It was created as a **utility to manage** and **organizate**

![43](img/43.png)

Resources groups have **their own location assigned** beside the resources themself **can reside in different locations**

The resources **can be moved** between the resources groups

> Resources groups **can't be nested**

## Organization

We can organize our resources in different ways, but the more common and **recommended** are:
- By Type:

![44](img/44.png)

- By Applications:

![45](img/45.png)

- By Department, Billing, Location (which is Azure Region) **or a combination of that**

This way it's **easier to manage data sovereignty and security**

> The organization **deppends on the needs**

## Resource Manager

However we communicate towards Azure, the same **Json template** is managed by a **common entity behind every interact**

That entity is the **Azure Resource Manager**

It is a **centralized service governing all resources** and groups of resources in Azure and it is the **responsible for creating** each service within Azure

It has an **unified template lenguage** so we always send the same **Json template form** with the same validations so everything is **consistent**

![46](img/46.png)

---
---
---