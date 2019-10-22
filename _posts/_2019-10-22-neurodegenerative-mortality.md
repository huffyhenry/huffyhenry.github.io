---
layout: post
title: ?
---
I think of my two fields of professional (in)activity, namely 
epidemiology and football analytics, as completely distinct, but 
now there is a tiny overlap. 
A [recent article](https://www.nejm.org/doi/full/10.1056/NEJMoa1908483) 
[paywalled] in the prestigious New England Journal of Medicine addresses the
long-standing hypothesis that playing football professionally increases the
risk of neurodegenerative disease. This effect is well-established for the more
brutal sports such as boxing and American football, but while it has always
been a decent bet that it is also the case for football, we have not had hard 
evidence. 

To study the question, the authors compiled a database of 7676 professional
football players in Scotland born before 1977. For every player, 3 non-players
born in the same year and living in an area with the same 
[Scottish Index of Multiple Deprivation](https://www2.gov.scot/Topics/Statistics/SIMD)
were found in the general population and served as the player's own mini-control 
group (so-called matched controls.) The prescription history and the cause of 
death (if the person died before 2017) was then obtained from medical records.
The data was analysed with Cox regression and related methods. The central
result is stark: ex-footballers have been dying of neurodegenerative disease at a rate 
3.5 times higher than the general population. They are also 
significantly more likely to have been prescribed dementia medication. What
stands out to me here is the strength of the effect -- a hazard ratio of 3.5 is 
large and unlikely to be explained away by any biases in the study.

Speaking of bias, and study design in general, I do have concerns.
The matching of footballers to controls was done only on the basis of the birth
year and SMID of the _last known_ postode. The last known postcode feels like a 
particularly weak proxy for lifelong socioeconomic status and other 
health-relevant habits. In
addition, it is conceivable that disease status could affect the last postcode,
with sick people moving to have better access to care and services, or indeed
_not_ moving while the healthy (potential) controls did. Without better covariates
on which to match footballers to controls, I'd have been tempted to save myself 
the trouble and simply draw a random control group with the same age structure 
from the general population.

In addition, I am not convinced that the findings can be generalised 
automatically to the modern game.
Unavoidably, the study reached deep into the past to find the subjects,  
but 1960s (say) Scotland was a particular time and place, and the sport was also 
different to what it is today. With the possible exception of Tony
Pulis' training sessions, football is no longer played with a wet medicine ball 
kept in the air non-stop. The professional players are also without a
doubt a much healthier bunch today, and with access to high quality health care 
and monitoring. The authors suggest to conduct a prospective cohort study (i.e. to
follow a sample of current players through their lives after they retire), but
naturally this would take a very long time. I can't help but wondering if a compromise
solution exists, where former players from an era more resembling the current game
are enrolled. For such more recent population, more data may also be available
to perform better matching to controls, and to include the relevant football
covariates in the analysis (for example the player's usual outfield position).

