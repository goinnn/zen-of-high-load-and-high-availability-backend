## Introduction

I am the CTO of [Joinup](https://joinup.es/) since early 2016, and by the end of the same year, we have a high availability (24x7) and high load backend (several thousand requests per minute). We are not on watch and we don’t have unexpected problems because we follow a list of basic rules: our Zen.

### Spanish version

There is a spanish version of this zen. Please click [here](index-es.html) to go to spanish version

### Our zen

Identify your bottlenecks.

Databases are one of the most common types of bottlenecks.

For each HTTP request, you must know, control, and optimize the number of queries made in the databases.

The speed of the query processing varies depending on its complexity. Comparing all the queries equally would be like comparing apples to oranges.  For each HTTP request, you must also know, control, and optimize the total time the queries need to be executed against the databases. 

Relational databases cannot be used for everything.

In the same way you must control and optimize the memory usage for each HTTP request. 

If the memory usage increases… analyze why!

You can compare memory to savings. If you have available memory, you can splurge once in a while, but avoid splurging. 

Lastly, control the overall time for each HTTP request. 

All requests to external systems should have a timeout. It is better to amputate an arm than dying of gangrene 

Have a background task system in your backend to maximize the foreground system’s speed (web server’s speed).  

Whenever possible, requests to external systems should be made in the background.  

Trust me when I say that the vast majority of requests can be made in the background. The end user might lose some information but will benefit from a more robust system.

What you know, control, and optimize in the background should also be known, controlled, and optimized in the foreground (web server).

Do not break these rules when you are tempted by a non-technical reason.

If your temptation has a technical rationale, reflect on it before deciding on breaking these rules. 

I don’t believe the Dutch are super-men; however, orange is my favorite color.

If you are responsible for the backend, you no longer report to your manager, you now report to the backend. Your backend can get you fired before your manager does. 


### Example of an implementation based on this Zen

1. Web server: Django
1. Task background system: celery
1. Relational database: Postgresql
1. Non-relational database: mongodb
1. Middlewares that control the number of queries against the databases, their execution time, memory increase, and overall HTTP request time.
1. Decorator for every celery task which controls the same thing that the middlewares do.
