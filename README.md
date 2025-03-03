# Multithreaded Air Traffic Control System

Entities: Plane (Process): Passenger (with passengers, crew) or Cargo (with pilots). Airport (Process): Multi-threaded. Air Traffic Controller (Process): Single-threaded. Passenger (Process): Child of Passenger Plane. Cleanup (Process): Single-threaded. Tasks:

Plane Program (plane.c): Create separate plane processes. User inputs: Plane ID, Type (1 for Passenger, 0 for Cargo). For Passenger Planes: Input occupied seats, luggage weight, and body weight. For Cargo Planes: Input cargo items and average weight. Store details: Departure and arrival airports, plane ID, total weight, type, number of passengers. Communicate with the Air Traffic Controller.

Air Traffic Controller Program (airtrafficcontroller.c): Manage airports (2-10). Single message queue for communication. Log plane journeys to AirTrafficController.txt. Terminate only when all planes have landed and no planes are at any airport.

Cleanup Program (cleanup.c): Query for termination (Y/N). Inform Air Traffic Controller to terminate if Y.

Airport Program (airport.c): Create separate airport processes. User inputs: Airport number, number of runways, runway load capacities. Handle plane departures/arrivals using threads. Best-fit runway selection. Synchronization with mutex/semaphore.

Running the Programs:

Open Linux Terminal/Ubuntu.

Compile Programs: gcc -o plane plane.c -lpthread gcc -o airtrafficcontroller airtrafficcontroller.c -lpthread gcc -o cleanup cleanup.c -lpthread gcc -o airport airport.c -lpthread

3.Execute Programs in Order:

Start Cleanup when ready to terminate: ./cleanup
Start the Air Traffic Controller: ./airtrafficcontroller
Start Airports: ./airport
Start Planes: ./plane
