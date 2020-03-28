# Midterm Feedback

## Overall Score: 
43 / 50

Overall you did well.  There are some things I didn't follow, like why you were using a Pandas Series in the functions.  Then it ocurred to me after I saw you last function that maybe this had to do with the trouble you had reading the patient data.


## Part 1: Creating a JSON Rules File
Comments - This is well organized and put together.  I was surprised to see a section for the Glasgow Coma score!  Not necessary, but nice to see here and I like how it was put together.

## Part 2: Functions to evaluate rules
### 2A Organ Failure History
Comments - Nicely done.  I didn't see a test case for having a list with more than one item, but it definitely works as expected.

### 2B All Factors Function
Comments - There's no problem with doing it this way, per se, but the scores don't actually depend on one another.  In practice, combining these things into one function makes it harder to debug where the underlying issue might be.  I can see where you headed this direction based on my warning that writing one function for every input would be problematic.  The intent there was to think about what logic would be similar and how you could avoid writing the >= and < comparisons multiple times.  See the solution. (-1)

At first, I thought this was a clever use of Pandas Series to avoid needing to loop through all the rules, but you are looping through all the rules.  Including Pandas in the evaluation of these rules in unnecessarily complex.  I added some notes to your notebook, but rather than using a Pandas Series, you can have a straight forward `if` statement like this.  (-1)
```
    if (age >= rule.get('min') and age < rule.get('max')):
        score= rule.get('points')
```


### 2C Rates
Comments - Similar comments as above.  No points off, though.

### 2D Serum
Comments - Similar comments as above.  No points off, though.

### 2E Blood
Comments - Similar comments as above.  No points off, though.

### 2F Glas
Comments - Nice work.  Very simple one, huh!?

### 2G Muscle
Comments - Nicely done.  Same comment as above regarding the use of Pandas Series.  Interestingly, when you implemented the Chronic side of this function, you didn't do it the same way.  Why did you change?

### 2H oxygen
Comments - Same comments.

### 2I Creatinine
Comments - Great work dealing with the acute / chronic difference.  Again, you're missing a default value for creatinine_score, but no points off for that here.


## Part 3: Put it all together
Comments - Nice and simple.  I'm not sure why you're adding 1 to the scores, though. (-1)


## Part 4: Accessing and processing the patient file
Comments - I see you got a bit stuck here after reading in the data with Pandas and trying to do something with it.  Here's where you went off track.

Looping over a dataframe like that doesn't go "row by row".  Rather it gives you column-wise view of the data.  And when you access `patients.get('Column')` it returns the entire column for you because you've referred to the whole data frame rather than just one single row.

You were definitely on the right track with this.  I'm giving you partial credit for most of it.  (-2)

Since you didn't get to the step of comparing your answers against the provided ones.  (-2)