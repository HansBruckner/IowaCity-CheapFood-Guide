# A/B Test Plan

Site: https://hansbruckner.github.io/IowaCity-CheapFood-Guide/
Plan committed on November 16, 2026. No trial has been run. The commit timestamp is the proof.

## 1. Page and element
- Page: cheap food page (target query: "iowa city cheap food").
- Element changed: the length of the opening paragraph. Nothing else differs: the H1, the jump links, all listings, the navigation and the footer are identical.
- Version A (current, 54 words): "Looking for cheap food in Iowa City? Start here. Every restaurant below is sorted by what a typical meal costs, so you can find a place that fits your budget in seconds. Distances are walking miles from the Pentacrest, and each listing tells you whether you can dine in, carry out, or do both."
- Version B (22 words): "Cheap food in Iowa City sorted by price, with walking distance from campus and whether you can dine in or carry out."
- Version B lives at cheap-food-b.html with a noindex meta tag. It has no navigation link and is not in sitemap.xml, so it does not compete with A in search.

## 2. Hypothesis
B will receive a higher mean rating than A.
Reasoning: student visitors on a budget usually scan and decide from the first thing they read, so a shorter intro gets them to the listings faster. The prediction is wrong if the ratings are equal or if A scores higher, for example because the longer intro explains how the page works and makes it look more trustworthy.

## 3. Method
- Visitor: Claude (claude-sonnet-5-5) through the API, default settings (temperature 1.0), max_tokens 150, no system prompt. Every trial is a fresh conversation with no memory. The same model and settings are used for all trials.
- Persona and prompt, word for word identical in every trial except the page text:
  "You are a University of Iowa sophomore living off campus on a tight food budget. You eat out about three times a week and usually decide where to go from the first thing you read online. Below is the full text of a web page you found by searching 'iowa city cheap food'. [PAGE TEXT] On a scale of 1 to 7, how likely are you to use this page to decide where to eat this week (1 = very unlikely, 7 = very likely)? Put the number on the first line, then give one sentence of reasoning."
- Page shown: the full visible text of the page (A or B), extracted the same way for both.
- Assignment: a list of 100 A and 100 B shuffled with Python's random.Random(20261116), saved as assignments.csv and committed before the first trial. Trials run in that order.
- Pilot: up to 5 trials on version A only, to check that replies can be read. They are excluded from the data and logged. The question will not be changed after this plan is committed.

## 4. Primary outcome
The 1 to 7 rating on the first line of each reply. Replies with no readable rating are kept in the raw data and excluded from the analysis. They are counted and reported, and no replacement trials are run.

## 5. Sample size and dates
200 trials (100 per version). All 200 will be collected, with no interim analysis and no early stopping.
- Batch 1 (trials 1 to 100): November 17, 2026.
- Batch 2 (trials 101 to 200): November 18, 2026.
Expected completion: November 18, 2026.

## 6. Comparison and decision rule
Compare the mean rating of B minus the mean rating of A with a two-sided Welch t-test at alpha = 0.05. Also report the 95% confidence interval and Cohen's d. A Mann-Whitney test is a robustness check only.
The hypothesis is supported if B's mean is higher than A's and p < 0.05. Any other result is reported as not supported.

## 7. Limits and changes
With 100 trials per version, power is about 94% for a medium effect (d = 0.5) and about 29% for a small effect (d = 0.2). A flat result is therefore likely and will be reported honestly. B also removes some explanatory wording, so length is partly confounded with information. Any change after launch will be logged with its date and reason.
