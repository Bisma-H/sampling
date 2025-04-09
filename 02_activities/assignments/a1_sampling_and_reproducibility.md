# ASSIGNMENT: Sampling and Reproducibility in Python

Read the blog post [Contact tracing can give a biased sample of COVID-19 cases](https://andrewwhitby.com/2020/11/24/contact-tracing-biased/) by Andrew Whitby to understand the context and motivation behind the simulation model we will be examining.

Examine the code in `whitby_covid_tracing.py`. Identify all stages at which sampling is occurring in the model. Describe in words the sampling procedure, referencing the functions used, sample size, sampling frame, any underlying distributions involved, and how these relate to the procedure outlined in the blog post.

Run the Python script file called whitby_covid_tracing.py as is and compare the results to the graphs in the original blog post. Does this code appear to reproduce the graphs from the original blog post?

Modify the number of repetitions in the simulation to 100 (from the original 1000). Run the script multiple times and observe the outputted graphs. Comment on the reproducibility of the results.

Alter the code so that it is reproducible. Describe the changes you made to the code and how they affected the reproducibility of the script file. The output does not need to match Whitby’s original blogpost/graphs, it just needs to produce the same output when run multiple times

# Author: Bisma Haseeb Khan

````````````

In this file, the first type of sampling that takes place is when we define the number fo infected individuals. Here the sampling frame is 1000 individuals that attend events (weddings or brunches). The underlying distribution is uniform and this relates to the description in the blog post as it gives us a picture of the true population distribution.

The second sampling process takes place when we conduct primary contact tracing. Here the sampling frame is all of the infected people (that is around 100 individuals). the sampling strategy used is simple random sampling, using the function np.random.rand to generate random numbers for each infected person. Each infected person has a 20% chance of being infected so the underlying distribution is binomial. This relates to the blog post as it in the post it mentions that due to imperfect recall, we can only trace an infection back to its source even 20% of the time. 

The third type of sampling, secondary contact tracing. Here the sampling frame is infected individuals at traced events and the sampling technique is rule-based - all individuals at an event where 2 or more infected individuals have been traced. Here the underlying distribution is a conditional distribution. This is related to the blog post as it shows that we’re more likely to overestimate the proportion of cases that result from weddings (and equivalently, underestimate this that come from brunches) as there is a higher likelihood of having more than 2 infected individuals traced to a wedding. 

The last type of sampling is performed when we perform the simulations. The type of sampling used here is bootstrap sampling - this is a repeated sampling technique used to get a sampling distribution for sample statistics such as the mean and standard deviation. This is related to the blog post as it shows that the observed distribution is skewed to the right of the true population distribution.


`````````

The code in the python file does not reproduce the results in the blog post. 

If we run the script multiple times with 100 repetitions, we find that the results change each time we run the python file. This is because each time we run the script, python draws new random samples. Different random samples drawn will give different results. The change I have made to the file is that I have set a seed before the bootstrap random sampling code is run. This fixes the starting point for python to draw the random sample s from - python's random number generator is actually pseudo random and if we fix the starting point, it will produce the same random numbers each time it is run. Therefore, setting the seed ensures reproducibility as we get the same random numbers and hence random samples each time we run the code. 



`````````````







## Criteria

|Criteria|Complete|Incomplete|
|--------|----|----|
|Altercation of the code|The code changes made, made it reproducible.|The code is still not reproducible.|
|Description of changes|The author explained the reasonings for the changes made well.|The author did not explain the reasonings for the changes made well.|

## Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `23:59 - 09/04/2025`
* The branch name for your repo should be: `assignment-1`
* What to submit for this assignment:
    * This markdown file (a1_sampling_and_reproducibility.md) should be populated.
    * The `whitby_covid_tracing.py` should be changed.
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sampling/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `assignment-1`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via the help channel in Slack. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
