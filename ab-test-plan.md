# A/B Test Plan

Site: https://hansbruckner.github.io/IowaCity-CheapFood-Guide/
Plan committed on November 16, 2026. No trial has been run. The commit timestamp is the proof.

## 1. Page and element
- Page: cheap food page (target query: "iowa city cheap food").
- Element changed: Iowa Cheap Food Title
- Version A: "Iowa City Cheap Food"
- Version B: "Iowa City Cheap Food Under $20"
- Version B lives at cheap-food-b.html with a noindex meta tag, no navigation link, and no sitemap entry, so it does not compete with A in search.
- Change before launch: the treatment was changed from the length of the opening paragraph to the headline on November 19, 2026, before any trial was run.

## 2. Hypothesis
A higher share of visitors will answer "yes" for B than for A
Reasoning: student visitors on a budget usually scan and decide from the first thing they read, so a shorter intro gets them to the listings faster. 
The prediction is wrong if the ratings are equal or if A scores higher, for example because the longer intro explains how the page works and makes it look more trustworthy.

## 3. Method
- Visitor: Claude (claude-sonnet-5-5, Free Version) Every trial is a fresh conversation with no memory. The same model and settings are used for all trials.
- Persona and prompt, word for word identical in every trial except the page URL:
  "You are a University of Iowa student living off campus on a tight food budget. You go eat out about three times a week and usually decide where to go from the first thing you read online. Below is the URL of a web page you found by searching 'iowa city cheap food'. [PAGE URL] Would you use this page to decide where to get food this week? Answer with the single word Yes or No on the first line, then give one sentence of reasoning"
- Page shown: the URL of the page (A or B), extracted the same way for both.
- Assignment: a  (total 100) using RANDBWETWEEN Feature in Excell to maintain random assignment 
## 4. Primary outcome
The Yes or No outcome (Yes=1, No= 0). Replies with reasoning 

## 5. Sample size and dates
100 trials randomized using the RANDBETWEEN function in Excell: Outcome 56 A, 44 Bs
Expected completion: November 29, 2026.

## 6. Comparison and decision rule
Compare the mean rating of B minus the mean rating of A with a two-sided t-test at alpha = 0.05. Also report the 95% confidence interval. The hypothesis is supported if B's mean is higher than A's and p < 0.05. 
