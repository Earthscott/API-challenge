# API-challenge

This project uses two python Jupyter Notebooks to show how web service APIs can be used to create a "Perfect Vacation" application.

In the first phase (WeatherPy) the Open Weather Map API is used to query and store weather conditions during the previous day from 500+ randomly selected cities across the globe. Graphical and statistical analyses are used to characterize meteorological conditions across changes in latitude.

In the second phase (VacationPy) the Google Maps family of APIs are used to a) show a global relative humidity heat map and b) screen cities for user-generated "perfect weather conditions" to identify ideal vacation spots. One hotel within a reasonable distance of the city center is identified for each candidate city and shown with a pin containing the hetel name and city/country.

## WeatherPy

When using the free OpenWeatherMap API, retrieving current weather is straightforward. However, weather conditions at a single point in time are not ideal for characterizing global weather patterns. Weather can be highly variable throughout the day, and conditions will be biased by the local time of day (e.g., noon versus midnight). OpenWeatherMap also allows for querying weather conditions recorded during the previous five days, though only one day can be retrieved per call and the daily call limit for free accounts is 1,000. Based on the limitations, I configured my project to retrieve 24 hours of data for each location, using midnight one day prior to script execution (i.e., yesterday) for all locations. This ensures that the same 24-hour period is used for all locations (regardless of time zone), and that a full 24 hours of data are available. I then calculated the maximum and minimum for temperature, and the 24-hour mean for dew point, relative humidity, percent cloud cover, and wind speed.

## VacationPy

One of the goals of this phase to screen the list of random cities for potential vacation spots using ideal weather conditions. I know from experience that the daily range in temperature is important to me. I also know that relative humidity is not a good indicator of my comfort level in humid climates, while dew point is an excellent indicator. I start feeling uncomfortable when dew point reaches 65<sup>o</sup>, and I'm completely miserable at 72<sup>o</sup> and higher. As a result, I included minimum and maximum daily temperature and mean daily dew point in my selected meteorological measures.