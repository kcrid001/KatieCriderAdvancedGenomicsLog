# Katie Crider's Advanced Genomics Log
## Spring 2021

## Day 02 Exercises: 1/22/21
``` sh
#exercises day02:

#1- Logon to the cluster @turing.hpc.odu.edu
(base) Katies-MacBook-Air-4:~ katiecrider$ ssh kcrid001@turing.hpc.odu.edu             
[kcrid001@turing1 ~]$ cd /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider

#2- Make a directory in your course workspace called data
[kcrid001@turing1 katiecrider]$ mkdir data

#3- Make a directory called exercises in your data directory
[kcrid001@turing1 katiecrider]$ cd data
[kcrid001@turing1 data]$ mkdir exercises
[kcrid001@turing1 data]$ cd exercises

#4- execute a pwd command and start a log of your commands with a header for today's date in your README.md github logfile in your workspace
[kcrid001@turing1 exercises]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/exercises

#5- cp the Exercise2.fasta.gz and Exercise2.fastq.tar.gz files into your exercises directory from the /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day02 directory
[kcrid001@turing1 exercises]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day02/Exercise2.fast* ./
[kcrid001@turing1 exercises]$ ls
Exercise2.fasta.gz  Exercise2.fastq.tar.gz

#6- unzip and untar the files
[kcrid001@turing1 exercises]$ gunzip Exercise2.fasta.gz
[kcrid001@turing1 exercises]$ ls
Exercise2.fasta  Exercise2.fastq.tar.gz
[kcrid001@turing1 exercises]$ tar -zxvf Exercise2.fastq.tar.gz
Exercise2.fastq
[kcrid001@turing1 exercises]$ ls
Exercise2.fasta  Exercise2.fastq  Exercise2.fastq.tar.gz
[kcrid001@turing1 exercises]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/exercises

#7- add these commands to your notebook file
Done!

#8- calculate how many sequences are in each file and add these results to your notebook file
[kcrid001@turing1 exercises]$ head -1 Exercise2.fasta
>scaffold10078|size20675
[kcrid001@turing1 exercises]$ grep -c \> Exercise2.fasta
138
[kcrid001@turing1 exercises]$ head -4 Exercise2.fastq
@HS3:541:HAYTUADXX:1:1101:1297:1938 1:N:0:AGTTCC
NCGGTGACAGGATTTTCAGGGCAGGAGGGACATTCGGGAAGGGGGAGGGAGATAAAAGAGGCAA
+
#1=DBDDFHHHHHJJJIJJJJJJJJIHJJIIIIJJJJJGIIJJJJAHFDBD?CDDDDDDDDDDD
[kcrid001@turing1 exercises]$ wc -l Exercise2.fastq
245216 Exercise2.fastq
[kcrid001@turing1 exercises]$ echo 245216/4 | bc
61304
[kcrid001@turing1 exercises]$ grep -c "@HS3:541" Exercise2.fastq
61304

#9 - cp the avg_cov_len_fasta_advbioinf.py from the /cm/shared/courses/dbarshis/21AdvGenomics/scripts directory into your class scripts directory
[kcrid001@turing1 exercises]$ cd ../../
[kcrid001@turing1 katiecrider]$ cd scripts
[kcrid001@turing1 scripts]$ cp /cm/shared/courses/dbarshis/21AdvGenomics//scripts/avg_cov_len_fasta_advbioinf.py ./ 

#10- start an interactive compute session and re-navigate to your exercises directory
I had trouble doing this with Turing so I switched over to Wahab

[kcrid001@turing1 katiecrider]$ exit
logout
Connection to turing.hpc.odu.edu closed.
(base) Katies-MacBook-Air-4:~ katiecrider$ ssh kcrid001@wahab.hpc.odu.edu
wahab-01:~> cd /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/
wahab-01:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider> salloc
salloc: Pending job allocation 133738
salloc: job 133738 queued and waiting for resources
salloc: job 133738 has been allocated resources
salloc: Granted job allocation 133738
This session will be terminated in 7 days. If your application requires
a longer excution time, please use command "salloc -t N-0" where N is the
number of days that you need.

#11- run the avg_cov_len_fasta_DJB.py script on your Exercise2.fasta file by typing the path to the script followed by the Exercise2.fasta file name
e2-w6420b-01:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider> cd data/exercises/
e2-w6420b-01:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/exercises> ../../scripts/avg_cov_len_fasta_advbioinf.py Exercise2.fasta
The total number of sequences is 138
The average sequence length is 126640
The total number of bases is 17476447
The minimum sequence length is 1122
The maximum sequence length is 562680
The N50 is 187037
Median Length = 92612
contigs < 150bp = 0
contigs >= 500bp = 138
contigs >= 1000bp = 138
contigs >= 2000bp = 135

#12- did you add all these entries to your notebook file, including the results of the script?
Yes

#13- push your notebook file to your github page
(base) Katies-MacBook-Air-4:KatieCriderAdvancedGenomicsLog katiecrider$ git add README.md
(base) Katies-MacBook-Air-4:KatieCriderAdvancedGenomicsLog katiecrider$ git commit -m 'updating notebook with day02 exercises'
(base) Katies-MacBook-Air-4:KatieCriderAdvancedGenomicsLog katiecrider$ git push -u origin main

```


## Day 03 Exercises/Day 2 HW: 1/27/21
``` sh
#exercises day03 /Day02HW:

#1 Write an sbatch script to cp the files /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/originalfastqs/ into your own data directory

(base) Katies-MacBook-Air-4:21sp_advgenomics katiecrider$ nano KCridCopyLane04.sh
(base) Katies-MacBook-Air-4:21sp_advgenomics katiecrider$ scp KCridCopyLane04.sh kcrid001@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/KCridCopyLane04.sh
kcrid001@turing.hpc.odu.edu's password: 
KCridCopyLane04.sh                                              100%  325    10.6KB/s   00:00    

[kcrid001@coreV2-25-072 data]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data
[kcrid001@coreV2-25-072 data]$ ls
exercises  KCridCopyLane04.sh

#2 Add the content of your sbatch script to your logfile

[kcrid001@coreV2-25-072 data]$ cat KCridCopyLane04.sh 
#!/bin/bash -l

#SBATCH -o KCridCopyLane04.txt
#SBATCH -n 1
#SBATCH --mail-user=kcrid001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=KCridCopyLane04


cp /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/originalfastqs/HADB04-* /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data


#3 submit the slurm script (sbatch scripname.sh) and verify that it's working (by squeue -u yourusername multiple times and checking the destination directory to make sure the files are being created)

[kcrid001@coreV2-25-072 data]$ sbatch KCridCopyLane04.sh 
Submitted batch job 9270446
[kcrid001@coreV2-25-072 data]$ squeue -u kcrid001
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON) 
           9270424      main       sh kcrid001  R      46:39      1 coreV2-25-072 
           9270446      main KCridCop kcrid001  R      10:45      1 coreV2-25-072 
#4 Make sure this is all documented on your github notebook
  #Done

#5 Write a sbatch script to gunzip all the fastq.gz files

[kcrid001@coreV2-25-072 data]$ nano KCridGunzipLane04.sh
[kcrid001@coreV2-25-072 data]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data
[kcrid001@coreV2-25-072 data]$ cat KCridGunzipLane04.sh
#!/bin/bash -l

#SBATCH -o KCridGunzipLane04.txt
#SBATCH -n 1
#SBATCH --mail-user=kcrid001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=KCridGunzipLane04

gunzip *.fastq.gz

[kcrid001@coreV2-25-072 data]$ sbatch KCridGunzipLane04.sh 
Submitted batch job 9270468
[kcrid001@coreV2-25-072 data]$ squeue -u kcrid001
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON) 
           9270424      main       sh kcrid001  R      57:21      1 coreV2-25-072 
           9270468      main KCridGun kcrid001  R       0:34      1 coreV2-25-072 
[kcrid001@coreV2-25-072 data]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data
[kcrid001@coreV2-25-072 data]$ ls
exercises                          HADB04-J_S74_L005_R1_001.fastq.gz
HADB04-A_S65_L005_R1_001.fastq     HADB04-K_S75_L005_R1_001.fastq.gz
HADB04-A_S65_L005_R1_001.fastq.gz  HADB04-L_S76_L005_R1_001.fastq.gz
HADB04-B_S66_L005_R1_001.fastq.gz  HADB04-M_S77_L005_R1_001.fastq.gz
HADB04-C_S67_L005_R1_001.fastq.gz  HADB04-N_S78_L005_R1_001.fastq.gz
HADB04-D_S68_L005_R1_001.fastq.gz  HADB04-O_S79_L005_R1_001.fastq.gz
HADB04-E_S69_L005_R1_001.fastq.gz  HADB04-P_S80_L005_R1_001.fastq.gz
HADB04-F_S70_L005_R1_001.fastq.gz  KCridCopyLane04.sh
HADB04-G_S71_L005_R1_001.fastq.gz  KCridCopyLane04.txt
HADB04-H_S72_L005_R1_001.fastq.gz  KCridGunzipLane04.sh
HADB04-I_S73_L005_R1_001.fastq.gz  KCridGunzipLane04.txt
[kcrid001@coreV2-25-072 data]$ ls
exercises                       HADB04-G_S71_L005_R1_001.fastq  HADB04-N_S78_L005_R1_001.fastq
HADB04-A_S65_L005_R1_001.fastq  HADB04-H_S72_L005_R1_001.fastq  HADB04-O_S79_L005_R1_001.fastq
HADB04-B_S66_L005_R1_001.fastq  HADB04-I_S73_L005_R1_001.fastq  HADB04-P_S80_L005_R1_001.fastq
HADB04-C_S67_L005_R1_001.fastq  HADB04-J_S74_L005_R1_001.fastq  KCridCopyLane04.sh
HADB04-D_S68_L005_R1_001.fastq  HADB04-K_S75_L005_R1_001.fastq  KCridCopyLane04.txt
HADB04-E_S69_L005_R1_001.fastq  HADB04-L_S76_L005_R1_001.fastq  KCridGunzipLane04.sh
HADB04-F_S70_L005_R1_001.fastq  HADB04-M_S77_L005_R1_001.fastq  KCridGunzipLane04.txt

```



## Day 03 HW: 1/28/21
``` sh
#HW day03:

#1. cp the /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day03 directory (and files) to your sandbox

[kcrid001@turing1 katiecrider]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider
[kcrid001@turing1 katiecrider]$ cp -r /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day03/ ./
[kcrid001@turing1 katiecrider]$ ls
data  day03  groundrules.txt  kcrid_exercise1.txt  scripts


#2. mkdir a fastq directory in your data directory and mv all the .fastq files into this directory

[kcrid001@turing1 katiecrider]$ cd data
[kcrid001@turing1 data]$ ls
exercises                       HADB04-G_S71_L005_R1_001.fastq  HADB04-N_S78_L005_R1_001.fastq
HADB04-A_S65_L005_R1_001.fastq  HADB04-H_S72_L005_R1_001.fastq  HADB04-O_S79_L005_R1_001.fastq
HADB04-B_S66_L005_R1_001.fastq  HADB04-I_S73_L005_R1_001.fastq  HADB04-P_S80_L005_R1_001.fastq
HADB04-C_S67_L005_R1_001.fastq  HADB04-J_S74_L005_R1_001.fastq  KCridCopyLane04.sh
HADB04-D_S68_L005_R1_001.fastq  HADB04-K_S75_L005_R1_001.fastq  KCridCopyLane04.txt
HADB04-E_S69_L005_R1_001.fastq  HADB04-L_S76_L005_R1_001.fastq  KCridGunzipLane04.sh
HADB04-F_S70_L005_R1_001.fastq  HADB04-M_S77_L005_R1_001.fastq  KCridGunzipLane04.txt
[kcrid001@turing1 data]$ mkdir fastq
[kcrid001@turing1 data]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data
[kcrid001@turing1 data]$ mv *.fastq ./fastq/
[kcrid001@turing1 data]$ ls
exercises  fastq  KCridCopyLane04.sh  KCridCopyLane04.txt  KCridGunzipLane04.sh  KCridGunzipLane04.txt
[kcrid001@turing1 data]$ cd fastq
[kcrid001@turing1 fastq]$ ls
HADB04-A_S65_L005_R1_001.fastq  HADB04-G_S71_L005_R1_001.fastq  HADB04-M_S77_L005_R1_001.fastq
HADB04-B_S66_L005_R1_001.fastq  HADB04-H_S72_L005_R1_001.fastq  HADB04-N_S78_L005_R1_001.fastq
HADB04-C_S67_L005_R1_001.fastq  HADB04-I_S73_L005_R1_001.fastq  HADB04-O_S79_L005_R1_001.fastq
HADB04-D_S68_L005_R1_001.fastq  HADB04-J_S74_L005_R1_001.fastq  HADB04-P_S80_L005_R1_001.fastq
HADB04-E_S69_L005_R1_001.fastq  HADB04-K_S75_L005_R1_001.fastq
HADB04-F_S70_L005_R1_001.fastq  HADB04-L_S76_L005_R1_001.fastq


#3. cp the renamingtable_complete.txt from the day03 directory into your fastq directory and the /cm/shared/courses/dbarshis/21AdvGenomics/scripts/renamer_advbioinf.py script into your sandbox scripts folder and less the new script and check out the usage statement

[kcrid001@turing1 fastq]$ cd ../
[kcrid001@turing1 data]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data
[kcrid001@turing1 data]$ cp ../day03/renamingtable_complete.txt ./fastq/
[kcrid001@turing1 data]$ cd fastq
[kcrid001@turing1 fastq]$ ls
HADB04-A_S65_L005_R1_001.fastq  HADB04-G_S71_L005_R1_001.fastq  HADB04-M_S77_L005_R1_001.fastq
HADB04-B_S66_L005_R1_001.fastq  HADB04-H_S72_L005_R1_001.fastq  HADB04-N_S78_L005_R1_001.fastq
HADB04-C_S67_L005_R1_001.fastq  HADB04-I_S73_L005_R1_001.fastq  HADB04-O_S79_L005_R1_001.fastq
HADB04-D_S68_L005_R1_001.fastq  HADB04-J_S74_L005_R1_001.fastq  HADB04-P_S80_L005_R1_001.fastq
HADB04-E_S69_L005_R1_001.fastq  HADB04-K_S75_L005_R1_001.fastq  renamingtable_complete.txt
HADB04-F_S70_L005_R1_001.fastq  HADB04-L_S76_L005_R1_001.fasq


[kcrid001@turing1 scripts]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/scripts
[kcrid001@turing1 scripts]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/scripts/renamer_advbioinf.py ./
[kcrid001@turing1 scripts]$ ls
avg_cov_len_fasta_advbioinf.py  renamer_advbioinf.py

[kcrid001@turing1 scripts]$ head renamer_advbioinf.py 
#!/usr/bin/env python
####usage renamer.py renamingtable
#### this script take the entries in the first column of table and renames (mv's) them to files with the names in the second column
import sys
import os

fin=open(sys.argv[1],'r')
linecount=0
for line in fin:
	linecount+=1


#4. run the renamer_advbioinf.py script in your fastq folder using the renamingtable_complete.txt as practice and verify the output to the screen by hand

[kcrid001@turing1 scripts]$ cd ../data/fastq/
[kcrid001@turing1 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq
[kcrid001@turing1 fastq]$ ../../scripts/renamer_advbioinf.py renamingtable_complete.txt
mv HADB01-A_S17_L002_R1_001.fastq VA_W_01_14.fastq
mv HADB01-B_S18_L002_R1_001.fastq VA_B_01_14.fastq
mv HADB01-C_S19_L002_R1_001.fastq RI_W_01_14.fastq
mv HADB01-D_S20_L002_R1_001.fastq RI_B_01_14.fastq
mv HADB01-E_S21_L002_R1_001.fastq VA_W_01_22.fastq
mv HADB01-F_S22_L002_R1_001.fastq VA_B_01_22.fastq
mv HADB01-G_S23_L002_R1_001.fastq RI_W_01_22.fastq
mv HADB01-H_S24_L002_R1_001.fastq RI_B_01_22.fastq
mv HADB01-I_S25_L002_R1_001.fastq VA_W_01_18.fastq
mv HADB01-J_S26_L002_R1_001.fastq VA_B_01_18.fastq
mv HADB01-K_S27_L002_R1_001.fastq RI_W_01_18.fastq
mv HADB01-L_S28_L002_R1_001.fastq RI_B_01_18.fastq
mv HADB01-M_S29_L002_R1_001.fastq VA_W_08_SNP.fastq
mv HADB01-N_S30_L002_R1_001.fastq VA_B_09_SNP.fastq
mv HADB01-O_S31_L002_R1_001.fastq RI_W_08_SNP.fastq
mv HADB01-P_S32_L002_R1_001.fastq RI_B_08_SNP.fastq
mv HADB02-A_S33_L003_R1_001.fastq VA_W_02_14.fastq
mv HADB02-B_S34_L003_R1_001.fastq VA_B_02_14.fastq
mv HADB02-C_S35_L003_R1_001.fastq RI_W_02_14.fastq
mv HADB02-D_S36_L003_R1_001.fastq RI_B_02_14.fastq
mv HADB02-E_S37_L003_R1_001.fastq VA_W_02_22.fastq
mv HADB02-F_S38_L003_R1_001.fastq VA_B_02_22.fastq
mv HADB02-G_S39_L003_R1_001.fastq RI_W_02_22.fastq
mv HADB02-H_S40_L003_R1_001.fastq RI_B_02_22.fastq
mv HADB02-I_S41_L003_R1_001.fastq VA_W_02_18.fastq
mv HADB02-J_S42_L003_R1_001.fastq VA_B_02_18.fastq
mv HADB02-K_S43_L003_R1_001.fastq RI_W_02_18.fastq
mv HADB02-L_S44_L003_R1_001.fastq RI_B_02_18.fastq
mv HADB02-M_S45_L003_R1_001.fastq VA_W_09_SNP.fastq
mv HADB02-N_S46_L003_R1_001.fastq VA_B_08_SNP.fastq
mv HADB02-O_S47_L003_R1_001.fastq RI_W_09_SNP.fastq
mv HADB02-P_S48_L003_R1_001.fastq RI_B_09_SNP.fastq
mv HADB03-A_S49_L004_R1_001.fastq VA_W_03_14.fastq
mv HADB03-B_S50_L004_R1_001.fastq VA_B_03_14.fastq
mv HADB03-C_S51_L004_R1_001.fastq RI_W_03_14.fastq
mv HADB03-D_S52_L004_R1_001.fastq RI_B_03_14.fastq
mv HADB03-E_S53_L004_R1_001.fastq VA_W_03_22.fastq
mv HADB03-F_S54_L004_R1_001.fastq VA_B_03_22.fastq
mv HADB03-G_S55_L004_R1_001.fastq RI_W_03_22.fastq
mv HADB03-H_S56_L004_R1_001.fastq RI_B_03_22.fastq
mv HADB03-I_S57_L004_R1_001.fastq VA_W_03_18.fastq
mv HADB03-J_S58_L004_R1_001.fastq VA_B_03_18.fastq
mv HADB03-K_S59_L004_R1_001.fastq RI_W_03_18.fastq
mv HADB03-L_S60_L004_R1_001.fastq RI_B_03_18.fastq
mv HADB03-M_S61_L004_R1_001.fastq VA_W_10_SNP.fastq
mv HADB03-N_S62_L004_R1_001.fastq VA_B_10_SNP.fastq
mv HADB03-O_S63_L004_R1_001.fastq RI_W_10_SNP.fastq
mv HADB03-P_S64_L004_R1_001.fastq RI_B_10_SNP.fastq
mv HADB04-A_S65_L005_R1_001.fastq VA_W_04_14.fastq
mv HADB04-B_S66_L005_R1_001.fastq VA_B_04_14.fastq
mv HADB04-C_S67_L005_R1_001.fastq RI_W_04_14.fastq
mv HADB04-D_S68_L005_R1_001.fastq RI_B_04_14.fastq
mv HADB04-E_S69_L005_R1_001.fastq VA_W_04_22.fastq
mv HADB04-F_S70_L005_R1_001.fastq VA_B_04_22.fastq
mv HADB04-G_S71_L005_R1_001.fastq RI_W_04_22.fastq
mv HADB04-H_S72_L005_R1_001.fastq RI_B_04_22.fastq
mv HADB04-I_S73_L005_R1_001.fastq VA_W_04_18.fastq
mv HADB04-J_S74_L005_R1_001.fastq VA_B_04_18.fastq
mv HADB04-K_S75_L005_R1_001.fastq RI_W_04_18.fastq
mv HADB04-L_S76_L005_R1_001.fastq RI_B_04_18.fastq
mv HADB04-M_S77_L005_R1_001.fastq VA_W_05_14.fastq
mv HADB04-N_S78_L005_R1_001.fastq VA_B_05_14.fastq
mv HADB04-O_S79_L005_R1_001.fastq RI_W_05_14.fastq
mv HADB04-P_S80_L005_R1_001.fastq RI_B_05_14.fastq
mv HADB05-A_S81_L006_R1_001.fastq VA_W_05_22.fastq
mv HADB05-B_S82_L006_R1_001.fastq VA_B_05_22.fastq
mv HADB05-C_S83_L006_R1_001.fastq RI_W_05_22.fastq
mv HADB05-D_S84_L006_R1_001.fastq RI_B_05_22.fastq
mv HADB05-E_S85_L006_R1_001.fastq VA_W_05_18.fastq
mv HADB05-F_S86_L006_R1_001.fastq VA_B_05_18.fastq
mv HADB05-G_S87_L006_R1_001.fastq RI_W_05_18.fastq
mv HADB05-H_S88_L006_R1_001.fastq RI_B_05_18.fastq
mv HADB05-I_S89_L006_R1_001.fastq VA_W_06_14.fastq
mv HADB05-J_S90_L006_R1_001.fastq VA_B_06_14.fastq
mv HADB05-K_S91_L006_R1_001.fastq RI_W_06_14.fastq
mv HADB05-L_S92_L006_R1_001.fastq RI_B_06_14.fastq
mv HADB05-M_S93_L006_R1_001.fastq VA_W_06_22.fastq
mv HADB05-N_S94_L006_R1_001.fastq VA_B_06_22.fastq
mv HADB05-O_S95_L006_R1_001.fastq RI_W_06_22.fastq
mv HADB05-P_S96_L006_R1_001.fastq RI_B_06_22.fastq
mv HADB06-A_S97_L007_R1_001.fastq VA_W_06_18.fastq
mv HADB06-B_S98_L007_R1_001.fastq VA_B_06_18.fastq
mv HADB06-C_S99_L007_R1_001.fastq RI_W_06_18.fastq
mv HADB06-D_S100_L007_R1_001.fastq RI_B_06_18.fastq
mv HADB06-E_S101_L007_R1_001.fastq VA_W_07_14.fastq
mv HADB06-F_S102_L007_R1_001.fastq VA_B_07_14.fastq
mv HADB06-G_S103_L007_R1_001.fastq RI_W_07_14.fastq
mv HADB06-H_S104_L007_R1_001.fastq RI_B_07_14.fastq
mv HADB06-I_S105_L007_R1_001.fastq VA_W_07_22.fastq
mv HADB06-J_S106_L007_R1_001.fastq VA_B_07_22.fastq
mv HADB06-K_S107_L007_R1_001.fastq RI_W_07_22.fastq
mv HADB06-L_S108_L007_R1_001.fastq RI_B_07_22.fastq
mv HADB06-M_S109_L007_R1_001.fastq VA_W_07_18.fastq
mv HADB06-N_S110_L007_R1_001.fastq VA_B_07_18.fastq
mv HADB06-O_S111_L007_R1_001.fastq RI_W_07_18.fastq
mv HADB06-P_S112_L007_R1_001.fastq RI_B_07_18.fastq




#5. Uncomment the last line of the renaming script in your scripts folder that starts with os.popen and comment out the next to last line that starts with print

[kcrid001@turing1 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq
[kcrid001@turing1 fastq]$ nano ../../scripts/renamer_advbioinf.py
[kcrid001@turing1 fastq]$ cat ../../scripts/renamer_advbioinf.py 
#!/usr/bin/env python
####usage renamer.py renamingtable
#### this script take the entries in the first column of table and renames (mv's) them to files with the names in the second column
import sys
import os

fin=open(sys.argv[1],'r')
linecount=0
for line in fin:
	linecount+=1
	if linecount>=2:
		cols=line.rstrip().split('\t')
#		print 'mv %s %s' %(cols[0], cols[1])
		os.popen('mv %s %s' %(cols[0], cols[1]))


#6. write a sbatch script and submit it to rename all the .fastq files according to the renaming table using your renamer_advbioinf.py script

[kcrid001@turing1 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq
[kcrid001@turing1 fastq]$ nano KCridRenamer.sh
[kcrid001@turing1 fastq]$ ls
HADB04-A_S65_L005_R1_001.fastq  HADB04-G_S71_L005_R1_001.fastq  HADB04-M_S77_L005_R1_001.fastq
HADB04-B_S66_L005_R1_001.fastq  HADB04-H_S72_L005_R1_001.fastq  HADB04-N_S78_L005_R1_001.fastq
HADB04-C_S67_L005_R1_001.fastq  HADB04-I_S73_L005_R1_001.fastq  HADB04-O_S79_L005_R1_001.fastq
HADB04-D_S68_L005_R1_001.fastq  HADB04-J_S74_L005_R1_001.fastq  HADB04-P_S80_L005_R1_001.fastq
HADB04-E_S69_L005_R1_001.fastq  HADB04-K_S75_L005_R1_001.fastq  KCridRenamer.sh
HADB04-F_S70_L005_R1_001.fastq  HADB04-L_S76_L005_R1_001.fastq  renamingtable_complete.txt
[kcrid001@turing1 fastq]$ cat KCridRenamer.sh 
#!/bin/bash -l

#SBATCH -o KCridRenamer.txt
#SBATCH -n 1
#SBATCH --mail-user=kcrid001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=FastqRename

../../scripts/renamer_advbioinf.py renamingtable_complete.txt

[kcrid001@turing1 fastq]$ sbatch ./KCridRenamer.sh
Submitted batch job 9270863

#7. Make sure this is all documented on your github page
* Yep

#8. The naming convention for the files is as follows:
  * SOURCEPOPULATION_SYMBIOTICSTATE_GENOTYPE_TEMPERATURE.fastq
  * There are 2 sources: Virginia and Rhode Island
  * There are 2 symbiotic states: Brown and White
  
#9. Next, you're going to start the process of adapter clipping and quality trimming all the renamed .fastq files in batches, by lane

#10. cp the script /cm/shared/courses/dbarshis/21AdvGenomics/scripts/Trimclipfilterstatsbatch_advbioinf.py into your scripts directory

[kcrid001@turing1 fastq]$ cd ../
[kcrid001@turing1 data]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data
[kcrid001@turing1 data]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/scripts/Trimclipfilterstatsbatch_advbioinf.py ../scripts/


#11. Less/head the new script and check out the usage statement
[kcrid001@turing1 data]$ head -14 ../scripts/Trimclipfilterstatsbatch_advbioinf.py
#!/usr/bin/env python
# Written by Dan Barshis

import sys, os

########### Usage #############
# Trimclipfilterstatsbatch.py barcodefile.txt anynumberoffastqfiles
# This should be run from within the folder with all of your original .fastqstrim
# Will quality trim multiple SINGLE-END fastq files
# Things to customize for your particular platform:
# qualoffset = 33 Quality score offset
# -t option in qualitytrim (the lower threshold quality score for trimming)
# -l option in qualitytrim and adapterclip (the length threshold for throwing out short reads)


#12. cp the /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day03/adapterlist_advbioinf.txt into the working directory with your fastq files

[kcrid001@turing1 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq
[kcrid001@turing1 fastq]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day03/adapterlist_advbioinf.txt ./
[kcrid001@turing1 fastq]$ ls
adapterlist_advbioinf.txt   RI_B_04_14.fastq  RI_W_04_14.fastq  VA_B_04_14.fastq  VA_W_04_14.fastq
KCridRenamer.sh             RI_B_04_18.fastq  RI_W_04_18.fastq  VA_B_04_18.fastq  VA_W_04_18.fastq
KCridRenamer.txt            RI_B_04_22.fastq  RI_W_04_22.fastq  VA_B_04_22.fastq  VA_W_04_22.fastq
renamingtable_complete.txt  RI_B_05_14.fastq  RI_W_05_14.fastq  VA_B_05_14.fastq  VA_W_05_14.fastq

#13. Make a sbatch script for the Trimclipfilter... script and run it on your fastq files
[kcrid001@turing1 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq
[kcrid001@turing1 fastq]$ nano TestTrimClip.sh
[kcrid001@turing1 fastq]$ cat TestTrimClip.sh
#!/bin/bash -l

#SBATCH -o KCridtestTrimclip.txt
#SBATCH -n 1
#SBATCH --mail-user=kcrid001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=KCridTrimTest

/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/scripts/Trimclipfilterstatsbatch_advbioinf.py adapterlist_advbioinf.txt *.fastq

[kcrid001@turing1 fastq]$ salloc
salloc: Pending job allocation 9271050
salloc: job 9271050 queued and waiting for resources
salloc: job 9271050 has been allocated resources
salloc: Granted job allocation 9271050
[kcrid001@coreV1-22-005 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq
[kcrid001@coreV1-22-005 fastq]$ sbatch TestTrimClip.sh
Submitted batch job 9271051
[kcrid001@coreV1-22-005 fastq]$ squeue -u kcrid001
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON) 
           9271051      main KCridTri kcrid001  R      10:22      1 coreV2-22-007 
           9271050      main       sh kcrid001  R      11:22      1 coreV1-22-005 

#I was confused on if I had to do the FullTrimClip next, because they look like the same thing, but I think the TestTrimClip is working (see list below)

[kcrid001@coreV1-22-005 fastq]$ ls
adapterlist_advbioinf.txt  renamingtable_complete.txt  RI_W_04_14.fastq  trimclipstats.txt  VA_W_04_18.fastq
FullTrimClip.sh            RI_B_04_14_clipped.fastq    RI_W_04_18.fastq  VA_B_04_14.fastq   VA_W_04_22.fastq
KCridFullTrimclip.txt      RI_B_04_14.fastq            RI_W_04_22.fastq  VA_B_04_18.fastq   VA_W_05_14.fastq
KCridRenamer.sh            RI_B_04_18.fastq            RI_W_05_14.fastq  VA_B_04_22.fastq
KCridRenamer.txt           RI_B_04_22.fastq            Testing           VA_B_05_14.fastq
KCridtestTrimclip.txt      RI_B_05_14.fastq            TestTrimClip.sh   VA_W_04_14.fastq

```

## Day 04 HW: 1/29/21
``` sh
#HW Day 04:

#1. Add your trimclipstats.txt output to the full class datafile /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/Fulltrimclipstatstable.txt using the following steps
#1a. run /cm/shared/courses/dbarshis/21AdvGenomics/scripts/Schafran_trimstatstable_advbioinf_clippedtrimmed.py -h to examine usage
[kcrid001@coreV1-22-005 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq
[kcrid001@coreV1-22-005 fastq]$ /cm/shared/courses/dbarshis/21AdvGenomics/scripts/Schafran_trimstatstable_advbioinf_clippedtrimmed.py -h
Written by Peter Schafran pscha005@odu.edu 5-Oct-2015

This script takes a stats output file from fastx_clipper and converts it into a table.

Usage: Schafran_trimstatstable.py [-c, -v, -h] inputfile.txt outputfile.txt

Options (-c and -v must be listed separately to run together):
-h	Display this help message
-c	Use comma delimiter instead of tabs
-v	Verbose mode (print steps to stdout)

#1b. Run the script on your data with the outputfilename YOURNAME_trimclipstatsout.txt
[kcrid001@coreV2-22-007 fastq]$ cd filteringstats
[kcrid001@coreV2-22-007 filteringstats]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq/filteringstats
[kcrid001@coreV2-22-007 filteringstats]$ /cm/shared/courses/dbarshis/21AdvGenomics/scripts/Schafran_trimstatstable_advbioinf_clippedtrimmed.py trimclipstats.txt KCrid_trimclipstatsout.txt

#1c. Add YOURNAME_trimclipstatsout.txt to the class file by running tail -n +2 YOURNAME_trimclipstatsout.txt >> /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/Fulltrimclipstatstable.txt

[kcrid001@coreV2-25-047 filteringstats]$ tail -n +2 KCrid_trimclipstatsout.txt >> /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/Fulltrimclipstatstable.txt


#2. Now we're going to map our reads back to our assembly using the bowtie2 alignment algorithm (starting to follow this pipeline https://github.com/bethsheets/SNPcalling_tutorial)
#3. write a sbatch script to do the following commands in sequence on your _clippedtrimmedfilterd.fastq datafiles from your lane of data
[kcrid001@coreV2-25-047 filteringstats]$ cd ../
[kcrid001@coreV2-25-047 fastq]$ cd QCFastqs/
[kcrid001@coreV2-25-047 QCFastqs]$ ls
RI_B_04_14_clippedtrimmed.fastq  RI_W_04_22_clippedtrimmed.fastq  VA_W_04_14_clippedtrimmed.fastq
RI_B_04_18_clippedtrimmed.fastq  RI_W_05_14_clippedtrimmed.fastq  VA_W_04_18_clippedtrimmed.fastq
RI_B_04_22_clippedtrimmed.fastq  VA_B_04_14_clippedtrimmed.fastq  VA_W_04_22_clippedtrimmed.fastq
RI_B_05_14_clippedtrimmed.fastq  VA_B_04_18_clippedtrimmed.fastq  VA_W_05_14_clippedtrimmed.fastq
RI_W_04_14_clippedtrimmed.fastq  VA_B_04_22_clippedtrimmed.fastq
RI_W_04_18_clippedtrimmed.fastq  VA_B_05_14_clippedtrimmed.fastq
[kcrid001@coreV2-25-047 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq/QCFastqs
[kcrid001@coreV2-25-047 QCFastqs]$ nano bowtiealn.sh
[kcrid001@coreV2-25-047 QCFastqs]$ cat bowtiealn.sh 
#!/bin/bash -l

#SBATCH -o KCridbowtie2.txt
#SBATCH -n 1
#SBATCH --mail-user=kcrid001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=newbowtie

module load bowtie2/2.4
for i in *_clippedtrimmed.fastq; do bowtie2 --rg-id ${i%_clippedtrimmed.fastq} \
--rg SM:${i%_clippedtrimmed.fastq} \
--very-sensitive -x /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/refassembly/Apoc_hostsym -U $i \
> ${i%_clippedtrimmedfilterd.fastq}.sam --no-unal -k 5; done
[kcrid001@coreV2-25-047 QCFastqs]$ sbatch bowtiealn.sh 
Submitted batch job 9271852
[kcrid001@coreV2-25-047 QCFastqs]$ squeue -u kcrid001
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON) 
           9271852      main newbowti kcrid001  R       0:01      1 coreV2-25-005 
           9271848      main       sh kcrid001  R      18:01      1 coreV2-25-047 

#4-Submit and add everything to your logfile
*yep!

## Day05 HW 2/3/21
```sh
##Day05HW

1-Team up with a partner for this one and work only on a combined set of data for your two lanes of sequences

[kcrid001@coreV3-23-050 fastq]$ mkdir KCKCfastq
[kcrid001@coreV3-23-050 fastq]$ ls
filteringstats         KCridRenamer.txt            renamingtable_complete.txt
FullTrimClip.sh        KCridtestTrimclip.txt       Testing
KCKCfastq              KCrid_trimclipstatsout.txt  TestTrimClip.sh
KCridFullTrimclip.txt  originalfastqs
KCridRenamer.sh        QCFastqs
[kcrid001@coreV3-23-050 fastq]$ cd KCKCfastq/
[kcrid001@coreV3-23-050 KCKCfastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq/KCKCfastq

[kcrid001@coreV3-23-050 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq/QCFastqs
[kcrid001@coreV3-23-050 QCFastqs]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq/QCFastqs/*.fastq /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq/KCKCfastq
# we both copied our clippedtrimmed.fastq files to the new KCKCfastq directory (Katie C & Kristina)
[kcrid001@coreV3-23-050 KCKCfastq]$ ls
KCKCTrinitydenovo.sh              VA_B_01_14_clippedtrimmed.fastq
RI_B_01_14_clippedtrimmed.fastq   VA_B_01_18_clippedtrimmed.fastq
RI_B_01_18_clippedtrimmed.fastq   VA_B_01_22_clippedtrimmed.fastq
RI_B_01_22_clippedtrimmed.fastq   VA_B_04_14_clippedtrimmed.fastq
RI_B_04_14_clippedtrimmed.fastq   VA_B_04_18_clippedtrimmed.fastq
RI_B_04_18_clippedtrimmed.fastq   VA_B_04_22_clippedtrimmed.fastq
RI_B_04_22_clippedtrimmed.fastq   VA_B_05_14_clippedtrimmed.fastq
RI_B_05_14_clippedtrimmed.fastq   VA_B_09_SNP_clippedtrimmed.fastq
RI_B_08_SNP_clippedtrimmed.fastq  VA_W_01_14_clippedtrimmed.fastq
RI_W_01_14_clippedtrimmed.fastq   VA_W_01_18_clippedtrimmed.fastq
RI_W_01_18_clippedtrimmed.fastq   VA_W_01_22_clippedtrimmed.fastq
RI_W_01_22_clippedtrimmed.fastq   VA_W_04_14_clippedtrimmed.fastq
RI_W_04_14_clippedtrimmed.fastq   VA_W_04_18_clippedtrimmed.fastq
RI_W_04_18_clippedtrimmed.fastq   VA_W_04_22_clippedtrimmed.fastq
RI_W_04_22_clippedtrimmed.fastq   VA_W_05_14_clippedtrimmed.fastq
RI_W_05_14_clippedtrimmed.fastq   VA_W_08_SNP_clippedtrimmed.fastq
RI_W_08_SNP_clippedtrimmed.fastq
# we have 32 files, 16 for each of us. All files have copied

2-Run the Trinity denovo assembler on your clippedtrimmed.fastq files for your two lanes together
3-Modify the below sbatch script (note the differences in the header compared to the previous one)

[kcrid001@coreV3-23-050 KCKCfastq]$ nano KCKCTrinitydenovo.sh
[kcrid001@coreV3-23-050 KCKCfastq]$ cat KCKCTrinitydenovo.sh 
#!/bin/bash -l

#SBATCH -o KCKCTrinitydenovo.txt
#SBATCH -n 32
#SBATCH -p himem
#SBATCH --mail-user=kcrid001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=KCKCTrinitydenovo

enable_lmod
module load container_env trinity

crun Trinity --seqType fq --max_memory 768G --normalize_reads --single RI_B_04_14_clippedtrimmed.fastq,VA_B_04_14_clippedtrimmed.fastq,RI_B_04_18_clippedtrimmed.fastq,VA_B_04_18_clippedtrimmed.fastq,RI_B_04_22_clippedtrimmed.fastq,VA_B_04_22_clippedtrimmed.fastq,RI_B_05_14_clippedtrimmed.fastq,VA_B_05_14_clippedtrimmed.fastq,RI_W_04_14_clippedtrimmed.fastq,VA_W_04_14_clippedtrimmed.fastq,RI_W_04_18_clippedtrimmed.fastq,VA_W_04_18_clippedtrimmed.fastq,RI_W_04_22_clippedtrimmed.fastq,VA_W_04_22_clippedtrimmed.fastq,RI_W_05_14_clippedtrimmed.fastq,VA_W_05_14_clippedtrimmed.fastq,RI_B_01_14_clippedtrimmed.fastq,RI_B_01_18_clippedtrimmed.fastq,RI_B_01_22_clippedtrimmed.fastq,RI_B_08_SNP_clippedtrimmed.fastq,RI_W_01_14_clippedtrimmed.fastq,RI_W_01_18_clippedtrimmed.fastq,RI_W_01_22_clippedtrimmed.fastq,RI_W_08_SNP_clippedtrimmed.fastq,VA_B_01_14_clippedtrimmed.fastq,VA_B_01_18_clippedtrimmed.fastq,VA_B_01_22_clippedtrimmed.fastq,VA_B_09_SNP_clippedtrimmed.fastq,VA_W_01_14_clippedtrimmed.fastq,VA_W_01_18_clippedtrimmed.fastq,VA_W_01_22_clippedtrimmed.fastq,VA_W_08_SNP_clippedtrimmed.fastq --CPU 32

4-Check https://trinityrnaseq.github.io/ for usage info

5-Submit your trinity script
[kcrid001@coreV3-23-050 KCKCfastq]$ sbatch KCKCTrinitydenovo.sh
Submitted batch job 9272362
[kcrid001@coreV3-23-050 KCKCfastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq/KCKCfastq

```
