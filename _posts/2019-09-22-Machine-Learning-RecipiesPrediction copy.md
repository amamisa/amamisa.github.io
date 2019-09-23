---
layout: post
title: ML Predicting the success of recipes
---

The main idea of this post, to highlight web scraping and machine learning using linear regression.


![recipes image]({{ site.url }}/images/recipes.png)

For the purpose of the second project for metis, I'll be taking the data set by using web scraping tool called BeautifulSoup, in order to apply the concepts that we have learned.

I have choose Allrecipes website which contain information about different food recipes.
This project uses libraries like Pandas, numpy, MatplotLib, seaborn, BeautifulSoup, statsmodels, sklearn and pickle.

### Challenge:
It all starts when a chef wanted to know if his recipes are gaining a massive popularity and success among people. For that amateur chef, I have used Allrecipes website data to predict recipes success, so he could start his new restaurant.


### Methodology
In order to create a decent model for predictions, the following list contain the main steps that we should take:

* Web scraping and data acquisition.
* Data cleaning and preprocessing.
* Feature engineering.
* Modeling using linear regression.
* Testing results.

### Data Acquisition
In general, the website has two types of templates, which made scraping more complicated. You can find them in these links [template1](https://www.allrecipes.com/recipe/13477/double-layer-pumpkin-cheesecake/) and [template2](https://www.allrecipes.com/recipe/8817/slow-cooker-chicken-cacciatore/). However, I cope with it by defining a scraping technique for each template separately. Finally, I got to collect more than 1000 observations and 9 features which will be explained more bellow:

![features image]({{ site.url }}/images/features.png)
![dataframe image]({{ site.url }}/images/dataframe.png)

**ratings** – The recipe's rating.

**title** – The recipe's title.

**made_it** – How many people have made this recipe.

> The **made_it** is our target.

**reviews** – The number of reviews for each recipe.

**no_photos** – The number of photos for each recipe.

**cals** – The amount of calories in each recipe.

**times** - The amount of time each recipe needs to be prepared in minutes.

**cats** - The recipe's category.

**servings** - The number of servings for each recipe.


### Pre-processing and Data Cleaning

Basically, I have spent a lot of time on this part because the scraping outcome was unclean and messy. Therefore, I had to deal with extra noisy information and change the others to numerical values. 

Furthermore, I had to handle missing values that appeared in two columns (time and calories). Then I have checked for negative values after that I dropped two columns (title and cats). Finally I plot the pair plot for my features to visualize it and scan it by intuition. However, I figure out I had to apply power transformation for the whole features including the target in order to have them look like Gaussian Distribution.

![pairplot image]({{ site.url }}/images/pairplot.png)
 
After we apply all the cleaning part I have saved the data frame in a pickle file to reduce the amount of time in processing the data and to reach it at anytime when it's needed.

### Data Exploration and Visualization

After finishing the cleaning part, I start analyzing the data by creating a scatter plot for no_photos - which is one of the features that has a linear relationship towards the target also we can see it colored by each category in the following figure.

![eda image]({{ site.url }}/images/eda.png)

From the previous figure, we can see the drinks -in pink- has the least popularity with the least number of photos. Whereas, desserts -in dark blue- has the most popularity among people with the highest number of pictures.  

### Modeling and Testing

In order to start our model we have to be sure that our target is a Gaussian like so it succeed to fit linear model. For that purpose I have plot my target -made_it- using histogram.

![target image]({{ site.url }}/images/target.png)

After that, I use heatmap plot to visualize correlations between features, also for discovering multicollinearity.

![heatmap image]({{ site.url }}/images/heatmap.png)

from the previous figure, there is a strong correlation between no_photos and reviews towards the target. In the other hand there is a weak correlation between cals, time and servings towards the target.

#### Baseline Model
 As the first step before creating our model, we need to split the data into training and testing sets by 80 and 20 respectively. By identifying X and Y values then using ```train_test_split``` with ```test_size=.2, random_state=42```

Then I create the linear Regression model using sklearn, after that I feed it with my training X and Y data.
Finally I calculate R^2 of 0.80 which was good.

Then I decided to apply cross validation technique using ``` KFold(n_splits=5, shuffle=True, random_state = 71) ``` and I end up with improved model performance by R^2 of 0.91 which is better than before.
So I test the model by using the test data set and I got R^2 of 0.93 and coefficients as follows:

![coefficients image]({{ site.url }}/images/coefficients.png)

The next figure illustrating the residual for the final model results. We can see it is randomized around the zero mean. which is a sign of a good model.

![residual image]({{ site.url }}/images/residual.png)



### Conclusion

To conclude, I recommend our chef to increase the number of recipes pictures as much as possible and encouraging him to focus on desserts, since its more popular. Moreover my model shows a good results of predicting the recipes success to help him to starts his new business.


