# WM

# Technical Assignment Answer

Your assignment is to develop a simple API that computes an optimized itinerary solving the [Traveling Salesman Problem](https://developers.google.com/optimization/routing/tsp/tsp).

### POST /routeOptimizer

- This method should consume the list of tasks, with their durations and coordinates, and return a **schedule**, that takes into account both the travel time between those points and the duration of the task at each point.
- The method should return the most efficient route, that accounts for **driving time**
- The task schedule returned should also take the **home coordinates** into account. *Example : If the first task is 30minutes away, and the departureTime is set to 09:00am, the first task should be scheduled at 09:30*

How TO setup :

1. install node modules from package.json => npm install
2. lunch tests => npm test
3. to lunch server => node ( or nodemon ) index.js
4. enjoy

## Analysis of the Problem

Suppose we have a home point [H] and 3 waypoint [A,B,C] with a duration of stop at each [S1,S2,S3] respectively


### CASE 1 : No trafic effects included

- we can get optimal Order via google API without taking into account the duration of stops
- for example : the optimal Order may be [B,A,C] with the duration of travels for a round trip [H->B , B->A, A->C, C->H ] are [D1,D2,D3,D4]
- with knowledge of time departure at home t0, we can generate the following result using the syntaxe [POINT,Start_time,End_time] :
- [H,t0,t0] -> [B,t0+D1,t0+D1+S1] -> [C,t0+D1+S1+D2,t0+D1+S1+D2+S2] and so on. We have now as output the ordered tasks taking into account duration

### CASE 2 : taking into account trafic effects

to do

## Solutions

  ### solution A

      * We google Directions API to get optimized node order, then reorder them and add duration of tasks

 ### solution B

      * We can use Google Directions Matrix to get distance between all nodes
      * compute algorithm to resolve TSP

 ### solution C

       * Using RouteXL (based on OSM)

 ### Solution D

       * Using Graphhopper (based on OSM)

 ### Solution for Bonus

      * Use recursive function to take into account estimated trafic

## Dev Environnement

* Node Js
* Atom Editor
* Code Linting : JsLint pluging for atom  ==> Code validation on file save

## Testing Environnement

I have set up Environnement for TDD : test driven developpement

* PostMan : to help build and test Restful API
* nodemon : Nodejs server auto-reload  and watching file changes
* mocha,chai,chaiHttp : testing API and functions
* istambul : testing coverage

```
To test developpement => in the folder /Wemaintain => do npm test
```

## List of steps :

- Endpoint that takes a list of tasks and their locations and return optimal schedule minimizing driving timeout
- Take list of location and get optimal road minimizing time using google Directions API [ DRIVING , OPTIMIZE ]
- Since the travel is optimal and trafic is not taken into account, we could just add tasks duration.

## Optimisation

- In order to get google Direction API optimise and recognize waypoint, it should take STOPs location not just any location => use ROAD API to convert location to nearest road location
- for tests, I've used location waypoints.
- Google Directions API return as result nearest road location to waypoints.
