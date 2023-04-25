# A-B-testing-Roadmap

## Step 0: Are You Sure You Should Do This?

- Are you sure this is a good thing to test with an AB experiment? A/B tests for everything!
- Is it ethical / legal?
- Has somebody already done this / has somebody done something sufficiently similar you can learn from their experience? Make sure to review relevant literature.


## Step 1: Define Your Goals

- Pick an Overall Evaluation Criterion (OEC)
  - *A good OEC should have enough variation to be measurable in short run, but also a good indicator of whether you are achieving what you care about in the long run.*
- Pick Guardrails: 
  - *Outcomes to measure to ensure your experiment DOESN'T cause changes that are problematic. e.g. big changes in other things you know matter.*
- Pick unit of observation *and* unit of randomization.
  - *Remember you can't have interactions between your randomization units (SUTVA), so if you're in a world with lots of interactions (social networks), choose a strategy to pick isolated units.*
- Pick population to study
  - *Ideally as similar to population in context where you want to roll out change.*
- Define the minimal effect size you care about.
  - *i.e. what's the smallest effect size that might cause your business to undertake a new course of action.*
  
  ## Step 2: Plan Implementation

- Combine the minimal effect you're interested in from Step 1 with a $\beta$ and $\alpha$ that makes sense given the cost of your A/B test (expensive tests probably warrant higher $\beta$, and more potentially costly decisions warrant higher $\alpha$ s).
  - *Do you want to over-power your test to allow for analysis of subpopulations?*
- Decide on a run time.
  - *Needs to be long enough to get the sample size you want*
  - *Want it to be long enough to capture seasonality effects, where feasible (e.g. run at least a full day, or a full week, depending on context)*
  - *Do you want to measure primacy effects / user adaptation? If you so you want a longer run!*

## Step 3: Run!

- First run your A/A test to validate randomization.
- No stopping the experiment early based on p-values you look at before the run is done 
  - **unless** *you invest in learning the more advanced statistical methods for early stopping correctly.*

## Step 4: Check Internal Validity

- Does it seem like your experiment ran correctly?
  - *Are covariates balanced across treatment and control?*
  - *Do your A/A validation analyses look correct?*
  - *Do you see any major unexpected changes to your guardrail metrics?*
  - *Do you have a sample ratio mismatch (SRM)?*
- Did you have good compliance?
  - *e.g. did subjects assigned to treatment "take" the treatment?*
  - *if not, is that a problem given application context?*

## Step 5: Interpret Results

- Consider **both** practical and statistical significance:
  - *Practical significance + statistical significance = great! It worked.*
  - *No practical significance or statistical significance:*
    - *if standard errors are small enough to rule out a minimally practical effect, you're done.*
    - *if standard errors are really big (don't rule out minimally practical effect), you've learned nothing except that your power calculations were too optimistic.*
  - *Practical significance but not statistically significant = hmmm... get more data if possible. If not, weight the costs and benefits of acting on data that suggests something promising, but isn't rock solid.*
- Is there any evidence that the effect of the treatment differed across sub-populations?
  - *If you look at lots of sub-populations, consider multi-test corrections. If so, look to something like Benjamini-Hochberg or Westfall-Young Step-Down. Unless you're measuring fully independent things, Bonferroni is too conservative.*
- Is there any evidence in changes in the effect over time?
  - *Good way to look for evidence of primacy effects. May require more statistical power than you have, and requires you ran for more than one "season" (day, week, etc.) so you can compare the start of your experiment with end without just effectively comparing start of week to end of the week.*

## Step 6: Consider External Validity 

- External validity is **always** defined *with respect to a specific context to which you want to generalize results.* Call this "application context."
- Do you have reason to believe the long-term effect may differ from what you measured in the short run?
- Do you have reason to believe the population in study may differ from population in application context?
- Was anything about your test unrealistic?
