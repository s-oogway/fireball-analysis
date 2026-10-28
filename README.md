# Bright Fireballs Around the World

## Authors

- Author #1: s-oogway
- Author #2: Unassigned; partner arrangements are pending.

## Project Description

This project will explore where bright fireballs have been reported and how their estimated energy varies. It will use NASA's CNEOS fireball records from 2000 through 2025. The analysis will compare reported events over time and examine whether higher-energy events tend to reach peak brightness at different altitudes. Five charts and an interactive map will help users explore the data by year and energy range. The final report will discuss missing measurements and explain why reported events do not represent every meteor entering Earth's atmosphere.

## Project Outline/Plan

1. Download the records and document the columns, units, and missing values.
2. Clean the data and save a separate CSV with a record of the changes.
3. Summarize the data and run one statistical test.
4. Make at least five static charts and explain the chart choices.
5. Build an interactive dashboard and revise it after peer feedback.
6. Write the final report and prepare the presentation.

### Interface Plan

Use Jupyter notebooks for data cleaning and analysis. Build a small Streamlit dashboard with a Plotly world map, a yearly count chart, and a table of filtered events. Users will select a year range and estimated energy range, then hover over a map point to see its date, energy, and reported altitude. Show how many matching records have no location and therefore cannot appear on the map. Load a saved CSV so the dashboard does not depend on live API requests.

### Data Collection and Storage Plan (Author #1)

Download the data once from the [NASA/JPL CNEOS Fireball API](https://ssd-api.jpl.nasa.gov/fireball.api?date-min=2000-01-01&date-max=2025-12-31&sort=date). Save the original response as `data/raw/fireballs.json`, record the download date and API version, and export the cleaned table to `data/processed/fireballs.csv`. The initial download returned 914 records, although NASA may add or revise historical records later.

Use the [API documentation](https://ssd-api.jpl.nasa.gov/doc/fireball.html) to record each column's meaning and units. Convert dates and numeric strings to their appropriate types, and convert latitude and longitude directions into signed coordinates. Check missing values, duplicate records, coordinate ranges, and nonpositive energy values. Review suspicious records before changing anything, and explain each cleaning decision in the notebook.

Keep missing locations and altitudes as missing rather than guessing them. Only exclude a record from a chart or test when a required measurement is unavailable, and report the number used. Keep the raw file unchanged. Credit NASA/JPL CNEOS as the data source; the MIT license in this repository applies to our code.

### Data Analysis and Visualization Plan (Author #2)

This is a proposed plan for an unassigned partner to review and update.

Use pandas to calculate event counts and summarize estimated impact energy and reported altitude. Report medians and ranges because a few very large events may distort averages. Use SciPy's Spearman correlation test to examine the relationship between altitude at peak brightness and estimated impact energy among records containing both measurements. Report the sample size, correlation coefficient, p-value, and limitations without assuming a significant relationship will be found.

Create these five static charts with Matplotlib and Seaborn:

- A line chart of the number of reported events each year.
- A histogram of estimated impact energy using a logarithmic energy axis.
- A scatter plot of reported altitude against estimated impact energy.
- A world scatter map of events with known coordinates, colored by energy.
- A bar chart showing the percentage of records missing location, altitude, or velocity.

Use clear titles, units, and a colorblind-friendly palette, and explain why each chart fits its question. Build interactive versions of the map and yearly count chart with Plotly. Ask a peer to try the filters, record their feedback, and make at least one useful revision.

Discuss incomplete reporting, missing measurements, extreme events, and the limits of comparing recorded counts across years. Estimated impact energy is calculated from radiated energy, so their relationship should not be presented as an independent discovery. This project will describe the available reports rather than predict future impacts or recommend meteor-watching times. Machine learning is outside the planned scope.

## Data Source

[NASA/JPL CNEOS Fireball and Bolide Reports](https://cneos.jpl.nasa.gov/fireballs/)
