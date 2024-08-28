# DroneSimulation
**Note: This only contains the ReadMe file of our final submission; per the course syllabus for this assignment, source code is not allowed to be shared.**

﻿Team number: team-001-22
Member names: Peter de Ruiter & Matthew Jenson


Youtube Demo: https://youtu.be/OVq_0nR32qg

Docker Link: https://hub.docker.com/r/derui019/final-project

UML Link: https://drive.google.com/file/d/1LQNQUIy2ijhVVcucfuIAX__AC8nSJzdz/view?usp=sharing 


What is the project about?: This should be an overview of the whole project, not just your extension


This project is a drone simulation running on the University of Minnesota - Twin Cities campus that utilizes a drone to pick up a specified package and deliver it to any specified location. As the drone is flying, the drone's battery will drain at a constant rate; if the battery's life is above 50%, the drone will be green. When the drone's battery life gets below 50%, the drone will turn yellow, signaling a low battery. When the drone's battery life is below 25, an alert will be sent to the UI saying that the drone's battery is critically low and needs to be charged, and the drone's color will turn red. When the drone's battery hits 25%, it will navigate to the nearest recharge station and recharge its battery back to 100%. The drone will turn back to green and continue on its route.


How do you run the simulation? This should also be an overview of the whole project, not just your extension. 


To run the simulation in the terminal, compile the code by running the command make -j, then to run the program, use the command make run. A server should be created at your specified port, and you utilize the simulation. In the simulation, you can schedule a package delivery by clicking the Schedule Trip button, selecting a start and end destination, and then naming the route; the first available drone will carry out the delivery in the order in which the trips were scheduled. You are able to add additional humans and drones to the simulation by clicking there corresponding Add buttons. To stop the simulation, click the Stop Simulation button, and the simulation will terminate.


What does the simulation do specifically? This should be an overview of the entire project and cover individual features such as movement of entities, etc. 


The simulation consists of a map of our campus. There are several entities that live on the map, like robots, drones, and humans. Entities can all move around the map using strategies that consist of pathfinding techniques, destinations, etc. 


The user can create a new drone. Deliveries can be scheduled for a drone, which consists of a package and a pickup and drop-off location. When assigned, the drone beelines it to the pickup location and gets the package. It then travels to the dropoff location using a strategy (pathfinding strategy) specified by the package's strategy. As the drone moves, its battery level is depleted over time. We extended the simulation to allow for the drones to be powered by batteries and to allow them to be recharged at stations in specified locations around the map. If the drone does not reach the station, it dies and is no longer accessible. The recharging happens when the drone reaches the station and finishes after around 10 seconds. The drone will then continue en route to the package drop-off location, where it will drop off the package and celebrate differently depending on the type of pathfinding strategy used.


New Feature: Drone Battery and Recharge stations
What does it do? 
The feature gives each drone a battery with a specified battery life; as the drone's battery drains, the color of the drone changes from green to yellow to red, corresponding with the drone's battery life. When the drone's battery life is below 25%, it finds the nearest recharge station around campus and flies to it. When the drone arrives, the drone “lands” at the station and waits 10 seconds (until fully charged). The drone's battery is then fully charged and turns back to green. The drone then leaves the recharge station and continues on its flight.


Why is it significantly interesting? 


This extension adds an element of realism to the simulation. The same principles can also be used in other scenarios or in real life when limitations (like battery power) are real and must be managed.


How does it add to the existing work?


We have added batteries to drones and recharge stations around the map. The drones now have a limited range for flight, and when they get low, they go to the nearest recharge station and charge back to full.


Which design pattern(s) did you choose to use in your implementation, and why? 


We used three design patterns to implement our feature.


The first and most important is the decorator design pattern. We used this design pattern when creating a decorator class, which wraps an IStrategy and manages all battery-related functionality for the entity. We chose this because it decoupled the battery functionality from the entity and placed it in a separate class, which can be modified and changed without affecting the drone itself. The battery-powered decorator manages the drone's regular movement as it delivers its packages. It also keeps track of its battery level and sends it to the nearest recharge station when necessary.


The second design pattern we used was the facade. It creates an interface for the simulation model to create new recharge stations because the recharge station entity does not take in a json file as a constructor. Instead, the simulation model uses this interface (or “facade”) to create them.


The final one used is the singleton design pattern. We used this to create the recharge station manager. Only one recharge station manager exists in the program, and it allows other classes to query it and access useful functionality for finding the nearest recharge station. It contains and manages the recharge stations. A pointer to this singleton is then given to functions and classes that need to access the recharge stations.


Instructions to use this new feature. If the new feature is not user-interactable, please mention this as well.


The new feature is not interactable. The simulation can be operated normally. However, you will notice that the drones now have a light on the top, representing their battery level. And you will now see how there are large structures dotting the campus. These are recharge stations, and when you send your drone on a mission to deliver a package, it will now have a battery, which may need to be recharged before it reaches the destination. It is unlikely that it will need to be recharged on the first delivery.


Sprint Retrospective 


The spring was relatively uneventful; we divided up the work at the beginning of the sprint as directed. Throughout the sprint, specific tasks were found to be no longer needed, and some new ones were added. These were managed at scrum meetings in which we reached a solution on who would pick up the new work. If we could do it again, it would be clearer how to specifically take advantage of the idea of a sprint because now we are more familiar with it.
