---
title: "MSc thesis projects"
permalink: /msc-student-projects-2/
---

The partners in the Nordic-IoT Hub invite MSc students to make their Master’s thesis project at the various departments. Students making their project at one of the departments associated with the Nordic IoT Hub can obtain support to travel and visit other Nordic Hub partners to exploit their knowledge, equipment and infrastructure. You may find more information on the various qualifications of the Hub partners at www.nordic-iot.org

##### 

#### MSc student projects at DTU-Compute** (tentative list)**:

Project #1  
**A test case generator for TSN**Deterministic real-time communication for critical applications has been required for realization of Industrial IoT [1] which brings computation closer to the industrial machines. The criticality of industrial applications needs evidences which shows certain degrees of deterministic behavior in the system architecture such as communication. IEEE 802.1 Qbv Time Sensitive Networking (TSN) task group [2] has standardized capabilities of Ethernet Networks which impacts on the deterministic behavior of communication. To solve the problem of having deterministic behavior over TSN, the scheduling of traffic in IEEE 802.1 Qbv has been proposed which simply says that the scheduling of traffic passing through each node creates a deterministic behavior on the network [3,4]. The traffic scheduling becomes an optimization problem for different applications with different objectives such as minimum latency for traffics, minimum jitters, etc. A tool has been developed in DTU compute which schedules traffic in TSN with respect to different criteria. In order to verify the scheduling tool, test cases in which traffic is characterized in critical situations are need.The purpose of this project is to develop a tool which generates test cases for our scheduling tool.  
[1]: Pop, Paul, et al. “Enabling fog computing for industrial automation through time-sensitive networking (TSN).” *IEEE Communications Standards Magazine* 2.2 (2018): 55-61.  
[2]: IEEE, “Official Website of the 802.1 Time-Sensitive Networking Task Group,” http://www.ieee802.org/1/pages/tsn.html, 2016.  
[3]: Oliver, Ramon Serna, Silviu S. Craciunas, and Wilfried Steiner. “IEEE 802.1 Qbv gate control list synthesis using array theory encoding.” *2018 IEEE Real-Time and Embedded Technology and Applications Symposium (RTAS)*. IEEE, 2018  
[4]: Craciunas, Silviu S., et al. “Scheduling real-time communication in IEEE 802.1 Qbv time sensitive networks.” *Proceedings of the 24th International Conference on Real-Time Networks and Systems*. ACM, 2016.

Project #2  
**Integrated routing and scheduling of traffic in IEEE 802.1 Qbv**Deterministic real-time communication for critical applications has been required for realization of Industrial IoT [1] which brings computation closer to the industrial machines. The criticality of industrial applications needs evidences which shows certain degrees of deterministic behavior in the system architecture such as communication.  
IEEE 802.1 Qbv Time Sensitive Networking (TSN) task group [2] has standardized capabilities of Ethernet Networks which impacts on the deterministic behavior of communication. To solve the problem of having deterministic behavior over TSN, the scheduling of traffic in IEEE 802.1 Qbv has been proposed which simply says that the scheduling of traffic passing through each node creates a deterministic behavior on the network [3,4]. The traffic scheduling becomes an optimization problem for different applications with different objectives such as minimum latency for traffics, minimum jitters, etc. A tool has been developed in DTU compute which schedules traffic in TSN with respect to different criteria. The tool uses Constraint Programming (CP) as the approach for optimization.  
Other than scheduling of traffic, the deterministic behavior of the network needs the routing to be determined. The routing problem is also an optimization problem which can be defined for various objectives [5]. A tool for routing of traffic has been developed in DTU Compute which design the routing based on given objectives with Constraint Programming.  
The purpose of this project is to merge the scheduling tool with the routing tool in order to find the optimal configuration of network based on the given objectives.

[1]: Pop, Paul, et al. “Enabling fog computing for industrial automation through time-sensitive networking (TSN).” *IEEE Communications Standards Magazine* 2.2 (2018): 55-61.  
[2]: IEEE, “Official Website of the 802.1 Time-Sensitive Networking Task Group,” http://www.ieee802.org/1/pages/tsn.html, 2016.  
[3]: Oliver, Ramon Serna, Silviu S. Craciunas, and Wilfried Steiner. “IEEE 802.1 Qbv gate control list synthesis using array theory encoding.” *2018 IEEE Real-Time and Embedded Technology and Applications Symposium (RTAS)*. IEEE, 2018  
[4]: Craciunas, Silviu S., et al. “Scheduling real-time communication in IEEE 802.1 Qbv time sensitive networks.” *Proceedings of the 24th International Conference on Real-Time Networks and Systems*. ACM, 2016.  
[5]: Gavrilut, Voica, et al. “Fault-tolerant topology and routing synthesis for ieee time-sensitive networking.” *Proceedings of the 25th International Conference on Real-Time Networks and Systems*. ACM, 2017.

Project #3  
**Incremental Scheduling of Tasks in Real-Time systems**The scheduling of tasks is an NP-complete problem [1] and it is important since it impact the non-functional properties of tasks because of the timing of execution. The static cyclic scheduling provides more deterministic behavior of task execution and eventually deterministic behavior for non-functional properties.  
Guaranteed non-functional behavior of tasks in critical applications has been required for realization of Industrial IoT which brings computation closer to the industrial machines. The realization of Industrial IoT needs a configuration of processing element which guarantees the non-functional properties of tasks such as Quality of Control [2] for critical control applications. QoC-ware scheduling is an approach to provide the required guarantees for tasks in scheduling [3]. Several tools have been developed to analyze the QoC [4, 5, 6].  
The purpose of this project is to apply a new approach called “Incremental Scheduling” of tasks which provides more flexibility to the schedule and provide better solutions.

[1]: Ullman, Jeffrey D. “NP-complete scheduling problems.” *Journal of Computer and System sciences* 10.3 (1975): 384-393.  
[2]: Seto, Danbing, et al. “On task schedulability in real-time control systems.” *17th IEEE real-time systems symposium*. IEEE, 1996.  
[3]: Barzegaran, Mohammadreza, Anton Cervin, and Paul Pop. “Towards quality-of-control-aware scheduling of industrial applications on fog computing platforms.” *Proceedings of the Workshop on Fog Computing and the IoT*. ACM, 2019.  
[4]: Cervin, Anton, et al. “Using jittertime to analyze transient performance in adaptive and reconfigurable control systems.” *2019 24th IEEE International Conference on Emerging Technologies and Factory Automation (ETFA)*. IEEE, 2019.  
[5]: Cervin, Anton, et al. “How does control timing affect performance? Analysis and simulation of timing using Jitterbug and TrueTime.” *IEEE control systems magazine* 23.3 (2003): 16-30.  
[6]: Ohlin, Martin, Dan Henriksson, and Anton Cervin. “TrueTime 1.5-reference manual.” (2016): 11.

Project #4  
**Modeling and Analysis of TSN Networks With AADL**Architecture Analysis and Design Language[2] is a well-known modelling language in the domain of real-time critical systems. It provides the ability to model large-scale architectures from many aspects in a single analyzable model via its strong syntactic and semantic support for the description of both hardware and software architectures.  
AADL is supported by several tools, covering many engineering steps, from modeling down to various steps of analysis such as scheduling, safety and reliability, model checking and code generation. These allow the analysis of system designs before development and supports an architecture-centric, model-based development approach throughout the system lifecycle.  
However, there is no support for AADL to model the networking system of integrated or distributed safety-critical systems, which require time-critical communication between different components of the system. The goal of this project is to provide an extension for AADL to support modelling and analysis of embedded real-time systems interconnected using Time-Sensitive Networking (TSN)[2], which extend the IEEE 802.1 standards for safety-critical and real-time applications.

[1]: Architecture Analysis and Design Language. [www.aadl.info](http://www.aadl.info/)  
[2]: TSN Task Group. Time-Sensitive Networking. 2017 [www.ieee802.org/1/pages/tsn.html](http://www.ieee802.org/1/pages/tsn.html)

Project #5  
**TSN configuration optimization using Constraint Programming and Network Calculus**Time-Sensitive Networking (TSN) [1] is an upcoming set of Ethernet standards designed for real-time and safety-critical applications, used in domains such as automotive, industrial automation, avionics and aerospace. It must comply with strong real-time requirements, thus validating end-to-end latency bounds of streams is particular important.  
Network Calculus (NC) [2] is a mature min-plus algebra-based theory proposed for deterministic performance analysis, such as the computation of the worst-case latency of a flow transmitted over a network. The approach in network calculus is to construct appropriate arrival and service curve models for the investigated flows and network nodes. On one aspect, it is a good method for the timing verification; on the other aspect, it can be used as the feedback for the configuration of the network, if the timing requirements are violated.  
Constraint Programming (CP) [3] is an approach for formulating and solving discrete variable constraint satisfaction or constrained optimization problems that allows for a wide variety of constraints. It is a good method used for scheduling and configuration problem in TSN networks.  
There are several existing NC-based timing analysis tools and configuration scheduling tools for TSN networks. However, they are independent from each other. Thus when configuring, it needs to constantly call the timing analysis tool, which is very time consuming.  
The purpose of this project is to construct constraints related to the Network Calculus formula into the Constraint Programming, to reduce the search space in order to improve the speed for network configuration.

[1]: TSN Task Group. Time-Sensitive Networking. 2017 [www.ieee802.org/1/pages/tsn.html](http://www.ieee802.org/1/pages/tsn.html)  
[2]: J. Y. Le Boudec, and P. Thiran, “Network Calculus: A Theory of Deterministic Queuing Systems for the Internet,” *Springer-Verlag Lecture Notes in Computer Science*, 5th ed., ISBN: 3-540-42184-X, 2001.  
[3]: Google OR-tools. <https://developers.google.com/optimization>
