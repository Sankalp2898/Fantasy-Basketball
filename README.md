# Fantasy-Basketball
Fantasy sports has turned into a mainstream activity over the last ten to twenty years with leagues now working with popular fantasy sports sites as official partners.
If you’re not familiar with fantasy sports, the goal is to select players from a slate of real games to fill out a virtual lineup.

The player’s selected then have their performance converted to fantasy points, So for example a basketball player’s points, rebounds, assists and turnovers will produce a single fantasy point value. The highest overall total is used to determine winners of large competitions. In short, you want to pick your dream team.

But it’s not so easy as just picking the best players as each one is given a salary value and your lineup’s total salary can’t exceed a given value (the salary cap). Your lineup also must satisfy position constraints which makes selecting a lineup a little more difficult.

This example begins with NBA box score data to build a supervised machine learning model that predicts players fantasy point output for a single days games. Those predictions are then used in an optimization model that will select the optimal team consisting of one player from each of the five main positions.

The second part expands the optimization model to reflect actual fantasy basketball competitions, shows different ways to model constraints, and introduces the slack of a constraint.
Objective and Prerequisites
In this example, we'll take on the role of a basketball coach and learn how to find the optimal lineup of National Basketball Association (NBA) players in the context of fantasy basketball. The goal is to select the five players who are going to perform the best in the NBA games played on December 25, 2017, by simultaneously satisfying player and position eligibility and budget constraints.

We aim to demonstrate that machine learning and mathematical optimization are closely connected, and how they can be integrated to derive optimal decisions. Simply starting from a dataset, we will apply machine learning techniques to make predictions about the performance of basketball players. But when taking into account the problem constraints, directly utilizing these forecasts to make player selections isn't straightforward. This is where mathematical optimization and the Gurobi Optimizer thrive to prove what the best viable lineup is, by formulating and solving a mixed-integer programming (MIP) problem that will maximize the lineup's total fantasy points.

This example is for beginners in mathematical optimization who may have some experience in data handling and predictive modeling and experience using Python.

The presented problem requires the installation of the following Python packages:

pandas for data analysis and manipulation
numpy for calculations
matplotlib and seaborn for plotting and visualizing information
scikit-learn for accessing data science predictive tools
gurobipy for utilizing Gurobi to formulate and solve the optimization problem
Problem Statement and Solution Approach
Given the regular season historical performances (box scores) of NBA players for the seasons 2016-2017 and 2017-2018, the eligible positions for each of the players, and a budget restriction on how much total salary we are allowed to spend for our team, select the five NBA players who are going to have the best performance on the NBA games played on Christmas day of the 2017-2018 season.

Among the eligible players that are going to play that day, we need to select a point guard, a shooting guard, a shooting forward, a power forward, and a center.

The solution to the problem consists of two components: 1) fantasy points forecast and 2) lineup optimization.

Fantasy Points Forecast
Let's start by loading the necessary libraries to solve our problem.
