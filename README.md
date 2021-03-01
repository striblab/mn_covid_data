# Minnesota COVID data from the Star Tribune

The Star Tribune has compiled daily data released by the Minnesota Department of Health on the COVID-19 outbreak in Minnesota. The health department generally released updated case information daily at 11 a.m. central time, but the scraper automatically updates these four spreadsheets hourly in case other updates or corrections are made to the site.

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

#### mn_age_timeseries.csv

|Column name|Format|Description|
|---|---|---|
|date|date|YYYY-MM-DD|
|week_num|string|Combination of year an MMWR week, e.g. 2021-01, to differentiate years|
|week_num_int|integer|MMWR week alone, without year.|
|start_date|date|Week start date. YYYY-MM-DD|
|end_date|date|Week end date. YYYY-MM-DD|
|strib_age_group|string|The age range, in 5-year increments from age 0 to 20, then 10-year increments, then 90+|
|age_group_cases|int|Weekly number of cases in this age group|
|total_weekly_cases|int|Weekly number of cases in ALL age groups|
|pct_cases|float|Percentage of total weekly cases that are in this age group|
|age_group_deaths|int|Weekly number of deaths in this age group|
|total_weekly_deaths|int|Weekly number of deaths in ALL age groups|
|pct_deaths|float|Percentage of total weekly deaths that are in this age group|

#### mn_county_timeseries_tall.csv

A "tall" timeseries of each county's positive tests and deaths by a given date. Only counties with at least one positive test on a given date are included. Compiled by daily scraping of the [Minnesota Department of Health's coronavirus situation page](https://www.health.state.mn.us/diseases/coronavirus/situation.html) Deaths are based on information from the Minnesota Department of Health and Star Tribune reporting.

|Column name|Format|Description|
|---|---|---|
|date|date|YYYY-MM-DD|
|county|string|County name|
|fips|string|County FIPS, including state code (27)|
|daily_cases|integer|Number of new confirmed cases reported on this date|
|daily_cases_per_1k|float|New confirmed cases per 1,000 county residents on this date|
|cumulative_cases|integer|Number of cumulative positive COVID-19 tests by this date|
|cases_per_1k|total|Number of total confirmed cases per 1,000 county residents (2019 ACS 5-year estimate)|
|daily_deaths|integer|Number of new COVID-19 deaths reported on this date|
|cumulative_deaths|integer|Number of cumulative COVID-19 deaths by this date|
|deaths_per_1k|total|Number of total deaths per 1,000 county residents (2019 ACS 5-year estimate)|
|cases_rolling|float|7-day rolling average (mean) of daily_cases|
|deaths_rolling|float|7-day rolling average (mean) of daily_deaths|
|cases_weekly_chg|integer|Change in total cases from 7 days before|
|cases_weekly_per_1k|float|Change in total cases from 7 days before per 1,000 county residents|
|cases_weekly_pct_chg|float|Percent change in total cases from 7 days before|

#### mn_county_timeseries_all_counties.csv

This file now has significantly less detail then the "tall" timeseries, but includes all Minnesota counties and all dates, even before a first confirmed case. This spreadsheet is likely to be deprecated in the future, but the "all dates" aspect will be migrated to the more complete "tall" timeseries.

|Column name|Format|Description|
|---|---|---|
|date|date|YYYY-MM-DD|
|county|string|County name|
|daily_cases|integer|Number of new positive COVID-19 tests reported on this date|
|cumulative_cases|integer|Number of cumulative positive COVID-19 tests by this date|
|daily_deaths|integer|Number of new COVID-19 deaths reported on this date|
|cumulative_deaths|integer|Number of cumulative COVID-19 deaths by this date|


#### mn_hosp_capacity_timeseries.csv
This file tracks hospital capacity overall rather than by COVID status, and is provided via the MNTRAC system by the Minnesota Department of Health. Data in MNTRAC is submitted by Minnesota hospitals daily and reported the following day. [Original file available for download here](https://mn.gov/covid19/data/response-prep/response-capacity.jsp). Data is updated on weekdays, with separate data for Saturdays and Sundays released on Mondays.

|Column name|Format|Description|
|---|---|---|
|data_date|date|Date reported to MDH, not date reported to public. YYYY-MM-DD|
|beds_surge_in_use|integer|Number of beds not normally in hospital census and operation are currently being re-purposed to care for a patient|
|icu_in_use|integer|Number of ICU beds currently in use|
|non_icu_in_use|integer|Number of non-ICU beds currently in use.|
|vents_in_use|integer|Number of ventilators currently in use|
|vents_surge_in_use|integer|Number of "surge" ventilators currently in use|
|bed_cap_surge|integer|Number of beds not normally in hospital census and operation that COULD be re-purposed to care for a patient with current constraints of staffing and space.|
|icu_cap|integer|Number of staffed ICU beds total, including beds currently occupied.|
|non_icu_cap|integer|Number of staffed non-ICU beds total, including beds currently occupied.|
|vent_cap|integer|Number of ventilators total, including those in use.|
|vent_cap_surge|integer|Number of "surge" ventilators total, including those in use.|
|hosp_icu_95pct+|integer|Number of hospitals where ICU is at more than 95% capacity.|
|hosp_icu_reporting|integer|Number of hospitals currently reporting their ICU data.|
|hosp_non_icu_95pct+|integer|Number of hospitals where non-ICU is at more than 95% capacity.|
|hosp_non_icu_reporting|integer|Number of hospitals currently reporting their non-ICU data.|
|hosp_pct_icu_reporting|float|Percent of total number of hospitals expected to report ICU data that reported on this date.|
|hosp_pct_non_icu_reporting|float|Percent of total number of hospitals expected to report non-ICU data that reported on this date.|
|icu_pct_cap|float|Statewide percent of total ICU bed capacity currently occupied.|
|non_icu_pct_cap|float|Statewide percent of total non-ICU bed capacity currently occupied.|
|vent_pct_cap|float|Statewide percent of total ventilators currently in use.|


#### mn_hosp_covid_timeseries.csv

This file is provided via the federal TeleTracking system and is not directly comparable to the MNTrac capacity data listed above because of differences in reporting schedules. [Original file available for download here](https://mn.gov/covid19/data/response-prep/response-capacity.jsp). Data is updated on weekdays, with separate data for Saturdays and Sundays released on Mondays.

|Column name|Format|Description|
|---|---|---|
|data_date|date|Date reported to MDH, not date reported to public. YYYY-MM-DD|
|icu_covid|integer|Number of ICU beds occupied by COVID+ patients.|
|icu_non_covid|integer|Number of non-ICU beds occupied by COVID+ patients.|
|non_icu_covid|integer|Number of ICU beds occupied by non-COVID patients.|
|non_icu_non_covid|integer|Number of non-ICU beds occupied by non-COVID patients.|
|covid_total|integer|Total number of beds currently occupied by COVID+ patients. Sum of ICU and non-ICU.|
|icu_total|integer|Total number of ICU beds occupied statewide. Please note that especially recent data may differ significantly from MNTrac data, as oulined above and is not directly comparable.|
|beds_total|integer|Total number of non-ICU beds occupied statewide. Please note that especially recent data may differ significantly from MNTrac data, as oulined above and is not directly comparable.|

#### mn_statewide_latest.csv

A snapshot of the latest cumulative statewide data from the Minnesota Department of Health. Sourced from https://www.health.state.mn.us/diseases/coronavirus/situation.html. Deaths are now based on information from the Minnesota Department of Health, though some of the earliest data comes from Star Tribune reporting. Likely to be deprecated in the future.

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
|total_hospitalized|integer|Number of cumulative hospitalized people statewide A single person who was hospitalized twice would could as two hospitalizations, according to MDH.|
|currently_hospitalized|integer|Number of people currently hospitalized. Reporting system changed by MDH starting Sept. 24, 2020. (See mn_hosp_covid_timeseries.csv)|
|currently_in_icu|integer|Number of people currently in ICU care. Reporting system changed by MDH starting Sept. 24, 2020. (See mn_hosp_covid_timeseries.csv)|
|last_update|datetime|Timestamp when scraper last ran|


#### mn_statewide_timeseries.csv

A statewide daily county of positive COVID-19 tests, compiled by daily scraping of the [Minnesota Department of Health's coronavirus situation page](https://www.health.state.mn.us/diseases/coronavirus/situation.html). Deaths are based on information from the Minnesota Department of Health and Star Tribune reporting.

**UPDATE May 14, 2020:** The Minnesota Department of Health changed its methodology and is now assigning positive tests to the date the specimen was taken, not the date it was reported to MDH. We have updated our data to reflect this change, including past numbers. We have also corrected a double-counting of total tests that MDH was reporting in error from April 25 through May 5.

**UPDATE April 3, 2020:** The Minnesota Department of Health released daily hospitalization numbers on April 3, 2020, in which the data for previous days differed significantly from the numbers they reported on conference calls at the time. The health department reports that the information on the calls was not final and that the data released later should be regarded as more accurate. We have updated our records to reflect these new numbers.

**UPDATE July 3, 2020:** The Minnesota Department of Health will not be updating its situation page on July 4. As a result, our records will not reflect updates on that day. MDH will still collect data for July 4, but will release that data on July 5. Some data may get backdated to July 4, but July 5's data may appear inflated as a result.

**UPDATE Sept. 24, 2020:** The Minnesota Department of Health has stopped reporting the number of patients currently hospitalized and in ICU. They also added two fields to track new hospital and ICU admissions by admission date.


|Column name|Format|Description|
|---|---|---|
|date|date|YYYY-MM-DD|
|total_confirmed_cases|integer|Number of cumulative positive COVID-19 tests statewide|
|cases_daily_change|integer|Difference between total_confirmed_cases this day and the previous day|
|cases_daily_change_rolling|float|7-day floating average (mean) of change in total confirmed cases|
|cases_newly_reported|integer|"New" cases as reported by MDH. This plus cases_removed should add up to daily change. Starts May 18, 2020.|
|cases_removed|integer|Cases removed on this day by MDH. This plus daily_cases_newly_reported should add up to daily change. Cases may be removed becase of false positives or because a patient is later determined to have been not a Minnesota resident, for example. Starts May 18, 2020.|
|cases_sample_date|integer|Number of new positive COVID-19 tests reported statewide on this date, calculated by the date each test speciman was given, not the date it was reported by MDH.|
|cases_sample_date_rolling|float|7-day floating average (mean) of cases_sample_date|
|cases_total_sample_date|integer|Number of cumulative positive COVID-19 tests statewide by this date, calculated by the date each test speciman was given, not the date it was reported by MDH.|
|new_hosp_admissions|integer|Number of patients admitted to a hospital for the first time on this date. Earlier dates are often updated as tests come back for patients admitted in days past.|
|new_hosp_admissions_rolling|float|7-day floating average (mean) of new_hosp_admissions|
|new_icu_admissions|integer|Number of patients admitted to an ICU for the first time on this date. Earlier dates are often updated as tests come back for patients admitted in days past. This is a subset of new_hosp_admissions, meaning these patients are also counted in new_hosp_admissions.|
|new_icu_admissions_rolling|float|7-day floating average (mean) of new_icu_admissions|
|total_hospitalized|integer|Number of cumulative hospitalized people statewide by this date. A single person who was hospitalized twice would could as two hospitalizations, according to MDH.|
|total_icu_admissions|integer|Number of cumulative people statewide admitted to the ICU by this date.|
|currently_hospitalized|integer|Number of people currently hospitalized on this date. Reporting system changed by MDH starting Sept. 24, 2020. (See mn_hosp_covid_timeseries.csv)|
|currently_in_icu|integer|Number of people currently in ICU care on this date. Reporting system changed by MDH starting Sept. 24, 2020. (See mn_hosp_covid_timeseries.csv)|
|hosp_total_daily_change|integer|Change in total_hospitalized since previous day|
|hosp_total_daily_rolling|float|7-day floating average (mean) of hosp_total_daily_change|
|icu_total_daily_change|integer|Change in total_icu_admissions since previous day|
|icu_total_daily_rolling|integer|7-day floating average (mean) of icu_total_daily_change|
|total_statewide_deaths|integer|Number of deaths statewide by this date|
|new_statewide_deaths|integer|Number of new deaths reported statewide on this date|
|new_statewide_deaths_rolling|float|7-day floating average (mean) of new deaths|
|total_statewide_recoveries|integer|Number of "patients who no longer need to be isolated," according to MDH.|
|total_completed_tests|integer|Number of total tests completed statewide, by both government and private labs. Please note that this number is pegged to the date MDH reported the number to the public, not the date when it was received by MDH, so this number may be time-shifted one day from what is published on MDH's website.|
|new_completed_tests|integer|Number of new tests completed statewide since the previous day. Please note that this number is pegged to the date MDH reported the number to the public, not the date when it was received by MDH, so this number may be time-shifted one day from what is published on MDH's website.|
|new_completed_tests_rolling|float|7-day floating average (mean) of change in completed tests|
|daily_pct_positive|float|cases_daily_change divided by new_completed_tests|
|daily_pct_positive_rolling|float|7-day floating average (mean) of daily_pct_positive|

#### mn_vaccine_admin_timeseries.csv

A statewide look at vaccine administration and distribution. Raw data available on the state's [Vaccine Data dashboard](https://mn.gov/covid19/vaccine/data/index.jsp).

|Column name|Format|Description|
|---|---|---|
|data_date|date|Date reported publicly. YYYY-MM-DD|
|admin_total|integer|Total doses injected statewide.|
|admin_pfizer|integer|Total doses of Pfizer vaccine injected statewide.|
|admin_moderna|integer|Total doses of Pfizer vaccine injected statewide.|
|admin_unknown|integer|Currently number of doses of unknown vaccine type injected statewide.|
|admin_people_total|integer|Total number of people who have received at least one dose of any COVID vaccine.|
|admin_people_completed_total|integer|Total number of people who have received both doses of any COVID vaccine.|
|shipped_pfizer_total|integer|Total doses of Pfizer vaccine that have been shipped to providers in all programs, except federal facilities that are not required to report to Minnesota officials.|
|shipped_moderna_total|integer|Total doses of Moderna vaccine that have been shipped to providers in all programs, except federal facilities that are not required to report to Minnesota officials.|
|shipped_pfizer_mn_providers|integer|"Cumulative count of COVID-19 vaccine doses recorded as shipped to Minnesota providers in the Centers for Disease Control and Prevention’s (CDC) Vaccine Tracking System (VTrckS) since Dec. 13, 2020." Does not include pharmacy doses below or federal facilities that are not required to report to Minnesota officials.|
|shipped_moderna_mn_providers|integer|Same as above, for Moderna.|
|shipped_pfizer_cdc_ltc|integer|"Cumulative count of [Pfizer] COVID-19 vaccine doses that have been transferred out of the state allocation to the federal Pharmacy Partnership Program. These doses are shipped to three large pharmacy chains, CVS, Walgreens, and Thrifty White, who vaccinate staff and residents within long-term care facilities."|
|shipped_moderna_cdc_ltc|integer|Same as above, for Moderna.|
|providers|integer|Number of Minnesota provider sites in all programs, except federal facilities that are not required to report to Minnesota officials.|
|shipped_combined|integer|Total doses of all vaccines that have been shipped to providers in all programs, except federal facilities that are not required to report to Minnesota officials.|
|admin_total_daily|integer|Daily change in total doses of all vaccines injected statewide. Includes data from previous days that was not previously reported.|
|admin_pfizer_daily|integer|Daily change in total doses of Pfizer vaccine injected statewide. Includes data from previous days that was not previously reported.|
|admin_moderna_daily|integer|Daily change in total doses of Moderna vaccine injected statewide. Includes data from previous days that was not previously reported.|
|admin_unknown_daily|integer|Daily change in total doses of unknown vaccine injected statewide.|
|admin_people_total_daily|integer|Daily change in the total number of people statewide who have received at least one vaccine dose.|
|admin_people_completed_total_daily|integer|Daily change in the total number of people statewide who have received both doses of any vaccine.|
|shipped_combined_daily|integer|Daily change of shipped_combined. Includes data from previous days that was not previously reported. |
|shipped_pfizer_daily|integer|Same as above, for Pfizer doses only.|
|shipped_moderna_daily|integer|Same as above, for Moderna doses only.|
|admin_total_weekly|integer|Change in admin_total in last 7 days.|
|admin_total_daily_rolling|integer|7-day rolling average (mean) of admin_total_daily.|
|admin_pfizer_daily_rolling|integer|7-day rolling average (mean) of admin_pfizer_daily.|
|admin_moderna_daily_rolling|integer|7-day rolling average (mean) of admin_moderna_daily.|
|admin_people_total_daily_rolling|integer|7-day rolling average (mean) of admin_people_total_dail.y.|
|admin_people_completed_total_daily_rolling|integer|7-day rolling average (mean) of admin_people_completed_total_daily.|
|shipped_combined_daily_rolling|integer|7-day rolling average (mean) of shipped_combined_daily.|
|shipped_pfizer_daily_rolling|integer|7-day rolling average (mean) of shipped_pfizer_daily.|
|shipped_moderna_daily_rolling|integer|7-day rolling average (mean) of shipped_moderna_daily.|
|admin_pfizer_weekly|integer|Change in admin_pfizer in last 7 days.|
|admin_moderna_weekly|integer|Change in admin_moderna in last 7 days.|
|admin_unknown_weekly|integer|Change in admin_unknown in last 7 days.|
|admin_people_total_weekly|integer|Change in admin_people_total in last 7 days.|
|admin_people_completed_total_weekly|integer|Change in admin_people_completed_total in last 7 days.|
|shipped_combined_weekly|integer|Change in shipped_combined in last 7 days.|
|shipped_pfizer_weekly|integer|Change in shipped_pfizer_total in last 7 days.|
|shipped_moderna_weekly|integer|Change in shipped_moderna_total in last 7 days.|
|admin_doses_total_per_cap|float|Doses administered per Minnesota resident. Population: [ACS 2019 5-year estimate](https://censusreporter.org/data/table/?table=B01003&geo_ids=04000US27,050|04000US27&primary_geo_id=04000US27)|
|admin_people_total_per_cap|float|Percent of Minnesota residents who have received at least one dose of any vaccine. Population: [ACS 2019 5-year estimate](https://censusreporter.org/data/table/?table=B01003&geo_ids=04000US27,050|04000US27&primary_geo_id=04000US27)|
|admin_people_completed_total_per_cap|float|Percent of Minnesota residents who have received both doses of any vaccine. Population: [ACS 2019 5-year estimate](https://censusreporter.org/data/table/?table=B01003&geo_ids=04000US27,050|04000US27&primary_geo_id=04000US27)|
|pct_of_shipped_admin_pct|float|Percent of shipped_combined that has been injected.|
|shipped_people_covered_pct|float|Total doses shipped per Minnesota resident, divided by 2 to account for full vaccine series. Population: [ACS 2019 5-year estimate](https://censusreporter.org/data/table/?table=B01003&geo_ids=04000US27,050|04000US27&primary_geo_id=04000US27)|

#### mn_vaccine_county_timeseries.csv

County-by-county vaccine administration. Raw data available on the state's [Vaccine Data dashboard](https://mn.gov/covid19/vaccine/data/index.jsp).

|Column name|Format|Description|
|---|---|---|
|county|string|County name|
|data_date|date|Date reported publicly. YYYY-MM-DD|
|people_admin_total|integer|Total number of people who have received at least one dose of any COVID vaccine.|
|people_admin_completed_total|integer|Total number of people who have received both doses of any COVID vaccine.|
|full_fips|string|U.S. Census FIPS code for this county, including state code.|
|pop_2019|integer|Estimated 2019 population. Population: [ACS 2019 5-year estimate](https://censusreporter.org/data/table/?table=B01003&geo_ids=04000US27,050|04000US27&primary_geo_id=04000US27)|
|people_pct_pop|float|Percent of county residents who have received at least one dose of any vaccine.|
|people_completed_pct_pop|float|Percent of county residents who have received both doses of any vaccine.|

#### mn_vaccine_gender_timeseries.csv

Gender breakdown of vaccine administration.

|Column name|Format|Description|
|---|---|---|
|data_date|date|Date reported publicly. YYYY-MM-DD|
|gender|string|Options: Female, Male, Other, Unknown/Missing|
|people_admin|integer|Total number of people who have received at least one dose of any COVID vaccine.|
|people_admin_completed|integer|Total number of people who have received both doses of any COVID vaccine.|
|one_dose_pct_total|float|Percent of total people_admin this gender accounts for.|
|completed_pct_total|float|Percent of total people_admin_completed this gender accounts for.|

#### mn_zip_timeseries.csv

A zip-level, weekly count of positive COVID-19 tests, compiled from data sent to the Star Tribune by the Minnesota Department of Health. Please note the geographic boundaries are Zip Code Tabulation Areas (ZCTAs), not necessarilly the precise mailing zip code at a given address. Demographics information is from U.S. Census Bureau American Community Survey 2018 5-year estimates.

|Column name|Format|Description|
|---|---|---|
|data_date|date|The date the data was released by MDH. Early datasets were as of the date distributed, but since July 27 the data ends the previous Thursday. Format: YYYY-MM-DD|
|zip|string|5-digit ZCTA identifer|
|cases_total|integer|Number of cumulative positive COVID-19 tests. -1 indicates that between 1 and 5 cases have been confirmed here. (MDH redacts the specific number of cases if it is between 1 and 5, but does report 0s for ZCTAs with no confirmed cases.)|
|cases_per_1k|float|Number of cumulative positive COVID-19 tests per 1,000 people in population|
|cases_weekly_change|float|Change in cases_total since last data update. Not calculated unless both current week and previous week have cases_total values that are not between 1 and 5 cases. (See note about redactions above.)|
|pop_total|integer|2019 ACS 5-year population estimate for this ZCTA|
|pct_nonwhite|float|Percentage of pop_total that has a race other than white and did not report Hispanic ethnicity, according to 2018 ACS 5-year estimate|
|pct_black|float|Percentage of pop total that is Black, according to 2018 ACS 5-year estimate|
|pct_latinx|float|Percentage of pop total that has Hispanic ethnicity, regardless of race, except for "two or more races," according to 2018 ACS 5-year estimate|
|pct_asian|float|Percentage of pop total that is Asian, according to 2018 ACS 5-year estimate|
|pct_nativeamer|float|Percentage of pop total that is Native American, according to 2019 ACS 5-year estimate|
|largest_minority|string|The nonwhite group listed above with the highest share of the ZCTA's population, according to 2019 ACS 5-year estimate|
|bool_metro|boolean|Whether ZCTA touches one of the 7 counties included in the Twin Cities metro area, according to the [Metropolitan Council](https://metrocouncil.org).|

### Deprecated files
Several files have been replaced as reporting methods have changed and the files have been removed from the repository. Generally, similar data is now available in other files listed above.

#### DEPRECATED: mn_ages_latest.csv
#### DEPRECATED: mn_positive_tests_by_county.csv
#### DEPRECATED: mn_death_ages_detailed_latest.csv
