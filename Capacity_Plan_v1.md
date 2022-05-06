# Capacity Plan

The SRE transformation movement that ABI is going through aims to optimize the reliability of the development process and, for that, it involves the adoption of some methods and practices. Among these, we can mention the PRR (Production Readiness Review), a process that reviews the quality of the delivery of a new system, or a new version of an existing system, and its infrastructure changes, before its implementation in the production. PRR validates important points for the development process, aiming to reduce the probability of new system releases causing unintended adverse impact to the company's business and its end users. The first of these points is the existence of a robust and assertive capacity plan, capable of accurately pointing out the volume of the structure needed to support what was developed.

In modern software environments, like those built on scalable microservices architectures, hitting capacity limits is a common cause of production-level incidents. It’s also, arguably, a type of incident teams can often prevent through proactive planning.

## What is

Capacity planning is work teams do to make sure their services have enough spare capacity to handle any likely increases in workload, and enough buffer capacity to absorb normal workload spikes, between planning iterations. This plan addresses the number of container instances and some resource types per instance, such as CPU, memory, storage, network throughput, TPS, latency, IOPS and concurrent clients.

During the capacity-planning process, teams answer these four questions:

1. How much free capacity currently exists in each of our services?
2. How much capacity buffer do we need for each of our services?
3. How much workload growth do we expect between now and our next capacity-planning iteration, factoring in both natural customer-driven growth and new product features?
4. How much capacity do we need to add to each of our services so that we’ll still have our targeted free capacity buffer after any expected workload growth?

The answers to those four questions—along with the architectures and uses of the services—help determine the methodology our teams use to calculate their capacity needs.

### Determining free capacity

There is three common methodologies to calculate how much free capacity exists for a given service:

1. Service-starvation
2. Load-generation
3. Static-resource analysis

#### Service-starvation analysis
Service starvation involves reducing the number of service instances available to a service tier until the service begins to falter under a given workload. The amount of resource “starvation” that’s possible without causing the service to fail represents the free capacity in the service tier.

For example, a team has 10 deployed instances of service x, which handle 10K RPM hard drives in a production environment. The team finds that it’s able to reduce the number of instances of service x to 8 and still support the same workload.

This tells the team two things:
- A single service instance is able to handle a max of 1.25K RPM drives (in other words, 10K drives divided by 8 instances);
- The service tier normally has 20% free capacity: Two “free” instances equals 20% of the service tier.

#### Load-generation analysis

Load generation is effectively the inverse of service starvation. Rather than scaling down a service tier to the point of failure, you generate synthetic loads on your services until they reach the point of failure.

A percentage of your normal workload then is based on the amount of synthetic workload that you were able to successfully process. This represents the free capacity in your service tier.

#### Static-resource analysis

This approach involves identifying the most constrained computational resource for a given service tier (typically, CPU, memory, disk space, or network I/O) and determining what percentage of that resource is available to the service as its currently deployed.

Although this can be a quick way to estimate free capacity in a service, there are a few important gotchas:

- Some services have dramatically different resource consumption profiles at different points in their lifecycle (for example, in startup mode versus normal operation);
- It may be necessary to look at an application’s internals to determine free memory. For example, an application may allocate its maximum configured memory at startup time even if it's not using that memory.

No matter which methodology you choose, experiment during both peak and non-peak workload periods to get an accurate understanding of what the service can handle.

## How to use the plan

The use of the plan occurs through the Capacity_Planning_vLive spreadsheet, composed of a series of quantitative items whose completion is divided into two moments, which are better detailed below.

### 1st moment
Some requirements estimated according to the implemented architecture for the service to work properly should be pointed out. The items of this moment are identified by the column "Moment" (1st moment) in the spreadsheet and also at the end of this document.

### 2nd moment

In the second moment, the current free capacity of the service (from the adopted methodology), the target free capacity and the expected workload growth until the date for next capacity planning must be determined. From these data, the quantities of each resource to be added to the service are calculated and predicted. The items of this moment are identified by the column "Moment" (2nd moment) in the spreadsheet.

## 1st moment items

| i | Item                                                  | Answer |
| - | ----------------------------------------------------- | ------ |
| A | Service tier size (# of hosts or container instances) |        |
| B | CPUs per service instance                             |        |
| C | Memory per service instance                           |        |
| D | Storage per service instance                          |        |
| E | Network throughput per service instance               |        |
| F | TPS per instance                                      |        |
| G | Maximum acceptable latency                            |        |
| H | IOPS                                                  |        |
| I | Number of concurrent clients                          |        |

