---
layout: post
title: "Forecasting the Candidates part 2"
---
<small>
Data and code are [available on Github.](https://github.com/huffyhenry/forecasting-candidates/2021)
</small>

It's this time of the year again. Eight of the world's most 
sartorially challenged millenials are about to reunite in Yekaterinburg
and play the second leg of the Candidates tournament. The winner will
incur serious trauma attempting to take the world championship from Magnus 
Carlsen later in the year. But who will it be? The favourites
Fabiano Caruana and Ding Liren disappointed during the first leg. 
Ian Nepomniachtchi of Russia and Maxime Vachier-Lagrave
of France emerged as joint leaders. Meanwhile, chess became a bona fide
e-sport, with almost all traditional events cancelled and top players competing 
for very serious money in online rapid events.

To predict the outcome of the tournament, I compiled a dataset
of 3617 classical and rapid games between top players since 
the 2018 Carlsen-Caruana match. The data comes from [Caissabase](http://caissabase.co.uk/) 
and [The Week in Chess](https://theweekinchess.com/). The model is still based on the
Davidson ratings described in [last year's post](https://kwiatkowski.io/candidates),
but with a major improvement:
the evolution of players' strengths over time is modelled with a Gaussian
Process. Performance in rapid and classical formats is assumed to be driven
by the same underlying rating, but with different baseline draw probabilities.

## The model

To explain the model quickly, let's ask it what it thinks about the world champion:

<figure>
  <img src="../assets/figures/candidates2_carlsen.png">
</figure>

Every blue line represents one possible course of Carlsen's
playing strength over the last two and a half years. These individual 
histories may differ significantly from one another. They are not equally
probable, but together they cover the spectrum of possibilities well. 
The red line summarises this sample by connecting the mean of the ratings at each date. 
The story that emerges is one of a prolonged slump since Carlsen's arguably best-ever form 
shortly after the last World Championship match.

One weakness of the model, shared by many rating systems, is that the
raw rating is hard to interpret. What does Carlsen's drop from 0.806 to 0.068
actually mean? We can get an insight by pitting him against his last
challenger:

<figure>
  <img src="../assets/figures/candidates2_caruanavscarlsen.png">
</figure>

In this plot, each line gives the probability that Caruana would win a
game against Carlsen if drawn games were voided. It looks like
Caruana has gained some ground since the 2018 match, but from this perspective
it is not possible to tell to what extent it is due to his own improvement
and to what extent to Carlsen's slump.

## The candidates
Let's have a look at how the eight candidates have fared according to the
model. We plot the mean rating again since no suitable baseline exists:

<figure>
  <img src="../assets/figures/candidates2_candidates.png">
</figure>

Wang Hao and Alekseenko are clear outsiders. Caruana 
is the strongest candidate, with a fairly
stable rating apart from the bump around his dominant victory at Wijk aan Zee.
The switch to online chess was kind to Giri and Nepomniachtchi. 
Giri especially has impressed by transforming himself over the course of 2020 
from a player with a reputation for solid and deliberate style into a speed chess
juggernaut, and the model recognises it clearly. Ding Liren,
Grischuk and Vachier-Lagrave lost a lot of rating in the same period
due to relatively poor performances and inactivity.

To predict the outcome of the tournament, I took the actual results from
last year and the current ratings and simulated the second round-robin 
10'000 times. The results are as follows:

| Rank | Player     | Win odds | Win probability |
|------|------------|----------|-----------------|
|    1 | Nepo       |     2.49 | 40.2%    
|    2 | MVL        |     2.52 | 39.7%    
|    3 | Caruana    |    11.8  | 8.5%     
|    4 | Giri       |    18.8  | 5.3%     
|    5 | Grischuk   |    24.4  | 4.1%     
|    6 | Wang Hao   |    54.1  | 1.8%     
|    7 | Ding Liren |    343   | 0.3%     
|    8 | Alekseenko |    1990  | 0.1%  

Nepomniachtchi and Vachier-Lagrave are almost equally likely to win, with
Caruana having an outside shot. But why isn't Nepo's clear rating advantage
over MVL reflected in the odds? The answer lies in the tie-break rules.
Currently, MVL has the tie-break on Nepo thanks to his win in their direct
encounter last year, and in addition has a slight edge in Sonneborn-Berger.
If the head-to-head tie-break did not exist, Nepo's win probability 
would be exactly 50%, and MVL's 31.5%. The model may well overestimate the
importance of the tie-break -- in particular it does not understand that 
Nepo will have white pieces against MVL in the second leg. But with only
seven rounds to go, the likelihood of a tie for first place is more than
1 in 4.

## Bonus: alternative rating list

Presented without comment.

| Model Rank | FIDE rank <br> (classical) | Player | vs Carlsen <br> (no draws) |
|------|-----------|------------------------|-------------------|
|    1 |         1 | Magnus Carlsen         |            
|    2 |         9 | Wesley So              | 37.2%        
|    3 |         2 | Fabiano Caruana        | 36.8%        
|    4 |         4 | Ian Nepomniachtchi     | 34.5%
|    5 |         7 | Anish Giri             | 34.5%
|    6 |        10 | Teimour Radjabov       | 34.3%
|    7 |        18 | Hikaru Nakamura        | 34.2%
|    8 |         3 | Ding Liren             | 30.8%
|    9 |        11 | Maxime Vachier-Lagrave | 29.7%
|   10 |         5 | Levon Aronian          | 28.8%
|   11 |        30 | Vladislav Artemiev     | 28.5%
|   12 |         6 | Alexander Grischuk     | 28.0%
|   13 |        28 | Daniil Dubov           | 28.0%
|   14 |        59 | Vasyl Ivanchuk         | 25.0%
|   15 |        11 | Richard Rapport        | 24.9%
|   16 |        33 | Yu Yangyi              | 24.8%
|   17 |        24 | Dmitry Andreikin       | 23.4%
|   18 |        13 | Alireza Firouzja       | 22.9%
|   19 |        47 | Maxim Matlakov         | 22.8%
|   20 |        17 | Viswanathan Anand      | 21.6%
| ...  |           |                        |
|   28 |        12 | Wang Hao               | 19.3%
| ...  |           |                        | 
|   40 |        42 | Kirill Alekseenko      | 13.4%
