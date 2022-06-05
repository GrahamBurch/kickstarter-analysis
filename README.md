                          Conclusions from Campaign Goals Analysis

  Introduction:

    This simple analysis searches for possible relationships between a campaign's initial fundraising goal and the final outcome of that goal. Initial fundraising goals are suspected to have some effect on the likelihood of successful final outcomes. Comparing initial goal ranges to the percentages of successful/failed campaigns within those ranges can shed some light on that suspicion. Additionally, we want to investigate the relationship between launch dates and theater outcomes to determine if theater campaigns perform especially better or worse when launched at different months of the year. To investigate that question we compare counts of successful versus failed or canceled outcomes based on year month. 

  Analysis and Challenges:

    To investigate the relationship between initial fundraising goal and final outcome, I began with filtering the Kickstarter worksheet's Outcomes column to only those campaigns who were successful, failed or canceled. I then needed a number of similar loops that could iterate through the outcomes column and sum the number of campaigns of each outcome type inside each starting goal range. I used these COUNTIF() loops to run those sums:
      * =COUNTIFS(Kickstarter!$F:$F,"=successful",Kickstarter!$D:$D,"<1000")
      * =COUNTIFS(Kickstarter!$F:$F,"=successful",Kickstarter!$D:$D,">=5000",Kickstarter!$D:$D,"<=9999")
      * =COUNTIFS(Kickstarter!$F:$F,"=successful",Kickstarter!$D:$D,">=10000",Kickstarter!$D:$D,"<=14999")

      Repeating this design pattern until...:

      * =COUNTIFS(Kickstarter!$F:$F,"=successful",Kickstarter!$D:$D,">=50000")

    Finding the percentages of successful, failed or canceled campaigns was done by dividing each outcome group by the total number of campaigns in that goal range. For example, the percentage of campaigns whose initial goal was between $15,000 and $19,999 that failed is 45%, found by using the code =(C6/E6).

    To investigate the relationship between launch date and theater outcomes, we created a pivot table that compares Date Created as rows to Count of Outcomes as columns subdivided into a "successful", "failed", "canceled" and "Grand Total" columns. Years and Parent Categories are the table's filters. 



    Results and Conclusions:

        The clear overall relationship from the line graph tracking fundraising goal range with likelihood of success/failure is that, unsurprisingly, campaigns with more modest fundraising goals are more likely to succeed. The likelihood of canceling a fundraiser also steadily increases with higher goal ranges. This trend shows itself clearly in the Outcomes_vs_goals.png image in the Resources folder for this assignment. The percentage of campaigns that complete their initial goal starts at ~72% at the <$1,000 range and the percentage that fail starts at ~25% in the <$1,000 range. As we move up the scales of fundraising goals, however, those percentages quickly change - around 19% of campaigns whose initial fundraising goal was $50,000 or more were successful but around 59% failed. 

        As for theater outcomes based on launch dates, the line graph Theater_outcome_vs_launch in the Resources folder for this readme shows that May is the launch month with the most successful theater outcomes and December is the month with the least. 

    
    Challenges and Considerations:

      The data for theater outcomes by launch date has room for improvement. With just a sum of successful outcomes for each month we don't see how the total number of campaigns started in each month is changing. May is the month with the highest total successful campaigns based on this data set but that could be for the likely reason that May is the most popular time to launch a fundraiser in general. A more informative figure would be percentage successful from each month. 

      The data for outcomes based on goals is more straightforward. With a percentage successful, failed etc we can capture the changing population sizes in each fundraising goal range, as it is certainly the case that the total number of campaigns in each fundraising range will decrease as you move up the goal amounts. We even see that the percentage canceled increases noticeably as you move up the goal amounts, which should be expected.  
