# NBA-heatmaps
**Team Members:** Nate Stringham and Adam Rees

This project was completed for Math 161 - Spatial Statistics in Spring 2019.
Data for the project comes from the 2016-17 NBA season contained in the SpatialBall package.

### RESEARCH QUESTIONS
How does an NBA player’s scoring efficiency change with shot location? Can we utilize Spatial Kriging to predict where they are most efficient?

### ABOUT KRIGING
Spatial Kriging is a statistical technique which uses a set of observations in space and its corresponding values of a covariate of interest--usually called z--to predict the values of that same covariate at a new set of locations within the sample space. Kriging is especially effective because its interpolation method accounts for the way in which z-values vary with distance.

### WHY KRIGING?
With this project, we set out to gain insights regarding the scoring efficiency of some of our favorite NBA players and teams. While statistics such as field goal percentage, 3 point percentage, and points per shot all can be used to measure efficiency, what we were really looking for was a way to visualize it. A traditional NBA shot chart does this with simple spatial plots of the location of every shot taken and a certain colored depending on whether the attempt was made or missed. Ordinary Spatial Kriging allows us to leverage the set of observed values and corresponding points scored from these plots to predict points scored at a set of new locations. By overlaying the court with a spatial pixels grid we can obtain kriged values for every other location on the court.

### DATA AND METHODS
The data used in our analysis comes entirely from the 2016-2017 regular season of the NBA. In particular, we made use of the season2017 table from Derek Corcoran’s SpatialBall Package in R. This table includes over 200,000 observations recording the coordinate location of every shot taken during the season along with 22 other variables.
The goal of our analysis was to use spatial kriging to predict the average points per shot (PPS) for a given player at every location within half court. We decided to limit our analysis only to shots taken within half court so as to eliminate potential spatial outliers. PPS is calculated as the total number of points scored divided by the number of shots taken. We chose this measure of scoring efficiency because it allows for a better comparison between 2 point and 3 point field goals.
Our first step was to transform the data table so that it only contained the information needed for the analysis. The first part of our analysis was focused on individual players, so we filtered our table to only include the shots from the chosen player. Next, we calculated the PPS variable for each of our observations. This was accomplished by first creating a points variable which simply recorded the points obtained from each shot attempt (either 0, 2, or 3). Since some shots were taken from identical locations, we groups these shots by location and found the average PPS at every location recorded.
With the values obtained from our PPS covariate, we proceeded to implement kriging by first creating a 504 by 515 grid to represent half court. Then, using the gstat package, we created a sample variogram, fitted the variogram, kriged the fit and then used spplot to display our results.

### DISCUSSION
A lot of the heat maps we created reflected the advantages to shooting three point shots. A player can shoot 33.3% from 3 and have the same eFG% [(FGM + 0.5 * 3PM)/FGA)] as a player shooting 50% from 2. Thus, when players have similar three point percentages to their overall percentages, they have a bump in their PPS predictions outside of the three point line. The heat maps also show benefits of getting to the rim; every heat map indicated a higher PPS prediction close to the basket. Some players, like Rudy Gobert, who only shoot in the paint, have high PPS close to the basket with very low predicted PPS at nearly all other locations. Additionally, we created some plots with Inverse Distance Weighting (IDW) and found the fact it only uses the closest neighbors, created a much less smooth and visually comprehensive map. Overall, this project provided a fun way to display the locations on the court where players thrive.
