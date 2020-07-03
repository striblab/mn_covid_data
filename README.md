# Minnesota COVID data from the Star Tribune

The Star Tribune has compiled daily data released by the Minnesota Department of Health on the COVID-19 outbreak in Minnesota. The health department generally released updated case information daily at 11 a.m. central time, but the scraper automatically updates these four spreadsheets hourly in case other updates or corrections are made to the site.

MDH releases additional information in a daily media briefing, including the county where deaths occurred, which is compiled manually.

Every effort has been made to keep the data accurate and up to date. However, MDH occasionally revises the location of a case after completing its investigation. In some instances in which a case was moved, the daily count may vary from what MDH originally reported. In other words, it is possible for the daily count for a county to be negative if a case was previously reported and then moved.

### Copyright and license
The Star Tribune's COVID-19 spreadsheets posted here are open data, licensed under the Open Data Commons Open Database License (ODbL) by the Star Tribune.

You are free to copy, distribute, transmit and adapt the spreadsheets, so long as you:

- Credit the Star Tribune as specified below.
- Inform the Star Tribune that you are using the spreadsheets in your work by emailing Michael Corey at michael.corey@startribune.com.

If you alter or build upon our data, you may distribute the result only under the same licence. The [full legal code](https://opendatacommons.org/licenses/odbl/1.0/) explains your rights and responsibilities.

### How to credit the Star Tribune

We require that you use the credit “Star Tribune and Minneasota Department of Health." The credit must link to https://www.startribune.com/coronavirus-covid-19-minnesota-tracker-map-county-data/568712601/, unless the credit is appearing in printed media.

You must also make it clear to anyone who requests access to the data that it is available under the Open Database License. If you are distributing the spreadsheets in a data form, you can name and [link directly to the license](https://opendatacommons.org/licenses/odbl/1.0/).

### Fields in the data

#### mn_positive_tests_by_county.csv

A snapshot of the latest cumulative county-by-county data from the Minnesota Department of Health. Positive tests are sourced from https://www.health.state.mn.us/diseases/coronavirus/situation.html. Deaths are based on information from the Minnesota Department of Health and Star Tribune reporting.

|Column name|Format|Description|
|---|---|---|
|county_fips|string|Combination of state and county FIPS codes|
|county_name|string|County name|
|total_positive_tests|integer|Number of cumulative positive COVID-19 tests in county|
|total_deaths|integer|Number of cumulative COVID-19 deaths in county|
|latitude|float|Latitude of county centroid|
|longitude|float|Longitude of county centroid|


#### mn_statewide_latest.csv

A snapshot of the latest cumulative statewide data from the Minnesota Department of Health. Test and hospitalization data are sourced from https://www.health.state.mn.us/diseases/coronavirus/situation.html. Deaths are based on information from the Minnesota Department of Health and Star Tribune reporting.

|Column name|Format|Description|
|---|---|---|
|total_confirmed_cases|integer|Number of cumulative positive COVID-19 tests statewide|
|cases_daily_change|integer|Difference between total_confirmed_cases yesterday and today|
|daily_cases_newly_reported|integer|"New" cases as reported by MDH. This plus cases_removed should add up to daily change. Starts May 18, 2020.|
|daily_cases_removed|integer|Cases removed on this day by MDH. This plus daily_cases_newly_reported should add up to daily change. Cases may be removed becase of false positives or because a patient is later determined to have been not a Minnesota resident, for example. Starts May 18, 2020.|
|total_statewide_deaths|integer|Number of deaths statewide|
|daily_statewide_deaths|integer|Number of newly reported deaths statewide|
|total_statewide_recoveries|integer|Number of "patients who no longer need to be isolated," according to MDH. Please note, this includes patients who have died.|
|last_update
|total_completed_tests|integer|Number of cumulative COVID-19 tests completed statewide, positive and negative|
|total_completed_mdh|integer|Number of cumulative COVID-19 tests completed statewide by the state's Public Health Lab. (Data begins April 1, 2020)|
|total_completed_private|integer|Number of cumulative COVID-19 tests completed statewide by external labs. (Data begins April 1, 2020)|
|total_hospitalized|integer|Number of cumulative hospitalized people statewide A single person who was hospitalized twice would could as two hospitalizations, according to MDH.|
|currently_hospitalized|integer|Number of people currently hospitalized|
|currently_in_icu|integer|Number of people currently in ICU care|
|last_update|datetime|Timestamp when scraper last ran|


#### mn_statewide_timeseries.csv

A statewide daily county of positive COVID-19 tests, compiled by daily scraping of the [Minnesota Department of Health's coronavirus situation page](https://www.health.state.mn.us/diseases/coronavirus/situation.html). Deaths are based on information from the Minnesota Department of Health and Star Tribune reporting.

**UPDATE May 14, 2020:** The Minnesota Department of Health changed its methodology and is now assigning positive tests to the date the specimen was taken, not the date it was reported to MDH. We have updated our data to reflect this change, including past numbers. We have also corrected a double-counting of total tests that MDH was reporting in error from April 25 through May 5.

**UPDATE April 3, 2020:** The Minnesota Department of Health released daily hospitalization numbers on April 3, 2020, in which the data for previous days differed significantly from the numbers they reported on conference calls at the time. The health department reports that the information on the calls was not final and that the data released later should be regarded as more accurate. We have updated our records to reflect these new numbers.

**UPDATE July 3, 2020:** The Minnesota Department of Health will not be updating its situation page on July 4. As a result, our records will not reflect updates on that day. MDH will still collect data for July 4, but will release that data on July 5. Some data may get backdated to July 4, but July 5's data may appear inflated as a result.

|Column name|Format|Description|
|---|---|---|
|date|date|YYYY-MM-DD|
|total_confirmed_cases|integer|Number of cumulative positive COVID-19 tests statewide|
|cases_daily_change|integer|Difference between total_confirmed_cases this day and the previous day|
|cases_newly_reported|integer|"New" cases as reported by MDH. This plus cases_removed should add up to daily change. Starts May 18, 2020.|
|cases_removed|integer|Cases removed on this day by MDH. This plus daily_cases_newly_reported should add up to daily change. Cases may be removed becase of false positives or because a patient is later determined to have been not a Minnesota resident, for example. Starts May 18, 2020.|
|cases_sample_date|integer|Number of new positive COVID-19 tests reported statewide on this date, calculated by the date each test speciman was given, not the date it was reported by MDH.|
|cases_total_sample_date|integer|Number of cumulative positive COVID-19 tests statewide by this date, calculated by the date each test speciman was given, not the date it was reported by MDH.|
|total_hospitalized|integer|Number of cumulative hospitalized people statewide by this date. A single person who was hospitalized twice would could as two hospitalizations, according to MDH.|
|currently_hospitalized|integer|Number of people currently hospitalized on this date|
|currently_in_icu|integer|Number of people currently in ICU care on this date|
|total_statewide_deaths|integer|Number of deaths statewide by this date|
|new_statewide_deaths|integer|Number of new deaths reported statewide on this date|
|total_statewide_recoveries|integer|Number of "patients who no longer need to be isolated," according to MDH.|
|total_completed_tests|integer|Number of total tests completed statewide, by both government and private labs. Please note that this number is pegged to the date MDH reported the number to the public, not the date when it was received by MDH, so this number may be time-shifted one day from what is published on MDH's website.|
|new_completed_tests|integer|Number of new tests completed statewide since the previous day. Please note that this number is pegged to the date MDH reported the number to the public, not the date when it was received by MDH, so this number may be time-shifted one day from what is published on MDH's website.|

#### mn_county_timeseries_tall.csv

A "tall" timeseries of each county's positive tests and deaths by a given date. Only counties with at least one positive test are included. Compiled by daily scraping of the [Minnesota Department of Health's coronavirus situation page](https://www.health.state.mn.us/diseases/coronavirus/situation.html) Deaths are based on information from the Minnesota Department of Health and Star Tribune reporting.

|Column name|Format|Description|
|---|---|---|
|date|date|YYYY-MM-DD|
|county|string|County name|
|daily_cases|integer|Number of new positive COVID-19 tests reported on this date|
|cumulative_cases|integer|Number of cumulative positive COVID-19 tests by this date|
|daily_deaths|integer|Number of new COVID-19 deaths reported on this date|
|cumulative_deaths|integer|Number of cumulative COVID-19 deaths by this date|

#### mn_county_timeseries_all_counties.csv

Same fields and sources as the "tall" timeseries. This file includes all Minnesota counties and all dates, even if that county has never had a confirmed COVID-19 case.

#### mn_ages_latest.csv

A snapshot of the latest cumulative statewide age data from the [Minnesota Department of Health's coronavirus situation page](https://www.health.state.mn.us/diseases/coronavirus/situation.html).

|Column name|Format|Description|
|---|---|---|
age_group|string|Description of age group
pct_of_cases|integer|Percentage of cumulative cases that are in this age group. -1 indicates a value of "<1%"|
pct_of_deaths|integer|Percentage of cumulative deaths that are in this age group. -1 indicates a value of "<1%"|

#### mn_county_timeseries.csv (Deprecated)

**This file is no longer being updated. If it's something you were using, please let us know and we will resume updates.**

A "wide" timeseries of each county's cumulative positive COVID-19 tests by the date in each column header. Only counties with at least one positive test are included. Compiled by daily scraping of the [Minnesota Department of Health's coronavirus situation page](https://www.health.state.mn.us/diseases/coronavirus/situation.html).

|Column name|Format|Description|
|---|---|---|
|county|string|County name|
|[YYYY-MM-DD]|integer|Number of cumulative positive COVID-19 tests statewide by this date|
