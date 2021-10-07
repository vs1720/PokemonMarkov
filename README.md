# PokemonMarkov
A Markov Model Pokemon Population Dynamics. I simulate all pokemon types to see which would win out in the end. See how it plays out:

![Simulation in Action](https://github.com/vs1720/PokemonMarkov/blob/master/PokemonPopulationDynamic.gif)

## Basic Description

We are simulating a simplistic pokemon world! We assume pokemon in our world are [well mixed](https://www.aiche.org/academy/webinars/what-does-well-mixed-mean-and-what-happens-if-cstr-not-perfectly-mixed), that is there are no herds and pokemon aren't attracted to any specific ttpes etc. They meet one another randomly. So let's say a fire-type meets a water type. The fire type is at a disadvantage (but it can still win, though at lower odds - see details below). When a type X beats a type Y pokemon, the type Y pokemon is killed off, and replaced with a type X pokemon. So, one multiples, the other loses a population. A sort of natural selection, if you will.  

Note that we do not consider stats, dual typings, moveset, or anything like that! This is a very simple model, though the dynamics that emerge are very interesting all the same. 

See [PokemonMarkov.ipynb](Notebook) for full walkthrough and graphs

