---
title: "Introduction to the Amber"
start: 0
teaching: 10
exercises: 0
questions:
- "What is AMBER?"
- "When do you use amber?"
- "What differences are there between abmer and other software?"
keypoints:
---
# The Amber package for molecular Dyanmics

Assisted Model Building with Energy Refinement(AMBER) dates all the way back to 1975 in the Lab of  Peter A. Kollman at the University of California, San Francisco.
Making the program the most established one that we will look at today. Amber 20 , the most current version of the code, is wirtten
in a combonation of C , Fortrain and python(mostly for analysis packages). We will on go over a small portion of what the
pacakge can do but The program can handell Molecular Dyanmics , QM/MM, and Monte Carlo. This and the number of analysis codes leades to the manaul of the pacakge
being about 1,000 pages. 

## A word of warning when using AMBER 
All of these programs demand a firm understanding of your system and Molecualr dyanamcis as a whole ,but the way amber has a steeper learing curve than gromacs or NAMD. This 
is due to how the configuration files for the pacakges.  For example when using a thermostat in a simulation:
| Engine | Keyword for The langevin thermostat|
|--------|------------------------------------|
| NAMD   |                langevin            |
| GROMACS|                v-rescale           |
| AMBER  |                ntt=3               |

There are a total of 12 differenvet tempature control option from 0 to 11 and each are diffecenert ways to apply heat to a system. It is not the same 
for the other two that are being covered today since they each have a keyword for each type of thermostat. 
 
**PS. if you really want to understand MD egengies this manual is one of the best to study from**

