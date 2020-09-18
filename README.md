
# coffea-casa-tutorials [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/CoffeaTeam/coffea-casa-tutorials/master)
This tutorial repository contains multiple guides for deploying [coffea](https://github.com/CoffeaTeam/coffea) on the [coffea-casa analysis facility](https://github.com/CoffeaTeam/coffea-casa).

It should be run from the coffea-casa facility, but a [binderized format](%28https://mybinder.org/v2/gh/CoffeaTeam/coffea-casa-tutorials/master) is included for those who want to play with subsets of this repository outside of coffea-casa.

## Summary
Roughly speaking, the repository is divided into three parts: a tutorial notebook ([notebook.ipynb](https://github.com/CoffeaTeam/coffea-casa-tutorials/blob/master/notebook.ipynb)), a set of simple benchmark examples ([benchmarks/](https://github.com/CoffeaTeam/coffea-casa-tutorials/tree/master/benchmarks)), and a larger analysis ([analysis-casa.ipynb](https://github.com/CoffeaTeam/coffea-casa-tutorials/blob/master/analysis-casa.ipynb)), all of which make use of coffea-casa.

***If you are completely new to the coffea framework***, it is recommended that you begin in the tutorial notebook, which features an overview of how analysis can be done in a columnar fashion. The notebook will lead you to the analysis, and the benchmarks/ provide additional resources if you need more examples or references.

***If you have previous coffea experience and are just interested in seeing how the coffea-casa facility works***, it is recommended that you go to the benchmarks/ folder and search through some of the simple examples there, without bulky coffea selections and physics getting in your way! See also the **Supplements** section below.

The rest of this is an entirely-too-detailed description of the repository's contents, in case anything up to this point has been unclear.

## Benchmarks
*Details on the provided benchmarks, as well as local (non-coffea-casa) implementations and older/alternate solutions, can be found on the [coffea-benchmarks](https://github.com/mat-adamec/coffea-benchmarks) page, whose basic information has been copied here.*

The benchmarks/ folder houses solutions to eight "functionality benchmarks" first proposed [here](https://github.com/iris-hep/adl-benchmarks-index). They are as follow:
1. Plot the missing ET of all events.
2. Plot pT of all jets in all events.
3. Plot pT of jets with |η| < 1.
4. Plot the missing ET of events that have at least two jets with pT > 40 GeV.
5. Plot the missing ET of events that have an opposite-sign muon pair with an invariant mass between 60 and 120 GeV.
6. Plot pT of the trijet system with the mass closest to 172.5 GeV in each event and plot the maximum b-tagging discriminant value among the jets in the triplet.
7. Plot the sum of pT of jets with pT > 30 GeV that are not within 0.4 in ΔR of any lepton with pT > 10 GeV.
8. For events with at least three leptons and a same-flavor opposite-sign lepton pair, find the same-flavor opposite-sign lepton pair with the mass closest to 91.2 GeV and plot the transverse mass of the missing energy and the leading other lepton.

**For most coffea-casa purposes, benchmark 1 should suffice** as an example, but the others are here because, well, there's nothing wrong with having more examples to look at!

## Tutorial
The tutorial notebook is a walkthrough of how to do analyses in coffea. It is updated to the newest 'standards' of coffea (as of 9/10/2020), and will take you (sequentially) through how to access data in NanoEvents, how to make selections on that data, how to handle some edge cases that don't play nicely in a columnar framework, and how to make plots of your data. I attempted to make this as self-explanatory as possible; thus, there are excessive explanations throughout.

This notebook was originally given as a tutorial for PyHEP 2020 ([which was recorded!](https://www.youtube.com/watch?v=oPl0t8J36-Q)). It concluded with a scaled-up demo of the tutorial's contents deployed on coffea-casa, which can't really be captured within the notebook itself. You'll have to make your own demo by playing around with the analysis notebook yourself (see **Analysis** below)!

## Analysis
The analysis notebook, in its current state in this repository, was precisely the demo I featured in PyHEP 2020 (mentioned above). You should be able to run it on coffea-casa without any further configuration.

The physical details of this analysis are largely irrelevant, but for those curious: it is an attempt to recreate the results of "*[Search for associated production of a Higgs boson and a single top quark in proton-proton collisions at √s=13TeV](https://journals.aps.org/prd/abstract/10.1103/PhysRevD.99.092005)*" within coffea. Explanations of cuts, selections, and other operations can be found there, or briefly explained in the tutorial notebook above. 

## Supplements
There is an extra file ([analysis-local.ipynb](https://github.com/CoffeaTeam/coffea-casa-tutorials/blob/master/analysis-local.ipynb)) which deploys locally, using coffea's `futures_executor` rather than the `dask_executor`, the latter of which should be used on coffea-casa. This file exists for comparison purposes, especially for those people who have previous coffea experience and want to see the differences in executor setup.
