# coffea-casa-tutorials
This tutorial repository contains resources for deploying [coffea](https://github.com/CoffeaTeam/coffea) on the [coffea-casa analysis facility](https://github.com/CoffeaTeam/coffea-casa). It should be run from the coffea-casa facility.

## Table of Contents
- [Summary](https://github.com/CoffeaTeam/coffea-casa-tutorials#summary)
  - [Cloning in JupyterLab](https://github.com/CoffeaTeam/coffea-casa-tutorials#cloning-in-jupyterlab)
- [Examples](https://github.com/CoffeaTeam/coffea-casa-tutorials#examples)
- [Analyses](https://github.com/CoffeaTeam/coffea-casa-tutorials#analyses)
  - [tHq](https://github.com/CoffeaTeam/coffea-casa-tutorials#thq)
    - [Tutorial](https://github.com/CoffeaTeam/coffea-casa-tutorials#tutorial)
    - [Benchmarking](https://github.com/CoffeaTeam/coffea-casa-tutorials#benchmarking)
  - [topcoffea](https://github.com/CoffeaTeam/coffea-casa-tutorials#topcoffea)
  - [HZZ](https://github.com/CoffeaTeam/coffea-casa-tutorials#HZZ)


## Summary
The repository is divided into several components, which may be more or less helpful depending on your goals. 

If you are completely new to coffea, it's suggested that you begin your journey with the [analyses/thq/analysis_tutorial.ipynb](https://github.com/CoffeaTeam/coffea-casa-tutorials/blob/master/analyses/thq/analysis_tutorial.ipynb) file. This is a walkthrough of how to construct the analysis in the [analysis/thq](https://github.com/CoffeaTeam/coffea-casa-tutorials/tree/master/analyses) folder, going into thorough details of how columnar analysis can be implemented. The coffea documentation also has [additional examples](https://coffeateam.github.io/coffea/examples.html) to help you learn!

The [examples/](https://github.com/CoffeaTeam/coffea-casa-tutorials/tree/master/examples) folder features examples which may further augment your understanding of coffea, but which are also useful to experienced coffea users as minimal examples for running on coffea-casa and Dask. These examples should run out of the box on our facility, and may thus be useful for debugging.

Finally, the template at [coffea-casa-template.ipynb](https://github.com/CoffeaTeam/coffea-casa-tutorials/blob/master/coffea-casa-template.ipynb) provides a holistic view for how to execute a file on coffea-casa. The latter sections of this are useful for experienced coffea users who want to deploy their analysis on the coffea-casa facility; just start with the *Running the Dask Executor,* and refer to the notes under *Miscellaneous* for how to employ additional tools. New users should look through the whole template to understand the standard structure of a coffea analysis.

### Cloning in JupyterLab
Cloning a repository into JupyterLab is simple, though it can be a little confusing because it is spread across two tabs in the sidebar: the *File Browser* and the *Git* tabs.

In order to clone a repository, first go to the Git tab. It should look like this:

<img src="docs/git.png" alt="Git" width="50%"/>

Simply click the appropriate button (initialize a repository, or clone a repository) and you'll be hooked up to GitHub. This should then take you to the *File Browser* tab, which is where you can see all of the repositories you have cloned in your JupyterLab instance. The File Browser should look like this:

<img src="docs/browser.png" alt="Browser" width="50%"/>

If you wish to change repositories, simply click the folder button to enter the root directory. If you are in the root directory, the Git tab will reset and allow you to clone another repository.

If you wish to commit, push, or pull from the repository you currently have active in the File Browser, then you can return to the Git tab. It should change to look like this, so long as you have a repository open in the File Browser:

<img src="docs/git2.png" alt="Git" width="50%"/>

The buttons in the top right allow for pulling and pushing respectively. When you have edited files in a directory, they will show up under the *Changed* category, at which point you can hit the **+** to add them to a commit (at which point they will show up under *Staged*). Filling out the box at the bottom of the sidebar will file your commit, and prepare it for you to push.

The rest of this readme provides extensive details and specifications about the files included, for those interested in their purpose/motivation beyond their function as a tutorial.

## Examples
*Details on the provided examples, as well as local (non-coffea-casa) implementations and older/alternate solutions, can be found on the [coffea-benchmarks](https://github.com/mat-adamec/coffea-benchmarks) page, whose basic information has been copied here.*

The examples/ folder houses solutions to eight "functionality benchmarks" first proposed [here](https://github.com/iris-hep/adl-benchmarks-index). They are as follow:
1. Plot the missing ET of all events.
2. Plot pT of all jets in all events.
3. Plot pT of jets with |η| < 1.
4. Plot the missing ET of events that have at least two jets with pT > 40 GeV.
5. Plot the missing ET of events that have an opposite-sign muon pair with an invariant mass between 60 and 120 GeV.
6. Plot pT of the trijet system with the mass closest to 172.5 GeV in each event and plot the maximum b-tagging discriminant value among the jets in the triplet.
7. Plot the sum of pT of jets with pT > 30 GeV that are not within 0.4 in ΔR of any lepton with pT > 10 GeV.
8. For events with at least three leptons and a same-flavor opposite-sign lepton pair, find the same-flavor opposite-sign lepton pair with the mass closest to 91.2 GeV and plot the transverse mass of the missing energy and the leading other lepton.

## Analyses
The analyses folder contains two subfolders: tHq and topcoffea, corresponding to two analyses which have been completed in coffea and adapted for coffea-casa.

### tHq
The tHq folder contains an analysis-casa.ipynb file for Dask deployment, an analysis-local.ipynb file for local testing, and an analysis_tutorial.ipynb file which thoroughly explains how the analysis was built, intended as a tutorial for coffea. The physical details of this analysis are largely irrelevant, but for those curious: it is an attempt to recreate the results of "*[Search for associated production of a Higgs boson and a single top quark in proton-proton collisions at √s=13TeV](https://journals.aps.org/prd/abstract/10.1103/PhysRevD.99.092005)*" within coffea. Explanations of cuts, selections, and other operations can be found there, or briefly explained in the tutorial notebook mentioned below.

#### Tutorial
The tutorial notebook is a walkthrough of how to do analyses in coffea. It is updated to the newest 'standards' of coffea (as of 9/10/2020), and will take you (sequentially) through how to access data in NanoEvents, how to make selections on that data, how to handle some edge cases that don't play nicely in a columnar framework, and how to make plots of your data. I attempted to make this as self-explanatory as possible; thus, there are excessive explanations throughout.

This notebook was originally given as a tutorial for PyHEP 2020 ([which was recorded!](https://www.youtube.com/watch?v=oPl0t8J36-Q)). It concluded with a scaled-up demo of the tutorial's contents deployed on coffea-casa, which can't really be captured within the notebook itself. You'll have to make your own demo by playing around with the analysis notebook yourself (see **Analysis** above)!

#### Benchmarking
There is a [subfolder](https://github.com/CoffeaTeam/coffea-casa-tutorials/tree/master/analyses/thq/benchmarking) within tHq which is a variation of the analysis-casa.ipynb file designed for benchmarking. It allows easy blowing-up of datasets to any size, as well as tools for manually requesting workers (rather than using autoscaling), so that benchmarks can be derived. For most users, this file probably isn't useful! For developers, however, it might be. Tweak the blocks pertaining to weak and strong scaling to vary your measurements.

### topcoffea
The topcoffea folder contains a work-in-progress notebook adaptation of top quark analyses using the Coffea framework for coffea-casa. The notebook works with the full repository, which can be found at: https://github.com/TopEFT/topcoffea.

### HZZ
The topcoffea folder contains HZZ ATLAS Opendata analysis which is syncronized from https://github.com/iris-hep/analysis-grand-challenge/tree/main/analyses/atlas-open-data-hzz repository and contributed by Storm Lin / improved by Alex Held (IRIS-HEP).
