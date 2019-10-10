_BioSB 2019 Project Instructions - October 14-18_

# Problem statement

You are given long read sequences of _E. coli_ in FASTQ format as well as short reads; in this project you are asked to implement an assembly pipeline comprising two Python scripts described below.

## - Script 1
Implement the minimap algorithm for read alignment, and miniasm algorithm for assembling the genome graph. 

__Input:__ Long reads in FASTQ format

__Output:__ Genome assembly in FASTA format

Your script should consist of __2 main functions__: first one for aligning with minimap and the second one for assembling with miniasm. Here is a quick recap of both methods from the [corresponding paper](https://academic.oup.com/bioinformatics/article/32/14/2103/1742895).

__1. Minimap__
 1.1. Computing minimizers
 >Recall: a (_w_, _k_) minimizer of a string _s_ is the smallest kmer in a surrounding window of _w_ consecutive kmers. 
 >
 ![](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/bioinformatics/32/14/10.1093_bioinformatics_btw152/3/m_btw152ilf1.gif?Expires=1570741081&Signature=CKgex4e2yQDeqRG5WZ4Y9PyehPr2GJkKcNPBSLm4~SYSKDt72kMta4KLkXiSLosWRoA1n5XtN5mFLZTvtQ0nyoij4OxDFZQ4Eq~kEDQ32t~cbyvRBnsLVDq8cGFzyUZeEkUIEyUULanL-JDf6COZDgszii96QuV9GVTit1NdRilRmbzh5aILXvTs5FTRd8gFS4ZS05T4Cs3OmpnlI0dy6EtKNHsUA-VQz1SnqdjCFlDF~~MQY9gJMDFsBODYnsSKbY2KpAn50-SdfdtJRJ1o1DjCejhy1CFKOGtITrhx54n5XPhzxhOSfmYLYqnbYxX0VSZxkLM6w3u9eHswJgpH~w__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)  ![](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/bioinformatics/32/14/10.1093_bioinformatics_btw152/3/m_btw152ilf2.gif?Expires=1570741081&Signature=ZLr3Bouk5ZWbKqlcuD9AKdCHxkQlOYX2-I1yIkH1PbAB6-EC9x0OKPkmUs3wu2Rhatz15ubhgm5WcH4JdoVPrZWjXRa2ig7KYdeRSr1PHcVW1DdV8WJnQuuAKNRO9eXei9P-if4F7841ikvygVneGNGSLGvIV0PjFKZyDVB227oCxbJJ8zw2d2DLeirViknypavpY~kAtCXE3lpGPyheVhYxKbZoJ5w64ov5Xz7WpVgQHR9lPoDU4CTePr-eQsoRZ-q20Jkb-wydepm7B5yrUjJO2CoX~wsu-JMz8vOscI270DLEfImDJKHIra-2OqsHCdWW4yUPAZjRjOSvTDqBZA__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)
 
 1.2. Indexing
 > Using the output from _Algorithm 1_ you should make a hash table for minimizers of all target sequences:  Key is the minimizer hash and the value is a set of target sequence index, the position of the minimizer and the strand. 
 > 
![](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/bioinformatics/32/14/10.1093_bioinformatics_btw152/3/m_btw152ilf3.gif?Expires=1570741081&Signature=YaSVIaAnb5VQ8Qi9OiLNSXd1GCPxjpsza3Z4UhPk~khphF2wKT8h2HYid~YR6sowoqnCovH3qsQsHx0Efz5TWobkO7~v2uEaBY3Ivgmytfn2vRNQteD8sLgSSlGcd3nHo3BsKM6lH55oCLr88x8q7Q4D1vggu-mVH-Xc9wu-7XYt51ILV1bcnZtC7tvlYQVPkikdTa15OUglVOm8wjakZEg7GpC6viFpxZiSBtnYtgRSZsZmbfQPVJhjEb8~HiivBYZwoANloI0gYNm9if7AmnIokFQUrLFQ9oZtCiZr6CLDdB6ErInvQFxspI4IWLGR04nYDJK-W~0rIF2rmy8TZw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)

_Hint: When you are implementing, you should append minimizers to an array (includes minimizer sequence and its position), and then sort this array once you have collected all the minimizers._

 1.3. Mapping
>Collect all the minimizer hits between the query and all the target sequences. Then, perform single-linkage clustering to group approximately colinear hits. 
>Recall: Some hits in a cluster may not be colinear because two minimizer hits within distance ϵ are always ϵ-away. To fix this issue, you should find the maximal colinear subset of hits by solving a longest increasing sequencing problem (see line 3 in _Algorithm 4_)
>
![](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/bioinformatics/32/14/10.1093_bioinformatics_btw152/3/m_btw152ilf4.gif?Expires=1570741081&Signature=Rlu~j80d5w0~D4NNdnny1Ifid-onpfkz0ebF0~CH5kEtvTuV6u-ZVJKZ5CsCLVuqCM23vKf1-ky6WZ~xnZtjOq9v5NVNYh9x6XCf7Cm3mE2C17gfwPQKXNartPePlwoIGzJT86ho6pUANdhOBJ3ggyvGx2BPUWNiRY4JcimOt7rs5z9wJbWPdoQZAkmyqaXEW8eeu3ijewD-WloJJYQSLMEVpTJcJHFhQue5DWK92sz9RV5w-lodFXE6KQBDGnXgx4wY1wPA32gp3ymNdwLnyyIky1LI-AceNN266fPV9rk1qZxtS0QKwTuS-VcvjsM7SLzWUwskjEy8TX6v3GtONA__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)

_Hint: In implementation, set thresholds on the size of the subset (size is 4 by default) and the number of matching bases in the subset to filter poor mappings (100 for read overlapping)._

__2. Miniasm__

2.1. Trimming reads

2.2. Generating assembly graph

2.3. Graph cleaning

2.4. Generating unitig sequences
 
Now, you have two options for writing _Script 1_:

(1) Implement both minimap and miniasm _from scratch_ 
(2) Implement minimap from scratch only, and use the _miniasm tool_ provided by the authors

_HINT: If you choose to take the second route, you have to **modify your first function** to generate a **PAF file** as output because the miniasm tool only accepts PAF as input for assembly. See [author's webpage for more details on PAF](https://lh3.github.io/minimap2/minimap2.html#10)_


## - Script 2
Implement [Burrows-Wheeler Alignment tool (BWA)](https://www.ncbi.nlm.nih.gov/pubmed/19451168) to align the given short sequencing reads against the assembly you obtained from _Script 1_. Identify SNPs in your alignment, and correct them to obtain the final, "polished" assembly. 

__Input:__ Genome assembly in FASTA format and short reads 

__Output:__ Improved genome assembly in FASTA format 
 
 _HINT: Use your script for Burrows Wheels transform exercise from Chapter 9 yesterday_
 
 __IMPORTANT NOTE:__ For those who could not obtain an assembly output using their _Script 1_, do let us know, we will provide you with the assembly file. 
 
 ---
# Script Submission

You are required to submit both of your scripts to the shared __Dropbox folder__ of this course. Your submission must include:

1. __Sufficient__ documentation on how to run the script 
2. Written comments that are __detailed__ enough to understand your scripts

Good luck!
