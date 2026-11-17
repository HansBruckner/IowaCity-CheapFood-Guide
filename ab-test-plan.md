# A/B Test Plan

Site: https://hansbruckner.github.io/IowaCity-CheapFood-Guide/
Plan committed on November 16, 2026. No trial has been run. The commit timestamp is the proof.

## 1. Page and element
- Page: cheap food page (target query: "iowa city cheap food").
- Element changed: the length of the opening paragraph. Nothing else differs: the H1, the jump links, all listings, the navigation and the footer are identical.
- Version A (current, 54 words): "Looking for cheap food in Iowa City? Start here. Every restaurant below is sorted by what a typical meal costs, so you can find a place that fits your budget in seconds. Distances are walking miles from the Pentacrest, and each listing tells you whether you can dine in, carry out, or do both."
- Version B (22 words): "Cheap food in Iowa City sorted by price, with walking distance from campus and whether you can dine in or carry out."

## 2. Hypothesis
B will receive a higher mean rating than A.
Reasoning: student visitors on a budget usually scan and decide from the first thing they read, so a shorter intro gets them to the listings faster. 
The prediction is wrong if the ratings are equal or if A scores higher, for example because the longer intro explains how the page works and makes it look more trustworthy.

## 3. Method
- Visitor: Claude (claude-sonnet-5-5) through the API, default settings (temperature 1.0), max_tokens 150, no system prompt. Every trial is a fresh conversation with no memory. The same model and settings are used for all trials.
- Persona and prompt, word for word identical in every trial except the page text:
  "You are a University of Iowa student living off campus on a tight food budget. You go eat out about three times a week and usually decide where to go from the first thing you read online. Below is the full text of a web page you found by searching 'iowa city cheap food'. [PAGE TEXT] On a scale of 1 to 7, how likely are you to use this page to decide where to eat this week (1 = very unlikely, 7 = very likely)? Put the number on the first line, then give one sentence of reasoning."
- Page shown: the full visible text of the page (A or B), extracted the same way for both.
- Assignment: a list of 50 A and 50 B (total 100) using RANDBWETWEEN Feature in Excell to maintain random assignment 
## 4. Primary outcome
The 1 to 7 rating on the first line of each reply. Replies with reasoning 

## 5. Sample size and dates
100 trials (50 per version). All 100 will be collected,
Expected completion: November 29, 2026.

## 6. Comparison and decision rule
Compare the mean rating of B minus the mean rating of A with a two-sided t-test at alpha = 0.05. Also report the 95% confidence interval
The hypothesis is supported if B's mean is higher than A's and p < 0.05. 
