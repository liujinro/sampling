# ASSIGNMENT: Sampling and Reproducibility in Python

Read the blog post [Contact tracing can give a biased sample of COVID-19 cases](https://andrewwhitby.com/2020/11/24/contact-tracing-biased/) by Andrew Whitby to understand the context and motivation behind the simulation model we will be examining.

Examine the code in `whitby_covid_tracing.py`. Identify all stages at which sampling is occurring in the model. Describe in words the sampling procedure, referencing the functions used, sample size, sampling frame, any underlying distributions involved, and how these relate to the procedure outlined in the blog post.

Run the Python script file called whitby_covid_tracing.py as is and compare the results to the graphs in the original blog post. Does this code appear to reproduce the graphs from the original blog post?

Modify the number of repetitions in the simulation to 1000 (from the original 50000). Run the script multiple times and observe the outputted graphs. Comment on the reproducibility of the results.

Alter the code so that it is reproducible. Describe the changes you made to the code and how they affected the reproducibility of the script file. The output does not need to match Whitby’s original blogpost/graphs, it just needs to produce the same output when run multiple times

# Author: Jinrong Liu

``` Please write your explanation here...
Here is the code analysis: 
1. Sampling Procedure:
- Population: 1000 individuals (200 at weddings, 800 at brunches).
Infection: Each individual has a 10% chance of being infected (ATTACK_RATE = 0.10).
- Primary Contact Tracing: 20% success rate for tracing infections (TRACE_SUCCESS = 0.20).
- Secondary Contact Tracing: If two or more infections are traced to the same event, 100% of infections at that event are traced. 
2. Functions and Key Steps: 
- 1000 people are categorized into events (200 weddings, 800 brunches).
- The infected column initially set to False.
- The traced column initialized as NaN and later converted to a nullable boolean type.
- Randomly infects 10% of individuals.
- Traces 20% of infected individuals.
- Traces all infections at events with two or more traced cases.
- Calculates the proportion of infections and traced cases attributed to weddings and brunches.
3. Relate to Blog:
The code closely follows the model outlined in the blog post. It simulates a community with predefined event attendance, infection rates, and tracing probabilities to show how contact tracing can bias the observed proportions of infections attributed to different event types. The results from the simulation illustrate the blog's point that contact tracing is not random and tends to overrepresent certain settings, such as weddings, due to more efficient tracing in these environments.

4. Comparison with the Blog Post:
Running the whitby_covid_tracing.py script produces histograms that compare the true and observed proportions of COVID-19 cases from weddings. The blue histogram, representing the actual infection rates, centers around 20%. The red histogram, showing traced cases, is higher due to secondary contact tracing, illustrating the bias discussed in the blog post. This confirms that the code effectively reproduces the graphs from the blog, demonstrating the overestimation of wedding-related infections in contact tracing data.
5. Analyzing the Results:
The blue histogram should align with the blog's depiction of the true infection proportions, centered around 20%. In contrast, the red histogram should show a skewed distribution, with a higher mean and possibly more spread, reflecting the bias introduced by contact tracing. This demonstrates how secondary contact tracing can cause an overestimation of infections attributed to weddings compared to the true proportion of infections.
- Conclusion:
Running the script and generating the histograms as described should confirm whether the code produces results similar to those in the blog post. The histograms are expected to demonstrate the overestimation of infections attributed to weddings due to the biases inherent in the contact tracing process.

7. Comment on Reproducibility:

- Consistency: The script with the seed set (np.random.seed(10)) ensures reproducible results across multiple runs.
- Effect of Repetitions: With fewer repetitions (100 vs. 1000), the variability in histograms might increase, but the overall shape and trends should remain consistent.
- Random Seed: The random seed ensures reproducibility of results.
- Running the Script: Run the modified script multiple times and confirm consistent output.









```


## Criteria

|Criteria|Complete|Incomplete|
|--------|----|----|
|Altercation of the code|The code changes made, made it reproducible.|The code is still not reproducible.|
|Description of changes|The author explained the reasonings for the changes made well.|The author did not explain the reasonings for the changes made well.|

## Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `HH:MM AM/PM - DD/MM/YYYY`
* The branch name for your repo should be: `sampling-and-reproducibility`
* What to submit for this assignment:
    * This markdown file (sampling_and_reproducibility.md) should be populated.
    * The `whitby_covid_tracing.py` should be changed.
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sampling/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `sampling-and-reproducibility`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-3-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
