# BioSB Algorithms for Genomics Course (BA4G)

October 10-14, 2022, Delft

Coordinators: Thomas Abeel (TU Delft), Sandra Smit (WUR) and Jasmijn Baaijens (TU Delft) 

## Location
TU Delft, Faculty of Applied Sciences, Lecture room G (F206), Building 22.
Lorentzweg 1, 2628 CJ Delft


### Travel instructions
You can find instructions for travel [here](https://iamap.tudelft.nl/en/poi/applied-physics-faculty-of-applied-physics-2/)



## Schedule
*To be updated for 2022*

|Day 1| Genome assembly      |
|------:|-----------------------------|
|  8:30 | Welcome                     |
|  9:00 | Lecture                     |
| 10:30 | Break                       |
| 11:00 | Programming exercises - [Rosalind][ex]|
| 12:30 | Lunch                       |
| 13:30 | Literature seminar - [papers][lit]|
| 15:00 | Break                       |
| 15:30 | Programming exercises - [Rosalind][ex]|
| 17:30 | Closing                     |

|Day 2  | Read alignment       |
|------:|-----------------------------|
|  8:55 | Welcome                     |
|  9:00 | Lecture                     |
| 10:30 | Break                       |
| 11:00 | Programming exercises - [Rosalind][ex]|
| 12:30 | Lunch                       |
| 13:00 | Literature seminar - [papers][lit]|
| 15:00 | Break                       |
| 15:30 | Programming exercises - [Rosalind][ex]|
| 17:00 | Exercise review             |
| 17:30 | Closing                     |

|Day 3  |Project              |
|------:|-----------------------------|
|  8:55 | Welcome                     |
|  9:00 | Project introduction [instructions][proj]|
|  9:30 | Project work                |
| 12:30 | Lunch                       |
| 13:30 | Project work                |
| 17:30 | Closing                     |

|Day 4  | Pan-genomics         |
|------:|-----------------------------|
|  8:55 | Welcome                     |
|  9:00 | Lecture                     |
| 10:30 | Break                       |
| 11:00 | Computer exercises          |
| 12:30 | Lunch                       |
| 13:30 | Literature seminar - [papers][lit]|
| 15:00 | Break                       |
| 15:30 | Computer exercises          |
| 17:30 | Closing                     |

|Day 5  | Putting it all together |
|------:|-----------------------------|
|  8:55 | Welcome                     |
|  9:00 | Project work - [instructions][proj]|
| 10:30 | Break                       |
| 10:30 | Project work - [instructions][proj]|
| 12:30 | Lunch                       |
| 13:30 | Talk\: Erwin Datema (Keygene) - Algorithm development for plant pan-genomics |
| 14:15 | Talk\: Sandra Smit  |
| 14:45 | Talk\: Thomas Abeel         |
| 15:15 | Wrap-up|
| 16:00 | Borrel                      |
| 17:00 | The End                     |

## Preparation
### Computer requirements
*To be updated*
You need to bring your own laptop. 

Requirements: 
* Python 3.6+
* At least 20Gb free disk-space

Desired (but not required): 
* Linux kernel system (Mac, Windows 10 or Linux based OS)

__NOTE:__ For those who are not familiar with unix shell, [click here][unix] for a quick tutorial.

### Course book
*To be updated*
On day 1 and 2, the course covers chapters 3 and 9 from the book ["Bioinformatics Algorithms - an active learning approach"](http://bioinformaticsalgorithms.com/). Having these chapters at hand during the programming exercises will prove very helpful.


## During the course

### Course material
*To be updated*
https://surfdrive.surf.nl/files/index.php/s/4fYFqUG76Fr7wZX

### Exercises 
*To be updated*
Exercises for Day 1 and Day 2 of the course are hosted on Rosalind. You first need to [enroll in the course](http://rosalind.info/classes/enroll/b694ec3604/).

After you have enrolled in the course, you can also [directly access it][ex] 

Exercises for Day 4 - Pangenomics will be shared during the course.

### Project
*To be updated*
You can find detailed instructions for the project [here][proj].

[unix]: https://ba4g.github.io/unix-intro.html
[ex]: http://rosalind.info/classes/614/
[proj]: https://ba4g.github.io/project-instructions.html

## Guest speakers

### Lucas van Dijk
Lucas van Dijk, Broad Institute of MIT and Harvard

Title: Pangenome-wide characterization of genetic variation for microbial species using linked De Bruijn graphs

Identifying genetic variation among microbial genomes is critical to understanding their evolution or tracking outbreaks. This, however, can be challenging because bacterial species often have highly diverse and plastic genomes: for example, two E. coli can have as little as 95% genome-wide nucleotide identity and share only 50% of their genes. Thus, any single reference is likely to produce lower accuracy variant calls in at least some regions, and may lack key genes present in the sample. In this lecture, I'll talk a new variant caller that aims to overcome these limitations by using multiple reference genomes combined in a graph, enabling characterization of genetic variation across a species's pangenome. I'll specifically focus on the data structure at the core of Pantry's variant assembly algorithm: a "linked De Bruijn graph". Linked De Bruijn graphs are an extension to a classical De Bruijn graph that integrates long-range connectivity information present in reference genomes or reads.


