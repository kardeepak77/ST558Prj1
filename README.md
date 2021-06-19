ProjectNHL
================
Deepak Karawande
June 13, 2021

-   [Introduction](#introduction)
-   [Packages](#packages)
-   [Accessing NHL Data](#accessing-nhl-data)
    -   [Contract REST-API and create
        dataframe](#contract-rest-api-and-create-dataframe)
    -   [Fetch data by Id or Name](#fetch-data-by-id-or-name)
    -   [Fetching datafrom NHL Records
        API](#fetching-datafrom-nhl-records-api)
    -   [Wrapper function](#wrapper-function)
-   [Exploratory Data Analysis](#exploratory-data-analysis)
    -   [Combine Franchise Summary and Details in single summary
        table.](#combine-franchise-summary-and-details-in-single-summary-table.)
    -   [You should create at least two new variables that are functions
        of the variables from a data set you
        use.](#you-should-create-at-least-two-new-variables-that-are-functions-of-the-variables-from-a-data-set-you-use.)

# Introduction

This vignette is an introduction on how to query REST-API endpoins using
R and perform exploratory data analysis using various R packages. We’ll
use be using the NHL REST-API endpoints which can be contracted by
folloiwng instruciton on
[https://gitlab.com/dword4/nhlapi/-/blob/master/records-api.md](NHL%20Records%20API)

# Packages

Folloiwng lsit of packages were used for accessing REST-API endpoints
and exploratory data analysis and presentation.

# Accessing NHL Data

## Contract REST-API and create dataframe

NHLAPI project on github provides REST-API endpoints to access various
datapoints for historical NHL games.

For this project, I accessed 7 differnt endpoints from NHLAPI to fetch
information about NHL - 1) Franchise summary 2) Franchise details 3)
Total stats for franchise 4) Season records 5) Skater records 6) Admin
history and retired numbers 7) Team stats

GET function from httr package was used for fetching data through
REST-API. Using content and fromJSON fuction data received was converted
into r dataframe object.

## Fetch data by Id or Name

By default NHL REST-APIs return data for all franchise or team. Using
helpfer functions I created a ability for user to provide Id or Name to
fetch data for sepcific franchise/team if desired. If no Id or Name is
passed query functions will return data for all franchise or teams.

## Fetching datafrom NHL Records API

With the help of wrapper funcions above, created a R function to fetch
data from deisred NHL Records endpoint using either franchise id or team
common name. If franchise id or team common name was not proivided api
will return data from all franchises. Simillar set of fucntions were
used to contract with NHL team stats RES-API end point.

## Wrapper function

Using Switch-Case, created wrapper function for providing simplicity for
fetching data from all NHL REST-API endpoints relvant to this project,

# Exploratory Data Analysis

## Combine Franchise Summary and Details in single summary table.

To explore data, started with combining data from franchise summary and
detail using inner\_join to get basic tabular view of all franchises.
Rendered such summary table using kable function from knitr.

<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Franchise Summary Preview
</caption>
<thead>
<tr>
<th style="text-align:right;">
id
</th>
<th style="text-align:left;">
heroImageUrl
</th>
<th style="text-align:left;">
teamCommonName
</th>
<th style="text-align:left;">
active
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:right;">
1
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/MTL/Price.jpg" width="100" />
</td>
<td style="text-align:left;">
Canadiens
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
2
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/images/hero/teams/defunct-franchises/montreal-wanderers.jpg" width="100" />
</td>
<td style="text-align:left;">
Wanderers
</td>
<td style="text-align:left;">
FALSE
</td>
</tr>
<tr>
<td style="text-align:right;">
3
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/1927SEN.JPG" width="100" />
</td>
<td style="text-align:left;">
Eagles
</td>
<td style="text-align:left;">
FALSE
</td>
</tr>
<tr>
<td style="text-align:right;">
4
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/images/hero/teams/defunct-franchises/hamilton-tigers.jpg" width="100" />
</td>
<td style="text-align:left;">
Tigers
</td>
<td style="text-align:left;">
FALSE
</td>
</tr>
<tr>
<td style="text-align:right;">
5
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/TOR/MatthewsMarner.jpg" width="100" />
</td>
<td style="text-align:left;">
Maple Leafs
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
6
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/BOS/BergeronPastrnak.jpg" width="100" />
</td>
<td style="text-align:left;">
Bruins
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
7
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/images/hero/teams/defunct-franchises/montreal-maroons.jpg" width="100" />
</td>
<td style="text-align:left;">
Maroons
</td>
<td style="text-align:left;">
FALSE
</td>
</tr>
<tr>
<td style="text-align:right;">
8
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/NYAmericans.jpg" width="100" />
</td>
<td style="text-align:left;">
Americans
</td>
<td style="text-align:left;">
FALSE
</td>
</tr>
<tr>
<td style="text-align:right;">
9
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/images/hero/teams/defunct-franchises/pittsburgh-pirates.jpg" width="100" />
</td>
<td style="text-align:left;">
Quakers
</td>
<td style="text-align:left;">
FALSE
</td>
</tr>
<tr>
<td style="text-align:right;">
10
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/NYR/PanarinZibanejad.jpg" width="100" />
</td>
<td style="text-align:left;">
Rangers
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
11
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/ToewsKane.jpg" width="100" />
</td>
<td style="text-align:left;">
Blackhawks
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
12
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/DET/WingsWin.jpg" width="100" />
</td>
<td style="text-align:left;">
Red Wings
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
13
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/Seals.jpg" width="100" />
</td>
<td style="text-align:left;">
Barons
</td>
<td style="text-align:left;">
FALSE
</td>
</tr>
<tr>
<td style="text-align:right;">
14
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/Kings.jpg" width="100" />
</td>
<td style="text-align:left;">
Kings
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
15
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/Stars.jpg" width="100" />
</td>
<td style="text-align:left;">
Stars
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
16
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/Giroux.jpg" width="100" />
</td>
<td style="text-align:left;">
Flyers
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
17
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/Penguins.jpg" width="100" />
</td>
<td style="text-align:left;">
Penguins
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
18
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/STL/PerronCelebrates.jpg" width="100" />
</td>
<td style="text-align:left;">
Blues
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
19
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/Sabres.jpg" width="100" />
</td>
<td style="text-align:left;">
Sabres
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
20
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/Canucks.jpg" width="100" />
</td>
<td style="text-align:left;">
Canucks
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
21
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/Flames.jpg" width="100" />
</td>
<td style="text-align:left;">
Flames
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
22
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/NYI/Barzal.jpg" width="100" />
</td>
<td style="text-align:left;">
Islanders
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
23
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/NJD/Subban.jpg" width="100" />
</td>
<td style="text-align:left;">
Devils
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
24
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/Capitals.jpg" width="100" />
</td>
<td style="text-align:left;">
Capitals
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
25
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/Oilers.jpg" width="100" />
</td>
<td style="text-align:left;">
Oilers
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
26
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/Aho.jpg" width="100" />
</td>
<td style="text-align:left;">
Hurricanes
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
27
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/MacKinnonLandeskog.jpg" width="100" />
</td>
<td style="text-align:left;">
Avalanche
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
28
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/ARI/OELKuemper.jpg" width="100" />
</td>
<td style="text-align:left;">
Coyotes
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
29
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/SJS/SharksGoal.jpg" width="100" />
</td>
<td style="text-align:left;">
Sharks
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
30
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/Senators.jpg" width="100" />
</td>
<td style="text-align:left;">
Senators
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
31
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/LightningCupTeamPhoto.jpg" width="100" />
</td>
<td style="text-align:left;">
Lightning
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
32
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/Getzlaf.jpg" width="100" />
</td>
<td style="text-align:left;">
Ducks
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
33
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/FLA/PanthersCelebrate.jpg" width="100" />
</td>
<td style="text-align:left;">
Panthers
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
34
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/PredatorsGoal.jpg" width="100" />
</td>
<td style="text-align:left;">
Predators
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
35
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/Jets.jpg" width="100" />
</td>
<td style="text-align:left;">
Jets
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
36
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/BlueJackets.jpg" width="100" />
</td>
<td style="text-align:left;">
Blue Jackets
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
37
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/MIN/WildTrio.jpg" width="100" />
</td>
<td style="text-align:left;">
Wild
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
38
</td>
<td style="text-align:left;">
<img src="https://records.nhl.com/site/asset/public/ext/hero/Team%20Pages/VGK/StonePacioretty.jpg" width="100" />
</td>
<td style="text-align:left;">
Golden Knights
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
<tr>
<td style="text-align:right;">
39
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
Kraken
</td>
<td style="text-align:left;">
TRUE
</td>
</tr>
</tbody>
</table>

## You should create at least two new variables that are functions of the variables from a data set you use.

<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Win/Loss Percentages by Franchise & Teams
</caption>
<thead>
<tr>
<th style="text-align:right;">
franchiseId
</th>
<th style="text-align:left;">
teamName
</th>
<th style="text-align:right;">
totalWins
</th>
<th style="text-align:right;">
totalLosses
</th>
<th style="text-align:right;">
perWins
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:right;">
38
</td>
<td style="text-align:left;">
Vegas Golden Knights
</td>
<td style="text-align:right;">
210
</td>
<td style="text-align:right;">
120
</td>
<td style="text-align:right;">
0.64
</td>
</tr>
<tr>
<td style="text-align:right;">
1
</td>
<td style="text-align:left;">
Montréal Canadiens
</td>
<td style="text-align:right;">
3917
</td>
<td style="text-align:right;">
2623
</td>
<td style="text-align:right;">
0.60
</td>
</tr>
<tr>
<td style="text-align:right;">
15
</td>
<td style="text-align:left;">
Dallas Stars
</td>
<td style="text-align:right;">
1189
</td>
<td style="text-align:right;">
833
</td>
<td style="text-align:right;">
0.59
</td>
</tr>
<tr>
<td style="text-align:right;">
16
</td>
<td style="text-align:left;">
Philadelphia Flyers
</td>
<td style="text-align:right;">
2310
</td>
<td style="text-align:right;">
1670
</td>
<td style="text-align:right;">
0.58
</td>
</tr>
<tr>
<td style="text-align:right;">
27
</td>
<td style="text-align:left;">
Colorado Avalanche
</td>
<td style="text-align:right;">
1131
</td>
<td style="text-align:right;">
822
</td>
<td style="text-align:right;">
0.58
</td>
</tr>
<tr>
<td style="text-align:right;">
6
</td>
<td style="text-align:left;">
Boston Bruins
</td>
<td style="text-align:right;">
3573
</td>
<td style="text-align:right;">
2740
</td>
<td style="text-align:right;">
0.57
</td>
</tr>
<tr>
<td style="text-align:right;">
34
</td>
<td style="text-align:left;">
Nashville Predators
</td>
<td style="text-align:right;">
906
</td>
<td style="text-align:right;">
723
</td>
<td style="text-align:right;">
0.56
</td>
</tr>
<tr>
<td style="text-align:right;">
35
</td>
<td style="text-align:left;">
Winnipeg Jets
</td>
<td style="text-align:right;">
398
</td>
<td style="text-align:right;">
315
</td>
<td style="text-align:right;">
0.56
</td>
</tr>
<tr>
<td style="text-align:right;">
37
</td>
<td style="text-align:left;">
Minnesota Wild
</td>
<td style="text-align:right;">
789
</td>
<td style="text-align:right;">
653
</td>
<td style="text-align:right;">
0.55
</td>
</tr>
<tr>
<td style="text-align:right;">
3
</td>
<td style="text-align:left;">
Ottawa Senators (1917)
</td>
<td style="text-align:right;">
276
</td>
<td style="text-align:right;">
238
</td>
<td style="text-align:right;">
0.54
</td>
</tr>
<tr>
<td style="text-align:right;">
12
</td>
<td style="text-align:left;">
Detroit Red Wings
</td>
<td style="text-align:right;">
3216
</td>
<td style="text-align:right;">
2739
</td>
<td style="text-align:right;">
0.54
</td>
</tr>
<tr>
<td style="text-align:right;">
21
</td>
<td style="text-align:left;">
Calgary Flames
</td>
<td style="text-align:right;">
1600
</td>
<td style="text-align:right;">
1354
</td>
<td style="text-align:right;">
0.54
</td>
</tr>
<tr>
<td style="text-align:right;">
32
</td>
<td style="text-align:left;">
Anaheim Ducks
</td>
<td style="text-align:right;">
1079
</td>
<td style="text-align:right;">
907
</td>
<td style="text-align:right;">
0.54
</td>
</tr>
<tr>
<td style="text-align:right;">
18
</td>
<td style="text-align:left;">
St. Louis Blues
</td>
<td style="text-align:right;">
2111
</td>
<td style="text-align:right;">
1866
</td>
<td style="text-align:right;">
0.53
</td>
</tr>
<tr>
<td style="text-align:right;">
19
</td>
<td style="text-align:left;">
Buffalo Sabres
</td>
<td style="text-align:right;">
1929
</td>
<td style="text-align:right;">
1696
</td>
<td style="text-align:right;">
0.53
</td>
</tr>
<tr>
<td style="text-align:right;">
23
</td>
<td style="text-align:left;">
New Jersey Devils
</td>
<td style="text-align:right;">
1531
</td>
<td style="text-align:right;">
1331
</td>
<td style="text-align:right;">
0.53
</td>
</tr>
<tr>
<td style="text-align:right;">
24
</td>
<td style="text-align:left;">
Washington Capitals
</td>
<td style="text-align:right;">
1838
</td>
<td style="text-align:right;">
1623
</td>
<td style="text-align:right;">
0.53
</td>
</tr>
<tr>
<td style="text-align:right;">
25
</td>
<td style="text-align:left;">
Edmonton Oilers
</td>
<td style="text-align:right;">
1629
</td>
<td style="text-align:right;">
1449
</td>
<td style="text-align:right;">
0.53
</td>
</tr>
<tr>
<td style="text-align:right;">
26
</td>
<td style="text-align:left;">
Carolina Hurricanes
</td>
<td style="text-align:right;">
885
</td>
<td style="text-align:right;">
779
</td>
<td style="text-align:right;">
0.53
</td>
</tr>
<tr>
<td style="text-align:right;">
29
</td>
<td style="text-align:left;">
San Jose Sharks
</td>
<td style="text-align:right;">
1189
</td>
<td style="text-align:right;">
1042
</td>
<td style="text-align:right;">
0.53
</td>
</tr>
<tr>
<td style="text-align:right;">
17
</td>
<td style="text-align:left;">
Pittsburgh Penguins
</td>
<td style="text-align:right;">
2112
</td>
<td style="text-align:right;">
1916
</td>
<td style="text-align:right;">
0.52
</td>
</tr>
<tr>
<td style="text-align:right;">
22
</td>
<td style="text-align:left;">
New York Islanders
</td>
<td style="text-align:right;">
1858
</td>
<td style="text-align:right;">
1726
</td>
<td style="text-align:right;">
0.52
</td>
</tr>
<tr>
<td style="text-align:right;">
28
</td>
<td style="text-align:left;">
Phoenix Coyotes
</td>
<td style="text-align:right;">
637
</td>
<td style="text-align:right;">
581
</td>
<td style="text-align:right;">
0.52
</td>
</tr>
<tr>
<td style="text-align:right;">
31
</td>
<td style="text-align:left;">
Tampa Bay Lightning
</td>
<td style="text-align:right;">
1086
</td>
<td style="text-align:right;">
1022
</td>
<td style="text-align:right;">
0.52
</td>
</tr>
<tr>
<td style="text-align:right;">
5
</td>
<td style="text-align:left;">
Toronto Maple Leafs
</td>
<td style="text-align:right;">
3132
</td>
<td style="text-align:right;">
2979
</td>
<td style="text-align:right;">
0.51
</td>
</tr>
<tr>
<td style="text-align:right;">
7
</td>
<td style="text-align:left;">
Montreal Maroons
</td>
<td style="text-align:right;">
291
</td>
<td style="text-align:right;">
281
</td>
<td style="text-align:right;">
0.51
</td>
</tr>
<tr>
<td style="text-align:right;">
10
</td>
<td style="text-align:left;">
New York Rangers
</td>
<td style="text-align:right;">
3127
</td>
<td style="text-align:right;">
2982
</td>
<td style="text-align:right;">
0.51
</td>
</tr>
<tr>
<td style="text-align:right;">
30
</td>
<td style="text-align:left;">
Ottawa Senators
</td>
<td style="text-align:right;">
1043
</td>
<td style="text-align:right;">
1019
</td>
<td style="text-align:right;">
0.51
</td>
</tr>
<tr>
<td style="text-align:right;">
11
</td>
<td style="text-align:left;">
Chicago Blackhawks
</td>
<td style="text-align:right;">
3080
</td>
<td style="text-align:right;">
3036
</td>
<td style="text-align:right;">
0.50
</td>
</tr>
<tr>
<td style="text-align:right;">
21
</td>
<td style="text-align:left;">
Atlanta Flames
</td>
<td style="text-align:right;">
270
</td>
<td style="text-align:right;">
275
</td>
<td style="text-align:right;">
0.50
</td>
</tr>
<tr>
<td style="text-align:right;">
33
</td>
<td style="text-align:left;">
Florida Panthers
</td>
<td style="text-align:right;">
910
</td>
<td style="text-align:right;">
903
</td>
<td style="text-align:right;">
0.50
</td>
</tr>
<tr>
<td style="text-align:right;">
5
</td>
<td style="text-align:left;">
Toronto St. Patricks
</td>
<td style="text-align:right;">
113
</td>
<td style="text-align:right;">
117
</td>
<td style="text-align:right;">
0.49
</td>
</tr>
<tr>
<td style="text-align:right;">
14
</td>
<td style="text-align:left;">
Los Angeles Kings
</td>
<td style="text-align:right;">
1865
</td>
<td style="text-align:right;">
1973
</td>
<td style="text-align:right;">
0.49
</td>
</tr>
<tr>
<td style="text-align:right;">
36
</td>
<td style="text-align:left;">
Columbus Blue Jackets
</td>
<td style="text-align:right;">
693
</td>
<td style="text-align:right;">
724
</td>
<td style="text-align:right;">
0.49
</td>
</tr>
<tr>
<td style="text-align:right;">
20
</td>
<td style="text-align:left;">
Vancouver Canucks
</td>
<td style="text-align:right;">
1760
</td>
<td style="text-align:right;">
1881
</td>
<td style="text-align:right;">
0.48
</td>
</tr>
<tr>
<td style="text-align:right;">
5
</td>
<td style="text-align:left;">
Toronto Arenas
</td>
<td style="text-align:right;">
22
</td>
<td style="text-align:right;">
25
</td>
<td style="text-align:right;">
0.47
</td>
</tr>
<tr>
<td style="text-align:right;">
12
</td>
<td style="text-align:left;">
Detroit Falcons
</td>
<td style="text-align:right;">
34
</td>
<td style="text-align:right;">
42
</td>
<td style="text-align:right;">
0.45
</td>
</tr>
<tr>
<td style="text-align:right;">
27
</td>
<td style="text-align:left;">
Quebec Nordiques
</td>
<td style="text-align:right;">
532
</td>
<td style="text-align:right;">
644
</td>
<td style="text-align:right;">
0.45
</td>
</tr>
<tr>
<td style="text-align:right;">
28
</td>
<td style="text-align:left;">
Arizona Coyotes
</td>
<td style="text-align:right;">
218
</td>
<td style="text-align:right;">
267
</td>
<td style="text-align:right;">
0.45
</td>
</tr>
<tr>
<td style="text-align:right;">
15
</td>
<td style="text-align:left;">
Minnesota North Stars
</td>
<td style="text-align:right;">
838
</td>
<td style="text-align:right;">
1056
</td>
<td style="text-align:right;">
0.44
</td>
</tr>
<tr>
<td style="text-align:right;">
35
</td>
<td style="text-align:left;">
Atlanta Thrashers
</td>
<td style="text-align:right;">
342
</td>
<td style="text-align:right;">
441
</td>
<td style="text-align:right;">
0.44
</td>
</tr>
<tr>
<td style="text-align:right;">
26
</td>
<td style="text-align:left;">
Hartford Whalers
</td>
<td style="text-align:right;">
552
</td>
<td style="text-align:right;">
740
</td>
<td style="text-align:right;">
0.43
</td>
</tr>
<tr>
<td style="text-align:right;">
28
</td>
<td style="text-align:left;">
Winnipeg Jets (1979)
</td>
<td style="text-align:right;">
525
</td>
<td style="text-align:right;">
703
</td>
<td style="text-align:right;">
0.43
</td>
</tr>
<tr>
<td style="text-align:right;">
12
</td>
<td style="text-align:left;">
Detroit Cougars
</td>
<td style="text-align:right;">
64
</td>
<td style="text-align:right;">
89
</td>
<td style="text-align:right;">
0.42
</td>
</tr>
<tr>
<td style="text-align:right;">
8
</td>
<td style="text-align:left;">
New York Americans
</td>
<td style="text-align:right;">
245
</td>
<td style="text-align:right;">
384
</td>
<td style="text-align:right;">
0.39
</td>
</tr>
<tr>
<td style="text-align:right;">
4
</td>
<td style="text-align:left;">
Hamilton Tigers
</td>
<td style="text-align:right;">
47
</td>
<td style="text-align:right;">
78
</td>
<td style="text-align:right;">
0.38
</td>
</tr>
<tr>
<td style="text-align:right;">
8
</td>
<td style="text-align:left;">
Brooklyn Americans
</td>
<td style="text-align:right;">
16
</td>
<td style="text-align:right;">
29
</td>
<td style="text-align:right;">
0.36
</td>
</tr>
<tr>
<td style="text-align:right;">
9
</td>
<td style="text-align:left;">
Pittsburgh Pirates
</td>
<td style="text-align:right;">
68
</td>
<td style="text-align:right;">
124
</td>
<td style="text-align:right;">
0.35
</td>
</tr>
<tr>
<td style="text-align:right;">
13
</td>
<td style="text-align:left;">
Cleveland Barons
</td>
<td style="text-align:right;">
47
</td>
<td style="text-align:right;">
87
</td>
<td style="text-align:right;">
0.35
</td>
</tr>
<tr>
<td style="text-align:right;">
13
</td>
<td style="text-align:left;">
Oakland Seals
</td>
<td style="text-align:right;">
69
</td>
<td style="text-align:right;">
126
</td>
<td style="text-align:right;">
0.35
</td>
</tr>
<tr>
<td style="text-align:right;">
13
</td>
<td style="text-align:left;">
California Golden Seals
</td>
<td style="text-align:right;">
116
</td>
<td style="text-align:right;">
283
</td>
<td style="text-align:right;">
0.29
</td>
</tr>
<tr>
<td style="text-align:right;">
23
</td>
<td style="text-align:left;">
Colorado Rockies
</td>
<td style="text-align:right;">
113
</td>
<td style="text-align:right;">
283
</td>
<td style="text-align:right;">
0.29
</td>
</tr>
<tr>
<td style="text-align:right;">
3
</td>
<td style="text-align:left;">
St. Louis Eagles
</td>
<td style="text-align:right;">
11
</td>
<td style="text-align:right;">
31
</td>
<td style="text-align:right;">
0.26
</td>
</tr>
<tr>
<td style="text-align:right;">
23
</td>
<td style="text-align:left;">
Kansas City Scouts
</td>
<td style="text-align:right;">
27
</td>
<td style="text-align:right;">
110
</td>
<td style="text-align:right;">
0.20
</td>
</tr>
<tr>
<td style="text-align:right;">
2
</td>
<td style="text-align:left;">
Montreal Wanderers
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
5
</td>
<td style="text-align:right;">
0.17
</td>
</tr>
<tr>
<td style="text-align:right;">
4
</td>
<td style="text-align:left;">
Quebec Bulldogs
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
20
</td>
<td style="text-align:right;">
0.17
</td>
</tr>
<tr>
<td style="text-align:right;">
9
</td>
<td style="text-align:left;">
Philadelphia Quakers
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
36
</td>
<td style="text-align:right;">
0.10
</td>
</tr>
</tbody>
</table>
You should create some contingency tables
<table class="table" style="margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:left;">
franchiseName
</th>
<th style="text-align:right;">
Center Forward
</th>
<th style="text-align:right;">
Defenseman
</th>
<th style="text-align:right;">
Left Wing Forward
</th>
<th style="text-align:right;">
Right Wing Forward
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Anaheim Ducks
</td>
<td style="text-align:right;">
1659
</td>
<td style="text-align:right;">
859
</td>
<td style="text-align:right;">
1392
</td>
<td style="text-align:right;">
1712
</td>
</tr>
<tr>
<td style="text-align:left;">
Arizona Coyotes
</td>
<td style="text-align:right;">
2909
</td>
<td style="text-align:right;">
1554
</td>
<td style="text-align:right;">
2362
</td>
<td style="text-align:right;">
2835
</td>
</tr>
<tr>
<td style="text-align:left;">
Boston Bruins
</td>
<td style="text-align:right;">
6687
</td>
<td style="text-align:right;">
3017
</td>
<td style="text-align:right;">
5649
</td>
<td style="text-align:right;">
5691
</td>
</tr>
<tr>
<td style="text-align:left;">
Brooklyn Americans
</td>
<td style="text-align:right;">
519
</td>
<td style="text-align:right;">
202
</td>
<td style="text-align:right;">
519
</td>
<td style="text-align:right;">
403
</td>
</tr>
<tr>
<td style="text-align:left;">
Buffalo Sabres
</td>
<td style="text-align:right;">
3966
</td>
<td style="text-align:right;">
1563
</td>
<td style="text-align:right;">
3229
</td>
<td style="text-align:right;">
3631
</td>
</tr>
<tr>
<td style="text-align:left;">
Calgary Flames
</td>
<td style="text-align:right;">
4036
</td>
<td style="text-align:right;">
1805
</td>
<td style="text-align:right;">
2729
</td>
<td style="text-align:right;">
3692
</td>
</tr>
<tr>
<td style="text-align:left;">
Carolina Hurricanes
</td>
<td style="text-align:right;">
3298
</td>
<td style="text-align:right;">
1328
</td>
<td style="text-align:right;">
2828
</td>
<td style="text-align:right;">
2113
</td>
</tr>
<tr>
<td style="text-align:left;">
Chicago Blackhawks
</td>
<td style="text-align:right;">
5932
</td>
<td style="text-align:right;">
2610
</td>
<td style="text-align:right;">
5546
</td>
<td style="text-align:right;">
5374
</td>
</tr>
<tr>
<td style="text-align:left;">
Cleveland Barons
</td>
<td style="text-align:right;">
713
</td>
<td style="text-align:right;">
335
</td>
<td style="text-align:right;">
446
</td>
<td style="text-align:right;">
802
</td>
</tr>
<tr>
<td style="text-align:left;">
Colorado Avalanche
</td>
<td style="text-align:right;">
3530
</td>
<td style="text-align:right;">
1441
</td>
<td style="text-align:right;">
2998
</td>
<td style="text-align:right;">
2440
</td>
</tr>
<tr>
<td style="text-align:left;">
Columbus Blue Jackets
</td>
<td style="text-align:right;">
1317
</td>
<td style="text-align:right;">
619
</td>
<td style="text-align:right;">
1250
</td>
<td style="text-align:right;">
835
</td>
</tr>
<tr>
<td style="text-align:left;">
Dallas Stars
</td>
<td style="text-align:right;">
4465
</td>
<td style="text-align:right;">
1643
</td>
<td style="text-align:right;">
3451
</td>
<td style="text-align:right;">
3099
</td>
</tr>
<tr>
<td style="text-align:left;">
Detroit Red Wings
</td>
<td style="text-align:right;">
7398
</td>
<td style="text-align:right;">
2536
</td>
<td style="text-align:right;">
5315
</td>
<td style="text-align:right;">
4841
</td>
</tr>
<tr>
<td style="text-align:left;">
Edmonton Oilers
</td>
<td style="text-align:right;">
3817
</td>
<td style="text-align:right;">
1612
</td>
<td style="text-align:right;">
2289
</td>
<td style="text-align:right;">
2983
</td>
</tr>
<tr>
<td style="text-align:left;">
Florida Panthers
</td>
<td style="text-align:right;">
1870
</td>
<td style="text-align:right;">
857
</td>
<td style="text-align:right;">
1303
</td>
<td style="text-align:right;">
1564
</td>
</tr>
<tr>
<td style="text-align:left;">
Hamilton Tigers
</td>
<td style="text-align:right;">
239
</td>
<td style="text-align:right;">
79
</td>
<td style="text-align:right;">
65
</td>
<td style="text-align:right;">
122
</td>
</tr>
<tr>
<td style="text-align:left;">
Los Angeles Kings
</td>
<td style="text-align:right;">
4231
</td>
<td style="text-align:right;">
1862
</td>
<td style="text-align:right;">
3452
</td>
<td style="text-align:right;">
3439
</td>
</tr>
<tr>
<td style="text-align:left;">
Minnesota Wild
</td>
<td style="text-align:right;">
1356
</td>
<td style="text-align:right;">
628
</td>
<td style="text-align:right;">
982
</td>
<td style="text-align:right;">
1129
</td>
</tr>
<tr>
<td style="text-align:left;">
Montréal Canadiens
</td>
<td style="text-align:right;">
6606
</td>
<td style="text-align:right;">
2828
</td>
<td style="text-align:right;">
6039
</td>
<td style="text-align:right;">
6256
</td>
</tr>
<tr>
<td style="text-align:left;">
Montreal Maroons
</td>
<td style="text-align:right;">
531
</td>
<td style="text-align:right;">
294
</td>
<td style="text-align:right;">
304
</td>
<td style="text-align:right;">
345
</td>
</tr>
<tr>
<td style="text-align:left;">
Montreal Wanderers
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
6
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
6
</td>
</tr>
<tr>
<td style="text-align:left;">
Nashville Predators
</td>
<td style="text-align:right;">
1696
</td>
<td style="text-align:right;">
883
</td>
<td style="text-align:right;">
1005
</td>
<td style="text-align:right;">
1070
</td>
</tr>
<tr>
<td style="text-align:left;">
New Jersey Devils
</td>
<td style="text-align:right;">
3611
</td>
<td style="text-align:right;">
1421
</td>
<td style="text-align:right;">
2126
</td>
<td style="text-align:right;">
3354
</td>
</tr>
<tr>
<td style="text-align:left;">
New York Islanders
</td>
<td style="text-align:right;">
4145
</td>
<td style="text-align:right;">
1643
</td>
<td style="text-align:right;">
2706
</td>
<td style="text-align:right;">
3464
</td>
</tr>
<tr>
<td style="text-align:left;">
New York Rangers
</td>
<td style="text-align:right;">
6090
</td>
<td style="text-align:right;">
2815
</td>
<td style="text-align:right;">
5060
</td>
<td style="text-align:right;">
5997
</td>
</tr>
<tr>
<td style="text-align:left;">
Ottawa Senators
</td>
<td style="text-align:right;">
2198
</td>
<td style="text-align:right;">
962
</td>
<td style="text-align:right;">
1281
</td>
<td style="text-align:right;">
1750
</td>
</tr>
<tr>
<td style="text-align:left;">
Philadelphia Flyers
</td>
<td style="text-align:right;">
4794
</td>
<td style="text-align:right;">
1839
</td>
<td style="text-align:right;">
3215
</td>
<td style="text-align:right;">
3788
</td>
</tr>
<tr>
<td style="text-align:left;">
Philadelphia Quakers
</td>
<td style="text-align:right;">
20
</td>
<td style="text-align:right;">
106
</td>
<td style="text-align:right;">
255
</td>
<td style="text-align:right;">
71
</td>
</tr>
<tr>
<td style="text-align:left;">
Pittsburgh Penguins
</td>
<td style="text-align:right;">
5195
</td>
<td style="text-align:right;">
1799
</td>
<td style="text-align:right;">
2829
</td>
<td style="text-align:right;">
3968
</td>
</tr>
<tr>
<td style="text-align:left;">
San Jose Sharks
</td>
<td style="text-align:right;">
2632
</td>
<td style="text-align:right;">
931
</td>
<td style="text-align:right;">
1330
</td>
<td style="text-align:right;">
1520
</td>
</tr>
<tr>
<td style="text-align:left;">
St. Louis Blues
</td>
<td style="text-align:right;">
4072
</td>
<td style="text-align:right;">
1645
</td>
<td style="text-align:right;">
2822
</td>
<td style="text-align:right;">
4214
</td>
</tr>
<tr>
<td style="text-align:left;">
St. Louis Eagles
</td>
<td style="text-align:right;">
294
</td>
<td style="text-align:right;">
323
</td>
<td style="text-align:right;">
522
</td>
<td style="text-align:right;">
405
</td>
</tr>
<tr>
<td style="text-align:left;">
Tampa Bay Lightning
</td>
<td style="text-align:right;">
2409
</td>
<td style="text-align:right;">
846
</td>
<td style="text-align:right;">
1399
</td>
<td style="text-align:right;">
1494
</td>
</tr>
<tr>
<td style="text-align:left;">
Toronto Maple Leafs
</td>
<td style="text-align:right;">
6739
</td>
<td style="text-align:right;">
2812
</td>
<td style="text-align:right;">
5485
</td>
<td style="text-align:right;">
5781
</td>
</tr>
<tr>
<td style="text-align:left;">
Vancouver Canucks
</td>
<td style="text-align:right;">
3641
</td>
<td style="text-align:right;">
1816
</td>
<td style="text-align:right;">
3507
</td>
<td style="text-align:right;">
3102
</td>
</tr>
<tr>
<td style="text-align:left;">
Vegas Golden Knights
</td>
<td style="text-align:right;">
344
</td>
<td style="text-align:right;">
145
</td>
<td style="text-align:right;">
226
</td>
<td style="text-align:right;">
213
</td>
</tr>
<tr>
<td style="text-align:left;">
Washington Capitals
</td>
<td style="text-align:right;">
3474
</td>
<td style="text-align:right;">
1754
</td>
<td style="text-align:right;">
2718
</td>
<td style="text-align:right;">
3502
</td>
</tr>
<tr>
<td style="text-align:left;">
Winnipeg Jets
</td>
<td style="text-align:right;">
1427
</td>
<td style="text-align:right;">
650
</td>
<td style="text-align:right;">
1610
</td>
<td style="text-align:right;">
914
</td>
</tr>
</tbody>
</table>
You should create numerical summaries for some quantitative variables at
each setting of some of your categorical variables
<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Summary Goals by Position Center Forward
</caption>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
goals
</th>
<th style="text-align:right;">
gamesPlayed
</th>
<th style="text-align:right;">
mostGoalsOneGame
</th>
<th style="text-align:right;">
mostGoalsOneSeason
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Min.
</td>
<td style="text-align:right;">
0.0
</td>
<td style="text-align:right;">
1.0
</td>
<td style="text-align:right;">
0.0
</td>
<td style="text-align:right;">
0.0
</td>
</tr>
<tr>
<td style="text-align:left;">
1st Qu.
</td>
<td style="text-align:right;">
1.0
</td>
<td style="text-align:right;">
15.0
</td>
<td style="text-align:right;">
1.0
</td>
<td style="text-align:right;">
1.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Median
</td>
<td style="text-align:right;">
6.0
</td>
<td style="text-align:right;">
55.0
</td>
<td style="text-align:right;">
1.0
</td>
<td style="text-align:right;">
5.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Mean
</td>
<td style="text-align:right;">
27.6
</td>
<td style="text-align:right;">
121.2
</td>
<td style="text-align:right;">
1.4
</td>
<td style="text-align:right;">
9.4
</td>
</tr>
<tr>
<td style="text-align:left;">
3rd Qu.
</td>
<td style="text-align:right;">
26.0
</td>
<td style="text-align:right;">
148.0
</td>
<td style="text-align:right;">
2.0
</td>
<td style="text-align:right;">
14.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Max.
</td>
<td style="text-align:right;">
692.0
</td>
<td style="text-align:right;">
1607.0
</td>
<td style="text-align:right;">
7.0
</td>
<td style="text-align:right;">
92.0
</td>
</tr>
</tbody>
</table>
<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Summary Goals by Position Defenseman
</caption>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
goals
</th>
<th style="text-align:right;">
gamesPlayed
</th>
<th style="text-align:right;">
mostGoalsOneGame
</th>
<th style="text-align:right;">
mostGoalsOneSeason
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Min.
</td>
<td style="text-align:right;">
0.0
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
0.0
</td>
<td style="text-align:right;">
0.0
</td>
</tr>
<tr>
<td style="text-align:left;">
1st Qu.
</td>
<td style="text-align:right;">
0.0
</td>
<td style="text-align:right;">
15
</td>
<td style="text-align:right;">
0.0
</td>
<td style="text-align:right;">
0.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Median
</td>
<td style="text-align:right;">
2.0
</td>
<td style="text-align:right;">
56
</td>
<td style="text-align:right;">
1.0
</td>
<td style="text-align:right;">
2.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Mean
</td>
<td style="text-align:right;">
8.7
</td>
<td style="text-align:right;">
117
</td>
<td style="text-align:right;">
0.9
</td>
<td style="text-align:right;">
3.4
</td>
</tr>
<tr>
<td style="text-align:left;">
3rd Qu.
</td>
<td style="text-align:right;">
8.0
</td>
<td style="text-align:right;">
150
</td>
<td style="text-align:right;">
1.0
</td>
<td style="text-align:right;">
5.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Max.
</td>
<td style="text-align:right;">
395.0
</td>
<td style="text-align:right;">
1564
</td>
<td style="text-align:right;">
5.0
</td>
<td style="text-align:right;">
48.0
</td>
</tr>
</tbody>
</table>
<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Summary Goals by Position Left Wing Forward
</caption>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
goals
</th>
<th style="text-align:right;">
gamesPlayed
</th>
<th style="text-align:right;">
mostGoalsOneGame
</th>
<th style="text-align:right;">
mostGoalsOneSeason
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Min.
</td>
<td style="text-align:right;">
0.0
</td>
<td style="text-align:right;">
1.0
</td>
<td style="text-align:right;">
0.0
</td>
<td style="text-align:right;">
0.0
</td>
</tr>
<tr>
<td style="text-align:left;">
1st Qu.
</td>
<td style="text-align:right;">
1.0
</td>
<td style="text-align:right;">
14.0
</td>
<td style="text-align:right;">
1.0
</td>
<td style="text-align:right;">
1.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Median
</td>
<td style="text-align:right;">
5.0
</td>
<td style="text-align:right;">
52.0
</td>
<td style="text-align:right;">
1.0
</td>
<td style="text-align:right;">
4.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Mean
</td>
<td style="text-align:right;">
24.1
</td>
<td style="text-align:right;">
110.5
</td>
<td style="text-align:right;">
1.4
</td>
<td style="text-align:right;">
8.8
</td>
</tr>
<tr>
<td style="text-align:left;">
3rd Qu.
</td>
<td style="text-align:right;">
24.0
</td>
<td style="text-align:right;">
141.0
</td>
<td style="text-align:right;">
2.0
</td>
<td style="text-align:right;">
14.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Max.
</td>
<td style="text-align:right;">
730.0
</td>
<td style="text-align:right;">
1436.0
</td>
<td style="text-align:right;">
6.0
</td>
<td style="text-align:right;">
65.0
</td>
</tr>
</tbody>
</table>
<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Summary Goals by Position Right Wing Forward
</caption>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
goals
</th>
<th style="text-align:right;">
gamesPlayed
</th>
<th style="text-align:right;">
mostGoalsOneGame
</th>
<th style="text-align:right;">
mostGoalsOneSeason
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Min.
</td>
<td style="text-align:right;">
0.0
</td>
<td style="text-align:right;">
1.0
</td>
<td style="text-align:right;">
0.0
</td>
<td style="text-align:right;">
0.0
</td>
</tr>
<tr>
<td style="text-align:left;">
1st Qu.
</td>
<td style="text-align:right;">
1.0
</td>
<td style="text-align:right;">
15.0
</td>
<td style="text-align:right;">
1.0
</td>
<td style="text-align:right;">
1.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Median
</td>
<td style="text-align:right;">
6.0
</td>
<td style="text-align:right;">
53.0
</td>
<td style="text-align:right;">
1.0
</td>
<td style="text-align:right;">
5.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Mean
</td>
<td style="text-align:right;">
28.2
</td>
<td style="text-align:right;">
117.9
</td>
<td style="text-align:right;">
1.5
</td>
<td style="text-align:right;">
9.9
</td>
</tr>
<tr>
<td style="text-align:left;">
3rd Qu.
</td>
<td style="text-align:right;">
27.0
</td>
<td style="text-align:right;">
146.5
</td>
<td style="text-align:right;">
2.0
</td>
<td style="text-align:right;">
15.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Max.
</td>
<td style="text-align:right;">
786.0
</td>
<td style="text-align:right;">
1687.0
</td>
<td style="text-align:right;">
5.0
</td>
<td style="text-align:right;">
86.0
</td>
</tr>
</tbody>
</table>

You should create at least five plots utilizing coloring, grouping, etc.
All plots should have nice labels and titles.
![](C:\Docs\NC-State\Course\558-DA~1\Project\project1\git-repo\ST558P~1\README~1/figure-gfm/unnamed-chunk-14-1.png)<!-- -->![](C:\Docs\NC-State\Course\558-DA~1\Project\project1\git-repo\ST558P~1\README~1/figure-gfm/unnamed-chunk-14-2.png)<!-- -->![](C:\Docs\NC-State\Course\558-DA~1\Project\project1\git-repo\ST558P~1\README~1/figure-gfm/unnamed-chunk-14-3.png)<!-- -->![](C:\Docs\NC-State\Course\558-DA~1\Project\project1\git-repo\ST558P~1\README~1/figure-gfm/unnamed-chunk-14-4.png)<!-- -->

sdfd

    ##  [1] 15 28 11 25 16 18 24 20 13  5  6  3  4  2  9 12  7  8 31 10  1 27 22 21 23 29
    ## [27] 32 33 30 19 37 26 17 38 34 35 14 36
