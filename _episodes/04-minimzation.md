---
title: "Miniaztion using Sander"
start: ??
teaching: 10
exercises: 0
questions: 
- " What is A comment in the AMBER configuration file?"
- "Why is Sander used for minizations?"
keypoints:
- "Something goes here"
---

# Minimaztion 
## General note on AMBER configuration files 
- ! how to commnet in infromation for the config 
-  &cntrl : The line that tell the program to start reading the config. 

Each line after the  &cntrl mustb have a common(,) and end in a /

## Minimaztion scipt for AMBER 
~~~
Min !this is not read by the program 
   &cntrl
    imin=1, !turn on the minimzier form the begining
    ntx=1, ! read the cordiantes from the rst7 file but we do not neeed any velocties 
    ireset=0 , ! we are not restarting a run 
    maxcyc=2000 , !number of cycles for minization 
    ncyc=1000 , ! the step taht we switch from the stepest descent algorthum to congejate gradainte alrogthum
    ntpr=100 , ! print the infomation every 100 steps 
    ntwx=0 , ! no trajecotry is given out 
    cut=8.0 , ! The cutoff for electrostatics. do not makeb it smalller because of accuray but large is okay just takes longer but better resutls
   /
~~~
