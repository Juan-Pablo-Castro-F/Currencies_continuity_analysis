# Data Optimization of time influence in the market. 
> In this section we will proceed to optimize the proposed strategy with a series of statistical tests and models in order to find the parameters that better suit the strategy. 

## Strategy description 
>The strategy we have chosen to employ the results of our research is based consist of drawing a range in the Asia market session and then in our chosen times take a buy when price crosses the high of that range or a sell when the price crosses the low of that level. In this way we expect to get the right direction since we followed the principle of the Asian range, and we improve our probabilities by adding the times that our analysis proposed as the best times to take trades. 

## Parameters description
The algorithmic robot has multiple parameters which can be modified, however we will only mention the ones that will be used in this optimization. We will divide them in different categories to understand which will be the process with each of the parameters:
### non-optimized variables
-	session times which we have found in our analysis results 
-	use a risk of 1 % per trade since this wont influence in the results of our trades.
### optimizable variables
-	Asia session range starting and end time 
-	Trading end time 
-	Stop Loss and take profit 
-	Trailing stop parameters (Trade management options)
-	Breakeven parameters (Trade management options)

## Initial Optimization

>We are approaching the optimization of the strategy as we would be doing with a regression model. We have a function which has different coefficients (parameters) that describe the behaviour and we are trying to find the most suitable parameters. For this reason, we need to be mindful of the statistical significance of our tests, as well of the overfitting of data and the confidence level of the model. 

The metric that we have decided to use to evaluate the fitness of each parameter is the profit factor which divides the total profit with the total loss and is considered one of the best measures to see the fitness of a model. 
We run a first optimization with the different variables that we have chosen to optimize. Nonetheless keep in mind that this first optimization is only run to see if we can identify some trend in the configuration of the patterns and that way establish what could be in a generalized way the most appropriate settings for the trading system. 


As we can see in the chart with the result of all the optimizations, the best results are consistently found when the Asia range starts at 4:00 a.m. For this reason, we are inclined to believe that this might be the best parameter to run later in the walk forward phase. 
![Asia range start time ](./img/Asia_range_start_time_chart.png)

When doing the same analysis with the end of the Asia range, we see quite different results. We can see that most of them are really similar except when the parameter takes the value 8, for this reason we will not consider it for the next test, instead we will use the value 7 and if needed the other ones under. 
![Asia range end time ](./img/Asia_range_end_time_chart.png)

If we do the same analysis with the end of the trading time, we will see that all the results are so similar therefore we will be indifferent to this parameter and we will forward test it in the next stage. 
Regarding the stop loss and the take profit, we need to evaluate these two variables together since they are strictly correlated to each other so we need to know which are the patterns in the combinations of this parameter.
> We have decided to use the take profit values using the risk reward method which states that the take profit is put in a equidistant of the stop loss and multiply it by a coefficient which is the called RR. 

As we can see the results in the 3D image, we can see that so many combinations give satisfactory results, however our objective is not to find the peaks but to fin the consistent valleys with profit. Due to the nature of the chart is quite hard to do this task however we can see that the most appropriate values for risk to reward are 3 and higher, therefore these will be the ones we will use in the forward test option. 
Regarding stop loss we can only identify that when it takes the value of 100 it yields the worst results, however it can be a matter of randomness and therefore we won’t exclude it from the next stage and we will prove its validity after. 
![Stop Loss and Take profit chart ](./img/RR_and_Slpoints_chart.png)

We have analyzed all the variables we wanted to evaluate, now we will proceed to the next stage of the optimization. 


## Walk forward analisis

>Forward optimization is a practice to reduce the overfittings of data in a model in order to make it more reliable and robust. To do so the period of optimization is divided in two different sections. The in-sample period, which is the part where you optimize the data in order to find the parameters that fit better your requirements, after that you run the 10% of the best combination of parameters in the second part of data which is called the out-sample data. In this second part you are trying to see if the optimized variables would perform as good as they did in the optimization. 
The reason of the implementation of this model is that we are interested in making sure our model would be able to provide profit in longer period of times and in live market conditions and to make sure that is not only performing well in the statistical tests that we are making. 

We will perform our test in the last year price data. We will use the in-sample data from January until end of September, and the out-sample data will be from October to the end of the year. This will give us a total of 9 months in data and 3 months out data to a forward ratio of 1:4. 
The results given by this method are two data files, first with the in sample run which can be found in the repository under the name Second_stage_optimization and the out-sample part Second_stage_forward. 

![Forward Results ](./img/Final_Forward_results.png)

In the image above we can see the best 10 results from boths of the tests. As we can see in multiple cases the reliability of the model stands and the predictability of the model works. We will chose the first set of parameters since we believe that’s what adjust the best to the parameters conditions and as well it has a low drawdown which is a key in strategy development. 
We then proceed to run specific test of the model in the whole data set to see more qualities about the system and familiarize better with other metrics which will help us to understand better the system. 

![Final Equity Curve ](./img/Final_equity_curve.png)

The above pictured depicts the simulated equity curve if we would have used our trading strategy in the last year. In this equity curve we can see that along the whole time the price has healthy fluctuations. We can also see that at the end there is some more steep growth which would teel us that this model had a good fitting period from the October until the end of the year. 

## Conclusions

The use of data analysis, statistical tests and different data transformation techniques can improve the development of trading systems and guarantee a longer lasting result. When investing in the markets it is main priority to have an edge that increases the probabilities of succeeding and analysing the data in the way that we have performed can provide you a good insight in tools and knowledge which can then be employed in the real market. 
There is many more analysis which could be employed. However, with the ones that we have already done we have gotten a great model and a great set of parameters which are ready to be used in financial market analysis. 
The same analysis was carried out with other assets yielding considerable results which can be taken into account in future live market tests to be ready to use. 

