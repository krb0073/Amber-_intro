---
title: "Understanding the differnet force feild and using tleap to make the system"
start: ??
teaching: 10
exercises: 0
questions: 
- "What is differenet between AMBER's force feild and the other two?"
- "How are the files formated for the amber simulations"
keypoints:
- "Something goes here"
---

# AMBER and the other force feilds
Here we will discus how the Amber forcefeild differes from the CHARMM forcefeild

## The amber force feild
All force feild used in MD are the Hamliationa of the system that descrides the ponteial energy landscape of the system at a given time. Motion can be evolved byy simple calacus(which will not be shown here)

<img src="https://ambermd.org/tutorials/basic/tutorial0/include/Amber_Hamiltonian.png">

These are grouped into two types of terms that we have covred already bonded and nonbounded. Lets comapre this to the CHARMM force feild to understand the differences 

<img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/1e5005f6ff57075c4a7eb71aed12de5bf5a30def">

| Forcefeild term| AMBER | CHARMM|
|----------------|-------|-------|
|  Bond Energy   |  same |  same |
|  Angle Energy  |  same |  same |
| Dihedral Energy|  same |  same |
| improper Dihe  |sometimes|  yes|
| van Der Waals  | same   | same |
| colombus      |  same  |  same |
| Urey-Bradley  |  No    |   yes |


### Notes 
The majorty of the foce feild is the same but in the base implamnetation of the forcefeild improper dihedrals and the Urey-Bradley term in the AMBER forcefeild are left out. 
- Urey-Bardley: The energy invloed with an anagle beding in a given plane

## Back to making the system

To make the system we will use tleap. Once the module is loaded we can type. The module that we loade has a built-in path to the AMBER direceotry that we will refrance as $AMBERHOME. We Can then call tleap by typing.

~~~
$> $AMBERHOME/bin/tleap 
~~~
{: .language-bash}

This will produce the message:

~~~
-I: Adding /shared/software/atomistic/amber/20_intel21_serial/dat/leap/prep to search path.
-I: Adding /shared/software/atomistic/amber/20_intel21_serial/dat/leap/lib to search path.
-I: Adding /shared/software/atomistic/amber/20_intel21_serial/dat/leap/parm to search path.
-I: Adding /shared/software/atomistic/amber/20_intel21_serial/dat/leap/cmd to search path.
Welcome to LEaP!
(no leaprc in search path)
> source leaprc.protein.ff19SB
----- Source: /shared/software/atomistic/amber/20_intel21_serial/dat/leap/cmd/leaprc.protein.ff19SB
----- Source of /shared/software/atomistic/amber/20_intel21_serial/dat/leap/cmd/leaprc.protein.ff19SB done
Log file: ./leap.log 
~~~ 
{: .language-bash}

We now soruce/load the force feild that we want to use.

~~~
>source leaprc.protein.ff19SB
~~~
{: .language-bash}

The program now has the force feild parmentes for the amino acid loaded which allows us to make a varaible that contians the protein of intrest

~~~
>diala = sequence {ACE ALA NME } 
~~~
{: .language-bash}

<img src="https://www.mrc-lmb.cam.ac.uk/public/xtal/doc/cns/cns_1.3/tutorial/generate/capping/aa_capped.gif">

- ACE: acetyl group cap 
- NME : Amide group cap 

## Water topology Aside 
There are sevrail differnet type of water topopies that can be used. They all have different applaictions that we will not cover now but in general they are grouped by the number of sites (bond between the atoms they have) The most common one that are used are OPC and TIP3P we will be using OPC water for this simuation. The current AMBER force feild we are working with show better results when using that water type.

## Back to tleap 
We are going to add in the parmetes for the water model we are using into tleapThe solvateoct command is used to add a octainalboc of OPC water with perodic boundries are 10 angstroums from the cneter. 
~~~
> source leaprc.water.opc 
>solvateoct diala OPCBOX 10.0
~~~
{: .language-bash}

the water padding is really important to pervent self interations across the PBC. We recomend that after you are done you inspect your system **makeing sure the distacne 15 A of water is between the peptide and the peptide across the periodic image**

saveing the rst7 and the parm7 to the working directory and qutting the program

~~~ 
> saveamberparm diala parm7 rst7
>quit
~~~
{: .language-bash}

We fianlly should have three file outputed:
- leap.log : a log file of all the setps and files that were used to make the system
- parm7: The topology file that contains all the conections,and parmamteres from the force feild for that atom type
- rst7: the X,Y,Z postions of all the atoms of the system 

Take some Time to look at each of the files that were made.
