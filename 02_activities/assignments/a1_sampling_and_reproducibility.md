# ASSIGNMENT: Sampling and Reproducibility in Python

Read the blog post [Contact tracing can give a biased sample of COVID-19 cases](https://andrewwhitby.com/2020/11/24/contact-tracing-biased/) by Andrew Whitby to understand the context and motivation behind the simulation model we will be examining.

Examine the code in `whitby_covid_tracing.py`. Identify all stages at which sampling is occurring in the model. Describe in words the sampling procedure, referencing the functions used, sample size, sampling frame, any underlying distributions involved, and how these relate to the procedure outlined in the blog post.

Run the Python script file called whitby_covid_tracing.py as is and compare the results to the graphs in the original blog post. Does this code appear to reproduce the graphs from the original blog post?

Modify the number of repetitions in the simulation to 100 (from the original 1000). Run the script multiple times and observe the outputted graphs. Comment on the reproducibility of the results.

Alter the code so that it is reproducible. Describe the changes you made to the code and how they affected the reproducibility of the script file. The output does not need to match Whitby’s original blogpost/graphs, it just needs to produce the same output when run multiple times

# Author: ALIYA ASAD

```
Sampling Procedure in the model
Stage 1: Primary infection sampling
The sample frame includes all 1000 event attendees. The model assumes that each person has a 10% probability(ATTACK_RATE = 0.10) of being infected, following a Bernoulli distribution. This means that, on average, 100 individuals are infected in each simulation, though the exact number varies due to randomness. Since infection status is assigned independently for each person, each simulation run produces slightly different results while maintaining the same probability distribution.
Stage 2: Contact tracing
 - Primary contact tracing: The sampling frame consists of infected individuals who have been traced back to the event where exposure occurred. The sampling process involves tracing infected individuals back to their exposure event.  Due to limitations in tracing methods, only 20%(TRACE_SUCCESS = 0.20)  of infections are successfully traced.  The sample size is thus 20% of the total infected population. This constitutes a non-probability, convenience-based sampling approach, as tracing efforts focus on readily identifiable infections within the discovered infected population.
 - Secondary contact tracing: the sampling frame is events where two or more infections were traced back to through primary contact. The sampling process will be, if an event meets this threshold (SECONDARY_TRACE_THRESHOLD = 2),everyone at that event is assumed to be tested, and all infected individuals are identified. Sample size here would vary according to the infected number of attendees. 


Comparing the results of both graphs: 
The graph from our Python simulation suggests that almost all infections can be traced back to the events, showing a strong correlation between infections from wedding and traced cases to wedding.
The graph from the article, however, shows a much weaker correlation between observed cases and the true proportion of infections from weddings. This suggests that in real-world scenarios, people can get infected from sources other than weddings. 

Changing number of simulations 
Reducing the number of simulations from 1000 to 100 still demonstrates a correlation between infections traced to weddings and infections originating from weddings. However, with only 100 simulations, the results show greater variability, making them less reliable and less reproducible compared to running 1000 simulations. This aligns with the Law of Large Numbers, which states that increasing the number of trials reduces variability, leading to more accurate and consistent results.

```


## Criteria

|Criteria|Complete|Incomplete|
|--------|----|----|
|Altercation of the code|The code changes made, made it reproducible.|The code is still not reproducible.|
|Description of changes|The author explained the reasonings for the changes made well.|The author did not explain the reasonings for the changes made well.|

## Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `23:59 - 16/02/2025`
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
