![Citi Bike Logo](images/Citi-Bike_Logo.png)

# Executive Summary
 This analysis takes a look at station usage, ride counts, and ride times to identify potential areas to deep dive into specific usage and growth (ride counts and revenue).

The stations added in May 2021 in zip code 07030 are a success showing similar ride counts to those stations in zip code 07302! 

Aside from the COVID-19 impact, ride counts have grown steadily YoY. The COVID-19 impact was strongest in March-May 2020 but did not subside until March-April 2021. Growth in May 2021 and after was helped by adding stations in the 07030 zip code. Filtering the map to 2022, you can see these stations are similar in ride counts as those in 07302 zip code. Looking at user growth, ad-hoc ride counts are growing faster than subscriber ride counts. With the current pricing model, this appears to benefit for revenue growth as the non-subscribers make up 80% of the revenue June 2021 - December 2022 despite being 35% of ride count. Having access to user ids and breaking down casual rides into day pass and single rides would allow for greater clarity and further recommendations. Another aspect important to consider for profit is the impact of "Angel Rides" on support costs as well as revenue. Clearly tagging these rides would allow for automation to further refine the analysis.

Additionally, it appears users prefer this service when ride times between stations are shorter. Adding more stations on the eastern portions of zip codes 07307, 07306, 07304 may attract more users. Focusing on the eastern portion of these areas is recommended before expanding further into the zip codes. This aligns with the focusing on more short ride availability. 

For interactive visuals, review the [JC Citi-Bike Usage & Revenue Story](https://public.tableau.com/app/profile/rebekah.aldrich/viz/2018-2020_JC-CitiBike_Analysis/JCCiti-BikeUsageRevenue?publish=yes) hosted on Tableau public.


## Overall Map Exploration

**Caveats / Limitations**<br>
Some rides have an end time more than one day from start time. These are excluded from the presented map views as "lost". There is a map view to capture these to begin a separate analysis. Additionally, some latitude / longitude coordinates do not have a station name so these are counted as "lost" and exclude for the purposes of the analysis.

**Analysis**<br>

Stations were added in May 2021 primarily in zip code 07030 so these stations will show fewer rides when all years are selected. Filtering the map overview for May 2021+, the ride counts at these stations is on par with the stations in zip code 07302 indicating a success for adding them. 
![Overall Station Usage 2021-22](images/JC_station_usage_May2021_2022.png)

It appears users prefer the service when ride times between stations are shorter. Adding more stations on the eastern portions of zip codes 07307, 07306, 07304 may attract more users.
* Reviewing the overall map, stations in zip codes 07304 and 07306 show fewer ride counts and higher average ride times. 
* Diving into the top 10 views, we can see that stations with lower average ride times (zip codes 07302, 07310) from the overview have longer total ride times logged. While the individual ride times are shorter, the number of rides makes up for it. Considering the pricing model for non-subscribers, this may help Citi-Bike's revenue stream.
* One station has overlap with being in the top 10 for ride count and average trip time as well as showing high total trip time: Liberty Light Rail. This is expected as an endpoint for longer commuting. A brief look (a deeper analysis may lead to some interesting business outcomes).
    * Ride counts are higher on the weekend.
    * During the week, subscribers account for more rides. While on the weekend, non-subscribers account for more rides.
    * The weekday pattern drives the overall monthly subscriber vs non-subscriber usage with subscribers accounting for 55% of rides.

![LIberty Rail](images/Liberty_Rail.png)

## Growth Over Time 2018 - 2022

Aside from the COVID-19 impact, ride counts have grown steadily YoY. The COVID impact was strongest in March-May 2020 but did not subside until March-April 2021. Looking at user growth, ad-hoc ride counts are growing faster than subscriber ride counts. With the current pricing model, this may be a benefit for revenue growth.
* Ride counts are highest July through September with lowest counts December through February.
* 2019 showed marginal growth over 2018.
* 2020 saw YoY monthly decreases starting in March (COVID-19 restrictions).
* March 2021 ride counts began to grow again showing the strongest YoY growth, but its compare was to a weak 2020.
* Rides by non-subscribers is growing faster than subscribers.

![Monthly Ride Counts](images/JC_Ride_Count_2018_2022.png)
<br>
![Monthly Ride Counts by User](images/JC_USer_Ride_Count_2018_2022.png)

## Revenue Jun 2021 - Dec 2022

Given my assumptions and data limitations, non-subscribers contribute the most revenue with more coming from electric bike usage even though classic rides are more common. Without knowing the benefit of "Bike Angel" rides on costs, it is challenging to make statements about profit and whether to campaign for more subscribers vs. boast the benefits of ad hoc / daily use. Given the high percentage of revenue from non-subscribers, it seems as though targeting ad hoc usage is ideal. To get good accuracy, I need a user_id attached to each ride as well as breaking "casual" into "single" and "day_pass". This would allow me to apply much more accurate formulas to revenue.

June 2021 - December 2022:
* Non-subscribers contribute 80% of the revenue despite being 35% of ride count
    * electric bike usage makes up slightly over half (52%) non-subscriber contribution.
* Electric bike rides contribute slightly more to revenue than classic bike rides (54% vs. 46%).
* Subscribers contribute a higher percentage to electric bike revenue than they do to classic bike revenue.

### Caveats & Assumptions for the purpose of creating Revenue charts for this project
**Basis of Assumptions**<br>
* I am using pricing based on current listings (https://citibikenyc.com/pricing) in the absence of knowing specifics over time.
    * "causal" riders either
        * purchasing single rides with unlock fee of $4.49 and $0.26/min for Ebikes.
        * purchasing a day pass with unlimited unlocks for $19 and $0.26/min for Ebikes.
    * "member" riders pay a yearly fee of $199 or $205 with unlimited unlocks and $0.17/min for Ebikes.
* Ride times are indicated to be up to 30 min for casuals or 45 min for members.
* Memberships include a "Bike Angels" incentive for riders to take bikes from crowded stations to stations needing more bikes.

**Assumptions**<br>
* Queries are limited to include 45 min ride times and under.
* This assumes all rides are paid (no accounting for "Bike Angel" rides).
* For the purpose of calculating ride unlock costs for casual riders in the absence of customer IDs to link records:
    * I am assuming day pass riders average 6 free unlocks with the $19 .
    * I am assuming for every single ride there is one day pass.
    * This means 7 unlocks for $19 + $4.49 ($3.36 per unlock on average).
* For the purpose of managing annual membership revenue without customer IDs, I'm going to assume that members average 2 rides a day thus splitting the annual fee across 730 rides: (Avg($205+$199))/(730) = $0.28.

![JC Revenue](images/JC_Revenue_Jun2021-2022.png)

