# ARACNe-AP
ARACNe-AP trial with the test dataset provided in the main repository



MI threshold estimation. This preprocessing step identifies a significance threshold of MI values from the GEPs provided. The threshold depends on the number of samples provided in the input.

Bootstrapping/MI network reconstruction. In this phase MI networks are reconstructed for randomly sampled GEP. For N such bootstraps of the data N MI networks are generated. The calculation of the networks involves three steps: (a) Compute MI for every TF/Target pair after rank-transformation of the GEPs. (b) Removal of non-statistically significant connections using the MI threshold. (c) Removal of indirect interactions by applying a Data Processing Inequality tolerance filter (DPI, Margolin et al., 2006).

Building consensus network. A consensus network is computed by estimating the statistical significance of the number of times a specific edge is detected across all bootstrap runs, based on a Poisson distribution. Only significant pairs are kept (P < 0.05, Bonferroni corrected).




get the repository
	wget https://github.com/califano-lab/ARACNe-AP/archive/refs/heads/master.zip

Look inside
	ls
	master.zip  

	unzip master.zip
	ls
	ARACNe-AP-master  master.zip
	cd ARACNe-AP-master/
 	ls
	aracne  build.xml  common  LICENSE.md  lib  README.md  test



	ant main

First look what we have
	
	ls
	aracne  bin  build.xml  common  dist  docs  LICENSE.md  lib  README.md  test

run the first command in order to obtain MI (mutual informartion) treshold with a fixed seed
	
	java -Xmx5G -jar dist/aracne.jar -e test/matrix.txt  -o outputFolder --tfs test/tfs.txt --pvalue 1E-8 --seed 1 --calculateThreshold
	Finding threshold for 200 samples
	Parameters for fitted threshold function: [0.12173630651920428, 6.225412313429598E-6]
	MI threshold: 0.14343244938161612


Run ARACNe on a single bootstrap

	java -Xmx5G -jar dist/aracne.jar -e test/matrix.txt  -o outputFolder --tfs test/tfs.txt --pvalue 1E-8 --seed 1
	
	
Run 100 reproducible bootstraps

	(unix) for i in {1..100}; do java -Xmx5G -jar dist/aracne.jar -e test/matrix.txt  -o outputFolder --tfs test/tfs.txt --pvalue 1E-8 --seed $i; done
	
	
	
	java -Xmx5G -jar dist/aracne.jar -o outputFolder --consolidate


	java -Xmx5G -jar dist/aracne.jar -e test/matrix.txt  -o outputFolder --tfs test/tfs.txt --pvalue 1E-8 --seed 1 --nobootstrap --nodpi
