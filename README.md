# PokemonMarkov
A Markov Model Pokemon Population Dynamics. I simulate all pokemon types to see which would win out in the end. See how it plays out:

![Simulation in Action](https://github.com/vs1720/PokemonMarkov/blob/master/PokemonPopulationDynamic.gif)

## Basic Description

We are simulating a simplistic pokemon world! We assume pokemon in our world are [well mixed](https://www.aiche.org/academy/webinars/what-does-well-mixed-mean-and-what-happens-if-cstr-not-perfectly-mixed), that is there are no herds and pokemon aren't attracted to any specific ttpes etc. They meet one another randomly. So let's say a fire-type meets a water type. The fire type is at a disadvantage (but it can still win, though at lower odds - see details below). When a type X beats a type Y pokemon, the type Y pokemon is killed off, and replaced with a type X pokemon. So, one multiples, the other loses a population. A sort of natural selection, if you will.  

Note that we do not consider stats, dual typings, moveset, or anything like that! This is a very simple model, though the dynamics that emerge are very interesting all the same. 

I mentioned above that the winner of a battle between pokemon type X and type Y is decided by chance. What is the chance? You can check out the pokemon typing chart over here. So Let's take steel and normal. Normal is 1/2 effectiveness against Steel, and steel is 1x effectiveness against normal. So The odds of normal winning against steel is (0.5)/(1 + 0.5) = 1/3. (There is an exception. Normal and ghosts can't touch each other, so their win-rate I have put as 0.5. Assume when they meet, they flip a coin to decide who wins).

We then making such a win probability matrix - call it W that has such probabilities for ALL possible matchups. Along with our population vector P0 we can advance a "round". P1 = P0 + (W - WT )*P0, iterated to whatever n you want. The simulation stops when an equilibrium is reached (i.e. the population vector is unchanged after successive multiplications by W). This is a sort of deterministic Markov Model.

So, you may have noticed that I specify N = 100000. This matters quite a bit, but it is not obvious why (it stumped me for a couple of hours). So you will notice, some pokemon types "die out." But our W matrix has no zero basis. The population vector should never have zero! Well, my astute reader, you'd be right. I have to manually include a "cutoff" Like, when n falls below this, it's dead. And this threshold, I decided, is when there would be less than 1 pokemon of a type left. Which is 1/N or, 1/100000. Notice how many times there are "comebacks," a type coming roaring back from the brink of extinction. A lower N means this happens less, and a higher N means this happens more! N = 10000000 or something could have drastically different results! But the animation took forever, so, I decided on this sweet spot.

See [PokemonMarkov.ipynb](Notebook) for full walkthrough and graphs

