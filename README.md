# Hawaii Temperatures Analysis

## Overview and Purpose

The purpose of this analysis was to look at the temperatures taken from an island in Hawaii
during the months of June and December throughout several years. We wanted to determine if
running a surf shop in this location would be sustainable permanently. I queried the 
SQLite database filtering on the month of the year, and using the .describe() method
to find summary stats.

### Results

Summary stats for June temperatures:

![June temps screenshot](https://github.com/KW0114/surfs_up/blob/840480195cdae4381c563765ffeb5d2caf2e3154/Resources/June_temps_screenshot.png)

Summary stats for December temperatures:

![December temps screenshot](https://github.com/KW0114/surfs_up/blob/840480195cdae4381c563765ffeb5d2caf2e3154/Resources/Dec_temps_screenshot.png)

* The mean temp for both months are pretty similar, so temperatures are still fairly warm
even in the month of December.

* Minimum temperatures are about 10 degrees lower during December, but condsidering the fact
that it can get as low as 64 degrees in June, this isn't too much of a difference. 

* Maximum temperatures are almost equal, so surfing temperatures in December should (generally) be 
just as nice as in June.

### Summary

Just considering temperatures, this seems to be an awesome location to host a surf shop. In 
the main analysis for the module, we were focusing on precipitation data. Combining these 
columns into a single filtered database would provide a much better look into what we are
trying to find. 

As an example, we could simply add the precipitation column in this filtered database we created
for June:

	session.query(Measurement.tobs, Measurement.prcp).filter(extract('month', Measurement.date) == 6).all()

This way, when we save our DataFrame, it will have two columns, temperature and precipitation. 
When we run the summary stats, we can see both columns.

We could also perform summary stats for ranges of dates, perhaps during the summer months of May, June, July:

	session.query(Measurement.tobs, Measurement.prcp).filter(extract('month', Measurement.date) >= 5 and extract('month', Measurement.date) <= 7).all()
	
