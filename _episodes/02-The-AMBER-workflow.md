---
title: "Common Workflow For AMBER Simulations"
start: ??
teaching: 10
exercises: 0
questions: 
- "What is the work flow for an Amber simluation?"
- "What format are the paramter files in ?"
- "Why is Sander used for minizations ?"
keypoints:
- "Something goes here"
---

# The AMBER Workflow 
This is the standard way to prefrom an Amber simuation

## The system 
For this tutoral we will be using Alanine dipeptide. Alana dipeptide is just two Alaine Amino acids connected togethere. This system is a well know model system for protein since the small size of protein allows it to easliy sample differnet confromations, and combonations of phi and psi angles of the backbone. 
<img src="https://ambermd.org/tutorials/basic/tutorial9/include/amber_flow.png">

## 1. System construction 
We have some options here:
- use a PDB of the full system and put that through pdb4amber 
- Have a pdb of the molecule of interst then solvate and add salt using Leap/tleap
- **Use Tleap/Leap to build the system**
<img src="https://ambermd.org/tutorials/basic/tutorial0/include/Alanine_Dipeptide_2D.png" title="Alaine dipeptide">

Loading the AMBER Module:
~~~
$> module load 
~~~
{: .language-bash}

Before we can build Lets talk about the force feild for AMBER.
