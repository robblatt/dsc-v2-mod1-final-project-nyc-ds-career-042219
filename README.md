
# Rob Blatt's Flatiron School Module 1 Final Project

My analysis of King County, WA housing data set

This repo contains:

* a PDF presentation, presentation.pdf, original here [https://docs.google.com/presentation/d/1PWzqFbbGCkITjyfn9XOqY2Jh3ms4eJBjDHWvfzlNT_U/edit?usp=sharing](https://docs.google.com/presentation/d/1PWzqFbbGCkITjyfn9XOqY2Jh3ms4eJBjDHWvfzlNT_U/edit?usp=sharing)
* a Jupyter notebook, Mod 1.ipynb with my first model Flatiron School Module 1 project.
* a second Jupyter notebook, Mod 1 outliers not removed.ipynb.ipynb with a different model, with less agressive removal of outliers, whose R-squared is higher.

# The Model

The model uses three features from the data set: view, condition, and grade, and two that I feature engineered: price_per_sqft and bpb. The R-Squared is 0.794 with the train and test mean squared errors at 0.057 and 0.058 respectively. They are so low because the price was log transformed.

* **price_per_sqft** - price divided by square foot above ground
* **bpb** - beds per bath

## With hindsight
I only realized the night of my presentation on this model that price per square foot of a house isn't determined until the house is sold, which would make it difficult to use this model in a real life situation. In future work, I would exchange this for something tangible in a house before it's sold. Maybe create a price of the nearest 15 neighbors. This can likely be achieved by doing some math with lat and long, without actually having to do the nearest neighbors math.

## Process
I cleaned the data bwhile doing some exploration and also being over-zealous with the removal of outliers. While this initially created a less useful model, it helped me focus on creating something functional. After reaching a conclusion, I had additional time to explore further, this time without being so aggressive with what I had thought were outliers and the model seemed to improve using this broader dataset. A learning experience.

I dealt with null values by villing them with 0, as they were in the waterfront, year renovated, and condition columns. Those columns were dominated by zeros to beginw ith, so using the mode did not seem like a farfetched idea.

### Failed features
I determined early that view, waterfront, grade, and condition were helpful based on looking at the mean of each while at zero or with any other data, so I had initially used all four in my first attempt at a model. I combined them into a new feature and tried running the model on that and the results appeared to be less accurate. With time I would consider binning this and making another attempt at this feature to simplify the model further.

I used Year Renovated to attempt to determind how recently a house was renovated, but the model performed better without it. I also looked a tthe size of a house or a lot compared to the nearest 15, but those did not help the model either.

# Future Updates

* A methematical model is missing and is necessary. Time constraints and realization of the non-outlier version of the model took time away at the very end of the project.
* Replace price_per_sqft with price_per_sqft_nearest15
* Attempt another run with 'Shiny' combination of view, waterfront, grade, and condition with binning
* Look into correlation between price_per_sqft and price, which will be addressed with the first bullet point, and price and grade. They're both under 0.7, but correlation is 0.63 and 0.69 at the moment.
