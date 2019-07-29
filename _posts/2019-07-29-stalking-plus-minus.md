---
layout: post
title: Stalking plus-minus
---
I have always had a huge soft spot for top-down metrics in soccer. I wrote why
at length 
[elsewhere](https://statsbomb.com/2014/05/picking-the-optimal-colombian-xi-for-the-world-cup/),
but briefly, their central promise to rate players
in a completely assumption-free fashion. This is in stark contrast with
mainstream player analytics, which measure
players' contributions in terms of individual actions that they perform or assist.
There are good reasons for the proliferation of bottom-up metrics, chief among them feasibility. 
Because
goals are so rare in football and players are subsitituted infrequently, it is
very difficult to tease apart the contributions of individual players without
additional assumptions.
In fact, every attempt at a plus-minus that has been written up in public consists at least in
part of teeth-gnashing and garment-rending brought about by this central problem.
Conversely, player ratings based on individual actions are easier to build, at
least from the technical standpoint. What is less appreciated is that they come 
at the huge price of accepting, largely on faith, that these individual actions 
ultimately matter. Because of that, until +/- is conclusively proven dead, it 
is always going to merit another look.

This post contains no orginal research. I have merely collected my notes and
links relating to +/- in soccer. Of course, the seminal contributions were
made in basketball and ice hockey, but I do not review them here. I focus 
on _adjusted_ +/-, that is where computing each player's contribution is done 
while controlling for all other players involved, usually in a massive regression.
The dependent variable in this regression is called the _target_; in the 
_classical_ approach, the target is the goal difference. 

#### prehistory
The beginnings of Jörg Seidel's [Goalimpact](https://www.goalimpact.com/about) project,
by far the best-established +/- model in soccer. The design of Goalimpact is
not public, but it is known to target goal difference and, in the current version, 
incorporate player age curves.

#### 2013
Dan Altman builds 
[player Shapley values](https://web.archive.org/web/20130922064558/www.bsports.com/statsinsights/football/introducing-the-shapley-value-to-football) 
<small>[archive.org link; see also a [2016 write-up](http://www.northyardanalytics.com/blog/2016/01/18/finding-the-weak-link/)
and a [high-level pitch](https://northyardanalytics.com/shapley-values-english-premier-league-2012-13.php)]</small>, 
which are a close cousin of +/-. The target measure is the expected goal difference.
  

#### 2014
Howard Hamilton describes his 
[attempt at a classical +/-](https://www.soccermetrics.net/player-performance/adjusted-plus-minus-deep-analysis).
Howard's post is very valuable as a clear demonstration of the key technical
issue with +/-, namely the (near-)singularity of the regression matrix, 
and how to overcome it with ridge regression.

Łukasz Szczepański experiments with +/- and concludes (in an 
unpublished report) that the classical approach is unworkable in soccer.

Matthias Kullowatz posts 
[unadjusted +/- ratings for the 2014 season of the MLS](https://www.americansocceranalysis.com/home/2014/12/28/plus-minus-mls).  

#### 2015
Martin Eastwood publishes his 
[Bayesian take on the problem](http://pena.lt/y/2015/02/26/playerrating-a-bayesian-method-for-evaluating-football-players/).
The key idea is to inject extra information into the system by creating
a prior on each player coefficient, presumably using on-the-ball event data.

#### 2016
Will Gürpınar-Morgan 
[tackles +/- head-on](https://2plus2equals11.com/2016/02/09/fools-gold-xg/),
using non-shot (i.e. play-level) expected goal difference as the target,
regularising the estimates via ridge regression, and investigating the 
precision of the estimates by bootstrapping.  

#### 2017
Tarak Kharrat and colleagues develop 
[three new +/- ratings](https://arxiv.org/abs/1706.04943), targeting
actual goals, expected goals and expected points. The player ratings are 
regularised with ridge regression and the observations are weighted by time 
elapsed until the present to emphasise current player ability. 
As befits an academic work, the paper is a good
source of references to previous +/- efforts.

#### 2018 
Steven Schultze and Christian-Matthias Wellbrock present 
an [idiosyncratic +/- model](https://content.iospress.com/articles/journal-of-sports-analytics/jsa225)
in the Journal of Sports Analytics. Unlike almost all other models considered here,
theirs does not estimate the ratings simultaneously for all players. Instead,
bookmakers' odds are used to obtain expected match outcomes, and calculations 
are done for each player separately. An additional novelty is valuing game-changing 
goals more than those that are not relevant to the game outcome.  

#### 2019
Lars Magnus Hvattum creates 
a [series of videos](https://www.youtube.com/channel/UC64jAkIQX-hD3pSnnOmr2MA)
about +/-, which I have yet to watch; and Garry Gelade
[models Lars' ratings](http://business-analytic.co.uk/blog/learning-to-love-plus-minus/)
using on-the-ball event data, thus providing perhaps the first formal connection
between top-down ratings and individual player actions.
