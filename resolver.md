# Technical Assignment Answer

Your assignment is to develop a simple API that computes an optimized itinerary solving the [Traveling Salesman Problem](https://developers.google.com/optimization/routing/tsp/tsp).

### POST /routeOptimizer

- This method should consume the list of tasks, with their durations and coordinates, and return a **schedule**, that takes into account both the travel time between those points and the duration of the task at each point.
- The method should return the most efficient route, that accounts for **driving time**
- The task schedule returned should also take the **home coordinates** into account. *Example : If the first task is 30minutes away, and the departureTime is set to 09:00am, the first task should be scheduled at 09:30*

# Solutions

  ## solution A
       => We google Directions API to get optimized node order, then reorder them and add duration of tasks

  ## solution B
        => We can use Google Directions Matrix to get distance between all nodes
        => compute algorithm to resolve TSP

  ## solution for Bonus
        => Use recursive function to take into account estimated trafic


** Dev Environnement **

-Node Js
-Atom Editor
-Code Linting : JsLint pluging for atom  ==> Code validation on file save

** Testing Environnement **

I have set up Environnement for TDD : test driven developpement

-PostMan : to help build and test Restful API
-nodemon : Nodejs server auto-reload  and watching file changes
-mocha,chai,chaiHttp : testing API and functions
-istambul : testing coverage

To test developement => in the folder /Wemaintain => do npm test


** List of steps **

  _ Endpoint that takes a list of tasks and their locations and return optimal schedule minimizing driving timeout
    _ Take list of location and get optimal road minimizing time using google Directions API [ DRIVING , OPTIMIZE ]
    _ Since the travel is optimal and trafic is not taken into account, we could just add tasks duration.

** Optimisation **

  _ In order to get google Direction API optimise and recognize waypoint, it should take STOPs location not just any location => use ROAD API to convert location to nearest road location
    _ For the tests, I've used location waypoints.
    _ Google Directions API return as result nearest road location to waypoints.
