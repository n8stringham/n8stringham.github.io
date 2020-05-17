# Simulating a NCAA DIII National XC Meet
Ethan Ashby, Danny Rosen, Nate Stringham

This project was completed for Math 154 - Computational Statistics in Fall 2019.
Data for the project comes from the 2016-17 NBA season contained in the [SpatialBall](https://cran.r-project.org/web/packages/SpatialBall/index.html) package.

See also
* a [simulation applet](https://n8stringham.shinyapps.io/CrossCountry_Simulator)
* the [poster]() we made for our presentation

### Goals
* Successfully simulate a National Championship meet using prior race results.
* Analyze these simulations to assess how well different college programs ``peak"
 
### Background
In NCAA Division III Cross Country, runners compete in an 8k race with the top 5 finishers from each team contributing to the overall team score. Specifically, a team score is calculated by taking a sum of the  places of the top 5 finishers from each team. The team with the lowest score wins the meet.

Each year every team in NCAA DIII vies for one of 32 spots in the National Championship Meet. Those that qualify send 7 runners to compete in this meet for the title of National Champions. Since this  

Background and The ability of a cross country program to ``peak" its runners well at the end of the season is often what determines national champions. To determine how well programs peak their athletes, we will use simulations of cross country results to score a hypothetical national meet.

### Method
To run the simulation, we first standardize the times run at various races leading up to the national meet for each athlete on a qualifying team. These adjusted times from the current season are used to create a normal distribution for each athlete; then, to simulate a national meet we simply sample from each athlete's distribution to get their national meet performance, sort the athletes into a meet ranking, and score the results as a cross country meet. We compare the actual nationals result from that year to our simulated result to determine how well a team peaked. We can do this over a number of years to evaluate different programs. We assign a score to each program based on how consistently they peaked at the national meet and how far they exceeded our simulated expectation of their finish at the national meet. IF we have time we'll make a shiny app!

### Data 
All race data was obtained from https://tfrrs.org/


			
