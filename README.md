# Kraken2Tutorial
--------------------------------------------------------
Kraken 2 Installation
--------------------------------------------------------
1. Clone the Kraken 2 in your own directory:
  git clone https://github.com/DerrickWood/kraken2
2. Go to the directory you cloned Kraken2, export the path and install:
	cd kraken2
	export KRAKEN_DIR=${HOME}/kraken2
  PATH=$PATH:</path/to/kraken2 folder>
  ./install_kraken.sh ${KRAKEN_DIR}

--------------------------------------------------------  
Download the Kraken 2 Database
--------------------------------------------------------
3. Downloading the pre-build “minikraken” database from the Kraken2 website that can be used to assign the taxonomic labels to sequences
    wget ftp://ftp.ccb.jhu.edu/pub/data/kraken2_dbs/minikraken2_v2_8GB_201904_UPDATE.tgz
4. Extract the archive content
	  tar -xvzf minikraken2_v2_8GB.tgz
    
--------------------------------------------------------
Download the Datasets need to be classified 
--------------------------------------------------------
5. Download or Create a dataset need to be classified
    wget http://compbio.massey.ac.nz/data/203341/trimmed.tar.gz
6. Extract the archive content
	  tar -xvzf trimmed.tar.gz
    
--------------------------------------------------------
Run Kraken2
--------------------------------------------------------
7. cd kraken2
8. Ensure Kraken 2 folder is in the Path. Use the below command to add to path:   PATH=$PATH:/mnt/HA/groups/rosenclassGrp/Kraken_tutorial/kraken2
9. Running the classifier--                                                                                      
  kraken2 --use-names --threads 4 --db  </path/to/database> --fastq-input --report evolved-6 --paired  <path/to/seqfile1>  <path/to/seqfile2> <outputfilename.kraken>

---------------------------------------------------------
Using Kraken 2 
---------------------------------------------------------
1. To classify a set of sequences use the command :  kraken2 --db $dbname seqs.fa
2. Options provided by Kraken2 :
-Multithreading - 
  Usage : --threads num
-Quick Operation - Stops classification after first database hit instead of searching all l-mers in a sequence. 
  Usage: --quick
-Sequence filtering - Classified and unclassified data can be sent to a file for processing.              
  Usage : --classified-out /--unclassified-out 
-Output redirection - Redirecting the output to a file. 
  Usage: --output <filename>
-FASTQ input - Specify the fastq option if input file is in FASTQ format. 
  Usage: --fastq-input
-Compressed input - Kraken can also handle compressed file formats.                                          
  Usage: --gzip-compressed/--bzip2-compressed
-Paired reads - Kraken2 is capable of handling paired read data. Rather than concatenating, provide this option to process noth files     Usage: --paired </filename1> </filename2>

