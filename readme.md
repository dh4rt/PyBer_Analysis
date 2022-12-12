#Overview of analysis
#Rename This

#Resources
Python 3.9.13
Jupyter 6.5.2

This analysis is being performed at the request of V. Isualize, by outside analysts, myself amd Omar. At their request we produced outputs for two different
outputs, the first a **Data Frame** that shows in table format at a glance stat for the app operation in three different city types, **Urban Cities**, 
**Suburban Cities", and **Rural Cities**. The second deliverable is a **Line Plot** that shows the weekly total fare by city type. This Data was collected 
across 2019, and while initially locations where included, for privacy concerns those have been dropped from the overall analysis. 




#Results

##Data Frame
This deliverable was requested to give a quick, simple, and easy to read table that would show, when included on a handout what your average driver can 
expect to see during the time period, to achieve this a new table needed to be generated. The best way to get the data we wanted was to use the 
`groupby()` code to create six new **DataFrame** to get eventually get the six columns shown. For example, the code count the number of rides per city type was:

```
total_drivers_by_type = city_data_df.groupby(["type"]).sum()["driver_count"]
total_drivers_by_type
```
What this code shows is the name of the new **DataFrame** name with-in the code `total_drivers_by_type` the `=` to effectively activate the equation, then
original **DataFrame** datapoint separated by what type of city they happened in. This code was repeated five more times using largely the same code for each.
Those separate **DataFrame** where then combined in to a singular frame, and some formatting was done to make the data more presentable for folks not using
computers.

##Line Plot

This deliverable was requested to a colorful and easy visual for reading from across a room on a slideshow. This was created by selecting a smaller sample
size of the data just five total months. From there the data points where organized in order of the ride's date and time, and grouped into a weekly point.
The code to do that follows:

```
date_sums_df = dates_df.resample('W').sum()
date_sums_df
```

Ultimately this **DateFrame** was the source of information for my **Line Plot** which was formatted in the Object-Oriented Interface method. The code for it
attached below the *italicized* text provides instruction for what each line of code does:

```
*tells the code what kind of plot to make and how big to make it*
ax = date_sums_df.plot(figsize=(15,8))

*y-axis label*
ax.set_ylabel("Fare ($USD)")
*x-axis label*
ax.set_xlabel("")
*title*
ax.set_title("Total Fare by City Type")
*legend placement*
ax.legend(loc="center",title= "Type")
* this code tells Jupyter Notebook to 'Import the style from Matplotlib.'*
from matplotlib import style
*this code tells Jupyter to Use the graph style fivethirtyeight.*
style.use('fivethirtyeight')
```
  

#Summary

These tow outputs each tell us something very important independently and together. I think that independently they tell use that in the case of the
**Data Frame** is that the app is maybe over saturated with drivers, in no type of city is a driver even making enough money to pay for a tank of fuel
What initially seems the most startlingly was that rural drivers can expect to get just 2 rides during the time period and those in the suburbs don’t
do much better. But the most galling thing was just how little urban drivers made. In the overall data sample rural drivers can expect more rides AND
more money over the course of the sample. What the **Line Plot** shows is that the weekly returns for **Urban Cities** is a more than triple that of
**Rural Cities**. What they show us together is that we have far too many drivers particularly in **Urban Cities** and **Suburban Cities** as well.

How I think the company should do firstly is invest in some more research. What Omar and I feel would be the best things to look into would be three
fold. Firstly, to allow us to access the timestamps of each ride, this would be done to allow us to track when during the day the app is most used
and in what type of city, this would allow the company to more effectively allocate drivers around the clock. The next date question is group size, if
we know how many groups of 4 or 5 we are getting that are turned away because drivers simply can’t fit the number of potential customers. The third
would be to have access to the age of the requesting user. This would allow us to know if your drivers would need to accept any rider concerns
particularly as it relates to the customers mobility.

With acces to this data, Omar and I would be able to advise more explicitly on three different operational decisions. The first would be to consider
capping a certain number of drivers at a certain time to allow drivers to make more money. The second suggestion that could be made with this data is
where to consider pushing drivers too. Since the app has the ability to set ranges for divers, if we could entice particualarly suburban drivers to
go to other types of cities they could stand to make more money. The third would be when to focus on sending drivers out, if there is a lack of
late night drivers, perhaps offering an extra incentive would prove useful.



