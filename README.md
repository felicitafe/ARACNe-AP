# ARACNe-AP
ARACNe-AP trial with the test dataset provided in the main repository

# get the repository
	wget https://github.com/califano-lab/ARACNe-AP/archive/refs/heads/master.zip

#look inside
	ls
	master.zip  

	unzip master.zip
	ls
	ARACNe-AP-master  master.zip
	cd ARACNe-AP-master/
 	ls
	aracne  build.xml  common  LICENSE.md  lib  README.md  test



	ant main


	main:
	BUILD SUCCESSFUL
	Total time: 24 seconds
	
	ls
	aracne  bin  build.xml  common  dist  docs  LICENSE.md  lib  README.md  test

# run the first command in order to obtain MI treshold
	java -Xmx5G -jar dist/aracne.jar -e test/matrix.txt  -o outputFolder --tfs test/tfs.txt --pvalue 1E-8 --seed 1 --calculateThreshold
	Finding threshold for 200 samples
	Parameters for fitted threshold function: [0.12173630651920428, 6.225412313429598E-6]
	MI threshold: 0.14343244938161612
