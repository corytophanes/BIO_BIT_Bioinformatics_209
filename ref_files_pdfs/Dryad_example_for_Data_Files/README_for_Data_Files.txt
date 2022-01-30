The folder contains files needed perform the analysis described in “Resistance Gene Carriage Predicts Growth of Natural and Clinical Escherichia coli Isolates in the Absence of Antibiotics”. 

As well as the data contained here, several data sets from a previous paper are used. This paper is titled "Associations among Antibiotic and Phage Resistance Phenotypes in Natural and Clinical Escherichia coli Isolates", for which the data are freely available at https://doi.org/10.5061/dryad.gj318.



A brief description of each file is given below.
===========================================================

Growth_Curves.csv

This file contains the raw growth data which was used to fit the Gompertz growth curves. The column headings are:
	
	Master-Which of the two frozen master plates was used to inoculate the overnight culture which inoculated this assay plate.

	Sub.plate-Which of the 2 plates inoculated by the master plate this is. Thus there are 4 replicates.

	Treatment-Which of the 3 environmental conditions this growth was for.

	Strain-Which strain the measurement came from. Those marked as blank had no strain inoculated. Blanks have not been subtracted, there was a single blank on each plate.

	OD-Optical density measured at 595nm.

	Read-An integer value for which read this is, takes values of 1-41.

	Time-The exact time (relative to the start of the growth experiment) that the read was taken in hours, shown as a fraction (e.g. 4.5 is 4Hrs30Mins).

____________________
Growth_Parameters.csv

This file gives the growth parameters taken from the Gompertz model fitted with SSGompertz, as well as the new transformed parameters. This file does not contain the growth parameters for rare growth curves where the inflection point (and thus the maximum growth rate) occurred outside the period of study (first 21 hours of growth), or where after removing these curves we did not have at least 2 independent growth curves. The column headings are:

	Strain-Which strain the measurement came from. 

	Treatment-Which of the 3 environmental conditions this growth was for.

	Master-Which of the two frozen mater plates was used to inoculate the overnight culture which inoculated this assay plate.

	Sub.Plate-Which of the 2 plates inoculated by the master plate this is. Thus there are 4 replicates for most entries.

	A-Asymptote of the SSGompertz fit

	b2-Offset parameter of the SSGompertz fit

	b3-Scale parameter of the SSGompertz fit.

	Sigma-Residual standard deviation of the fitted model

	AEst- Parameter used in final analysis, the value of the model at t=21, usually close to A.

	Rate- The rate of growth calculated as:  -log(b3)

	Infl- The inflection point calculated as:  log(b2)/-log(b3) 

	Max.Rate-Parameter used in the final analysis. The maximum population growth rate, which occurs at the inflection point. Calculated as: A*Rate/exp(1)

______________________________________________

ARG_Raw.csv

This is a data table of the output of running BLASTn with the contigs of the draft genome assemblies of the isolates against the ResFinder database (nucleotide). The column headings mostly correspond to standard blast outputs but are outlined below:

	Strain-Which strain genome the hit was.

	Contig-Most genomes are draft assemblies so there are multiple segments (here called nodes), this shows which node the hit occurred in.

	ARG- which antibiotic resistance gene in the query matched the sequence.

	Per.ID- Percentage identity.

	Length- Length of the matching region

	MiMa- Number of mismatches 

	Gap- Total length of gaps

	C.Start & C.End- Start and end of the matching region on the contig

	A.Start & A.End- Start and end of the matching region on the query

	E. value- Significance value for the hit, calculated within strain.

	Bit.Score- overall score for the strength of the Hit. For overlapping hits, only the highest bit score was retained.

__________________________________
ARG_Final.csv

A matrix of presence (1) or absence (0) of 12 antibiotic resistance genes grouped at the level of gene family. In this table short hits have been filtered out, and then entries have been grouped into gene families.  Rows represent the isolates while columns represent the genes.

__________________________________
MBRG_Raw.csv

A data table with rows corresponding to hits using blastx against the BacMet experimentally verified database of metal and biocide resistance genes. The contigs of the draft assemblies for the isolates were used to query the BacMet database. The column headings mostly correspond to standard blast outputs outlined in the entry for ARG_raw.csv. In addition this table includes:

	Per.Pos-The percentage of amino acids in the hit which had a positive score according to the BLOSUM62 matrix, indicating that the amino acid is the same OR conserved.

___________________________________
MBRG_Final.csv

A matrix of presence(1) or absence (0) of 25 metal and biocide resistance genes grouped at the level of operons (see text). In this table overlapping hits and short hits have been filtered out, and only entries where the gene is found in less than 80 of the isolates are retained.

___________________________________
Genome_lengths.csv

A table showing the length of the genomes of the isolates, calculated by summing the length of all the contigs in the draft genomes. Column headings are:

	Strain-Which strain the entry is for

	Length-The length of the genome in base pairs.



=================================================

The following data files are also required for analysis but found in the following dryad file https://doi.org/10.5061/dryad.gj318 along with more details.

Processed_Data.csv- File containing the antibiotic resistance phenotype data

Plasmid_Content.csv- File containing a blast hits from plasmidFinder.

cgMLST_Rooted_Tree.tre- A core genome MLST tree for the phylogenetic relationship between strains.

