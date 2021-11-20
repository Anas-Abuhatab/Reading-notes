#  *Data Science*


![](https://elitedatascience.com/wp-content/uploads/2018/05/What-Goes-Into-a-Successful-Model.jpg)

###  Bird's Eye View : 

* **Machine learning is not about algorithms.** 
...and individual algorithms are only one piece of the puzzle. The rest of the puzzle is how you apply them the right way.

#### `What makes machine learning so special? 
M achine learning is the practice of teaching computers how to learn patterns from data, often for making decisions or predictions.
For true machine learning, the computer must be able to learn patterns that it's not explicitly programmed to identify.
#### Key Terminology 
Model - a set of patterns learned from data.
Algorithm - a specific ML process used to train a model.
Training data - the dataset from which the algorithm learns the model.
Test data - a new dataset for reliably evaluating model performance.
Test data - a new dataset for reliably evaluating model performance.
Target variable - A specific variable you're trying to predict.
Observations - Data points (rows) in the dataset.
#### Machine Learning Tasks
Academic machine learning starts with and focuses on individual algorithms. However, in applied machine learning, you should first pick the right machine learning task for the job.
* A task is a specific objective for your algorithms.
* Algorithms can be swapped in and out, as long as you pick the right task.
In fact, you should always try multiple algorithms because you most likely won't know which one will perform best for your dataset.
#### The 3 Elements of Great Machine Learning
1. A skilled chef (human guidance)
First, even though we are "teaching computers to learn on their own," human guidance plays a huge role.
2. Fresh ingredients (clean, relevant data)
The second essential element is the quality of your data.
3.  Don't overcook it (avoid overfitting)
One of the most dangerous pitfalls in machine learning is overfitting. An overfit model has "memorized" the noise in the training set, instead of learning the true underlying patterns.
### Data Cleaning
Data cleaning is one those things that everyone does but no one really talks about. Sure, it’s not the "sexiest" part of machine learning. And no, there aren’t hidden tricks and secrets to uncover.
However, proper data cleaning can make or break your project. Professional data scientists usually spend a very large portion of their time on this step.


***Exploratory Analysis***

* There’s a big challenge in data science called “Tactical Hell.” This is actually a term from startups, and it’s when you have too many tactics to choose from:

* Should you develop your product more? Invest in marketing? Hire an accountant? Etc.

* In many ways, training a ML model is like growing a startup. You also have too many tactics to choose from:

* Should you clean your data more? Engineer features? Test new algorithms? Etc.

* There’s a lot of trial and error, so how do you avoid chasing dead ends? The answer is “Exploratory Analysis.” (Which is just fancy-talk for “getting to know” your data.)

* Doing this upfront helps you save time and avoid wild goose chases… As a data scientist, you are a commander with limited resources (i.e. time). Exploratory analysis is like sending scouts to learn where to deploy your forces!



***Data Cleaning***

* Proper data cleaning is the “secret” sauce behind machine learning… Well, it’s not really a “secret”… It’s just a bit boring, so no one really talks about it. But the truth is:

* Better data beats fancier algorithms…

(Even if you forget everything else from this primer, please remember this point)

* Garbage in = Garbage out... Plain and Simple! If you have a clean dataset, even simple algorithms can learn impressive insights from it!

* Now, as you might imagine, different problems will require different methods… For now though, let’s at least ensure we know how to fix the most common issues. This chapter will give you a reliable starting point, regardless of your dataset.



***Feature Engineering*** ![](https://elitedatascience.com/wp-content/uploads/2018/05/feature-engineering.png)
In a nutshell, “feature engineering” is creating new model input features from your existing ones.

That doesn’t sounds like much… Yet Andrew Ng, former head of Baidu AI and Google Brain, said:

“Coming up with features is difficult, time-consuming, requires expert knowledge.
‘Applied machine learning’ is basically feature engineering.”

Wow! No pressure, right?

So why is it so difficult and time-consuming?

To start, feature engineering is very open-ended. There are literally infinite options for new features to create. Plus, you’ll need domain knowledge to add informative features instead of more noise.

This is a skill that you’ll develop with time and practice, but heuristics will give you a head start. Heuristics help you know where to start looking, spark ideas, and get unstuck.




***Algorithm Selection***
![](https://elitedatascience.com/wp-content/uploads/2018/05/algorithm-selection.png)
Next, we'll introduce 5 very effective ML algorithms for regression. They each have classification counterparts as well.

Just 5?

Yes. Instead of giving you a long list of algorithms...

...our goal is to explain a few essential concepts (e.g. regularization, ensembling, automatic feature selection) that will teach you why some algorithms tend to perform better than others.

In applied machine learning, individual algorithms should be swapped in and out depending on which performs best for the problem and the dataset.

Therefore, we will focus on intuition and practical benefits over math and theory.

***We have two main goals:***

1. To explain powerful mechanisms in modern ML.
2. To introduce several algorithms that use those mechanisms.
So if you're ready, then we’re ready. Let’s go!



***Model Training***
At last… it’s time to build our models!

It might seem like it took a while to get here, but data scientists actually do spend most their time on the earlier steps:

Exploring the data.
Cleaning the data.
Engineering new features.
Again, that’s because better data beats fancier algorithms.

Now you'll learn how to maximize model performance while safeguarding against overfitting. Plus, you'll learn how to automatically find the best parameters for each algorithm.

We'll get an overview of splitting your dataset, deciding on hyperparameters, setting up cross-validation, fitting and tuning models, and finally… selecting a winner!