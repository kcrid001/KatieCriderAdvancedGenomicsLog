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

## Day06 HW
```sh
#day06HW
####Make sure to add all this to your logfile as you go, including the output from the various scripts/greps/etc.
###Assembly quality assessment (following the first two steps in the recommended trinity assessment protocol from https://github.com/trinityrnaseq/trinityrnaseq/wiki/Transcriptome-Assembly-Quality-Assessment)


#1- start an interactive session via salloc and run the /cm/shared/apps/trinity/2.0.6/util/TrinityStats.pl script on your Trinity.fasta output from your assembly

[kcrid001@turing1 trinity_out_dir]$ salloc
salloc: Pending job allocation 9272857
salloc: job 9272857 queued and waiting for resources
salloc: job 9272857 has been allocated resources
salloc: Granted job allocation 9272857
[kcrid001@coreV2-22-028 trinity_out_dir]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq/KCKCfastq/trinity_out_dir

[kcrid001@coreV2-22-028 trinity_out_dir]$ /cm/shared/apps/trinity/2.0.6/util/TrinityStats.pl Trinity.fasta


################################
## Counts of transcripts, etc.
################################
Total trinity 'genes':	39219
Total trinity transcripts:	41303
Percent GC: 44.54

########################################
Stats based on ALL transcript contigs:
########################################

	Contig N10: 1323
	Contig N20: 783
	Contig N30: 562
	Contig N40: 440
	Contig N50: 364

	Median contig length: 277
	Average contig: 371.08
	Total assembled bases: 15326666


#####################################################
## Stats based on ONLY LONGEST ISOFORM per 'GENE':
#####################################################

	Contig N10: 1094
	Contig N20: 682
	Contig N30: 511
	Contig N40: 410
	Contig N50: 347

	Median contig length: 274
	Average contig: 355.69
	Total assembled bases: 13949619


#2- compare this with the output from avg_cov_len_fasta_advbioinf.py on our class reference assembly (/cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/refassembly/15079_Apoc_hostsym.fasta) and add both to your logfile

[kcrid001@coreV2-22-028 trinity_out_dir]$ /cm/shared/courses/dbarshis/21AdvGenomics/scripts/avg_cov_len_fasta_advbioinf.py Trinity.fasta
The total number of sequences is 41303
The average sequence length is 371
The total number of bases is 15326666
The minimum sequence length is 184
The maximum sequence length is 10771
The N50 is 364
Median Length = 627
contigs < 150bp = 0
contigs >= 500bp = 5936
contigs >= 1000bp = 1364
contigs >= 2000bp = 265


#3- less or head your bowtie2 job output file to look at your alignment statistics and calculate the following from the information:
	a-the mean percent "overall alignment rate"
	b-the mean percent reads "aligned exactly 1 time"
	c-the mean number of reads "aligned exactly 1 time"
	d-the mean percent reads "aligned >1 times"
	
	hint use grep and paste into excel

[kcrid001@coreV2-22-028 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq/QCFastqs
[kcrid001@coreV2-22-028 QCFastqs]$ less KCridbowtie2.txt 
    366410 (2.11%) aligned exactly 1 time
    196159 (1.13%) aligned >1 times
3.25% overall alignment rate
28980402 reads; of these:
  28980402 (100.00%) were unpaired; of these:
    28428026 (98.09%) aligned 0 times
    302622 (1.04%) aligned exactly 1 time
    249754 (0.86%) aligned >1 times
1.91% overall alignment rate
22997803 reads; of these:
  22997803 (100.00%) were unpaired; of these:
    22542136 (98.02%) aligned 0 times
    281735 (1.23%) aligned exactly 1 time
    173932 (0.76%) aligned >1 times
1.98% overall alignment rate
18509735 reads; of these:
  18509735 (100.00%) were unpaired; of these:
    18027510 (97.39%) aligned 0 times
    262310 (1.42%) aligned exactly 1 time
    219915 (1.19%) aligned >1 times
2.61% overall alignment rate
15268908 reads; of these:
  15268908 (100.00%) were unpaired; of these:
    14979814 (98.11%) aligned 0 times
    178865 (1.17%) aligned exactly 1 time
    110229 (0.72%) aligned >1 times
1.89% overall alignment rate


kcrid001@coreV2-22-028 QCFastqs]$ grep "overall alignment rate" KCridbowtie2.txt | cut -d " " -f 1 | cut -d "%" -f 1
2.48
1.70
1.45
2.32
6.81
2.25
2.12
1.85
2.00
2.70
2.36
3.25
1.91
1.98
2.61
1.89
[kcrid001@coreV2-22-028 QCFastqs]$ grep "aligned exactly 1 time" KCridbowtie2.txt | cut -d "(" -f 2 | cut -d "%" -f 1
1.41
1.12
0.85
1.66
1.18
1.26
1.06
1.10
1.10
1.51
1.53
2.11
1.04
1.23
1.42
1.17
[kcrid001@coreV2-22-028 QCFastqs]$ grep "aligned exactly 1 time" KCridbowtie2.txt | cut -d " " -f 5
370715
569956
82036
677289
38461
303192
11115
409225
189559
281489
300187
366410
302622
281735
262310
178865
[kcrid001@coreV2-22-028 QCFastqs]$ grep "aligned >1 times" KCridbowtie2.txt | cut -d "(" -f 2 | cut -d "%" -f 1
1.07
0.58
0.60
0.67
5.63
1.00
1.06
0.74
0.90
1.19
0.83
1.13
0.86
0.76
1.19
0.72

# copy these values to excel, calculate averages as needed
# answers
	# a - 2.48% - the mean percent "overall alignment rate"
	# b - 1.30% - the mean percent reads "aligned exactly 1 time"
	# c - 289072.88 - the mean number of reads "aligned exactly 1 time"
	# d - 1.18% - the mean percent reads "aligned >1 times"


#4- add your statistics as single rows to the shared table /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/alignmentstatstable.txt as tab-delimited text in the following order:
LaneX_yourinitials	b-the mean percent "overall alignment rate"	c-the mean percent reads "aligned exactly 1 time"	d-the mean number of reads "aligned exactly 1 time"	e-the mean percent reads "aligned >1 times"

[kcrid001@coreV2-22-028 QCFastqs]$ nano alignstats.txt
[kcrid001@coreV2-22-028 QCFastqs]$ cat alignstats.txt >> /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/alignmentstatstable.txt
[kcrid001@coreV2-22-028 QCFastqs]$ cat /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/alignmentstatstable.txt
LaneX	overallalignmentrate	percsinglyaligned	numsinglyaligned	percmultiplyaligned
LaneX_djb	2.495714286	1.251428571	247656.7143	1.247142857
LaneX_djb	2.495714286	1.251428571	247656.7143	1.247142857
Lane1AP	5.378125	1.3725	300361.8125	4.005
lane5_sg	2.03%	1.11%	235455.75	0.92%
LaneX_jcw	2.495714286	1.251428571	247656.7143	1.247142857
Lane4_KCrid	2.48	1.30	289072.88	1.18

#5- Data cleanup and archiving:
*a-mv your Trinity.fasta file from your trinity_out_dir to a folder called testassembly in your data directory
	
[kcrid001@turing1 data]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data
[kcrid001@turing1 data]$ mkdir testassembly
[kcrid001@turing1 data]$ ls
exercises  KCridCopyLane04.sh   KCridGunzipLane04.sh   testassembly
fastq      KCridCopyLane04.txt  KCridGunzipLane04.txt
[kcrid001@turing1 trinity_out_dir]$ salloc
salloc: Pending job allocation 9275008
salloc: job 9275008 queued and waiting for resources
salloc: job 9275008 has been allocated resources
salloc: Granted job allocation 9275008
[kcrid001@coreV1-22-016 trinity_out_dir]$ mv /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq/KCKCfastq/trinity_out_dir/Trinity.fasta /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/testassembly

*b-set up a sbatch script to:
		rm -r YOURtrinity_out_dir
		rm -r YOURoriginalfastqs
		rm -r YOURfilteringstats # as long as you've already appended your filteringstats output to the class table as part of homework_day04.txt

[kcrid001@coreV1-22-016 data]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data
[kcrid001@coreV1-22-016 data]$ nano Cleanup.txt
[kcrid001@coreV1-22-016 data]$ cat Cleanup.txt 
#!/bin/bash -l

#SBATCH -o Cleanup.txt
#SBATCH -n 1
#SBATCH --mail-user=kcrid001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=Cleanup

rm -r /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq/KCKCfastq/trinity_out_dir
rm -r /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq/originalfastqs
rm -r /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq/filteringstats

[kcrid001@coreV1-22-016 data]$ sbatch Cleanup.sh 
Submitted batch job 9275062
[kcrid001@coreV1-22-016 data]$ squeue -u kcrid001
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON) 
           9275062      main  Cleanup kcrid001  R       0:07      1 coreV1-22-016 
           9275008      main       sh kcrid001  R      22:37      1 coreV1-22-016 

#6- submit a blast against sprot from your testassembly folder using the following command

[kcrid001@coreV1-22-016 testassembly]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/testassembly
[kcrid001@coreV1-22-016 testassembly]$ ls
Trinity.fasta
[kcrid001@coreV1-22-016 testassembly]$ nano Blast.sh
[kcrid001@coreV1-22-016 testassembly]$ cat Blast.sh 
#!/bin/bash -l

#SBATCH -o Blast.txt
#SBATCH -n 6         
#SBATCH --mail-user=kcrid001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=Blast

enable_lmod
module load container_env blast
blastx -query Trinity.fasta -db /cm/shared/apps/blast/databases/uniprot_sprot_Sep2018 -out blastx.outfmt6 \
        -evalue 1e-20 -num_threads 6 -max_target_seqs 1 -outfmt 6
[kcrid001@coreV1-22-016 testassembly]$ sbatch Blast.sh 
Submitted batch job 9275071
[kcrid001@coreV1-22-016 testassembly]$ squeue -u kcrid001
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON) 
           9275071      main    Blast kcrid001  R       1:53      1 coreV3-23-027 
           9275062      main  Cleanup kcrid001  R       6:23      1 coreV1-22-016 
           9275008      main       sh kcrid001  R      28:53      1 coreV1-22-016 

###Exploring our SAM files, check out http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#sam-output for bowtie2 specific output and http://bio-bwa.sourceforge.net/bwa.shtml#4 for general SAM output

#7- head one of your .sam files to look at the header

[kcrid001@coreV2-22-028 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq/QCFastqs
[kcrid001@coreV2-22-028 QCFastqs]$ head RI_B_04_14_clippedtrimmed.fastq.sam
@HD	VN:1.0	SO:unsorted
@SQ	SN:TR78|c0_g1_i1_coral	LN:1109
@SQ	SN:TR78|c0_g2_i1_coral	LN:1109
@SQ	SN:TR79|c0_g1_i1_coral	LN:610
@SQ	SN:TR79|c0_g2_i1_coral	LN:1549
@SQ	SN:TR87|c0_g1_i1_coral	LN:732
@SQ	SN:TR93|c0_g1_i1_coral	LN:550
@SQ	SN:TR101|c0_g1_i1_coral	LN:673
@SQ	SN:TR104|c0_g1_i1_coral	LN:607
@SQ	SN:TR105|c0_g1_i1_coral	LN:587


#8- grep -v '@' your.sam | head to look at the sequence read lines, why does this work to exclude the header lines?
	#because the -v flag means to omit lines with the indicated symbol

[kcrid001@coreV2-22-028 QCFastqs]$ grep -v '@' RI_B_04_14_clippedtrimmed.fastq.sam | head
K00188:59:HMTFHBBXX:5:1101:6055:1648	16	TR13320|c0_g2_i1_coral	2	253M4I44M	*	0	0	TTGAATCATTCTTGTCTACTCCAAGGGGTCTACTTTCCTCAAGGTTTCCNJJJFJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJFJJJJJJJJJJFFA#A	AS:i:-30	XN:i:0	XM:i:3	XO:i:1	XG:i:4	NM:i:7	MD:Z:0A1C42A1	YT:Z:UU	RG:Z:RI_B_04_14
K00188:59:HMTFHBBXX:5:1101:9597:1666	0	TR35685|c1_g2_i1_coral	535	2520M	*	0	0	GACAACCCCGTCTGTGGCGC	AAFFFJJJJJJJJJJJJJJJ	AS:i:-6	XN:i:0	XM:i:1	XO:i:0	XG:i:0	NM:i:1	MD:Z:6A13	YT:Z:UU	RG:Z:RI_B_04_14
K00188:59:HMTFHBBXX:5:1101:26281:1666	16	TR59703|c0_g1_i3_sym	244	1	51M	*	0	0	CTGCTTCTAAACAGCTGGAGAAAGCTGAAATTCTGGAAAAGACAATTAGTFJJFJJFJJJJJJJJJJJFJJJJJJJJAJJJJJJJJFJJJJJJFJJFFFAA	AS:i:0	XS:i:0	XN:i:0	XM:i:0	XO:i:0	XG:i:0	NM:i:0	MD:Z:51	YT:Z:UU	RG:Z:RI_B_04_14
K00188:59:HMTFHBBXX:5:1101:26281:1666	272	TR59703|c0_g1_i1_sym	277	2551M	*	0	0	CTGCTTCTAAACAGCTGGAGAAAGCTGAAATTCTGGAAAAGACAATTAGTFJJFJJFJJJJJJJJJJJFJJJJJJJJAJJJJJJJJFJJJJJJFJJFFFAA	AS:i:0	XS:i:0	XN:i:0	XM:i:0	XO:i:0	XG:i:0	NM:i:0	MD:Z:51	YT:Z:UU	RG:Z:RI_B_04_14
K00188:59:HMTFHBBXX:5:1101:26281:1666	272	TR59703|c0_g1_i3_coral	244	2551M	*	0	0	CTGCTTCTAAACAGCTGGAGAAAGCTGAAATTCTGGAAAAGACAATTAGTFJJFJJFJJJJJJJJJJJFJJJJJJJJAJJJJJJJJFJJJJJJFJJFFFAA	AS:i:0	XS:i:0	XN:i:0	XM:i:0	XO:i:0	XG:i:0	NM:i:0	MD:Z:51	YT:Z:UU	RG:Z:RI_B_04_14
K00188:59:HMTFHBBXX:5:1101:26281:1666	272	TR59703|c0_g1_i1_coral	277	2551M	*	0	0	CTGCTTCTAAACAGCTGGAGAAAGCTGAAATTCTGGAAAAGACAATTAGTFJJFJJFJJJJJJJJJJJFJJJJJJJJAJJJJJJJJFJJJJJJFJJFFFAA	AS:i:0	XS:i:0	XN:i:0	XM:i:0	XO:i:0	XG:i:0	NM:i:0	MD:Z:51	YT:Z:UU	RG:Z:RI_B_04_14
K00188:59:HMTFHBBXX:5:1101:9557:1701	0	TR30871|c0_g1_i1_coral	16	253M3I45M	*	0	0	GTGATAATGATGTTGGTGATAATGATGATGATGGTGGTGGTTGTGGTGTTAAFFFJJJJJFFJJJJJFJFJJAFJJJJJJJJJJFJJAJJJJJFJJFJFFJ	AS:i:-26	XN:i:0	XM:i:2	XO:i:1	XG:i:3	NM:i:5	MD:Z:6G5A35	YT:Z:UU	RG:Z:RI_B_04_14
K00188:59:HMTFHBBXX:5:1101:28270:1701	16	TR5604|c0_g1_i1_coral	515	2551M	*	0	0	CTAAGGTTTGCTTTAAAGCACTTAGTTCAGAATCCTTTGTCTGTACAATTJJJJJJFJJJJJJJJJJJJJJJJJJJJF-JJJFJFJJJJJJJJJJJFFFAA	AS:i:0	XN:i:0	XM:i:0	XO:i:0	XG:i:0	NM:i:0	MD:Z:51	YT:Z:UU	RG:Z:RI_B_04_14
K00188:59:HMTFHBBXX:5:1101:28371:1701	16	TR59703|c0_g1_i3_sym	244	1	51M	*	0	0	CTGCTTCTAAACAGCTGGAGAAAGCTGAAATTCTGGAAAAGACAATTAGTJJJ7JJJJJJFJJJJJJJJJJJJJJJFAJJJJJJJJAJJJJJAJJJFFFAA	AS:i:0	XS:i:0	XN:i:0	XM:i:0	XO:i:0	XG:i:0	NM:i:0	MD:Z:51	YT:Z:UU	RG:Z:RI_B_04_14
K00188:59:HMTFHBBXX:5:1101:28371:1701	272	TR59703|c0_g1_i1_sym	277	2551M	*	0	0	CTGCTTCTAAACAGCTGGAGAAAGCTGAAATTCTGGAAAAGACAATTAGTJJJ7JJJJJJFJJJJJJJJJJJJJJJFAJJJJJJJJAJJJJJAJJJFFFAA	AS:i:0	XS:i:0	XN:i:0	XM:i:0	XO:i:0	XG:i:0	NM:i:0	MD:Z:51	YT:Z:UU	RG:Z:RI_B_04_14


#9- in an interactive session run /cm/shared/courses/dbarshis/21AdvGenomics/scripts/get_explain_sam_flags_advbioinf.py on 2-3 of your .sam files using * to select 2-3 at the same time.

[kcrid001@coreV1-22-016 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq/QCFastqs
[kcrid001@coreV1-22-016 QCFastqs]$ /cm/shared/courses/dbarshis/21AdvGenomics/scripts/get_explain_sam_flags_advbioinf.py RI_B_04_14_clippedtrimmed.fastq.sam RI_B_04_18_clippedtrimmed.fastq.sam RI_B_04_22_clippedtrimmed.fastq.sam
RI_B_04_14_clippedtrimmed.fastq.sam
['0', '272', '256', '16']
0 :
272 :
	read reverse strand
	not primary alignment
256 :
	not primary alignment
16 :
	read reverse strand
RI_B_04_18_clippedtrimmed.fastq.sam
['0', '272', '256', '16']
0 :
272 :
	read reverse strand
	not primary alignment
256 :
	not primary alignment
16 :
	read reverse strand
RI_B_04_22_clippedtrimmed.fastq.sam
['0', '272', '256', '16']
0 :
272 :
	read reverse strand
	not primary alignment
256 :
	not primary alignment
16 :
	read reverse strand


#10- we need to run the read sorting step required for SNP calling, so if you have time, set up and run the following script on your .sam files to finish before Wednesday:

#!/bin/bash -l

#SBATCH -o KCridBamandSort.txt
#SBATCH -n 1         
#SBATCH --mail-user=kcrid001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=KCridBamandSort

enable_lmod
module load samtools/1
for i in *.sam; do `samtools view -bS $i > ${i%.sam}_UNSORTED.bam`; done

for i in *UNSORTED.bam; do samtools sort $i > ${i%_UNSORTED.bam}.bam
samtools index ${i%_UNSORTED.bam}.bam
done

[kcrid001@coreV1-22-016 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq/QCFastqs
[kcrid001@coreV1-22-016 QCFastqs]$ cat bamandsort.sh
#!/bin/bash -l

#SBATCH -o KCridBamandSort.txt
#SBATCH -n 1         
#SBATCH --mail-user=kcrid001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=KCridBamandSort

enable_lmod
module load samtools/1
for i in *.sam; do `samtools view -bS $i > ${i%.sam}_UNSORTED.bam`; done

for i in *UNSORTED.bam; do samtools sort $i > ${i%_UNSORTED.bam}.bam
samtools index ${i%_UNSORTED.bam}.bam
done

[kcrid001@coreV1-22-016 QCFastqs]$ sbatch bamandsort.sh
Submitted batch job 9275211
[kcrid001@coreV1-22-016 QCFastqs]$ squeue -u kcrid001
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON) 
           9275071      main    Blast kcrid001  R      16:38      1 coreV3-23-027 
           9275062      main  Cleanup kcrid001  R      21:08      1 coreV1-22-016 
           9275008      main       sh kcrid001  R      43:38      1 coreV1-22-016 
           9275211      main KCridBam kcrid001  R       0:08      1 coreV2-22-007 

```

## Day07 HW
```sh
#day07HW

#1- Run the following command on your sprot output file to process into the contig length/match format that trinity examines

[kcrid001@turing1 testassembly]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/testassembly
[kcrid001@turing1 testassembly]$ ls
Blast.sh  Blast.txt  blastx.outfmt6  Trinity.fasta
[kcrid001@turing1 testassembly]$ nano blastparsing.sh
[kcrid001@turing1 testassembly]$ cat blastparsing.sh 
#!/bin/bash -l

#SBATCH -o KCridBlastParse.TXT
#SBATCH -n 1
#SBATCH --mail-user=kcrid001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=KCridBlastParse

/cm/shared/apps/trinity/2.0.6/util/analyze_blastPlus_topHit_coverage.pl blastx.outfmt6 Trinity.fasta /cm/shared/apps/blast/databases/uniprot_sprot_Sep2018.fasta
[kcrid001@turing1 testassembly]$ salloc
salloc: Pending job allocation 9276475
salloc: job 9276475 queued and waiting for resources
salloc: job 9276475 has been allocated resources
salloc: Granted job allocation 9276475
[kcrid001@coreV3-23-040 testassembly]$ sbatch blastparsing.sh 
Submitted batch job 9276476
[kcrid001@coreV3-23-040 testassembly]$ ls
blastparsing.sh  blastx.outfmt6            blastx.outfmt6.w_pct_hit_length
Blast.sh         blastx.outfmt6.hist       KCridBlastParse.TXT
Blast.txt        blastx.outfmt6.hist.list  Trinity.fasta
[kcrid001@coreV3-23-040 testassembly]$ cat blastx.outfmt6.hist
#hit_pct_cov_bin	count_in_bin	>bin_below
100	212	212
90	98	310
80	104	414
70	137	551
60	182	733
50	256	989
40	413	1402
30	719	2121
20	1440	3561
10	984	4545

#2- Rm UNSORTED.bam from your QCFastqs directory (or wherever your .bams and .sams are)

[kcrid001@turing1 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/fastq/QCFastqs
[kcrid001@coreV3-23-040 QCFastqs]$ nano KCridrmunsortbam.sh
[kcrid001@coreV3-23-040 QCFastqs]$ cat KCridrmunsortbam.sh

#!/bin/bash -l

#SBATCH -o KCridrmunsortbam.txt
#SBATCH -n 1         
#SBATCH --mail-user=kcrid001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=KCridrmunsortbam

rm *UNSORTED.bam

[kcrid001@coreV3-23-040 QCFastqs]$ sbatch KCridrmunsortbam.sh 
Submitted batch job 9276495


#3- Run the following to start genotyping your SNPs for filtering next class

[kcrid001@coreV3-23-040 QCFastqs]$ nano KCridfreebayessubref.sh
[kcrid001@coreV3-23-040 QCFastqs]$ cat KCridfreebayessubref.sh
#!/bin/bash -l

#SBATCH -o KCridfreebayessubref.txt
#SBATCH -n 1         
#SBATCH --mail-user=kcrid001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=KCridfreebayessubref

enable_lmod
module load dDocent
freebayes --genotype-qualities -f /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/refassembly/15079_Apoc_hostsym.fasta *.bam > KCridEmergedfastqs.vcf
[kcrid001@coreV3-23-040 QCFastqs]$ sbatch KCridfreebayessubref.sh 
Submitted batch job 9276573
[kcrid001@coreV3-23-040 QCFastqs]$ squeue -u kcrid001
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON) 
           9276475      main       sh kcrid001  R    1:42:22      1 coreV3-23-040 
           9276573      main KCridfre kcrid001  R       1:22      1 coreV3-23-046 
```
## Day08 HW
```sh
#day08HW

#1- Clean up your data directory by:
	-Making a SAMS folder and mv all your .sam files into that directory
	-Make a BAMS folder and mv all your .bam files and .bam.bai files into that directory
	-rm your _unfiltered.vcf files if you have any
	-rm your .fastq files
	-Make a VCF folder in your data directory and mv your YOURNAMEmergedfastqs.vcf into this directory (if your freebayes job didn't complete then skip this step)

#2- Start an interactive session via salloc

[kcrid001@turing1 QCFastqs]$ cd ../../
[kcrid001@turing1 data]$ mkdir SAMS
[kcrid001@turing1 QCFastqs]$ mv *.sam ../../SAMS/
[kcrid001@turing1 QCFastqs]$ salloc
salloc: Pending job allocation 9278244
salloc: job 9278244 queued and waiting for resources
salloc: job 9278244 has been allocated resources
salloc: Granted job allocation 9278244
[kcrid001@coreV3-23-040 QCFastqs]$ mkdir ../../BAMS
[kcrid001@coreV3-23-040 QCFastqs]$ mv *.bam *.bam.bai ../../BAMS/


#3- cp the /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/VCF/mergedfastq_HEAAstrangiaAssembly.vcf to your VCF folder

[kcrid001@coreV3-23-040 QCFastqs]$ mkdir ../../VCF
[kcrid001@coreV3-23-040 QCFastqs]$ cd ../../VCF
[kcrid001@coreV3-23-040 VCF]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/VCF
[kcrid001@coreV3-23-040 VCF]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/VCF/mergedfastq_HEAAstrangiaAssembly.vcf ./


#4- Determine the number of individuals and variant sites in the class vcf file (and yours if it worked) using:
/cm/shared/apps/vcftools/0.1.12b/bin/vcftools --vcf mergedfastq_HEAAstrangiaAssembly.vcf
[kcrid001@coreV3-23-040 VCF]$ enable_lmod
[kcrid001@coreV3-23-040 VCF]$ module load dDocent
[kcrid001@coreV3-23-040 VCF]$ vcftools

VCFtools (0.1.14)
© Adam Auton and Anthony Marcketta 2009

Process Variant Call Format files

For a list of options, please go to:
	https://vcftools.github.io/man_latest.html

Alternatively, a man page is available, type:
	man vcftools

Questions, comments, and suggestions should be emailed to:
	vcftools-help@lists.sourceforge.net

[kcrid001@coreV3-23-040 VCF]$  vcftools --vcf mergedfastq_HEAAstrangiaAssembly.vcf

VCFtools - 0.1.14
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf mergedfastq_HEAAstrangiaAssembly.vcf

After filtering, kept 40 out of 40 Individuals
After filtering, kept 1214003 out of a possible 1214003 Sites
Run Time = 14.00 seconds


[kcrid001@coreV3-23-040 VCF]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/VCF
[kcrid001@coreV3-23-040 VCF]$ cp ../fastq/QCFastqs/KCridEmergedfastqs.vcf ./
[kcrid001@coreV3-23-040 VCF]$ vcftools --vcf KCridEmergedfastqs.vcf 

VCFtools - 0.1.14
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf KCridEmergedfastqs.vcf

\After filtering, kept 16 out of 16 Individuals
After filtering, kept 21896 out of a possible 21896 Sites
Run Time = 0.00 seconds


#5- cp the /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/VCF/GoodCoralGenelistForVCFSubsetter.txt into your directory with your .vcf files

[kcrid001@coreV3-23-040 VCF]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/VCF/GoodCoralGenelistForVCFSubsetter.txt ./
[kcrid001@coreV3-23-040 VCF]$ ls
GoodCoralGenelistForVCFSubsetter.txt  mergedfastq_HEAAstrangiaAssembly.vcf
KCridEmergedfastqs.vcf                out.log


#6- Run our host vcf extractor on your merged vcf file using the following syntax:

/cm/shared/courses/dbarshis/21AdvGenomics/scripts/21Sp_vcfsubsetter_advbioinf.py GoodCoralGenelistForVCFSubsetter.txt mergedfastq_HEAAstrangiaAssembly.vcf


[kcrid001@coreV3-23-040 VCF]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/VCF
[kcrid001@coreV3-23-040 VCF]$ /cm/shared/courses/dbarshis/21AdvGenomics/scripts/21Sp_vcfsubsetter_advbioinf.py GoodCoralGenelistForVCFSubsetter.txt mergedfastq_HEAAstrangiaAssembly.vcf
Read in ContigList
^CTraceback (most recent call last):
  File "/cm/shared/courses/dbarshis/21AdvGenomics/scripts/21Sp_vcfsubsetter_advbioinf.py", line 38, in <module>
    if Contig in ContigsToKeep.keys(): #is our contig one we want to keep
KeyboardInterrupt
[kcrid001@turing1 VCF]$ /cm/shared/courses/dbarshis/21AdvGenomics/scripts/vcfsubsetter_advbioinf.py GoodCoralGenelistForVCFSubsetter.txt mergedfastq_HEAAstrangiaAssembly.vcf
[kcrid001@turing1 VCF]$ ls
GoodCoralGenelistForVCFSubsetter.txt
KCridEmergedfastqs.vcf
mergedfastq_HEAAstrangiaAssembly_subset18sp.vcf
mergedfastq_HEAAstrangiaAssembly_subset.vcf
mergedfastq_HEAAstrangiaAssembly.vcf
out.log


#7- Compare the number of variant sites in your three files (YOURNAMEmergedfastqs.vcf,  mergedfastq_HEAAstrangiaAssembly.vcf, and  mergedfastq_HEAAstrangiaAssembly_subset.vcf) using:
/cm/shared/apps/vcftools/0.1.12b/bin/vcftools --vcf


[kcrid001@coreV3-23-002 VCF]$ vcftools --vcf mergedfastq_HEAAstrangiaAssembly_subset.vcf

VCFtools - 0.1.14
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf mergedfastq_HEAAstrangiaAssembly_subset.vcf

After filtering, kept 40 out of 40 Individuals
After filtering, kept 383467 out of a possible 383467 Sites
Run Time = 6.00 seconds
[kcrid001@coreV3-23-002 VCF]$ vcftools --vcf mergedfastq_HEAAstrangiaAssembly.vcf

VCFtools - 0.1.14
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf mergedfastq_HEAAstrangiaAssembly.vcf

After filtering, kept 40 out of 40 Individuals
After filtering, kept 1214003 out of a possible 1214003 Sites
Run Time = 15.00 seconds
[kcrid001@coreV3-23-002 VCF]$ vcftools --vcf KCridEmergedfastqs.vcf

VCFtools - 0.1.14
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf KCridEmergedfastqs.vcf

After filtering, kept 16 out of 16 Individuals
After filtering, kept 21896 out of a possible 21896 Sites
Run Time = 0.00 seconds



#8- Work through the VCF filtering tutorial until the following step:
#http://www.ddocent.com/filtering/
#Now that we have a list of individuals to remove, we can feed that directly into VCFtools for filtering.

#vcftools --vcf raw.g5mac3dp3.recode.vcf --remove lowDP.indv --recode --recode-INFO-all --out raw.g5mac3dplm


[kcrid001@coreV3-23-002 VCF]$ vcftools --vcf mergedfastq_HEAAstrangiaAssembly_subset.vcf --max-missing 0.5 --minQ 30 --recode --recode-INFO-all --out raw.g5mac3

VCFtools - 0.1.14
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf mergedfastq_HEAAstrangiaAssembly_subset.vcf
	--recode-INFO-all
	--minQ 30
	--max-missing 0.5
	--out raw.g5mac3
	--recode

After filtering, kept 40 out of 40 Individuals
Outputting VCF file...
After filtering, kept 133004 out of a possible 383467 Sites
Run Time = 25.00 seconds

[kcrid001@coreV3-23-002 VCF]$ vcftools --vcf raw.g5mac3.recode.vcf --minDP 3 --recode --recode-INFO-all --out raw.g5mac3dp3

VCFtools - 0.1.14
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf raw.g5mac3.recode.vcf
	--recode-INFO-all
	--minDP 3
	--out raw.g5mac3dp3
	--recode

After filtering, kept 40 out of 40 Individuals
Outputting VCF file...
After filtering, kept 133004 out of a possible 133004 Sites
Run Time = 26.00 seconds

[kcrid001@coreV3-23-002 VCF]$ vcftools --vcf raw.g5mac3dp3.recode.vcf --missing-indv

VCFtools - 0.1.14
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf raw.g5mac3dp3.recode.vcf
	--missing-indv

After filtering, kept 40 out of 40 Individuals
Outputting Individual Missingness
After filtering, kept 133004 out of a possible 133004 Sites
Run Time = 2.00 seconds

[kcrid001@coreV3-23-002 VCF]$ cat out.imiss
INDV	N_DATA	N_GENOTYPES_FILTERED	N_MISS	F_MISS
RI_W_06_merged	133004	0	86665	0.651597
RI_W_07_merged	133004	0	82904	0.62332
VA_B_03_merged	133004	0	72661	0.546307
RI_W_02_merged	133004	0	94767	0.712512
RI_W_04_merged	133004	0	92258	0.693648
VA_W_09_SNP_clipped	133004	0	24563	0.184679
RI_B_08_SNP_clipped	133004	0	116118	0.873041
VA_W_08_SNP_clipped	133004	0	109256	0.821449
VA_B_08_SNP_clipped	133004	0	124485	0.935949
VA_W_02_merged	133004	0	92331	0.694197
VA_B_07_merged	133004	0	80522	0.60541
RI_B_05_merged	133004	0	55934	0.420544
VA_W_06_merged	133004	0	84347	0.634169
VA_W_04_merged	133004	0	64460	0.484647
VA_W_01_merged	133004	0	86924	0.653544
VA_B_10_SNP_clipped	133004	0	107967	0.811758
VA_B_06_merged	133004	0	73841	0.555179
VA_W_05_merged	133004	0	85184	0.640462
RI_B_09_SNP_clipped	133004	0	111872	0.841118
VA_W_10_SNP_clipped	133004	0	108814	0.818126
RI_W_08_SNP_clipped	133004	0	101731	0.764872
RI_B_06_merged	133004	0	103948	0.78154
RI_W_10_SNP_clipped	133004	0	120375	0.905048
RI_B_04_merged	133004	0	59639	0.4484
VA_W_03_merged	133004	0	82018	0.616658
RI_B_07_merged	133004	0	91804	0.690235
RI_W_05_merged	133004	0	73522	0.55278
RI_W_09_SNP_clipped	133004	0	116492	0.875853
VA_B_01_merged	133004	0	59653	0.448505
VA_B_09_SNP_clipped	133004	0	103404	0.77745
RI_B_10_SNP_clipped	133004	0	108283	0.814133
RI_W_01_merged	133004	0	95024	0.714445
RI_B_01_merged	133004	0	89764	0.674897
VA_B_04_merged	133004	0	74178	0.557713
RI_B_02_merged	133004	0	114857	0.86356
RI_W_03_merged	133004	0	49393	0.371365
VA_B_02_merged	133004	0	102051	0.767278
VA_W_07_merged	133004	0	83818	0.630192
VA_B_05_merged	133004	0	69075	0.519345
RI_B_03_merged	133004	0	104979	0.789292


[kcrid001@coreV3-23-002 VCF]$ bash
kcrid001@coreV3-23-002:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/VCF$ mawk '!/IN/' out.imiss | cut -f5 > totalmissing
kcrid001@coreV3-23-002:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/VCF$ 
kcrid001@coreV3-23-002:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/VCF$ gnuplot << \EOF 
> set terminal dumb size 120, 30
> set autoscale 
> unset label
> set title "Histogram of % missing data per individual"
> set ylabel "Number of Occurrences"
> set xlabel "% of missing data"
> #set yr [0:100000]
> binwidth=0.01
> bin(x,width)=width*floor(x/width) + binwidth/2.0
> plot 'totalmissing' using (bin($1,binwidth)):(1.0) smooth freq with boxes
> pause -1
> EOF

                                         Histogram of % missing data per individual
  Number of Occurrences
      3 ++----------+-----------+-----------+-----------+------****--+---------***-----------***---------+----------++
        +           +           +           +           +      *'totalmissing' using (bin($1,binwidth)):(1.0) ****** +
        |                                                      *  *            * *           * *                     |
        |                                                      *  *            * *           * *                     |
        |                                                      *  *            * *           * *                     |
        |                                                      *  *            * *           * *                     |
    2.5 ++                                                     *  *            * *           * *                    ++
        |                                                      *  *            * *           * *                     |
        |                                                      *  *            * *           * *                     |
        |                                                      *  *            * *           * *                     |
        |                                                      *  *            * *           * *                     |
        |                                                      *  *            * *           * *                     |
      2 ++                                       ****          *  *     ** **  * ************* *     ****           ++
        |                                        *  *          *  *     ** **  * *    *  **  * *     *  *            |
        |                                        *  *          *  *     ** **  * *    *  **  * *     *  *            |
        |                                        *  *          *  *     ** **  * *    *  **  * *     *  *            |
        |                                        *  *          *  *     ** **  * *    *  **  * *     *  *            |
        |                                        *  *          *  *     ** **  * *    *  **  * *     *  *            |
    1.5 ++                                       *  *          *  *     ** **  * *    *  **  * *     *  *           ++
        |                                        *  *          *  *     ** **  * *    *  **  * *     *  *            |
        |                                        *  *          *  *     ** **  * *    *  **  * *     *  *            |
        |                                        *  *          *  *     ** **  * *    *  **  * *     *  *            |
        |                                        *  *          *  *     ** **  * *    *  **  * *     *  *            |
        +           +           +           +    *  *   +      *  *  +  ** **  * *    *  **  * *     *  *+           +
      1 ********************************************************************************************************----++
       0.1         0.2         0.3         0.4         0.5          0.6         0.7         0.8         0.9          1
                                                      % of missing data

```
## Day09 HW
```sh
#day09HW - VCF to Genepop to PCAs


#1-  Run one of the following sets of prescribed filters on your mergedfastq_HEAAstrangiaAssembly_subset.vcf, note these are fairly conservative filters

##Half the class run the following
/cm/shared/apps/vcftools/0.1.12b/bin/vcftools --vcf mergedfastq_HEAAstrangiaAssembly_subset.vcf --maf 0.015 --max-alleles 2 --max-missing 0.5 --minQ 30 --minGQ 20 --minDP 3 --remove-indels --hwe 0.01 --recode --recode-INFO-all --out 18718_mergedfastq_HEAAstrangiaAssembly_subset_ClassFilters

##the other half run the filters we used from the paper
/cm/shared/apps/vcftools/0.1.12b/bin/vcftools --vcf mergedfastq_HEAAstrangiaAssembly_subset.vcf --max-missing 0.5 --mac 3 --minQ 30 --minDP 10 --max-alleles 2 --maf 0.015 --remove-indels --recode --recode-INFO-all --out 1578_mergedfastq_HEAAstrangiaAssembly_subset_HEAFilters


[kcrid001@turing1 data]$ salloc
salloc: Pending job allocation 9280290
salloc: job 9280290 queued and waiting for resources
salloc: job 9280290 has been allocated resources
salloc: Granted job allocation 9280290
[kcrid001@coreV3-23-004 data]$ cd VCF/
[kcrid001@coreV3-23-004 VCF]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/VCF
[kcrid001@coreV3-23-004 VCF]$ ls
GoodCoralGenelistForVCFSubsetter.txt             out.log
KCridEmergedfastqs.vcf                           raw.g5mac3dp3.log
mergedfastq_HEAAstrangiaAssembly_subset18sp.vcf  raw.g5mac3dp3.recode.vcf
mergedfastq_HEAAstrangiaAssembly_subset.vcf      raw.g5mac3.log
mergedfastq_HEAAstrangiaAssembly.vcf             raw.g5mac3.recode.vcf
out.imiss                                        totalmissing
[kcrid001@coreV3-23-004 VCF]$ enable_lmod
[kcrid001@coreV3-23-004 VCF]$ module load dDocent
[kcrid001@coreV3-23-004 VCF]$ vcftools --vcf mergedfastq_HEAAstrangiaAssembly_subset.vcf

VCFtools - 0.1.14
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf mergedfastq_HEAAstrangiaAssembly_subset.vcf

After filtering, kept 40 out of 40 Individuals
After filtering, kept 383467 out of a possible 383467 Sites
Run Time = 6.00 seconds
[kcrid001@coreV3-23-004 VCF]$ /cm/shared/apps/vcftools/0.1.12b/bin/vcftools --vcf mergedfastq_HEAAstrangiaAssembly_subset.vcf --maf 0.015 --max-alleles 2 --max-missing 0.5 --minQ 30 --minGQ 20 --minDP 3 --remove-indels --hwe 0.01 --recode --recode-INFO-all --out 18718_mergedfastq_HEAAstrangiaAssembly_subset_ClassFilters

VCFtools - v0.1.12b
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf mergedfastq_HEAAstrangiaAssembly_subset.vcf
	--recode-INFO-all
	--maf 0.015
	--max-alleles 2
	--minDP 3
	--minGQ 20
	--hwe 0.01
	--minQ 30
	--max-missing 0.5
	--out 18718_mergedfastq_HEAAstrangiaAssembly_subset_ClassFilters
	--recode
	--remove-indels

After filtering, kept 40 out of 40 Individuals
Outputting VCF file...
After filtering, kept 16843 out of a possible 383467 Sites
Run Time = 11.00 seconds
## these numbers look wrong, so I used the other subset vcf file that was in my directory

[kcrid001@coreV3-23-004 VCF]$ ls
18718_mergedfastq_HEAAstrangiaAssembly_subset_ClassFilters.log
18718_mergedfastq_HEAAstrangiaAssembly_subset_ClassFilters.recode.vcf
GoodCoralGenelistForVCFSubsetter.txt
KCridEmergedfastqs.vcf
mergedfastq_HEAAstrangiaAssembly_subset18sp.vcf
mergedfastq_HEAAstrangiaAssembly_subset.vcf
mergedfastq_HEAAstrangiaAssembly.vcf
out.imiss
out.log
raw.g5mac3dp3.log
raw.g5mac3dp3.recode.vcf
raw.g5mac3.log
raw.g5mac3.recode.vcf
totalmissing
[kcrid001@coreV3-23-004 VCF]$ /cm/shared/apps/vcftools/0.1.12b/bin/vcftools --vcf mergedfastq_HEAAstrangiaAssembly_subset18sp.vcf --maf 0.015 --max-alleles 2 --max-missing 0.5 --minQ 30 --minGQ 20 --minDP 3 --remove-indels --hwe 0.01 --recode --recode-INFO-all --out 18718_mergedfastq_HEAAstrangiaAssembly_subset_ClassFilters

VCFtools - v0.1.12b
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf mergedfastq_HEAAstrangiaAssembly_subset18sp.vcf
	--recode-INFO-all
	--maf 0.015
	--max-alleles 2
	--minDP 3
	--minGQ 20
	--hwe 0.01
	--minQ 30
	--max-missing 0.5
	--out 18718_mergedfastq_HEAAstrangiaAssembly_subset_ClassFilters
	--recode
	--remove-indels

After filtering, kept 40 out of 40 Individuals
Outputting VCF file...
After filtering, kept 18718 out of a possible 432676 Sites
Run Time = 14.00 seconds

[kcrid001@coreV3-23-004 VCF]$ vcftools --vcf 18718_mergedfastq_HEAAstrangiaAssembly_subset_ClassFilters.recode.vcf --missing-indv

VCFtools - 0.1.14
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf 18718_mergedfastq_HEAAstrangiaAssembly_subset_ClassFilters.recode.vcf
	--missing-indv

After filtering, kept 40 out of 40 Individuals
Outputting Individual Missingness
After filtering, kept 18718 out of a possible 18718 Sites
Run Time = 1.00 seconds
[kcrid001@coreV3-23-004 VCF]$ ls
18718_mergedfastq_HEAAstrangiaAssembly_subset_ClassFilters.log
18718_mergedfastq_HEAAstrangiaAssembly_subset_ClassFilters.recode.vcf
GoodCoralGenelistForVCFSubsetter.txt
KCridEmergedfastqs.vcf
mergedfastq_HEAAstrangiaAssembly_subset18sp.vcf
mergedfastq_HEAAstrangiaAssembly_subset.vcf
mergedfastq_HEAAstrangiaAssembly.vcf
out.imiss
out.log
raw.g5mac3dp3.log
raw.g5mac3dp3.recode.vcf
raw.g5mac3.log
raw.g5mac3.recode.vcf
totalmissing
[kcrid001@coreV3-23-004 VCF]$ cat out.imiss
INDV	N_DATA	N_GENOTYPES_FILTERED	N_MISS	F_MISS
RI_W_06_merged	18718	0	5674	0.303131
RI_W_07_merged	18718	0	4701	0.251149
VA_B_03_merged	18718	0	3474	0.185597
RI_W_02_merged	18718	0	7137	0.381291
RI_W_04_merged	18718	0	7811	0.417299
VA_W_09_SNP_clipped	18718	0	786	0.0419917
RI_B_08_SNP_clipped	18718	0	14130	0.754888
VA_W_08_SNP_clipped	18718	0	11806	0.63073
VA_B_08_SNP_clipped	18718	0	16264	0.868896
VA_W_02_merged	18718	0	7067	0.377551
VA_B_07_merged	18718	0	4916	0.262635
RI_B_05_merged	18718	0	2439	0.130302
VA_W_06_merged	18718	0	4639	0.247836
VA_W_04_merged	18718	0	3015	0.161075
VA_W_01_merged	18718	0	5970	0.318944
VA_B_10_SNP_clipped	18718	0	10773	0.575542
VA_B_06_merged	18718	0	3608	0.192756
VA_W_05_merged	18718	0	5904	0.315418
RI_B_09_SNP_clipped	18718	0	12981	0.693504
VA_W_10_SNP_clipped	18718	0	10890	0.581793
RI_W_08_SNP_clipped	18718	0	9193	0.491132
RI_B_06_merged	18718	0	8881	0.474463
RI_W_10_SNP_clipped	18718	0	14714	0.786088
RI_B_04_merged	18718	0	2421	0.129341
VA_W_03_merged	18718	0	4740	0.253232
RI_B_07_merged	18718	0	6586	0.351854
RI_W_05_merged	18718	0	3762	0.200983
RI_W_09_SNP_clipped	18718	0	13901	0.742654
VA_B_01_merged	18718	0	3472	0.18549
VA_B_09_SNP_clipped	18718	0	9209	0.491986
RI_B_10_SNP_clipped	18718	0	11091	0.592531
RI_W_01_merged	18718	0	7875	0.420718
RI_B_01_merged	18718	0	6067	0.324127
VA_B_04_merged	18718	0	4853	0.259269
RI_B_02_merged	18718	0	13042	0.696762
RI_W_03_merged	18718	0	1968	0.105139
VA_B_02_merged	18718	0	10252	0.547708
VA_W_07_merged	18718	0	4860	0.259643
VA_B_05_merged	18718	0	3311	0.176889
RI_B_03_merged	18718	0	9817	0.524468

#2- Make a population file containing two columns with no header, tab delimited text the first column should be the individual name and the second column the population to which that individual belongs

[kcrid001@coreV3-23-004 VCF]$ grep '#CHROM' mergedfastq_HEAAstrangiaAssembly.vcf
#CHROM	POS	ID	REF	ALT	QUAL	FILTER	INFO	FORMAT	RI_W_06_merged	RI_W_07_merged	VA_B_03_merged	RI_W_02_merged	RI_W_04_merged	VA_W_09_SNP_clipped	RI_B_08_SNP_clipped	VA_W_08_SNP_clipped	VA_B_08_SNP_clipped	VA_W_02_merged	VA_B_07_merged	RI_B_05_merged	VA_W_06_merged	VA_W_04_merged	VA_W_01_merged	VA_B_10_SNP_clipped	VA_B_06_mergedVA_W_05_merged	RI_B_09_SNP_clipped	VA_W_10_SNP_clipped	RI_W_08_SNP_clipped	RI_B_06_merged	RI_W_10_SNP_clipped	RI_B_04_merged	VA_W_03_merged	RI_B_07_merged	RI_W_05_mergedRI_W_09_SNP_clipped	VA_B_01_merged	VA_B_09_SNP_clipped	RI_B_10_SNP_clipped	RI_W_01_merged	RI_B_01_merged	VA_B_04_merged	RI_B_02_merged	RI_W_03_merged	VA_B_02_merged	VA_W_07_merged	VA_B_05_merged	RI_B_03_merged
[kcrid001@coreV3-23-004 VCF]$ grep '#CHROM' mergedfastq_HEAAstrangiaAssembly.vcf > samplenames.txt
[kcrid001@coreV3-23-004 VCF]$ cat samplenames.txt 
#CHROM	POS	ID	REF	ALT	QUAL	FILTER	INFO	FORMAT	RI_W_06_merged	RI_W_07_merged	VA_B_03_merged	RI_W_02_merged	RI_W_04_merged	VA_W_09_SNP_clipped	RI_B_08_SNP_clipped	VA_W_08_SNP_clipped	VA_B_08_SNP_clipped	VA_W_02_merged	VA_B_07_merged	RI_B_05_merged	VA_W_06_merged	VA_W_04_merged	VA_W_01_merged	VA_B_10_SNP_clipped	VA_B_06_mergedVA_W_05_merged	RI_B_09_SNP_clipped	VA_W_10_SNP_clipped	RI_W_08_SNP_clipped	RI_B_06_merged	RI_W_10_SNP_clipped	RI_B_04_merged	VA_W_03_merged	RI_B_07_merged	RI_W_05_mergedRI_W_09_SNP_clipped	VA_B_01_merged	VA_B_09_SNP_clipped	RI_B_10_SNP_clipped	RI_W_01_merged	RI_B_01_merged	VA_B_04_merged	RI_B_02_merged	RI_W_03_merged	VA_B_02_merged	VA_W_07_merged	VA_B_05_merged	RI_B_03_merged
[kcrid001@coreV3-23-004 VCF]$ cut -f 1 out.imiss
INDV
RI_W_06_merged
RI_W_07_merged
VA_B_03_merged
RI_W_02_merged
RI_W_04_merged
VA_W_09_SNP_clipped
RI_B_08_SNP_clipped
VA_W_08_SNP_clipped
VA_B_08_SNP_clipped
VA_W_02_merged
VA_B_07_merged
RI_B_05_merged
VA_W_06_merged
VA_W_04_merged
VA_W_01_merged
VA_B_10_SNP_clipped
VA_B_06_merged
VA_W_05_merged
RI_B_09_SNP_clipped
VA_W_10_SNP_clipped
RI_W_08_SNP_clipped
RI_B_06_merged
RI_W_10_SNP_clipped
RI_B_04_merged
VA_W_03_merged
RI_B_07_merged
RI_W_05_merged
RI_W_09_SNP_clipped
VA_B_01_merged
VA_B_09_SNP_clipped
RI_B_10_SNP_clipped
RI_W_01_merged
RI_B_01_merged
VA_B_04_merged
RI_B_02_merged
RI_W_03_merged
VA_B_02_merged
VA_W_07_merged
VA_B_05_merged
RI_B_03_merged

# paste in excel and use the 'left' command to get the first 4 characters of each name. copy and paste to the cluster

[kcrid001@coreV3-23-004 VCF]$ nano popfile.txt
[kcrid001@coreV3-23-004 VCF]$ cat popfile.txt 
RI_W_06_merged	RI_W
RI_W_07_merged	RI_W
VA_B_03_merged	VA_B
RI_W_02_merged	RI_W
RI_W_04_merged	RI_W
VA_W_09_SNP_clipped	VA_W
RI_B_08_SNP_clipped	RI_B
VA_W_08_SNP_clipped	VA_W
VA_B_08_SNP_clipped	VA_B
VA_W_02_merged	VA_W
VA_B_07_merged	VA_B
RI_B_05_merged	RI_B
VA_W_06_merged	VA_W
VA_W_04_merged	VA_W
VA_W_01_merged	VA_W
VA_B_10_SNP_clipped	VA_B
VA_B_06_merged	VA_B
VA_W_05_merged	VA_W
RI_B_09_SNP_clipped	RI_B
VA_W_10_SNP_clipped	VA_W
RI_W_08_SNP_clipped	RI_W
RI_B_06_merged	RI_B
RI_W_10_SNP_clipped	RI_W
RI_B_04_merged	RI_B
VA_W_03_merged	VA_W
RI_B_07_merged	RI_B
RI_W_05_merged	RI_W
RI_W_09_SNP_clipped	RI_W
VA_B_01_merged	VA_B
VA_B_09_SNP_clipped	VA_B
RI_B_10_SNP_clipped	RI_B
RI_W_01_merged	RI_W
RI_B_01_merged	RI_B
VA_B_04_merged	VA_B
RI_B_02_merged	RI_B
RI_W_03_merged	RI_W
VA_B_02_merged	VA_B
VA_W_07_merged	VA_W
VA_B_05_merged	VA_B
RI_B_03_merged	RI_B


#3- Convert your filtered .vcf file to genepop format using the following command:

/cm/shared/courses/dbarshis/21AdvGenomics/scripts/vcftogenepop_advbioinf.py YOURFILTERED.vcf YOUR_PopFile.txt

[kcrid001@coreV3-23-004 VCF]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/VCF
[kcrid001@coreV3-23-004 VCF]$ /cm/shared/courses/dbarshis/21AdvGenomics/scripts/vcftogenepop_advbioinf.py 18718_mergedfastq_HEAAstrangiaAssembly_subset_ClassFilters.recode.vcf popfile.txt
Indivs with genotypes in vcf file: RI_W_06_merged	RI_W_07_merged	VA_B_03_merged	RI_W_02_merged	RI_W_04_merged	VA_W_09_SNP_clipped	RI_B_08_SNP_clipped	VA_W_08_SNP_clipped	VA_B_08_SNP_clipped	VA_W_02_merged	VA_B_07_merged	RI_B_05_merged	VA_W_06_merged	VA_W_04_merged	VA_W_01_merged	VA_B_10_SNP_clipped	VA_B_06_merged	VA_W_05_merged	RI_B_09_SNP_clipped	VA_W_10_SNP_clipped	RI_W_08_SNP_clipped	RI_B_06_merged	RI_W_10_SNP_clipped	RI_B_04_merged	VA_W_03_merged	RI_B_07_merged	RI_W_05_merged	RI_W_09_SNP_clipped	VA_B_01_merged	VA_B_09_SNP_clipped	RI_B_10_SNP_clipped	RI_W_01_merged	RI_B_01_merged	VA_B_04_merged	RI_B_02_merged	RI_W_03_merged	VA_B_02_merged	VA_W_07_merged	VA_B_05_merged	RI_B_03_merged
44 18718 18718 18718 18718 40

#4- SCP your YOURFILE_allfilters.recode_subset_genepop.gen file to your laptop
(base) Katies-MacBook-Air-4:day09 katiecrider$ pwd
/Users/katiecrider/Desktop/Genomics/21sp_advgenomics/assignments_exercises/day09
(base) Katies-MacBook-Air-4:day09 katiecrider$ scp kcrid001@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/VCF/18718_mergedfastq_HEAAstrangiaAssembly_subset_ClassFilters.recode_genepop.gen ./

#5- Switch to the adegenet_PCAs.R script and follow through the steps to produce some of the figures.

install.packages("deldir")
library("adegenet")
library("ape")
library("pegas")
library("seqinr")
library("ggplot2")
library("viridis")
library("scales")
library("factoextra")

#set working directory
setwd("/Users/katiecrider/Desktop/Genomics/21sp_advgenomics/assignments_exercises/day09")

datafile<-read.genepop('18718_mergedfastq_HEAAstrangiaAssembly_subset_ClassFilters.recode_genepop.gen', ncode=2)


sum(is.na(datafile$tab))
datafile #shows info
YOURdata<-scaleGen(datafile, NA.method='mean')
X<-YOURdata
Y<-as.factor(substring(pop(datafile),1,4)) #change the second number here to change how many letters/numbers you keep in the name
pca1 <- dudi.pca(X,cent=T, scale=T, scannf=F, nf=3)
summary(pca1)


#### PCAs ####
# individual labels
s.label(pca1$li)

# population elipses
s.class(pca1$li, pop(datafile))

#color symbols, pop names
#pdf("YOURINITIALS_ColorPCA1v2.pdf")
col <- c("blue","red", "green", "black")
s.class(pca1$li, Y,xax=1,yax=2, col=transp(col,.6), axesell=F, cstar=0, cpoint=3, grid=FALSE, addaxes=TRUE)
add.scatter.eig(pca1$eig[1:3], 3,1,2, posi="topright")
title("PCA of DJB_data\naxes 1-2")
#dev.off()

#### Snapclust ####
a.clust<-snapclust(datafile, k = 4)
class(a.clust)
names(a.clust)
a.tab <- table(pop(datafile), a.clust$group)
table.value(a.tab, col.labels = 1:2)

compoplot(a.clust)

```
## Day10 HW
```sh
#1- Work through the adegenet_PCAs.R script and follow through the steps to produce some of the figures.

setwd("/Users/katiecrider/Desktop/Genomics/21sp_advgenomics/assignments_exercises/day09")
datafile<-read.genepop('coral_279_cloneremoved_neutral.filtered1SNPper_genepop.gen', ncode=2)
#follow the same scripts as day09 #5, with the other genepop files

###run step 2 as an sbatch .sh script because it will take a while to finish
#2- cd into your SAMS folder containing your .sams and run the following as an sbatch script on your sam files to generate read mapping counts from each individual file:
/cm/shared/courses/dbarshis/21AdvGenomics/scripts/countxpression_SB_advbioinf.py *.sam

[kcrid001@turing1 SAMS]$ salloc
salloc: Pending job allocation 9280850
salloc: job 9280850 queued and waiting for resources
salloc: job 9280850 has been allocated resources
salloc: Granted job allocation 9280850
[kcrid001@coreV2-25-015 SAMS]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/SAMS
[kcrid001@coreV2-25-015 SAMS]$ nano SAMSreadmap.sh
[kcrid001@coreV2-25-015 SAMS]$ cat SAMSreadmap.sh 
#!/bin/bash -l

#SBATCH -o SAMSreadmap.txt
#SBATCH -n 1
#SBATCH --mail-user=kcrid001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=SAMSreadmap


/cm/shared/courses/dbarshis/21AdvGenomics/scripts/countxpression_SB_advbioinf.py *.sam
[kcrid001@coreV2-25-015 SAMS]$ sbatch SAMSreadmap.sh 
Submitted batch job 9280858
[kcrid001@coreV2-25-015 SAMS]$ squeue -u kcrid001
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON) 
           9280858      main SAMSread kcrid001  R       0:07      1 coreV1-22-016 
           9280850      main       sh kcrid001  R    1:08:38      1 coreV2-25-015 


#3- Once your job from step 1 is finished, start an salloc session and run the following on your outputted _counts.txt files:

/cm/shared/courses/dbarshis/21AdvGenomics/scripts/ParseExpression2BigTable_advbioinf.py /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/host_genelist.txt KCridFullCounts_summed.txt NoMatch *_counts.txt


[kcrid001@coreV2-25-015 SAMS]$ /cm/shared/courses/dbarshis/21AdvGenomics/scripts/ParseExpression2BigTable_advbioinf.py /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/host_genelist.txt KCridFullCounts_summed.txt NoMatch *_counts.txt
Hits not matchedRI_B_04_14_clippedtrimmed.fastq_counts.txt=1698	RI_B_04_18_clippedtrimmed.fastq_counts.txt=1698	RI_B_04_22_clippedtrimmed.fastq_counts.txt=1698	RI_B_05_14_clippedtrimmed.fastq_counts.txt=1698	RI_W_04_14_clippedtrimmed.fastq_counts.txt=1698	RI_W_04_18_clippedtrimmed.fastq_counts.txt=1698	RI_W_04_22_clippedtrimmed.fastq_counts.txt=1698	RI_W_05_14_clippedtrimmed.fastq_counts.txt=1698	VA_B_04_14_clippedtrimmed.fastq_counts.txt=1698	VA_B_04_18_clippedtrimmed.fastq_counts.txt=1698	VA_B_04_22_clippedtrimmed.fastq_counts.txt=1698	VA_B_05_14_clippedtrimmed.fastq_counts.txt=1698	VA_W_04_14_clippedtrimmed.fastq_counts.txt=1698	VA_W_04_18_clippedtrimmed.fastq_counts.txt=1698	VA_W_04_22_clippedtrimmed.fastq_counts.txt=1698	VA_W_05_14_clippedtrimmed.fastq_counts.txt=1698

#4- scp YOURNAMEFullCounts_summed.txt to your laptop

(base) Katies-MacBook-Air-4:day10 katiecrider$ scp kcrid001@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/katiecrider/data/SAMS/KCridFullCounts_summed.txt ./
kcrid001@turing.hpc.odu.edu's password: 
KCridFullCounts_summed.txt                              100%  885KB   5.4MB/s   00:00    
(base) Katies-MacBook-Air-4:day10 katiecrider$ ls
KCridFullCounts_summed.txt
coral_279_cloneremoved_neutral.filtered1SNPper_genepop.gen
coral_66_cloneremoved_highoutliers.filtered1SNPper_genepop.gen
homework_day10.txt
(base) Katies-MacBook-Air-4:day10 katiecrider$ pwd
/Users/katiecrider/Desktop/Genomics/21sp_advgenomics/assignments_exercises/day10

#5- edit the first line of YOURNAMEFullCounts_summed.txt to remove the _counts.txt_UniqueTotReads from each sample name to just retain the actual informative part of the sample name (e.g., RI_W_06_18)

```
## Day11 HW
```sh

#1- Download the DESeq2Script_advbioinf.R script and work through on the shared djbFullCounts_summed.txt file

#/Users/katiecrider/Desktop/Genomics/21sp_advgenomics/assignments_exercises/day11/DESeq2Script_advbioinf.R

#copy this and the summed.txt file to the Genomics folder

#make sure to have downloaded these packages already

>library(DESeq2)
>library(gplots)
>vignette('DESeq2')

>setwd("/Users/katiecrider/Desktop/Genomics")  # The drag and drop from finder works in R, too.
> conds<-data.frame("Sample"=names(countsTable))
> conds$Origin<-factor(substring(conds$Sample,1,2))
> conds$SymState<-factor(substring(conds$Sample,4,4))
> conds$Temp<-factor(substring(conds$Sample,9,10))
> conds$Origin_SymState<-factor(paste(conds$Origin,conds$SymState, sep="_"))
> conds$Origin_SymState_Temp<-factor(paste(conds$Origin,conds$SymState,conds$Temp, sep="_"))
> conds
       Sample Origin SymState Temp Origin_SymState Origin_SymState_Temp
1  RI_B_01_14     RI        B   14            RI_B              RI_B_14
2  RI_B_01_18     RI        B   18            RI_B              RI_B_18
3  RI_B_01_22     RI        B   22            RI_B              RI_B_22
4  RI_B_02_14     RI        B   14            RI_B              RI_B_14
5  RI_B_02_18     RI        B   18            RI_B              RI_B_18
6  RI_B_02_22     RI        B   22            RI_B              RI_B_22
7  RI_B_03_14     RI        B   14            RI_B              RI_B_14
8  RI_B_03_22     RI        B   22            RI_B              RI_B_22
9  RI_B_04_14     RI        B   14            RI_B              RI_B_14
10 RI_B_04_18     RI        B   18            RI_B              RI_B_18
11 RI_B_04_22     RI        B   22            RI_B              RI_B_22
12 RI_B_05_14     RI        B   14            RI_B              RI_B_14
13 RI_B_05_18     RI        B   18            RI_B              RI_B_18
14 RI_B_05_22     RI        B   22            RI_B              RI_B_22
15 RI_B_06_14     RI        B   14            RI_B              RI_B_14
16 RI_B_06_18     RI        B   18            RI_B              RI_B_18
17 RI_B_06_22     RI        B   22            RI_B              RI_B_22
18 RI_B_07_14     RI        B   14            RI_B              RI_B_14
19 RI_B_07_18     RI        B   18            RI_B              RI_B_18
20 RI_B_07_22     RI        B   22            RI_B              RI_B_22
21 RI_W_01_14     RI        W   14            RI_W              RI_W_14
22 RI_W_01_18     RI        W   18            RI_W              RI_W_18
23 RI_W_01_22     RI        W   22            RI_W              RI_W_22
24 RI_W_02_14     RI        W   14            RI_W              RI_W_14
25 RI_W_02_18     RI        W   18            RI_W              RI_W_18
26 RI_W_02_22     RI        W   22            RI_W              RI_W_22
27 RI_W_03_14     RI        W   14            RI_W              RI_W_14
28 RI_W_03_18     RI        W   18            RI_W              RI_W_18
29 RI_W_03_22     RI        W   22            RI_W              RI_W_22
30 RI_W_04_14     RI        W   14            RI_W              RI_W_14
31 RI_W_04_18     RI        W   18            RI_W              RI_W_18
32 RI_W_04_22     RI        W   22            RI_W              RI_W_22
33 RI_W_05_14     RI        W   14            RI_W              RI_W_14
34 RI_W_05_18     RI        W   18            RI_W              RI_W_18
35 RI_W_05_22     RI        W   22            RI_W              RI_W_22
36 RI_W_06_14     RI        W   14            RI_W              RI_W_14
37 RI_W_06_18     RI        W   18            RI_W              RI_W_18
38 RI_W_06_22     RI        W   22            RI_W              RI_W_22
39 RI_W_07_14     RI        W   14            RI_W              RI_W_14
40 RI_W_07_18     RI        W   18            RI_W              RI_W_18
41 RI_W_07_22     RI        W   22            RI_W              RI_W_22
42 VA_B_01_14     VA        B   14            VA_B              VA_B_14
43 VA_B_01_18     VA        B   18            VA_B              VA_B_18
44 VA_B_01_22     VA        B   22            VA_B              VA_B_22
45 VA_B_02_14     VA        B   14            VA_B              VA_B_14
46 VA_B_02_18     VA        B   18            VA_B              VA_B_18
47 VA_B_02_22     VA        B   22            VA_B              VA_B_22
48 VA_B_03_14     VA        B   14            VA_B              VA_B_14
49 VA_B_03_18     VA        B   18            VA_B              VA_B_18
50 VA_B_03_22     VA        B   22            VA_B              VA_B_22
51 VA_B_04_14     VA        B   14            VA_B              VA_B_14
52 VA_B_04_18     VA        B   18            VA_B              VA_B_18
53 VA_B_04_22     VA        B   22            VA_B              VA_B_22
54 VA_B_05_14     VA        B   14            VA_B              VA_B_14
55 VA_B_05_18     VA        B   18            VA_B              VA_B_18
56 VA_B_05_22     VA        B   22            VA_B              VA_B_22
57 VA_B_06_14     VA        B   14            VA_B              VA_B_14
58 VA_B_06_18     VA        B   18            VA_B              VA_B_18
59 VA_B_06_22     VA        B   22            VA_B              VA_B_22
60 VA_B_07_14     VA        B   14            VA_B              VA_B_14
61 VA_B_07_18     VA        B   18            VA_B              VA_B_18
62 VA_B_07_22     VA        B   22            VA_B              VA_B_22
63 VA_W_01_14     VA        W   14            VA_W              VA_W_14
64 VA_W_01_18     VA        W   18            VA_W              VA_W_18
65 VA_W_02_14     VA        W   14            VA_W              VA_W_14
66 VA_W_02_18     VA        W   18            VA_W              VA_W_18
67 VA_W_03_14     VA        W   14            VA_W              VA_W_14
68 VA_W_03_18     VA        W   18            VA_W              VA_W_18
69 VA_W_03_22     VA        W   22            VA_W              VA_W_22
70 VA_W_04_14     VA        W   14            VA_W              VA_W_14
71 VA_W_04_18     VA        W   18            VA_W              VA_W_18
72 VA_W_04_22     VA        W   22            VA_W              VA_W_22
73 VA_W_05_14     VA        W   14            VA_W              VA_W_14
74 VA_W_05_18     VA        W   18            VA_W              VA_W_18
75 VA_W_05_22     VA        W   22            VA_W              VA_W_22
76 VA_W_06_14     VA        W   14            VA_W              VA_W_14
77 VA_W_06_18     VA        W   18            VA_W              VA_W_18
78 VA_W_06_22     VA        W   22            VA_W              VA_W_22
79 VA_W_07_14     VA        W   14            VA_W              VA_W_14
80 VA_W_07_18     VA        W   18            VA_W              VA_W_18
81 VA_W_07_22     VA        W   22            VA_W              VA_W_22
> prop.null <- apply(countsTable, 2, function(x) 100*mean(x==0))
> 
> barplot(prop.null, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> 
> pdf(file="OverallNullCounts.pdf",14, 14)
> barplot(prop.null, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> dev.off()
RStudioGD 
        2 
> 
> # how many genes have mean count >=3 
> means = apply(countsTable, 1, mean)
> table(means>=3)

TRUE 
7543 
> 
> countsTable<-countsTable[means>=3,]
> dim(countsTable)
[1] 7543   81
> 
> prop.nullv2 <- apply(countsTable, 2, function(x) 100*mean(x==0))
> pdf(file="Mean3NullCounts.pdf",14, 14)
> barplot(prop.nullv2, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> dev.off()
RStudioGD 
        2 
> 
> #make count data set
> dds <- DESeqDataSetFromMatrix(countData=countsTable, colData=conds, design=~ Origin_SymState_Temp)
> 
> dds <- DESeq(dds)
estimating size factors
estimating dispersions
gene-wise dispersion estimates
mean-dispersion relationship
final dispersion estimates
fitting model and testing
-- replacing outliers and refitting for 8 genes
-- DESeq argument 'minReplicatesForReplace' = 7 
-- original counts are preserved in counts(dds)
estimating dispersions
fitting model and testing
> 
> #transform counts to variance stablized counts
> vstCounts<-varianceStabilizingTransformation(dds)
> 
> #plot cluster dendrogram across samples
> dists<-dist(t(assay(vstCounts)))
> plot(hclust(dists))
> 
> plotPCA(vstCounts, intgroup="Origin")
> plotPCA(vstCounts, intgroup="SymState")
> plotPCA(vstCounts, intgroup="Temp")
> plotPCA(vstCounts, intgroup="Origin_SymState")
> plotPCA(vstCounts, intgroup="Origin_SymState_Temp")
> resultsNames(dds)
 [1] "Intercept"                              
 [2] "Origin_SymState_Temp_RI_B_18_vs_RI_B_14"
 [3] "Origin_SymState_Temp_RI_B_22_vs_RI_B_14"
 [4] "Origin_SymState_Temp_RI_W_14_vs_RI_B_14"
 [5] "Origin_SymState_Temp_RI_W_18_vs_RI_B_14"
 [6] "Origin_SymState_Temp_RI_W_22_vs_RI_B_14"
 [7] "Origin_SymState_Temp_VA_B_14_vs_RI_B_14"
 [8] "Origin_SymState_Temp_VA_B_18_vs_RI_B_14"
 [9] "Origin_SymState_Temp_VA_B_22_vs_RI_B_14"
[10] "Origin_SymState_Temp_VA_W_14_vs_RI_B_14"
[11] "Origin_SymState_Temp_VA_W_18_vs_RI_B_14"
[12] "Origin_SymState_Temp_VA_W_22_vs_RI_B_14"
> 
> dim(dds)
[1] 7543   81
> 
> ###Figure out which contrast you want to examine (i.e. which two groups do you want to compare)
> res <- results(dds, contrast=c("Origin_SymState_Temp", "RI_B_18", "VA_B_18"))
> head(res)
log2 fold change (MLE): Origin_SymState_Temp RI_B_18 vs VA_B_18 
Wald test p-value: Origin_SymState_Temp RI_B_18 vs VA_B_18 
DataFrame with 6 rows and 6 columns
                        baseMean log2FoldChange     lfcSE      stat
                       <numeric>      <numeric> <numeric> <numeric>
TR10083|c0_g2_i1_coral   5.92149      -0.124352  0.881723 -0.141032
TR10090|c0_g1_i1_coral   2.41467       0.403769  0.959279  0.420909
TR10090|c0_g2_i1_coral   3.75861      -0.835423  0.865239 -0.965540
TR10103|c0_g1_i1_coral   2.98376      -0.801464  0.848308 -0.944780
TR10108|c0_g1_i1_coral   5.73440      -0.526701  0.837420 -0.628957
TR10132|c0_g1_i1_coral   8.52630       1.071572  1.160128  0.923667
                          pvalue      padj
                       <numeric> <numeric>
TR10083|c0_g2_i1_coral  0.887844  0.996375
TR10090|c0_g1_i1_coral  0.673822  0.990719
TR10090|c0_g2_i1_coral  0.334274  0.964876
TR10103|c0_g1_i1_coral  0.344771  0.967913
TR10108|c0_g1_i1_coral  0.529377  0.987729
TR10132|c0_g1_i1_coral  0.355660  0.967913
> summary(res)

out of 7542 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 3, 0.04%
LFC < 0 (down)     : 5, 0.066%
outliers [1]       : 4, 0.053%
low counts [2]     : 1, 0.013%
(mean count < 1)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> 
> res <- results(dds, contrast=c("Origin_SymState_Temp", "RI_W_18", "VA_W_18"))
> summary(res)

out of 7542 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 22, 0.29%
LFC < 0 (down)     : 38, 0.5%
outliers [1]       : 4, 0.053%
low counts [2]     : 3801, 50%
(mean count < 6)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> 
> res <- results(dds, contrast=c("Origin_SymState_Temp", "RI_B_14", "VA_B_14"))
> summary(res)

out of 7542 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 8, 0.11%
LFC < 0 (down)     : 4, 0.053%
outliers [1]       : 4, 0.053%
low counts [2]     : 1, 0.013%
(mean count < 1)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> 
> res <- results(dds, contrast=c("Origin_SymState_Temp", "RI_W_14", "VA_W_14"))
> summary(res)

out of 7542 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 10, 0.13%
LFC < 0 (down)     : 3, 0.04%
outliers [1]       : 4, 0.053%
low counts [2]     : 5263, 70%
(mean count < 8)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> 
> res <- results(dds, contrast=c("Origin_SymState_Temp", "RI_B_22", "VA_B_22"))
> summary(res)

out of 7542 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 8, 0.11%
LFC < 0 (down)     : 2, 0.027%
outliers [1]       : 4, 0.053%
low counts [2]     : 1, 0.013%
(mean count < 1)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> 
> res <- results(dds, contrast=c("Origin_SymState_Temp", "RI_W_22", "VA_W_22"))
> summary(res)

out of 7542 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 11, 0.15%
LFC < 0 (down)     : 5, 0.066%
outliers [1]       : 4, 0.053%
low counts [2]     : 146, 1.9%
(mean count < 2)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> 
> head(res[order(res$padj),])
log2 fold change (MLE): Origin_SymState_Temp RI_W_22 vs VA_W_22 
Wald test p-value: Origin_SymState_Temp RI_W_22 vs VA_W_22 
DataFrame with 6 rows and 6 columns
                        baseMean log2FoldChange     lfcSE      stat
                       <numeric>      <numeric> <numeric> <numeric>
TR42879|c0_g2_i1_coral  15.41058       17.05753  3.137478   5.43670
TR13286|c1_g1_i1_coral  32.61026       -3.38044  0.648393  -5.21357
TR47617|c0_g1_i1_coral   3.74656       19.72616  3.835159   5.14351
TR8327|c0_g3_i1_coral    8.73277       19.73384  4.063853   4.85594
TR29560|c0_g1_i1_coral  12.79556        2.74246  0.651668   4.20838
TR58072|c1_g1_i1_coral  53.85583        1.38039  0.330572   4.17576
                            pvalue        padj
                         <numeric>   <numeric>
TR42879|c0_g2_i1_coral 5.42760e-08 0.000401263
TR13286|c1_g1_i1_coral 1.85241e-07 0.000664526
TR47617|c0_g1_i1_coral 2.69658e-07 0.000664526
TR8327|c0_g3_i1_coral  1.19814e-06 0.002214469
TR29560|c0_g1_i1_coral 2.57208e-05 0.036593740
TR58072|c1_g1_i1_coral 2.96987e-05 0.036593740
> plotCounts(dds, "TR2367|c0_g1_i1_coral", intgroup="Origin_SymState_Temp")
> 
> #count the number of significantly differentially expressed genes
> sum(res$padj < 0.3, na.rm =T)
[1] 30
> sum(res$padj < 0.2, na.rm =T)
[1] 20
> sum(res$padj < 0.1, na.rm =T)
[1] 16
> sum(res$pvalue < 0.05, na.rm =T)
[1] 343
> summary(res)

out of 7542 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 11, 0.15%
LFC < 0 (down)     : 5, 0.066%
outliers [1]       : 4, 0.053%
low counts [2]     : 146, 1.9%
(mean count < 2)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results
> scaledcounts = counts(dds, normalized=T)
> head(scaledcounts)
                       RI_B_01_14 RI_B_01_18 RI_B_01_22 RI_B_02_14
TR10083|c0_g2_i1_coral          0    0.84279   2.292953   0.000000
TR10090|c0_g1_i1_coral          0    2.52837   1.146477   0.000000
TR10090|c0_g2_i1_coral          0    3.37116   2.292953   3.553607
TR10103|c0_g1_i1_coral          0    0.84279   4.585907   0.000000
TR10108|c0_g1_i1_coral          0    1.68558   4.585907   0.000000
TR10132|c0_g1_i1_coral          0    5.89953   1.146477  17.768037
                       RI_B_02_18 RI_B_02_22 RI_B_03_14 RI_B_03_22
TR10083|c0_g2_i1_coral   3.273656   4.312157  12.353943   1.269319
TR10090|c0_g1_i1_coral  13.094624   0.000000   0.000000   0.000000
TR10090|c0_g2_i1_coral   0.000000   0.000000   0.000000   3.807956
TR10103|c0_g1_i1_coral   0.000000   8.624315   1.235394   3.807956
TR10108|c0_g1_i1_coral   6.547312   0.000000  13.589337  15.231824
TR10132|c0_g1_i1_coral  49.104839   0.000000   6.176972   2.538637
                       RI_B_04_14 RI_B_04_18 RI_B_04_22 RI_B_05_14
TR10083|c0_g2_i1_coral  12.576774  8.1319863   0.000000   4.298440
TR10090|c0_g1_i1_coral   2.028512  4.0659932   6.219661   0.537305
TR10090|c0_g2_i1_coral   4.868429  3.6593938   0.000000   0.537305
TR10103|c0_g1_i1_coral   6.085536  3.2527945   0.000000   4.835745
TR10108|c0_g1_i1_coral   2.839917  4.8791918  15.549153   5.641703
TR10132|c0_g1_i1_coral   0.000000  0.8131986   3.109831   1.343263
                       RI_B_05_18 RI_B_05_22 RI_B_06_14 RI_B_06_18
TR10083|c0_g2_i1_coral          0  2.3823188  18.130668   3.272361
TR10090|c0_g1_i1_coral          0  0.0000000   0.000000   1.963417
TR10090|c0_g2_i1_coral          0  2.3823188   0.000000   4.581305
TR10103|c0_g1_i1_coral          0  3.9705313   0.000000   3.272361
TR10108|c0_g1_i1_coral          0  0.7941063   6.043556   9.817083
TR10132|c0_g1_i1_coral          0  1.5882125   0.000000   1.308944
                       RI_B_06_22 RI_B_07_14 RI_B_07_18 RI_B_07_22
TR10083|c0_g2_i1_coral   19.38574  1.3676909  7.9128854   36.52879
TR10090|c0_g1_i1_coral    0.00000  0.6838455  1.9782213    0.00000
TR10090|c0_g2_i1_coral    0.00000  3.4192273  0.9891107    0.00000
TR10103|c0_g1_i1_coral    0.00000  2.0515364  1.9782213    0.00000
TR10108|c0_g1_i1_coral   42.00244  3.4192273  0.9891107    0.00000
TR10132|c0_g1_i1_coral    0.00000  8.2061454 43.5208696   27.39659
                       RI_W_01_14 RI_W_01_18 RI_W_01_22 RI_W_02_14
TR10083|c0_g2_i1_coral   63.29565  10.257613   4.369327   0.000000
TR10090|c0_g1_i1_coral    0.00000  11.625295   1.456442   0.000000
TR10090|c0_g2_i1_coral    0.00000  11.625295   7.282212   4.027688
TR10103|c0_g1_i1_coral   28.77075   7.522249   0.000000   0.000000
TR10108|c0_g1_i1_coral    0.00000   2.735363   1.456442   8.055376
TR10132|c0_g1_i1_coral    0.00000   1.367682   0.000000   0.000000
                       RI_W_02_18 RI_W_02_22 RI_W_03_14 RI_W_03_18
TR10083|c0_g2_i1_coral  4.8924878   3.593465   8.078028   5.344367
TR10090|c0_g1_i1_coral  1.9569951   0.000000   4.039014   1.068873
TR10090|c0_g2_i1_coral  4.8924878   4.791286   2.885010   3.206620
TR10103|c0_g1_i1_coral  0.9784976   3.593465   2.885010   3.206620
TR10108|c0_g1_i1_coral  6.8494829   2.395643   2.308008   4.631785
TR10132|c0_g1_i1_coral  5.8709854  44.319396   1.154004   1.068873
                       RI_W_03_22 RI_W_04_14 RI_W_04_18 RI_W_04_22
TR10083|c0_g2_i1_coral  4.4092608   12.32321  2.9466826    17.8865
TR10090|c0_g1_i1_coral  1.4697536    0.00000  3.4377964     0.0000
TR10090|c0_g2_i1_coral  1.4697536    0.00000  7.3667065     0.0000
TR10103|c0_g1_i1_coral  0.9798357    0.00000  0.9822275     0.0000
TR10108|c0_g1_i1_coral  1.9596715   20.53868 12.7689580     0.0000
TR10132|c0_g1_i1_coral  0.9798357   28.75416  7.8578203     0.0000
                       RI_W_05_14 RI_W_05_18 RI_W_05_22 RI_W_06_14
TR10083|c0_g2_i1_coral  3.0758634  0.9718221   5.123934  0.9786798
TR10090|c0_g1_i1_coral  0.8788181  7.7745767   0.000000  0.0000000
TR10090|c0_g2_i1_coral  3.5152724  9.7182208   1.280983  2.9360395
TR10103|c0_g1_i1_coral  3.9546815  1.9436442   2.561967  9.7867983
TR10108|c0_g1_i1_coral  5.2729086  1.9436442   6.404917 10.7654782
TR10132|c0_g1_i1_coral  1.7576362  9.7182208  25.619669  4.8933992
                       RI_W_06_18 RI_W_06_22 RI_W_07_14 RI_W_07_18
TR10083|c0_g2_i1_coral    1.28024   5.416550   4.050051   5.034881
TR10090|c0_g1_i1_coral    0.00000   4.333240   0.000000   0.000000
TR10090|c0_g2_i1_coral    1.28024   7.583169   2.025025   1.006976
TR10103|c0_g1_i1_coral    1.28024   2.166620   5.400067  12.083715
TR10108|c0_g1_i1_coral    0.00000   5.416550   0.000000   1.006976
TR10132|c0_g1_i1_coral    1.28024  41.165776   1.350017   2.013953
                       RI_W_07_22 VA_B_01_14 VA_B_01_18 VA_B_01_22
TR10083|c0_g2_i1_coral   7.075440   2.275221   1.310363   2.753792
TR10090|c0_g1_i1_coral   0.000000   6.825663   6.879404   1.652275
TR10090|c0_g2_i1_coral   5.660352   9.100884   4.258679   5.507584
TR10103|c0_g1_i1_coral   1.415088   3.412832   1.965544   2.753792
TR10108|c0_g1_i1_coral   5.660352   3.412832   6.879404   2.753792
TR10132|c0_g1_i1_coral  89.150546   1.137611   0.982772   0.000000
                       VA_B_02_14 VA_B_02_18 VA_B_02_22 VA_B_03_14
TR10083|c0_g2_i1_coral          0   13.08723  17.568884  15.220246
TR10090|c0_g1_i1_coral          0    0.00000   0.000000   5.534635
TR10090|c0_g2_i1_coral          0    0.00000   0.000000  10.377440
TR10103|c0_g1_i1_coral          0    0.00000   1.952098   2.075488
TR10108|c0_g1_i1_coral          0    0.00000   0.000000  13.836587
TR10132|c0_g1_i1_coral          0    0.00000   7.808393   8.993782
                       VA_B_03_18 VA_B_03_22 VA_B_04_14 VA_B_04_18
TR10083|c0_g2_i1_coral  13.204264   7.514330   0.000000  0.8308866
TR10090|c0_g1_i1_coral   1.980640   7.514330   0.000000  4.1544330
TR10090|c0_g2_i1_coral   3.961279   3.415604   6.526643  2.9081031
TR10103|c0_g1_i1_coral   3.961279   3.415604   4.079152  0.0000000
TR10108|c0_g1_i1_coral  17.165543  20.493627   2.447491  4.5698763
TR10132|c0_g1_i1_coral  28.389167   8.197451   0.000000  2.4926598
                       VA_B_04_22 VA_B_05_14 VA_B_05_18 VA_B_05_22
TR10083|c0_g2_i1_coral   6.207028   1.933974  2.9919941   1.718262
TR10090|c0_g1_i1_coral   3.342246   4.512607  0.9973314   6.873047
TR10090|c0_g2_i1_coral   0.000000   1.289316  0.4986657   5.154785
TR10103|c0_g1_i1_coral   0.000000   0.000000  2.9919941   0.000000
TR10108|c0_g1_i1_coral   3.342246   8.380556  4.9866569   0.000000
TR10132|c0_g1_i1_coral   0.000000   0.000000  4.4879912   5.154785
                       VA_B_06_14 VA_B_06_18 VA_B_06_22 VA_B_07_14
TR10083|c0_g2_i1_coral   1.213849   0.000000  5.4126287   3.585182
TR10090|c0_g1_i1_coral   7.283093   0.000000  0.4510524   0.000000
TR10090|c0_g2_i1_coral   0.000000   3.961279  1.3531572   1.434073
TR10103|c0_g1_i1_coral   4.855395   6.338047  3.6084191   1.434073
TR10108|c0_g1_i1_coral  10.317715   3.961279  3.1573667   2.151109
TR10132|c0_g1_i1_coral  16.386958   2.376767 13.0805193   8.604437
                       VA_B_07_18 VA_B_07_22 VA_W_01_14 VA_W_01_18
TR10083|c0_g2_i1_coral  0.6877679   1.987011   6.431470   7.522889
TR10090|c0_g1_i1_coral  3.4388395   1.987011   3.675126   1.074698
TR10090|c0_g2_i1_coral 14.4431257   5.961033   0.000000   3.761445
TR10103|c0_g1_i1_coral  7.5654468   3.974022   0.000000   3.761445
TR10108|c0_g1_i1_coral  2.0633037   4.967527   1.837563   4.298794
TR10132|c0_g1_i1_coral 15.8186615   1.987011   0.000000  10.209636
                       VA_W_02_14 VA_W_02_18 VA_W_03_14 VA_W_03_18
TR10083|c0_g2_i1_coral   0.000000   4.374769  2.8394448    0.00000
TR10090|c0_g1_i1_coral   6.346543   0.624967  4.9690284    0.00000
TR10090|c0_g2_i1_coral   3.966589  12.499340  6.3887508   36.13826
TR10103|c0_g1_i1_coral   4.759907   0.624967  6.3887508    0.00000
TR10108|c0_g1_i1_coral   0.000000   8.749538  2.8394448    0.00000
TR10132|c0_g1_i1_coral   2.379953  12.499340  0.7098612    0.00000
                       VA_W_03_22 VA_W_04_14 VA_W_04_18 VA_W_04_22
TR10083|c0_g2_i1_coral   6.328591  0.9650112   3.976631   6.009333
TR10090|c0_g1_i1_coral   8.629897  2.4125279   5.302175   3.698051
TR10090|c0_g2_i1_coral   2.876632  1.9300224   7.069566  10.169640
TR10103|c0_g1_i1_coral   2.301306  3.3775391   3.534783   2.773538
TR10108|c0_g1_i1_coral   3.451959  6.2725727  18.557612   7.858358
TR10132|c0_g1_i1_coral  12.081856  2.4125279   0.000000   0.000000
                       VA_W_05_14 VA_W_05_18 VA_W_05_22 VA_W_06_14
TR10083|c0_g2_i1_coral  0.0000000   3.511099  11.297065   4.584168
TR10090|c0_g1_i1_coral  0.0000000   1.003171  11.297065   0.000000
TR10090|c0_g2_i1_coral  0.0000000   2.507928   6.778239   2.750501
TR10103|c0_g1_i1_coral  0.7675164   3.009514   2.259413   7.334669
TR10108|c0_g1_i1_coral  1.5350328   5.015856  35.020902   3.667335
TR10132|c0_g1_i1_coral  2.3025492   8.025369   2.259413   8.251503
                       VA_W_06_18 VA_W_06_22 VA_W_07_14 VA_W_07_18
TR10083|c0_g2_i1_coral  2.3825360   0.000000  9.2975805   1.022439
TR10090|c0_g1_i1_coral  0.7941787   1.585195  1.4303970   1.022439
TR10090|c0_g2_i1_coral  0.7941787   0.000000  5.0063895   3.067318
TR10103|c0_g1_i1_coral  2.3825360   3.962988  4.2911910   0.000000
TR10108|c0_g1_i1_coral  6.3534292   4.755585  2.8607940   1.022439
TR10132|c0_g1_i1_coral 27.0020742  23.777926  0.7151985   6.134635
                       VA_W_07_22
TR10083|c0_g2_i1_coral  0.8584103
TR10090|c0_g1_i1_coral  6.0088720
TR10090|c0_g2_i1_coral  2.5752309
TR10103|c0_g1_i1_coral  1.7168206
TR10108|c0_g1_i1_coral  1.7168206
TR10132|c0_g1_i1_coral  7.7256926
> genes4heatmap<-res[res$pvalue <0.05 & !is.na(res$pvalue),]
> names(genes4heatmap)
[1] "baseMean"       "log2FoldChange" "lfcSE"          "stat"          
[5] "pvalue"         "padj"          
> head(genes4heatmap)
log2 fold change (MLE): Origin_SymState_Temp RI_W_22 vs VA_W_22 
Wald test p-value: Origin_SymState_Temp RI_W_22 vs VA_W_22 
DataFrame with 6 rows and 6 columns
                        baseMean log2FoldChange     lfcSE      stat
                       <numeric>      <numeric> <numeric> <numeric>
TR10090|c0_g1_i1_coral   2.41467       -2.16024  1.066582  -2.02538
TR10450|c0_g1_i1_coral   3.06295       -3.43891  1.358159  -2.53204
TR10768|c0_g1_i1_coral   4.11391        1.64720  0.816317   2.01785
TR10773|c0_g1_i1_coral   2.74300        3.89665  1.286283   3.02939
TR11771|c0_g1_i1_coral   2.86558        2.26910  0.996534   2.27700
TR11938|c0_g1_i2_coral   3.17991        1.92891  0.932250   2.06910
                          pvalue      padj
                       <numeric> <numeric>
TR10090|c0_g1_i1_coral 0.0428281  0.996985
TR10450|c0_g1_i1_coral 0.0113402  0.882510
TR10768|c0_g1_i1_coral 0.0436070  0.996985
TR10773|c0_g1_i1_coral 0.0024505  0.437812
TR11771|c0_g1_i1_coral 0.0227864  0.989064
TR11938|c0_g1_i2_coral 0.0385371  0.996985
> dim(genes4heatmap)
[1] 343   6
> data4heatmap<-scaledcounts[row.names(scaledcounts)%in%row.names(genes4heatmap),]
> dim(data4heatmap)
[1] 343  81
> head(data4heatmap)
                       RI_B_01_14 RI_B_01_18 RI_B_01_22 RI_B_02_14
TR10090|c0_g1_i1_coral    0.00000    2.52837   1.146477   0.000000
TR10450|c0_g1_i1_coral    0.00000    2.52837   0.000000   0.000000
TR10768|c0_g1_i1_coral   10.84813    4.21395   4.585907   7.107215
TR10773|c0_g1_i1_coral    0.00000    5.89953   2.292953   3.553607
TR11771|c0_g1_i1_coral    0.00000    2.52837   3.439430   0.000000
TR11938|c0_g1_i2_coral    0.00000    2.52837   0.000000   0.000000
                       RI_B_02_18 RI_B_02_22 RI_B_03_14 RI_B_03_22
TR10090|c0_g1_i1_coral   13.09462   0.000000   0.000000   0.000000
TR10450|c0_g1_i1_coral    0.00000   6.468236   0.000000   1.269319
TR10768|c0_g1_i1_coral    0.00000   8.624315   1.235394   1.269319
TR10773|c0_g1_i1_coral    0.00000   0.000000   1.235394   0.000000
TR11771|c0_g1_i1_coral    0.00000   0.000000   1.235394   5.077275
TR11938|c0_g1_i2_coral    0.00000   4.312157   2.470789   3.807956
                       RI_B_04_14 RI_B_04_18 RI_B_04_22 RI_B_05_14
TR10090|c0_g1_i1_coral  2.0285120  4.0659932   6.219661  0.5373050
TR10450|c0_g1_i1_coral  2.4342144  0.4065993  18.658984  0.2686525
TR10768|c0_g1_i1_coral  0.8114048  4.8791918   0.000000  2.9551775
TR10773|c0_g1_i1_coral  0.0000000  0.4065993   0.000000  0.0000000
TR11771|c0_g1_i1_coral  1.6228096  4.0659932   0.000000  1.0746100
TR11938|c0_g1_i2_coral  0.0000000  1.2197979   9.329492  4.2984400
                       RI_B_05_18 RI_B_05_22 RI_B_06_14 RI_B_06_18
TR10090|c0_g1_i1_coral   0.000000   0.000000    0.00000   1.963417
TR10450|c0_g1_i1_coral  15.182145   6.352850    0.00000   1.308944
TR10768|c0_g1_i1_coral   0.000000   1.588213    0.00000   4.581305
TR10773|c0_g1_i1_coral   0.000000   0.000000    0.00000   0.000000
TR11771|c0_g1_i1_coral   6.900975   1.588213   12.08711   4.581305
TR11938|c0_g1_i2_coral   4.140585   3.176425    0.00000   1.963417
                       RI_B_06_22 RI_B_07_14 RI_B_07_18 RI_B_07_22
TR10090|c0_g1_i1_coral    0.00000  0.6838455  1.9782213    0.00000
TR10450|c0_g1_i1_coral   42.00244  2.0515364  5.9346640    0.00000
TR10768|c0_g1_i1_coral    0.00000  2.7353818  8.9019960   45.66098
TR10773|c0_g1_i1_coral    0.00000  0.0000000  0.9891107    0.00000
TR11771|c0_g1_i1_coral    0.00000  2.0515364  7.9128854    0.00000
TR11938|c0_g1_i2_coral    0.00000  0.0000000  0.0000000    0.00000
                       RI_W_01_14 RI_W_01_18 RI_W_01_22 RI_W_02_14
TR10090|c0_g1_i1_coral    0.00000  11.625295   1.456442   0.000000
TR10450|c0_g1_i1_coral    0.00000   0.000000   0.000000   4.027688
TR10768|c0_g1_i1_coral   17.26245   7.522249   1.456442   0.000000
TR10773|c0_g1_i1_coral    0.00000   7.522249  16.020867   0.000000
TR11771|c0_g1_i1_coral    0.00000   2.051523   2.912885   0.000000
TR11938|c0_g1_i2_coral    0.00000   4.103045   1.456442   2.013844
                       RI_W_02_18 RI_W_02_22 RI_W_03_14 RI_W_03_18
TR10090|c0_g1_i1_coral   1.956995   0.000000   4.039014   1.068873
TR10450|c0_g1_i1_coral   0.000000   1.197822   1.154004   0.000000
TR10768|c0_g1_i1_coral   4.892488   5.989108   4.616016   2.850329
TR10773|c0_g1_i1_coral  14.677463   5.989108  21.926075  12.470189
TR11771|c0_g1_i1_coral   5.870985  14.373858   4.616016   1.781456
TR11938|c0_g1_i2_coral   2.935493  10.780394   4.039014   1.425164
                       RI_W_03_22 RI_W_04_14 RI_W_04_18 RI_W_04_22
TR10090|c0_g1_i1_coral  1.4697536    0.00000   3.437796     0.0000
TR10450|c0_g1_i1_coral  0.0000000    0.00000   4.911138     0.0000
TR10768|c0_g1_i1_coral  6.8588501    0.00000   2.946683    17.8865
TR10773|c0_g1_i1_coral 26.9454824    0.00000   1.964455     0.0000
TR11771|c0_g1_i1_coral  0.4899179    0.00000   1.964455     0.0000
TR11938|c0_g1_i2_coral  3.4294250   12.32321   3.928910     0.0000
                       RI_W_05_14 RI_W_05_18 RI_W_05_22 RI_W_06_14
TR10090|c0_g1_i1_coral  0.8788181  7.7745767   0.000000   0.000000
TR10450|c0_g1_i1_coral  1.3182272  0.9718221   0.000000   1.957360
TR10768|c0_g1_i1_coral  5.7123177  0.9718221   3.842950   0.000000
TR10773|c0_g1_i1_coral  5.2729086  1.9436442   0.000000   4.893399
TR11771|c0_g1_i1_coral  4.3940905  1.9436442   5.123934   4.893399
TR11938|c0_g1_i2_coral  2.6364543  2.9154662   5.123934   6.850759
                       RI_W_06_18 RI_W_06_22 RI_W_07_14 RI_W_07_18
TR10090|c0_g1_i1_coral   0.000000   4.333240  0.0000000   0.000000
TR10450|c0_g1_i1_coral   1.280240   0.000000  0.6750084   2.013953
TR10768|c0_g1_i1_coral   7.681439   5.416550  6.7500843   3.020929
TR10773|c0_g1_i1_coral   2.560480   9.749789  1.3500169   2.013953
TR11771|c0_g1_i1_coral   0.000000   3.249930  0.6750084   2.013953
TR11938|c0_g1_i2_coral   0.000000   2.166620  1.3500169   8.055810
                       RI_W_07_22 VA_B_01_14 VA_B_01_18 VA_B_01_22
TR10090|c0_g1_i1_coral   0.000000   6.825663   6.879404  1.6522753
TR10450|c0_g1_i1_coral   0.000000   5.688053  15.724353  2.7537921
TR10768|c0_g1_i1_coral   2.830176   1.137611   6.224223  3.8553090
TR10773|c0_g1_i1_coral   0.000000   5.688053   3.603497  2.7537921
TR11771|c0_g1_i1_coral  14.150880   3.412832   1.965544  0.5507584
TR11938|c0_g1_i2_coral   2.830176   3.412832   3.931088  1.1015169
                       VA_B_02_14 VA_B_02_18 VA_B_02_22 VA_B_03_14
TR10090|c0_g1_i1_coral   0.000000   0.000000   0.000000   5.534635
TR10450|c0_g1_i1_coral   0.000000   8.328238   0.000000   0.000000
TR10768|c0_g1_i1_coral   1.417949   0.000000   3.904196   4.842806
TR10773|c0_g1_i1_coral   1.417949   0.000000   5.856295   0.000000
TR11771|c0_g1_i1_coral   0.000000   0.000000   0.000000   9.685611
TR11938|c0_g1_i2_coral   4.253846   0.000000   0.000000   2.075488
                       VA_B_03_18 VA_B_03_22 VA_B_04_14 VA_B_04_18
TR10090|c0_g1_i1_coral   1.980640  7.5143298   0.000000   4.154433
TR10450|c0_g1_i1_coral   1.320426  2.7324836   0.000000   0.000000
TR10768|c0_g1_i1_coral   2.640853  2.0493627   1.631661   1.246330
TR10773|c0_g1_i1_coral   1.320426  0.6831209   0.000000   6.647093
TR11771|c0_g1_i1_coral   1.980640  0.0000000   0.000000   2.908103
TR11938|c0_g1_i2_coral   3.301066  3.4156045   2.447491   4.985320
                       VA_B_04_22 VA_B_05_14 VA_B_05_18 VA_B_05_22
TR10090|c0_g1_i1_coral   3.342246   4.512607  0.9973314   6.873047
TR10450|c0_g1_i1_coral   1.909855   1.611645  1.4959971   0.000000
TR10768|c0_g1_i1_coral   0.000000   3.867949  2.4933284   0.000000
TR10773|c0_g1_i1_coral   7.639419   1.289316  0.9973314   0.000000
TR11771|c0_g1_i1_coral   0.000000   2.578632  2.9919941   5.154785
TR11938|c0_g1_i2_coral   7.161955   2.256303  3.9893255   1.718262
                       VA_B_06_14 VA_B_06_18 VA_B_06_22 VA_B_07_14
TR10090|c0_g1_i1_coral   7.283093   0.000000  0.4510524   0.000000
TR10450|c0_g1_i1_coral   1.820773   0.000000  4.5105239   0.000000
TR10768|c0_g1_i1_coral   6.676168   2.376767  4.5105239   2.151109
TR10773|c0_g1_i1_coral   2.427698   0.000000  4.9615763   1.434073
TR11771|c0_g1_i1_coral   3.641546   5.545791  1.3531572   4.302218
TR11938|c0_g1_i2_coral   7.283093   0.000000  3.6084191   7.170364
                       VA_B_07_18 VA_B_07_22 VA_W_01_14 VA_W_01_18
TR10090|c0_g1_i1_coral   3.438839  1.9870109   3.675126   1.074698
TR10450|c0_g1_i1_coral   1.375536  0.9935055   0.000000   5.373492
TR10768|c0_g1_i1_coral   1.375536  2.9805164   1.837563   8.060239
TR10773|c0_g1_i1_coral   2.751072  5.9610327   5.512689   1.074698
TR11771|c0_g1_i1_coral   0.000000  4.9675273   5.512689   1.612048
TR11938|c0_g1_i2_coral   8.253215 10.9285600   2.756344   3.224095
                       VA_W_02_14 VA_W_02_18 VA_W_03_14 VA_W_03_18
TR10090|c0_g1_i1_coral   6.346543   0.624967   4.969028    0.00000
TR10450|c0_g1_i1_coral   0.000000   1.874901   4.969028   31.88670
TR10768|c0_g1_i1_coral   1.586636   6.249670   2.839445    0.00000
TR10773|c0_g1_i1_coral   0.000000   3.749802   1.419722    0.00000
TR11771|c0_g1_i1_coral   1.586636   3.124835   7.098612   21.25780
TR11938|c0_g1_i2_coral   1.586636   6.874637   4.259167   23.38358
                       VA_W_03_22 VA_W_04_14 VA_W_04_18 VA_W_04_22
TR10090|c0_g1_i1_coral   8.629897  2.4125279   5.302175  3.6980510
TR10450|c0_g1_i1_coral   1.150653  0.9650112   0.000000  1.8490255
TR10768|c0_g1_i1_coral   1.725979  1.4475168   3.976631  2.3112819
TR10773|c0_g1_i1_coral   2.301306  0.9650112   0.000000  0.4622564
TR11771|c0_g1_i1_coral   1.725979  0.0000000   0.000000  0.4622564
TR11938|c0_g1_i2_coral   1.725979  4.8250559   1.767392  0.4622564
                       VA_W_05_14 VA_W_05_18 VA_W_05_22 VA_W_06_14
TR10090|c0_g1_i1_coral          0  1.0031712  11.297065   0.000000
TR10450|c0_g1_i1_coral          0  0.0000000  12.426772   1.833667
TR10768|c0_g1_i1_coral          0  6.5206127   0.000000   2.750501
TR10773|c0_g1_i1_coral          0  0.0000000   0.000000   0.000000
TR11771|c0_g1_i1_coral          0  0.5015856   1.129707   1.833667
TR11938|c0_g1_i2_coral          0  2.5079280   0.000000   1.833667
                       VA_W_06_18 VA_W_06_22 VA_W_07_14 VA_W_07_18
TR10090|c0_g1_i1_coral  0.7941787  1.5851950  1.4303970   1.022439
TR10450|c0_g1_i1_coral  1.5883573  3.9629876  2.1455955   0.000000
TR10768|c0_g1_i1_coral  5.5592506  0.0000000  2.8607940   8.179514
TR10773|c0_g1_i1_coral  1.5883573  0.0000000  0.0000000   0.000000
TR11771|c0_g1_i1_coral  2.3825360  0.7925975  0.7151985   4.089757
TR11938|c0_g1_i2_coral  0.7941787  2.3777926  1.4303970   0.000000
                       VA_W_07_22
TR10090|c0_g1_i1_coral  6.0088720
TR10450|c0_g1_i1_coral  3.4336412
TR10768|c0_g1_i1_coral  3.4336412
TR10773|c0_g1_i1_coral  0.0000000
TR11771|c0_g1_i1_coral  2.5752309
TR11938|c0_g1_i2_coral  0.8584103
> temp = as.matrix(rowMeans(data4heatmap))
> head(temp)
                           [,1]
TR10090|c0_g1_i1_coral 2.414669
TR10450|c0_g1_i1_coral 3.062953
TR10768|c0_g1_i1_coral 4.113910
TR10773|c0_g1_i1_coral 2.742998
TR11771|c0_g1_i1_coral 2.865582
TR11938|c0_g1_i2_coral 3.179912
> scaledmatrix<-matrix(data=temp, nrow=nrow(data4heatmap), ncol=ncol(data4heatmap), byrow=FALSE)
> data4heatmapscaled = data4heatmap/scaledmatrix
> head(data4heatmapscaled)
                       RI_B_01_14 RI_B_01_18 RI_B_01_22 RI_B_02_14
TR10090|c0_g1_i1_coral   0.000000  1.0470877  0.4747967   0.000000
TR10450|c0_g1_i1_coral   0.000000  0.8254680  0.0000000   0.000000
TR10768|c0_g1_i1_coral   2.636938  1.0243174  1.1147318   1.727606
TR10773|c0_g1_i1_coral   0.000000  2.1507597  0.8359295   1.295519
TR11771|c0_g1_i1_coral   0.000000  0.8823235  1.2002554   0.000000
TR11938|c0_g1_i2_coral   0.000000  0.7951069  0.0000000   0.000000
                       RI_B_02_18 RI_B_02_22 RI_B_03_14 RI_B_03_22
TR10090|c0_g1_i1_coral   5.422948   0.000000  0.0000000  0.0000000
TR10450|c0_g1_i1_coral   0.000000   2.111764  0.0000000  0.4144100
TR10768|c0_g1_i1_coral   0.000000   2.096379  0.3002969  0.3085431
TR10773|c0_g1_i1_coral   0.000000   0.000000  0.4503810  0.0000000
TR11771|c0_g1_i1_coral   0.000000   0.000000  0.4311147  1.7718129
TR11938|c0_g1_i2_coral   0.000000   1.356062  0.7769990  1.1975035
                       RI_B_04_14 RI_B_04_18 RI_B_04_22 RI_B_05_14
TR10090|c0_g1_i1_coral  0.8400788  1.6838720   2.575782 0.22251707
TR10450|c0_g1_i1_coral  0.7947279  0.1327475   6.091827 0.08771028
TR10768|c0_g1_i1_coral  0.1972344  1.1860229   0.000000 0.71833786
TR10773|c0_g1_i1_coral  0.0000000  0.1482317   0.000000 0.00000000
TR11771|c0_g1_i1_coral  0.5663107  1.4189067   0.000000 0.37500589
TR11938|c0_g1_i2_coral  0.0000000  0.3835949   2.933884 1.35174810
                       RI_B_05_18 RI_B_05_22 RI_B_06_14 RI_B_06_18
TR10090|c0_g1_i1_coral   0.000000  0.0000000   0.000000  0.8131205
TR10450|c0_g1_i1_coral   4.956701  2.0740929   0.000000  0.4273471
TR10768|c0_g1_i1_coral   0.000000  0.3860591   0.000000  1.1136133
TR10773|c0_g1_i1_coral   0.000000  0.0000000   0.000000  0.0000000
TR11771|c0_g1_i1_coral   2.408228  0.5542374   4.218031  1.5987348
TR11938|c0_g1_i2_coral   1.302107  0.9989034   0.000000  0.6174437
                       RI_B_06_22 RI_B_07_14 RI_B_07_18 RI_B_07_22
TR10090|c0_g1_i1_coral    0.00000  0.2832047  0.8192517    0.00000
TR10450|c0_g1_i1_coral   13.71305  0.6697903  1.9375626    0.00000
TR10768|c0_g1_i1_coral    0.00000  0.6649104  2.1638771   11.09917
TR10773|c0_g1_i1_coral    0.00000  0.0000000  0.3605947    0.00000
TR11771|c0_g1_i1_coral    0.00000  0.7159232  2.7613540    0.00000
TR11938|c0_g1_i2_coral    0.00000  0.0000000  0.0000000    0.00000
                       RI_W_01_14 RI_W_01_18 RI_W_01_22 RI_W_02_14
TR10090|c0_g1_i1_coral   0.000000  4.8144470  0.6031645  0.0000000
TR10450|c0_g1_i1_coral   0.000000  0.0000000  0.0000000  1.3149687
TR10768|c0_g1_i1_coral   4.196117  1.8284914  0.3540287  0.0000000
TR10773|c0_g1_i1_coral   0.000000  2.7423457  5.8406405  0.0000000
TR11771|c0_g1_i1_coral   0.000000  0.7159184  1.0165074  0.0000000
TR11938|c0_g1_i2_coral   0.000000  1.2903015  0.4580134  0.6333018
                       RI_W_02_18 RI_W_02_22 RI_W_03_14 RI_W_03_18
TR10090|c0_g1_i1_coral  0.8104611  0.0000000  1.6726989  0.4426584
TR10450|c0_g1_i1_coral  0.0000000  0.3910675  0.3767618  0.0000000
TR10768|c0_g1_i1_coral  1.1892549  1.4558187  1.1220507  0.6928515
TR10773|c0_g1_i1_coral  5.3508832  2.1834164  7.9934703  4.5461892
TR11771|c0_g1_i1_coral  2.0487936  5.0160350  1.6108477  0.6216733
TR11938|c0_g1_i2_coral  0.9231364  3.3901547  1.2701653  0.4481773
                       RI_W_03_22 RI_W_04_14 RI_W_04_18 RI_W_04_22
TR10090|c0_g1_i1_coral  0.6086771   0.000000  1.4237135    0.00000
TR10450|c0_g1_i1_coral  0.0000000   0.000000  1.6033994    0.00000
TR10768|c0_g1_i1_coral  1.6672338   0.000000  0.7162729    4.34781
TR10773|c0_g1_i1_coral  9.8233684   0.000000  0.7161707    0.00000
TR11771|c0_g1_i1_coral  0.1709663   0.000000  0.6855345    0.00000
TR11938|c0_g1_i2_coral  1.0784654   3.875331  1.2355405    0.00000
                       RI_W_05_14 RI_W_05_18 RI_W_05_22 RI_W_06_14
TR10090|c0_g1_i1_coral  0.3639498  3.2197281  0.0000000  0.0000000
TR10450|c0_g1_i1_coral  0.4303778  0.3172827  0.0000000  0.6390432
TR10768|c0_g1_i1_coral  1.3885373  0.2362283  0.9341357  0.0000000
TR10773|c0_g1_i1_coral  1.9223157  0.7085838  0.0000000  1.7839600
TR11771|c0_g1_i1_coral  1.5334026  0.6782721  1.7880955  1.7076460
TR11938|c0_g1_i2_coral  0.8290966  0.9168387  1.6113445  2.1543863
                       RI_W_06_18 RI_W_06_22 RI_W_07_14 RI_W_07_18
TR10090|c0_g1_i1_coral  0.0000000  1.7945483  0.0000000  0.0000000
TR10450|c0_g1_i1_coral  0.4179756  0.0000000  0.2203783  0.6575198
TR10768|c0_g1_i1_coral  1.8671868  1.3166426  1.6407952  0.7343205
TR10773|c0_g1_i1_coral  0.9334602  3.5544277  0.4921683  0.7342157
TR11771|c0_g1_i1_coral  0.0000000  1.1341257  0.2355572  0.7028076
TR11938|c0_g1_i2_coral  0.0000000  0.6813458  0.4245453  2.5333437
                       RI_W_07_22 VA_B_01_14 VA_B_01_18 VA_B_01_22
TR10090|c0_g1_i1_coral  0.0000000  2.8267494  2.8490054  0.6842658
TR10450|c0_g1_i1_coral  0.0000000  1.8570484  5.1337224  0.8990643
TR10768|c0_g1_i1_coral  0.6879528  0.2765278  1.5129700  0.9371398
TR10773|c0_g1_i1_coral  0.0000000  2.0736626  1.3137075  1.0039351
TR11771|c0_g1_i1_coral  4.9382226  1.1909734  0.6859145  0.1921978
TR11938|c0_g1_i2_coral  0.8900171  1.0732472  1.2362254  0.3463985
                       VA_B_02_14 VA_B_02_18 VA_B_02_22 VA_B_03_14
TR10090|c0_g1_i1_coral  0.0000000   0.000000  0.0000000  2.2920887
TR10450|c0_g1_i1_coral  0.0000000   2.719022  0.0000000  0.0000000
TR10768|c0_g1_i1_coral  0.3446718   0.000000  0.9490232  1.1771782
TR10773|c0_g1_i1_coral  0.5169339   0.000000  2.1349975  0.0000000
TR11771|c0_g1_i1_coral  0.0000000   0.000000  0.0000000  3.3799808
TR11938|c0_g1_i2_coral  1.3377245   0.000000  0.0000000  0.6526873
                       VA_B_03_18 VA_B_03_22 VA_B_04_14 VA_B_04_18
TR10090|c0_g1_i1_coral  0.8202531  3.1119506  0.0000000  1.7204981
TR10450|c0_g1_i1_coral  0.4310958  0.8921074  0.0000000  0.0000000
TR10768|c0_g1_i1_coral  0.6419325  0.4981544  0.3966204  0.3029551
TR10773|c0_g1_i1_coral  0.4813807  0.2490417  0.0000000  2.4232946
TR11771|c0_g1_i1_coral  0.6911824  0.0000000  0.0000000  1.0148387
TR11938|c0_g1_i2_coral  1.0380998  1.0741192  0.7696726  1.5677539
                       VA_B_04_22 VA_B_05_14 VA_B_05_18 VA_B_05_22
TR10090|c0_g1_i1_coral  1.3841426  1.8688306  0.4130303  2.8463728
TR10450|c0_g1_i1_coral  0.6235337  0.5261736  0.4884165  0.0000000
TR10768|c0_g1_i1_coral  0.0000000  0.9402122  0.6060726  0.0000000
TR10773|c0_g1_i1_coral  2.7850616  0.4700390  0.3635917  0.0000000
TR11771|c0_g1_i1_coral  0.0000000  0.8998635  1.0441141  1.7988618
TR11938|c0_g1_i2_coral  2.2522495  0.7095490  1.2545396  0.5403489
                       VA_B_06_14 VA_B_06_18 VA_B_06_22 VA_B_07_14
TR10090|c0_g1_i1_coral  3.0161871  0.0000000  0.1867968  0.0000000
TR10450|c0_g1_i1_coral  0.5944502  0.0000000  1.4726061  0.0000000
TR10768|c0_g1_i1_coral  1.6228279  0.5777393  1.0964079  0.5228868
TR10773|c0_g1_i1_coral  0.8850525  0.0000000  1.8088149  0.5228121
TR11771|c0_g1_i1_coral  1.2707878  1.9353107  0.4722103  1.5013421
TR11938|c0_g1_i2_coral  2.2903441  0.0000000  1.1347544  2.2548938
                       VA_B_07_18 VA_B_07_22 VA_W_01_14 VA_W_01_18
TR10090|c0_g1_i1_coral  1.4241454  0.8228917  1.5220000  0.4450708
TR10450|c0_g1_i1_coral  0.4490880  0.3243619  0.0000000  1.7543500
TR10768|c0_g1_i1_coral  0.3343621  0.7244972  0.4466706  1.9592646
TR10773|c0_g1_i1_coral  1.0029432  2.1731814  2.0097310  0.3917970
TR11771|c0_g1_i1_coral  0.0000000  1.7335145  1.9237590  0.5625552
TR11938|c0_g1_i2_coral  2.5954223  3.4367492  0.8667989  1.0138946
                       VA_W_02_14 VA_W_02_18 VA_W_03_14 VA_W_03_18
TR10090|c0_g1_i1_coral  2.6283285  0.2588210  2.0578510   0.000000
TR10450|c0_g1_i1_coral  0.0000000  0.6121219  1.6222997  10.410443
TR10768|c0_g1_i1_coral  0.3856758  1.5191556  0.6902058   0.000000
TR10773|c0_g1_i1_coral  0.0000000  1.3670450  0.5175805   0.000000
TR11771|c0_g1_i1_coral  0.5536871  1.0904714  2.4771976   7.418320
TR11938|c0_g1_i2_coral  0.4989558  2.1618953  1.3393978   7.353531
                       VA_W_03_22 VA_W_04_14 VA_W_04_18 VA_W_04_22
TR10090|c0_g1_i1_coral  3.5739467  0.9991134  2.1958187  1.5314941
TR10450|c0_g1_i1_coral  0.3756678  0.3150590  0.0000000  0.6036740
TR10768|c0_g1_i1_coral  0.4195472  0.3518591  0.9666305  0.5618212
TR10773|c0_g1_i1_coral  0.8389746  0.3518089  0.0000000  0.1685223
TR11771|c0_g1_i1_coral  0.6023138  0.0000000  0.0000000  0.1613133
TR11938|c0_g1_i2_coral  0.5427759  1.5173552  0.5557989  0.1453677
                       VA_W_05_14 VA_W_05_18 VA_W_05_22 VA_W_06_14
TR10090|c0_g1_i1_coral          0  0.4154488  4.6785155  0.0000000
TR10450|c0_g1_i1_coral          0  0.0000000  4.0571206  0.5986599
TR10768|c0_g1_i1_coral          0  1.5850158  0.0000000  0.6685856
TR10773|c0_g1_i1_coral          0  0.0000000  0.0000000  0.0000000
TR11771|c0_g1_i1_coral          0  0.1750380  0.3942329  0.6398936
TR11938|c0_g1_i2_coral          0  0.7886784  0.0000000  0.5766409
                       VA_W_06_18 VA_W_06_22 VA_W_07_14 VA_W_07_18
TR10090|c0_g1_i1_coral  0.3288976  0.6564855  0.5923782  0.4234284
TR10450|c0_g1_i1_coral  0.5185705  1.2938452  0.7004989  0.0000000
TR10768|c0_g1_i1_coral  1.3513301  0.0000000  0.6953953  1.9882577
TR10773|c0_g1_i1_coral  0.5790588  0.0000000  0.0000000  0.0000000
TR11771|c0_g1_i1_coral  0.8314319  0.2765922  0.2495823  1.4271996
TR11938|c0_g1_i2_coral  0.2497486  0.7477542  0.4498228  0.0000000
                       VA_W_07_22
TR10090|c0_g1_i1_coral  2.4884871
TR10450|c0_g1_i1_coral  1.1210230
TR10768|c0_g1_i1_coral  0.8346417
TR10773|c0_g1_i1_coral  0.0000000
TR11771|c0_g1_i1_coral  0.8986765
TR11938|c0_g1_i2_coral  0.2699478
> 
> dim(data4heatmapscaled)
[1] 343  81
> 
> pairs.breaks <- seq(0, 3.0, by=0.1)
> length(pairs.breaks)
[1] 31
> mycol <- colorpanel(n=30, low="black", high="yellow")
> pdf(file="XXXXXX_byrow.pdf",14,7)
> heatmap.2(data.matrix(data4heatmapscaled), Rowv=T, Colv=F, dendrogram = c("row"), scale="none", keysize=1, breaks=pairs.breaks, col=mycol, trace = "none", symkey = F, density.info = "density", colsep=c(24), sepcolor=c("white"), sepwidth=c(.1,.1), margins=c(10,10), labRow=F)
> dev.off()
RStudioGD 
        2 
> pdf(file="XXXXXX_bycolumn.pdf",14,7)
> heatmap.2(data.matrix(data4heatmapscaled), Rowv=T, Colv=T, dendrogram = c("col"), scale="none", keysize=1, breaks=pairs.breaks, col=mycol, trace = "none", symkey = F, density.info = "density", colsep=c(24), sepcolor=c("white"), sepwidth=c(.1,.1), margins=c(10,10), labRow=F)
> dev.off()
RStudioGD 
        2
> plotPCA(vstCounts[rownames(vstCounts)%in%row.names(genes4heatmap),], intgroup="Origin")
> prop.nullv3 <- apply(countsTable[rownames(countsTable)%in%row.names(genes4heatmap),], 2, function(x) 100*mean(x==0))
> pdf(file="ResNullCounts.pdf",14, 14)
> barplot(prop.nullv3, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> dev.off()
RStudioGD 
        2 

```
## Day12 HW
```sh
#1- mkdir a directory with your name in the 

#2- cp/mv your logfile to the /cm/shared/courses/dbarshis/18AdvBioinf/archive/YOURNAME directory

#3- cp/mv your merged, unfiltered .vcf file YOURINITIALS_unfiltered.vcf into the /cm/shared/courses/dbarshis/18AdvBioinf/archive/YOURNAME directory

#4- cp/mv any other files you might want to keep to the /cm/shared/courses/dbarshis/18AdvBioinf/archive/YOURNAME directory

#5- create an sbatch script to rm -r your sandbox/YOURNAME directory

#6- scp/winscp /cm/shared/courses/dbarshis/18AdvBioinf/classdata/Astrangia_poculata/expressioncounts/ALLLANESFullCounts_summed.txt to your laptop

#7- scp/winscp /cm/shared/courses/dbarshis/18AdvBioinf/classdata/Astrangia_poculata/expressioncounts/ALLLANES_conditions.txt to your laptop

#8- Download the DESeq2Script_advbioinf_day12.R script and work through to generate a PCA of your data.


> library(DESeq2)
> library(gplots)
> library(goseq)
> library(GO.db)
> 
> setwd("/Users/katiecrider/Desktop/Genomics")  # The drag and drop from finder works in R, too.
> 
> #useful functions
> #head() - prints out the top 6 lines
> #dim() - prints the dimensions of a variable
> #nrow() - returns the number of rows in a vector or matrix
> # ?[functionName] - opens documentation describing the function
> 
> #read in your data to make counts table
> countsTable <- read.delim('djbFullCounts_summed.txt', header=TRUE, stringsAsFactors=TRUE, row.names=1)
> head(countsTable)
                       RI_B_01_14 RI_B_01_18 RI_B_01_22 RI_B_02_14 RI_B_02_18 RI_B_02_22
TR10054|c0_g1_i1_coral          0          0          0          0          0          0
TR10054|c0_g2_i1_coral          0          1          6          0          0          0
TR10083|c0_g2_i1_coral          0          1          2          0          1          2
TR10090|c0_g1_i1_coral          0          3          1          0          4          0
TR10090|c0_g2_i1_coral          0          4          2          1          0          0
TR10103|c0_g1_i1_coral          0          1          4          0          0          4
                       RI_B_03_14 RI_B_03_18 RI_B_03_22 RI_B_04_14 RI_B_04_18 RI_B_04_22
TR10054|c0_g1_i1_coral          0          0          0          0          0          0
TR10054|c0_g2_i1_coral          0          0          0          9          1          0
TR10083|c0_g2_i1_coral         10          0          1         31         20          0
TR10090|c0_g1_i1_coral          0          0          0          5         10          2
TR10090|c0_g2_i1_coral          0          0          3         12          9          0
TR10103|c0_g1_i1_coral          1          0          3         15          8          0
                       RI_B_05_14 RI_B_05_18 RI_B_05_22 RI_B_06_14 RI_B_06_18 RI_B_06_22
TR10054|c0_g1_i1_coral          0          0          0          0          0          0
TR10054|c0_g2_i1_coral          2          0          0          0          2          0
TR10083|c0_g2_i1_coral         16          0          3          3          5          6
TR10090|c0_g1_i1_coral          2          0          0          0          3          0
TR10090|c0_g2_i1_coral          2          0          3          0          7          0
TR10103|c0_g1_i1_coral         18          0          5          0          5          0
                       RI_B_07_14 RI_B_07_18 RI_B_07_22 RI_W_01_14 RI_W_01_18 RI_W_01_22
TR10054|c0_g1_i1_coral          0          0          0          0          0          0
TR10054|c0_g2_i1_coral          2          1          0          0          0          1
TR10083|c0_g2_i1_coral          2          8          4         11         15          3
TR10090|c0_g1_i1_coral          1          2          0          0         17          1
TR10090|c0_g2_i1_coral          5          1          0          0         17          5
TR10103|c0_g1_i1_coral          3          2          0          5         11          0
                       RI_W_02_14 RI_W_02_18 RI_W_02_22 RI_W_03_14 RI_W_03_18 RI_W_03_22
TR10054|c0_g1_i1_coral          0          0          0          0          0          0
TR10054|c0_g2_i1_coral          1          1          2          0          5          0
TR10083|c0_g2_i1_coral          0          5          3         14         15          9
TR10090|c0_g1_i1_coral          0          2          0          7          3          3
TR10090|c0_g2_i1_coral          2          5          4          5          9          3
TR10103|c0_g1_i1_coral          0          1          3          5          9          2
                       RI_W_04_14 RI_W_04_18 RI_W_04_22 RI_W_05_14 RI_W_05_18 RI_W_05_22
TR10054|c0_g1_i1_coral          0          0          0          0          0          0
TR10054|c0_g2_i1_coral          1          1          0          2          0          0
TR10083|c0_g2_i1_coral          3          6          1          7          1          4
TR10090|c0_g1_i1_coral          0          7          0          2          8          0
TR10090|c0_g2_i1_coral          0         15          0          8         10          1
TR10103|c0_g1_i1_coral          0          2          0          9          2          2
                       RI_W_06_14 RI_W_06_18 RI_W_06_22 RI_W_07_14 RI_W_07_18 RI_W_07_22
TR10054|c0_g1_i1_coral          0          0          0          0          0          0
TR10054|c0_g2_i1_coral          2          6          0          4          0          0
TR10083|c0_g2_i1_coral          1          1          5          6          5          5
TR10090|c0_g1_i1_coral          0          0          4          0          0          0
TR10090|c0_g2_i1_coral          3          1          7          3          1          4
TR10103|c0_g1_i1_coral         10          1          2          8         12          1
                       VA_B_01_14 VA_B_01_18 VA_B_01_22 VA_B_02_14 VA_B_02_18 VA_B_02_22
TR10054|c0_g1_i1_coral          0          0          0          0          0          0
TR10054|c0_g2_i1_coral          0          2          2          0          0          0
TR10083|c0_g2_i1_coral          2          4          5          0         11          9
TR10090|c0_g1_i1_coral          6         21          3          0          0          0
TR10090|c0_g2_i1_coral          8         13         10          0          0          0
TR10103|c0_g1_i1_coral          3          6          5          0          0          1
                       VA_B_03_14 VA_B_03_18 VA_B_03_22 VA_B_04_14 VA_B_04_18 VA_B_04_22
TR10054|c0_g1_i1_coral          0          0          0          0          0          0
TR10054|c0_g2_i1_coral          1          0          6          0         10          4
TR10083|c0_g2_i1_coral         22         20         11          0          2         13
TR10090|c0_g1_i1_coral          8          3         11          0         10          7
TR10090|c0_g2_i1_coral         15          6          5          8          7          0
TR10103|c0_g1_i1_coral          3          6          5          5          0          0
                       VA_B_05_14 VA_B_05_18 VA_B_05_22 VA_B_06_14 VA_B_06_18 VA_B_06_22
TR10054|c0_g1_i1_coral          0          0          0          0          0          0
TR10054|c0_g2_i1_coral          2          2          0         10          0          1
TR10083|c0_g2_i1_coral          6          6          1          2          0         12
TR10090|c0_g1_i1_coral         14          2          4         12          0          1
TR10090|c0_g2_i1_coral          4          1          3          0          5          3
TR10103|c0_g1_i1_coral          0          6          0          8          8          8
                       VA_B_07_14 VA_B_07_18 VA_B_07_22 VA_W_01_14 VA_W_01_18 VA_W_01_22
TR10054|c0_g1_i1_coral          0          0          0          0          0          0
TR10054|c0_g2_i1_coral          0          4          1          1          3          0
TR10083|c0_g2_i1_coral          5          1          2          7         14          0
TR10090|c0_g1_i1_coral          0          5          2          4          2          0
TR10090|c0_g2_i1_coral          2         21          6          0          7          0
TR10103|c0_g1_i1_coral          2         11          4          0          7          0
                       VA_W_02_14 VA_W_02_18 VA_W_02_22 VA_W_03_14 VA_W_03_18 VA_W_03_22
TR10054|c0_g1_i1_coral          0          0          0          0          0          0
TR10054|c0_g2_i1_coral          4          0          0          4          0          6
TR10083|c0_g2_i1_coral          0          7          0          4          0         11
TR10090|c0_g1_i1_coral          8          1          0          7          0         15
TR10090|c0_g2_i1_coral          5         20          0          9         17          5
TR10103|c0_g1_i1_coral          6          1          0          9          0          4
                       VA_W_04_14 VA_W_04_18 VA_W_04_22 VA_W_05_14 VA_W_05_18 VA_W_05_22
TR10054|c0_g1_i1_coral          0          0          0          0          0          0
TR10054|c0_g2_i1_coral          2          0          2          0          3          0
TR10083|c0_g2_i1_coral          2          9         13          0          7         10
TR10090|c0_g1_i1_coral          5         12          8          0          2         10
TR10090|c0_g2_i1_coral          4         16         22          0          5          6
TR10103|c0_g1_i1_coral          7          8          6          1          6          2
                       VA_W_06_14 VA_W_06_18 VA_W_06_22 VA_W_07_14 VA_W_07_18 VA_W_07_22
TR10054|c0_g1_i1_coral          0          0          0          0          0          0
TR10054|c0_g2_i1_coral          2          0          0          0          0          3
TR10083|c0_g2_i1_coral          5          3          0         13          1          1
TR10090|c0_g1_i1_coral          0          1          2          2          1          7
TR10090|c0_g2_i1_coral          3          1          0          7          3          3
TR10103|c0_g1_i1_coral          8          3          5          6          0          2
> dim(countsTable)
[1] 13381    84
> 
> colSums(countsTable)
RI_B_01_14 RI_B_01_18 RI_B_01_22 RI_B_02_14 RI_B_02_18 RI_B_02_22 RI_B_03_14 RI_B_03_18 
     97406     207372     173843      47481      58036      84501     170330       5972 
RI_B_03_22 RI_B_04_14 RI_B_04_18 RI_B_04_22 RI_B_05_14 RI_B_05_18 RI_B_05_22 RI_B_06_14 
    199204     357124     544267      71600     630609     227313     225639      37012 
RI_B_06_18 RI_B_06_22 RI_B_07_14 RI_B_07_18 RI_B_07_22 RI_W_01_14 RI_W_01_18 RI_W_01_22 
    296071      72254     257730     218198      25369      39419     292612     174666 
RI_W_02_14 RI_W_02_18 RI_W_02_22 RI_W_03_14 RI_W_03_18 RI_W_03_22 RI_W_04_14 RI_W_04_18 
     54184     192092     155178     281297     428532     359053      37579     300578 
RI_W_04_22 RI_W_05_14 RI_W_05_18 RI_W_05_22 RI_W_06_14 RI_W_06_18 RI_W_06_22 RI_W_07_14 
     10848     392818     214887     158683     186568     205135     198272     342795 
RI_W_07_18 RI_W_07_22 VA_B_01_14 VA_B_01_18 VA_B_01_22 VA_B_02_14 VA_B_02_18 VA_B_02_22 
    220630     176946     261824     548448     328198      79276     152742      85224 
VA_B_03_14 VA_B_03_18 VA_B_03_22 VA_B_04_14 VA_B_04_18 VA_B_04_22 VA_B_05_14 VA_B_05_18 
    226784     251696     271959     172636     264192     268290     323715     288121 
VA_B_05_22 VA_B_06_14 VA_B_06_18 VA_B_06_22 VA_B_07_14 VA_B_07_18 VA_B_07_22 VA_W_01_14 
     89943     232578     195521     362054     215616     234465     169742     164874 
VA_W_01_18 VA_W_01_22 VA_W_02_14 VA_W_02_18 VA_W_02_22 VA_W_03_14 VA_W_03_18 VA_W_03_22 
    321900        313     170250     241804        134     278000     138573     295382 
VA_W_04_14 VA_W_04_18 VA_W_04_22 VA_W_05_14 VA_W_05_18 VA_W_05_22 VA_W_06_14 VA_W_06_18 
    292041     280007     261344     178096     388532     157123     176579     188506 
VA_W_06_22 VA_W_07_14 VA_W_07_18 VA_W_07_22 
    209003     228792     171481     233899 
> colSums(countsTable)[order(colSums(countsTable))]
VA_W_02_22 VA_W_01_22 RI_B_03_18 RI_W_04_22 RI_B_07_22 RI_B_06_14 RI_W_04_14 RI_W_01_14 
       134        313       5972      10848      25369      37012      37579      39419 
RI_B_02_14 RI_W_02_14 RI_B_02_18 RI_B_04_22 RI_B_06_22 VA_B_02_14 RI_B_02_22 VA_B_02_22 
     47481      54184      58036      71600      72254      79276      84501      85224 
VA_B_05_22 RI_B_01_14 VA_W_03_18 VA_B_02_18 RI_W_02_22 VA_W_05_22 RI_W_05_22 VA_W_01_14 
     89943      97406     138573     152742     155178     157123     158683     164874 
VA_B_07_22 VA_W_02_14 RI_B_03_14 VA_W_07_18 VA_B_04_14 RI_B_01_22 RI_W_01_22 VA_W_06_14 
    169742     170250     170330     171481     172636     173843     174666     176579 
RI_W_07_22 VA_W_05_14 RI_W_06_14 VA_W_06_18 RI_W_02_18 VA_B_06_18 RI_W_06_22 RI_B_03_22 
    176946     178096     186568     188506     192092     195521     198272     199204 
RI_W_06_18 RI_B_01_18 VA_W_06_22 RI_W_05_18 VA_B_07_14 RI_B_07_18 RI_W_07_18 RI_B_05_22 
    205135     207372     209003     214887     215616     218198     220630     225639 
VA_B_03_14 RI_B_05_18 VA_W_07_14 VA_B_06_14 VA_W_07_22 VA_B_07_18 VA_W_02_18 VA_B_03_18 
    226784     227313     228792     232578     233899     234465     241804     251696 
RI_B_07_14 VA_W_04_22 VA_B_01_14 VA_B_04_18 VA_B_04_22 VA_B_03_22 VA_W_03_14 VA_W_04_18 
    257730     261344     261824     264192     268290     271959     278000     280007 
RI_W_03_14 VA_B_05_18 VA_W_04_14 RI_W_01_18 VA_W_03_22 RI_B_06_18 RI_W_04_18 VA_W_01_18 
    281297     288121     292041     292612     295382     296071     300578     321900 
VA_B_05_14 VA_B_01_22 RI_W_07_14 RI_B_04_14 RI_W_03_22 VA_B_06_22 VA_W_05_18 RI_W_05_14 
    323715     328198     342795     357124     359053     362054     388532     392818 
RI_W_03_18 RI_B_04_18 VA_B_01_18 RI_B_05_14 
    428532     544267     548448     630609 
> 
> table(substring(names(countsTable),1,2))

RI VA 
42 42 
> table(substring(names(countsTable),4,4))

 B  W 
42 42 
> table(substring(names(countsTable),9,10))

14 18 22 
28 28 28 
> table(paste(substring(names(countsTable),1,2),substring(names(countsTable),4,4), sep="_"))

RI_B RI_W VA_B VA_W 
  21   21   21   21 
> table(paste(substring(names(countsTable),1,2),substring(names(countsTable),4,4), substring(names(countsTable),9,10), sep="_"))

RI_B_14 RI_B_18 RI_B_22 RI_W_14 RI_W_18 RI_W_22 VA_B_14 VA_B_18 VA_B_22 VA_W_14 VA_W_18 VA_W_22 
      7       7       7       7       7       7       7       7       7       7       7       7 
> 
> LowCounts<-c("VA_W_02_22","VA_W_01_22","RI_B_03_18", "RI_W_01_14", "RI_W_04_22", "VA_W_03_18")
> names(countsTable)%in%LowCounts
 [1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[16] FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[31] FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[46] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[61] FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE FALSE  TRUE FALSE FALSE FALSE FALSE
[76] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
> !(names(countsTable)%in%LowCounts)
 [1]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
[16]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
[31]  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
[46]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
[61]  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE FALSE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE
[76]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
> countsTable<-countsTable[,!(names(countsTable)%in%LowCounts)]
> dim(countsTable)
[1] 13381    78
> 
> #make a table with conditions of each individual (e.g. "VA" and "RI")  There should be the same number of conditions described as there are samples in your data file, and in the same order.
> #NOTE: It is absolutely critical that the columns of the count matrix and the rows of the column data (information about samples) are in the same order. DESeq2 will not make guesses as to which column of the count matrix belongs to which row of the column data, these must be provided to DESeq2 already in consistent order.
> #Here's an example
> # Sample		Origin	SymState	Temp  Origin_SymState Origin_SymState_Temp
> # RI_B_06_18		RI	B	18  RI_B  RI_B_18
> # VA_B_07_14		VA	B	14  VA_B  VA_B_14
> # VA_W_07_22		VA	W	22  VA_W  VA_W_22
> # safest way to do this is in R
> 
> conds<-data.frame("Sample"=names(countsTable))
> conds$Origin<-factor(substring(conds$Sample,1,2))
> conds$SymState<-factor(substring(conds$Sample,4,4))
> conds$Temp<-factor(substring(conds$Sample,9,10))
> conds$Origin_SymState<-factor(paste(conds$Origin,conds$SymState, sep="_"))
> conds$Origin_SymState_Temp<-factor(paste(conds$Origin,conds$SymState,conds$Temp, sep="_"))
> 
> ##Check null counts per sample
> prop.null <- apply(countsTable, 2, function(x) 100*mean(x==0))
> 
> barplot(prop.null, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> 
> pdf(file="OverallNullCountsv2.pdf",14, 14)
> barplot(prop.null, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> dev.off()
RStudioGD 
        2 
> 
> # how many genes have mean count >=3 
> means = apply(countsTable, 1, mean)
> table(means>=3)

FALSE  TRUE 
 5721  7660 
> 
> countsTable<-countsTable[means>=3,]
> dim(countsTable)
[1] 7660   78
> 
> prop.nullv2 <- apply(countsTable, 2, function(x) 100*mean(x==0))
> 
> barplot(prop.nullv2, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> 
> pdf(file="Mean3NullCountsv2.pdf",14, 14)
> barplot(prop.nullv2, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> dev.off()
RStudioGD 
        2 
> 
> #make count data sets
> dds <- DESeqDataSetFromMatrix(countData=countsTable, colData=conds, design=~ Origin + SymState + Temp + Origin:SymState)
> 
> dds <- DESeq(dds)
estimating size factors
estimating dispersions
gene-wise dispersion estimates
mean-dispersion relationship
final dispersion estimates
fitting model and testing
-- replacing outliers and refitting for 14 genes
-- DESeq argument 'minReplicatesForReplace' = 7 
-- original counts are preserved in counts(dds)
estimating dispersions
fitting model and testing
> 
> dim(dds)
[1] 7660   78
> 
> #transform counts to variance stablized counts
> vstCounts<-varianceStabilizingTransformation(dds)
> 
> #plot cluster dendrogram across samples
> dists<-dist(t(assay(vstCounts)))
> plot(hclust(dists))
> heatmap.2(as.matrix(dists), key=F, trace="none",
+           col=colorpanel(100, "black", "white"),
+           margin=c(10, 10))
> 
> ###Figure out which contrast you want to examine (i.e. which two groups do you want to compare)
> resultsNames(dds)
[1] "Intercept"          "Origin_VA_vs_RI"    "SymState_W_vs_B"    "Temp_18_vs_14"     
[5] "Temp_22_vs_14"      "OriginVA.SymStateW"
> 
> res <- results(dds)
> head(res)
log2 fold change (MLE): OriginVA.SymStateW 
Wald test p-value: OriginVA.SymStateW 
DataFrame with 6 rows and 6 columns
                        baseMean log2FoldChange     lfcSE      stat    pvalue      padj
                       <numeric>      <numeric> <numeric> <numeric> <numeric> <numeric>
TR10083|c0_g2_i1_coral   5.36648       0.107690  0.644646  0.167053  0.867328  0.999364
TR10090|c0_g1_i1_coral   2.70436      -0.247209  0.831371 -0.297351  0.766198  0.995209
TR10090|c0_g2_i1_coral   3.65756      -0.976997  0.654110 -1.493627  0.135273  0.958807
TR10103|c0_g1_i1_coral   2.91279      -0.172220  0.641026 -0.268662  0.788189  0.995209
TR10108|c0_g1_i1_coral   6.31144       0.366046  0.664401  0.550942  0.581673  0.991107
TR10132|c0_g1_i1_coral   9.26737      -0.589357  0.975809 -0.603967  0.545865  0.990477
> summary(res)

out of 7659 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 2, 0.026%
LFC < 0 (down)     : 9, 0.12%
outliers [1]       : 10, 0.13%
low counts [2]     : 1, 0.013%
(mean count < 1)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> 
> resSymState <- results(dds, contrast=c("SymState", "B", "W"))
> head(resSymState)
log2 fold change (MLE): SymState B vs W 
Wald test p-value: SymState B vs W 
DataFrame with 6 rows and 6 columns
                        baseMean log2FoldChange     lfcSE      stat    pvalue      padj
                       <numeric>      <numeric> <numeric> <numeric> <numeric> <numeric>
TR10083|c0_g2_i1_coral   5.36648       0.304875  0.463588  0.657643 0.5107675  0.986343
TR10090|c0_g1_i1_coral   2.70436      -0.340214  0.624845 -0.544477 0.5861132  0.995961
TR10090|c0_g2_i1_coral   3.65756      -1.044272  0.488673 -2.136956 0.0326015  0.816270
TR10103|c0_g1_i1_coral   2.91279      -0.316211  0.469123 -0.674047 0.5002815  0.986343
TR10108|c0_g1_i1_coral   6.31144       0.257974  0.481341  0.535948 0.5919943  0.995961
TR10132|c0_g1_i1_coral   9.26737      -0.604957  0.692218 -0.873939 0.3821514  0.986343
> summary(resSymState)

out of 7659 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 6, 0.078%
LFC < 0 (down)     : 6, 0.078%
outliers [1]       : 10, 0.13%
low counts [2]     : 1, 0.013%
(mean count < 1)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> 
> resOrigin <- results(dds, contrast=c("Origin", "VA", "RI"))
> head(resOrigin)
log2 fold change (MLE): Origin VA vs RI 
Wald test p-value: Origin VA vs RI 
DataFrame with 6 rows and 6 columns
                        baseMean log2FoldChange     lfcSE       stat    pvalue      padj
                       <numeric>      <numeric> <numeric>  <numeric> <numeric> <numeric>
TR10083|c0_g2_i1_coral   5.36648     -0.2712427  0.446225 -0.6078616 0.5432793  0.865661
TR10090|c0_g1_i1_coral   2.70436      1.1125117  0.589306  1.8878328 0.0590484        NA
TR10090|c0_g2_i1_coral   3.65756      0.9431346  0.474719  1.9867203 0.0469534  0.418043
TR10103|c0_g1_i1_coral   2.91279      0.0386643  0.456720  0.0846565 0.9325345  0.984590
TR10108|c0_g1_i1_coral   6.31144     -0.0179010  0.461958 -0.0387502 0.9690895  0.992150
TR10132|c0_g1_i1_coral   9.26737     -0.2649903  0.677608 -0.3910675 0.6957473  0.921517
> summary(resOrigin)

out of 7659 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 73, 0.95%
LFC < 0 (down)     : 104, 1.4%
outliers [1]       : 10, 0.13%
low counts [2]     : 594, 7.8%
(mean count < 3)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> 
> res14v18 <- results(dds, contrast=c("Temp", "14", "18"))
> head(res14v18)
log2 fold change (MLE): Temp 14 vs 18 
Wald test p-value: Temp 14 vs 18 
DataFrame with 6 rows and 6 columns
                        baseMean log2FoldChange     lfcSE       stat    pvalue      padj
                       <numeric>      <numeric> <numeric>  <numeric> <numeric> <numeric>
TR10083|c0_g2_i1_coral   5.36648      0.0134106  0.389675  0.0344147 0.9725464  0.994763
TR10090|c0_g1_i1_coral   2.70436     -0.7500403  0.493720 -1.5191625 0.1287216        NA
TR10090|c0_g2_i1_coral   3.65756     -0.5278497  0.385227 -1.3702295 0.1706153        NA
TR10103|c0_g1_i1_coral   2.91279      0.1448997  0.377624  0.3837147 0.7011899        NA
TR10108|c0_g1_i1_coral   6.31144     -0.1171316  0.401865 -0.2914700 0.7706919  0.956296
TR10132|c0_g1_i1_coral   9.26737     -1.1666726  0.592603 -1.9687238 0.0489848  0.440134
> summary(res14v18)

out of 7659 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 31, 0.4%
LFC < 0 (down)     : 111, 1.4%
outliers [1]       : 10, 0.13%
low counts [2]     : 2671, 35%
(mean count < 4)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> 
> res14v22 <- results(dds, contrast=c("Temp", "14", "22"))
> head(res14v22)
log2 fold change (MLE): Temp 14 vs 22 
Wald test p-value: Temp 14 vs 22 
DataFrame with 6 rows and 6 columns
                        baseMean log2FoldChange     lfcSE      stat    pvalue      padj
                       <numeric>      <numeric> <numeric> <numeric> <numeric> <numeric>
TR10083|c0_g2_i1_coral   5.36648      -0.381080  0.396906 -0.960127 0.3369915  0.796010
TR10090|c0_g1_i1_coral   2.70436      -0.420391  0.517100 -0.812978 0.4162304        NA
TR10090|c0_g2_i1_coral   3.65756      -0.149468  0.407436 -0.366851 0.7137303        NA
TR10103|c0_g1_i1_coral   2.91279       0.327506  0.400038  0.818686 0.4129654        NA
TR10108|c0_g1_i1_coral   6.31144      -0.504681  0.409220 -1.233275 0.2174733  0.699820
TR10132|c0_g1_i1_coral   9.26737      -1.240058  0.602190 -2.059248 0.0394705  0.387444
> summary(res14v22)

out of 7659 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 64, 0.84%
LFC < 0 (down)     : 97, 1.3%
outliers [1]       : 10, 0.13%
low counts [2]     : 2226, 29%
(mean count < 4)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> 
> res18v22 <- results(dds, contrast=c("Temp", "18", "22"))
> head(res18v22)
log2 fold change (MLE): Temp 18 vs 22 
Wald test p-value: Temp 18 vs 22 
DataFrame with 6 rows and 6 columns
                        baseMean log2FoldChange     lfcSE      stat    pvalue      padj
                       <numeric>      <numeric> <numeric> <numeric> <numeric> <numeric>
TR10083|c0_g2_i1_coral   5.36648     -0.3944906  0.395010 -0.998685  0.317947  0.838585
TR10090|c0_g1_i1_coral   2.70436      0.3296494  0.503430  0.654807  0.512592        NA
TR10090|c0_g2_i1_coral   3.65756      0.3783816  0.396935  0.953259  0.340459  0.847759
TR10103|c0_g1_i1_coral   2.91279      0.1826059  0.399214  0.457414  0.647374        NA
TR10108|c0_g1_i1_coral   6.31144     -0.3875492  0.406736 -0.952828  0.340677  0.847759
TR10132|c0_g1_i1_coral   9.26737     -0.0733858  0.596241 -0.123081  0.902043  0.991572
> summary(res18v22)

out of 7659 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 34, 0.44%
LFC < 0 (down)     : 10, 0.13%
outliers [1]       : 10, 0.13%
low counts [2]     : 1337, 17%
(mean count < 3)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> 
> #count the number of significantly differentially expressed genes
> sum(resOrigin$padj < 0.1, na.rm =T)
[1] 177
> sum(resOrigin$pvalue < 0.05, na.rm =T)
[1] 866
> 
> # Make a counts table that is scaled by the size factors
> scaledcounts = counts(dds, normalize=T)
> head(scaledcounts)
                       RI_B_01_14 RI_B_01_18 RI_B_01_22 RI_B_02_14 RI_B_02_18 RI_B_02_22
TR10083|c0_g2_i1_coral          0  0.8671827   2.447866   0.000000   3.455170   4.432653
TR10090|c0_g1_i1_coral          0  2.6015481   1.223933   0.000000  13.820681   0.000000
TR10090|c0_g2_i1_coral          0  3.4687308   2.447866   3.772786   0.000000   0.000000
TR10103|c0_g1_i1_coral          0  0.8671827   4.895733   0.000000   0.000000   8.865306
TR10108|c0_g1_i1_coral          0  1.7343654   4.895733   0.000000   6.910341   0.000000
TR10132|c0_g1_i1_coral          0  6.0702789   1.223933  18.863931  51.827555   0.000000
                       RI_B_03_14 RI_B_03_22 RI_B_04_14 RI_B_04_18 RI_B_04_22 RI_B_05_14
TR10083|c0_g2_i1_coral  12.871970   1.272998  12.424473  8.1878079   0.000000   4.563408
TR10090|c0_g1_i1_coral   0.000000   0.000000   2.003947  4.0939039   6.765958   0.570426
TR10090|c0_g2_i1_coral   0.000000   3.818995   4.809473  3.6845136   0.000000   0.570426
TR10103|c0_g1_i1_coral   1.287197   3.818995   6.011842  3.2751232   0.000000   5.133834
TR10108|c0_g1_i1_coral  14.159167  15.275980   2.805526  4.9126847  16.914895   5.989473
TR10132|c0_g1_i1_coral   6.435985   2.545997   0.000000  0.8187808   3.382979   1.426065
                       RI_B_05_18 RI_B_05_22 RI_B_06_14 RI_B_06_18 RI_B_06_22 RI_B_07_14
TR10083|c0_g2_i1_coral          0  2.4538305   19.55961   3.448566   18.78455  1.4936671
TR10090|c0_g1_i1_coral          0  0.0000000    0.00000   2.069140    0.00000  0.7468335
TR10090|c0_g2_i1_coral          0  2.4538305    0.00000   4.827992    0.00000  3.7341677
TR10103|c0_g1_i1_coral          0  4.0897176    0.00000   3.448566    0.00000  2.2405006
TR10108|c0_g1_i1_coral          0  0.8179435    6.51987  10.345698   40.69986  3.7341677
TR10132|c0_g1_i1_coral          0  1.6358870    0.00000   1.379426    0.00000  8.9620025
                       RI_B_07_18 RI_B_07_22 RI_W_01_18 RI_W_01_22 RI_W_02_14 RI_W_02_18
TR10083|c0_g2_i1_coral   8.070182   36.85316  10.815190   4.646396   0.000000  4.9947759
TR10090|c0_g1_i1_coral   2.017545    0.00000  12.257216   1.548799   0.000000  1.9979104
TR10090|c0_g2_i1_coral   1.008773    0.00000  12.257216   7.743994   4.651361  4.9947759
TR10103|c0_g1_i1_coral   2.017545    0.00000   7.931140   0.000000   0.000000  0.9989552
TR10108|c0_g1_i1_coral   1.008773    0.00000   2.884051   1.548799   9.302721  6.9926863
TR10132|c0_g1_i1_coral  44.386000   27.63987   1.442025   0.000000   0.000000  5.9937311
                       RI_W_02_22 RI_W_03_14 RI_W_03_18 RI_W_03_22 RI_W_04_14 RI_W_04_18
TR10083|c0_g2_i1_coral   3.615216   8.525621   5.407467   4.745758   12.82564  2.9768406
TR10090|c0_g1_i1_coral   0.000000   4.262810   1.081493   1.581919    0.00000  3.4729807
TR10090|c0_g2_i1_coral   4.820288   3.044865   3.244480   1.581919    0.00000  7.4421015
TR10103|c0_g1_i1_coral   3.615216   3.044865   3.244480   1.054613    0.00000  0.9922802
TR10108|c0_g1_i1_coral   2.410144   2.435892   4.686471   2.109226   21.37607 12.8996426
TR10132|c0_g1_i1_coral  44.587667   1.217946   1.081493   1.054613   29.92650  7.9382416
                       RI_W_05_14 RI_W_05_18 RI_W_05_22 RI_W_06_14 RI_W_06_18 RI_W_06_22
TR10083|c0_g2_i1_coral  3.1630643   1.010704   5.526636   1.044347   1.336966   5.564881
TR10090|c0_g1_i1_coral  0.9037326   8.085630   0.000000   0.000000   0.000000   4.451904
TR10090|c0_g2_i1_coral  3.6149306  10.107037   1.381659   3.133041   1.336966   7.790833
TR10103|c0_g1_i1_coral  4.0667969   2.021407   2.763318  10.443469   1.336966   2.225952
TR10108|c0_g1_i1_coral  5.4223959   2.021407   6.908296  11.487816   0.000000   5.564881
TR10132|c0_g1_i1_coral  1.8074653  10.107037  27.633182   5.221735   1.336966  42.293092
                       RI_W_07_14 RI_W_07_18 RI_W_07_22 VA_B_01_14 VA_B_01_18 VA_B_01_22
TR10083|c0_g2_i1_coral   4.124636   5.593017   6.900578   2.551157   1.731769   2.845097
TR10090|c0_g1_i1_coral   0.000000   0.000000   0.000000   7.653472   9.091789   1.707058
TR10090|c0_g2_i1_coral   2.062318   1.118603   5.520462  10.204629   5.628251   5.690194
TR10103|c0_g1_i1_coral   5.499514  13.423242   1.380116   3.826736   2.597654   2.845097
TR10108|c0_g1_i1_coral   0.000000   1.118603   5.520462   3.826736   9.091789   2.845097
TR10132|c0_g1_i1_coral   1.374879   2.237207  86.947282   1.275579   1.298827   0.000000
                       VA_B_02_14 VA_B_02_18 VA_B_02_22 VA_B_03_14 VA_B_03_18 VA_B_03_22
TR10083|c0_g2_i1_coral          0    14.2516  19.312637  16.029307  14.339493   7.833217
TR10090|c0_g1_i1_coral          0     0.0000   0.000000   5.828839   2.150924   7.833217
TR10090|c0_g2_i1_coral          0     0.0000   0.000000  10.929073   4.301848   3.560553
TR10103|c0_g1_i1_coral          0     0.0000   2.145849   2.185815   4.301848   3.560553
TR10108|c0_g1_i1_coral          0     0.0000   0.000000  14.572098  18.641340  21.363318
TR10132|c0_g1_i1_coral          0     0.0000   8.583394   9.471863  30.829909   8.545327
                       VA_B_04_14 VA_B_04_18 VA_B_04_22 VA_B_05_14 VA_B_05_18 VA_B_05_22
TR10083|c0_g2_i1_coral   0.000000  0.9006809   6.731616   2.098865  3.3173156   1.813677
TR10090|c0_g1_i1_coral   0.000000  4.5034046   3.624716   4.897352  1.1057719   7.254707
TR10090|c0_g2_i1_coral   7.108517  3.1523832   0.000000   1.399244  0.5528859   5.441030
TR10103|c0_g1_i1_coral   4.442823  0.0000000   0.000000   0.000000  3.3173156   0.000000
TR10108|c0_g1_i1_coral   2.665694  4.9537450   3.624716   9.095083  5.5288593   0.000000
TR10132|c0_g1_i1_coral   0.000000  2.7020428   0.000000   0.000000  4.9759734   5.441030
                       VA_B_06_14 VA_B_06_18 VA_B_06_22 VA_B_07_14 VA_B_07_18 VA_B_07_22
TR10083|c0_g2_i1_coral   1.383946   0.000000  5.9098781   3.728534  0.7405861   2.098499
TR10090|c0_g1_i1_coral   8.303676   0.000000  0.4924898   0.000000  3.7029304   2.098499
TR10090|c0_g2_i1_coral   0.000000   4.206352  1.4774695   1.491414 15.5523076   6.295498
TR10103|c0_g1_i1_coral   5.535784   6.730163  3.9399187   1.491414  8.1464468   4.196999
TR10108|c0_g1_i1_coral  11.763540   4.206352  3.4474289   2.237121  2.2217582   5.246248
TR10132|c0_g1_i1_coral  18.683270   2.523811 14.2822054   8.948482 17.0334798   2.098499
                       VA_W_01_14 VA_W_01_18 VA_W_02_14 VA_W_02_18 VA_W_03_14 VA_W_03_22
TR10083|c0_g2_i1_coral   6.699293   7.732656   0.000000  4.5789684  3.1096023   6.888125
TR10090|c0_g1_i1_coral   3.828167   1.104665   6.978382  0.6541383  5.4418040   9.392897
TR10090|c0_g2_i1_coral   0.000000   3.866328   4.361489 13.0827667  6.9966052   3.130966
TR10103|c0_g1_i1_coral   0.000000   3.866328   5.233787  0.6541383  6.9966052   2.504773
TR10108|c0_g1_i1_coral   1.914084   4.418660   0.000000  9.1579367  3.1096023   3.757159
TR10132|c0_g1_i1_coral   0.000000  10.494319   2.616893 13.0827667  0.7774006  13.150056
                       VA_W_04_14 VA_W_04_18 VA_W_04_22 VA_W_05_14 VA_W_05_18 VA_W_05_22
TR10083|c0_g2_i1_coral   1.026752   4.334366   6.410680  0.0000000   3.848517  12.379823
TR10090|c0_g1_i1_coral   2.566880   5.779155   3.945034  0.0000000   1.099576  12.379823
TR10090|c0_g2_i1_coral   2.053504   7.705540  10.848842  0.0000000   2.748941   7.427894
TR10103|c0_g1_i1_coral   3.593631   3.852770   2.958775  0.8118702   3.298729   2.475965
TR10108|c0_g1_i1_coral   6.673887  20.227043   8.383196  1.6237403   5.497882  38.377452
TR10132|c0_g1_i1_coral   2.566880   0.000000   0.000000  2.4356105   8.796611   2.475965
                       VA_W_06_14 VA_W_06_18 VA_W_06_22 VA_W_07_14 VA_W_07_18 VA_W_07_22
TR10083|c0_g2_i1_coral   5.042735  2.5895188   0.000000 10.2466895   1.127608  0.9473408
TR10090|c0_g1_i1_coral   0.000000  0.8631729   1.764014  1.5764138   1.127608  6.6313859
TR10090|c0_g2_i1_coral   3.025641  0.8631729   0.000000  5.5174482   3.382824  2.8420225
TR10103|c0_g1_i1_coral   8.068376  2.5895188   4.410036  4.7292413   0.000000  1.8946817
TR10108|c0_g1_i1_coral   4.034188  6.9053834   5.292043  3.1528275   1.127608  1.8946817
TR10132|c0_g1_i1_coral   9.076923 29.3478796  26.460214  0.7882069   6.765648  8.5260676

> #building heat map data
> head(scaledcounts)
                       RI_B_01_14 RI_B_01_18 RI_B_01_22
TR10083|c0_g2_i1_coral          0  0.8671827   2.447866
TR10090|c0_g1_i1_coral          0  2.6015481   1.223933
TR10090|c0_g2_i1_coral          0  3.4687308   2.447866
TR10103|c0_g1_i1_coral          0  0.8671827   4.895733
TR10108|c0_g1_i1_coral          0  1.7343654   4.895733
TR10132|c0_g1_i1_coral          0  6.0702789   1.223933
                       RI_B_02_14 RI_B_02_18 RI_B_02_22
TR10083|c0_g2_i1_coral   0.000000   3.455170   4.432653
TR10090|c0_g1_i1_coral   0.000000  13.820681   0.000000
TR10090|c0_g2_i1_coral   3.772786   0.000000   0.000000
TR10103|c0_g1_i1_coral   0.000000   0.000000   8.865306
TR10108|c0_g1_i1_coral   0.000000   6.910341   0.000000
TR10132|c0_g1_i1_coral  18.863931  51.827555   0.000000
                       RI_B_03_14 RI_B_03_22 RI_B_04_14
TR10083|c0_g2_i1_coral  12.871970   1.272998  12.424473
TR10090|c0_g1_i1_coral   0.000000   0.000000   2.003947
TR10090|c0_g2_i1_coral   0.000000   3.818995   4.809473
TR10103|c0_g1_i1_coral   1.287197   3.818995   6.011842
TR10108|c0_g1_i1_coral  14.159167  15.275980   2.805526
TR10132|c0_g1_i1_coral   6.435985   2.545997   0.000000
                       RI_B_04_18 RI_B_04_22 RI_B_05_14
TR10083|c0_g2_i1_coral  8.1878079   0.000000   4.563408
TR10090|c0_g1_i1_coral  4.0939039   6.765958   0.570426
TR10090|c0_g2_i1_coral  3.6845136   0.000000   0.570426
TR10103|c0_g1_i1_coral  3.2751232   0.000000   5.133834
TR10108|c0_g1_i1_coral  4.9126847  16.914895   5.989473
TR10132|c0_g1_i1_coral  0.8187808   3.382979   1.426065
                       RI_B_05_18 RI_B_05_22 RI_B_06_14
TR10083|c0_g2_i1_coral          0  2.4538305   19.55961
TR10090|c0_g1_i1_coral          0  0.0000000    0.00000
TR10090|c0_g2_i1_coral          0  2.4538305    0.00000
TR10103|c0_g1_i1_coral          0  4.0897176    0.00000
TR10108|c0_g1_i1_coral          0  0.8179435    6.51987
TR10132|c0_g1_i1_coral          0  1.6358870    0.00000
                       RI_B_06_18 RI_B_06_22 RI_B_07_14
TR10083|c0_g2_i1_coral   3.448566   18.78455  1.4936671
TR10090|c0_g1_i1_coral   2.069140    0.00000  0.7468335
TR10090|c0_g2_i1_coral   4.827992    0.00000  3.7341677
TR10103|c0_g1_i1_coral   3.448566    0.00000  2.2405006
TR10108|c0_g1_i1_coral  10.345698   40.69986  3.7341677
TR10132|c0_g1_i1_coral   1.379426    0.00000  8.9620025
                       RI_B_07_18 RI_B_07_22 RI_W_01_18
TR10083|c0_g2_i1_coral   8.070182   36.85316  10.815190
TR10090|c0_g1_i1_coral   2.017545    0.00000  12.257216
TR10090|c0_g2_i1_coral   1.008773    0.00000  12.257216
TR10103|c0_g1_i1_coral   2.017545    0.00000   7.931140
TR10108|c0_g1_i1_coral   1.008773    0.00000   2.884051
TR10132|c0_g1_i1_coral  44.386000   27.63987   1.442025
                       RI_W_01_22 RI_W_02_14 RI_W_02_18
TR10083|c0_g2_i1_coral   4.646396   0.000000  4.9947759
TR10090|c0_g1_i1_coral   1.548799   0.000000  1.9979104
TR10090|c0_g2_i1_coral   7.743994   4.651361  4.9947759
TR10103|c0_g1_i1_coral   0.000000   0.000000  0.9989552
TR10108|c0_g1_i1_coral   1.548799   9.302721  6.9926863
TR10132|c0_g1_i1_coral   0.000000   0.000000  5.9937311
                       RI_W_02_22 RI_W_03_14 RI_W_03_18
TR10083|c0_g2_i1_coral   3.615216   8.525621   5.407467
TR10090|c0_g1_i1_coral   0.000000   4.262810   1.081493
TR10090|c0_g2_i1_coral   4.820288   3.044865   3.244480
TR10103|c0_g1_i1_coral   3.615216   3.044865   3.244480
TR10108|c0_g1_i1_coral   2.410144   2.435892   4.686471
TR10132|c0_g1_i1_coral  44.587667   1.217946   1.081493
                       RI_W_03_22 RI_W_04_14 RI_W_04_18
TR10083|c0_g2_i1_coral   4.745758   12.82564  2.9768406
TR10090|c0_g1_i1_coral   1.581919    0.00000  3.4729807
TR10090|c0_g2_i1_coral   1.581919    0.00000  7.4421015
TR10103|c0_g1_i1_coral   1.054613    0.00000  0.9922802
TR10108|c0_g1_i1_coral   2.109226   21.37607 12.8996426
TR10132|c0_g1_i1_coral   1.054613   29.92650  7.9382416
                       RI_W_05_14 RI_W_05_18 RI_W_05_22
TR10083|c0_g2_i1_coral  3.1630643   1.010704   5.526636
TR10090|c0_g1_i1_coral  0.9037326   8.085630   0.000000
TR10090|c0_g2_i1_coral  3.6149306  10.107037   1.381659
TR10103|c0_g1_i1_coral  4.0667969   2.021407   2.763318
TR10108|c0_g1_i1_coral  5.4223959   2.021407   6.908296
TR10132|c0_g1_i1_coral  1.8074653  10.107037  27.633182
                       RI_W_06_14 RI_W_06_18 RI_W_06_22
TR10083|c0_g2_i1_coral   1.044347   1.336966   5.564881
TR10090|c0_g1_i1_coral   0.000000   0.000000   4.451904
TR10090|c0_g2_i1_coral   3.133041   1.336966   7.790833
TR10103|c0_g1_i1_coral  10.443469   1.336966   2.225952
TR10108|c0_g1_i1_coral  11.487816   0.000000   5.564881
TR10132|c0_g1_i1_coral   5.221735   1.336966  42.293092
                       RI_W_07_14 RI_W_07_18 RI_W_07_22
TR10083|c0_g2_i1_coral   4.124636   5.593017   6.900578
TR10090|c0_g1_i1_coral   0.000000   0.000000   0.000000
TR10090|c0_g2_i1_coral   2.062318   1.118603   5.520462
TR10103|c0_g1_i1_coral   5.499514  13.423242   1.380116
TR10108|c0_g1_i1_coral   0.000000   1.118603   5.520462
TR10132|c0_g1_i1_coral   1.374879   2.237207  86.947282
                       VA_B_01_14 VA_B_01_18 VA_B_01_22
TR10083|c0_g2_i1_coral   2.551157   1.731769   2.845097
TR10090|c0_g1_i1_coral   7.653472   9.091789   1.707058
TR10090|c0_g2_i1_coral  10.204629   5.628251   5.690194
TR10103|c0_g1_i1_coral   3.826736   2.597654   2.845097
TR10108|c0_g1_i1_coral   3.826736   9.091789   2.845097
TR10132|c0_g1_i1_coral   1.275579   1.298827   0.000000
                       VA_B_02_14 VA_B_02_18 VA_B_02_22
TR10083|c0_g2_i1_coral          0    14.2516  19.312637
TR10090|c0_g1_i1_coral          0     0.0000   0.000000
TR10090|c0_g2_i1_coral          0     0.0000   0.000000
TR10103|c0_g1_i1_coral          0     0.0000   2.145849
TR10108|c0_g1_i1_coral          0     0.0000   0.000000
TR10132|c0_g1_i1_coral          0     0.0000   8.583394
                       VA_B_03_14 VA_B_03_18 VA_B_03_22
TR10083|c0_g2_i1_coral  16.029307  14.339493   7.833217
TR10090|c0_g1_i1_coral   5.828839   2.150924   7.833217
TR10090|c0_g2_i1_coral  10.929073   4.301848   3.560553
TR10103|c0_g1_i1_coral   2.185815   4.301848   3.560553
TR10108|c0_g1_i1_coral  14.572098  18.641340  21.363318
TR10132|c0_g1_i1_coral   9.471863  30.829909   8.545327
                       VA_B_04_14 VA_B_04_18 VA_B_04_22
TR10083|c0_g2_i1_coral   0.000000  0.9006809   6.731616
TR10090|c0_g1_i1_coral   0.000000  4.5034046   3.624716
TR10090|c0_g2_i1_coral   7.108517  3.1523832   0.000000
TR10103|c0_g1_i1_coral   4.442823  0.0000000   0.000000
TR10108|c0_g1_i1_coral   2.665694  4.9537450   3.624716
TR10132|c0_g1_i1_coral   0.000000  2.7020428   0.000000
                       VA_B_05_14 VA_B_05_18 VA_B_05_22
TR10083|c0_g2_i1_coral   2.098865  3.3173156   1.813677
TR10090|c0_g1_i1_coral   4.897352  1.1057719   7.254707
TR10090|c0_g2_i1_coral   1.399244  0.5528859   5.441030
TR10103|c0_g1_i1_coral   0.000000  3.3173156   0.000000
TR10108|c0_g1_i1_coral   9.095083  5.5288593   0.000000
TR10132|c0_g1_i1_coral   0.000000  4.9759734   5.441030
                       VA_B_06_14 VA_B_06_18 VA_B_06_22
TR10083|c0_g2_i1_coral   1.383946   0.000000  5.9098781
TR10090|c0_g1_i1_coral   8.303676   0.000000  0.4924898
TR10090|c0_g2_i1_coral   0.000000   4.206352  1.4774695
TR10103|c0_g1_i1_coral   5.535784   6.730163  3.9399187
TR10108|c0_g1_i1_coral  11.763540   4.206352  3.4474289
TR10132|c0_g1_i1_coral  18.683270   2.523811 14.2822054
                       VA_B_07_14 VA_B_07_18 VA_B_07_22
TR10083|c0_g2_i1_coral   3.728534  0.7405861   2.098499
TR10090|c0_g1_i1_coral   0.000000  3.7029304   2.098499
TR10090|c0_g2_i1_coral   1.491414 15.5523076   6.295498
TR10103|c0_g1_i1_coral   1.491414  8.1464468   4.196999
TR10108|c0_g1_i1_coral   2.237121  2.2217582   5.246248
TR10132|c0_g1_i1_coral   8.948482 17.0334798   2.098499
                       VA_W_01_14 VA_W_01_18 VA_W_02_14
TR10083|c0_g2_i1_coral   6.699293   7.732656   0.000000
TR10090|c0_g1_i1_coral   3.828167   1.104665   6.978382
TR10090|c0_g2_i1_coral   0.000000   3.866328   4.361489
TR10103|c0_g1_i1_coral   0.000000   3.866328   5.233787
TR10108|c0_g1_i1_coral   1.914084   4.418660   0.000000
TR10132|c0_g1_i1_coral   0.000000  10.494319   2.616893
                       VA_W_02_18 VA_W_03_14 VA_W_03_22
TR10083|c0_g2_i1_coral  4.5789684  3.1096023   6.888125
TR10090|c0_g1_i1_coral  0.6541383  5.4418040   9.392897
TR10090|c0_g2_i1_coral 13.0827667  6.9966052   3.130966
TR10103|c0_g1_i1_coral  0.6541383  6.9966052   2.504773
TR10108|c0_g1_i1_coral  9.1579367  3.1096023   3.757159
TR10132|c0_g1_i1_coral 13.0827667  0.7774006  13.150056
                       VA_W_04_14 VA_W_04_18 VA_W_04_22
TR10083|c0_g2_i1_coral   1.026752   4.334366   6.410680
TR10090|c0_g1_i1_coral   2.566880   5.779155   3.945034
TR10090|c0_g2_i1_coral   2.053504   7.705540  10.848842
TR10103|c0_g1_i1_coral   3.593631   3.852770   2.958775
TR10108|c0_g1_i1_coral   6.673887  20.227043   8.383196
TR10132|c0_g1_i1_coral   2.566880   0.000000   0.000000
                       VA_W_05_14 VA_W_05_18 VA_W_05_22
TR10083|c0_g2_i1_coral  0.0000000   3.848517  12.379823
TR10090|c0_g1_i1_coral  0.0000000   1.099576  12.379823
TR10090|c0_g2_i1_coral  0.0000000   2.748941   7.427894
TR10103|c0_g1_i1_coral  0.8118702   3.298729   2.475965
TR10108|c0_g1_i1_coral  1.6237403   5.497882  38.377452
TR10132|c0_g1_i1_coral  2.4356105   8.796611   2.475965
                       VA_W_06_14 VA_W_06_18 VA_W_06_22
TR10083|c0_g2_i1_coral   5.042735  2.5895188   0.000000
TR10090|c0_g1_i1_coral   0.000000  0.8631729   1.764014
TR10090|c0_g2_i1_coral   3.025641  0.8631729   0.000000
TR10103|c0_g1_i1_coral   8.068376  2.5895188   4.410036
TR10108|c0_g1_i1_coral   4.034188  6.9053834   5.292043
TR10132|c0_g1_i1_coral   9.076923 29.3478796  26.460214
                       VA_W_07_14 VA_W_07_18 VA_W_07_22
TR10083|c0_g2_i1_coral 10.2466895   1.127608  0.9473408
TR10090|c0_g1_i1_coral  1.5764138   1.127608  6.6313859
TR10090|c0_g2_i1_coral  5.5174482   3.382824  2.8420225
TR10103|c0_g1_i1_coral  4.7292413   0.000000  1.8946817
TR10108|c0_g1_i1_coral  3.1528275   1.127608  1.8946817
TR10132|c0_g1_i1_coral  0.7882069   6.765648  8.5260676
> genes4heatmap<-resOrigin[resOrigin$pvalue <0.05 & !is.na(resOrigin$pvalue),]
> names(genes4heatmap)
[1] "baseMean"       "log2FoldChange" "lfcSE"         
[4] "stat"           "pvalue"         "padj"          
> head(genes4heatmap)
log2 fold change (MLE): Origin VA vs RI 
Wald test p-value: Origin VA vs RI 
DataFrame with 6 rows and 6 columns
                        baseMean log2FoldChange     lfcSE
                       <numeric>      <numeric> <numeric>
TR10090|c0_g2_i1_coral   3.65756       0.943135  0.474719
TR10487|c0_g1_i1_coral   6.57170       0.727123  0.363907
TR1069|c0_g1_i1_coral    4.14205       4.490291  1.982381
TR10748|c0_g1_i1_coral   2.93642       1.787984  0.559059
TR10773|c0_g1_i1_coral   3.02516       1.758477  0.659498
TR10773|c1_g1_i1_coral   2.32876       1.292223  0.632168
                            stat     pvalue      padj
                       <numeric>  <numeric> <numeric>
TR10090|c0_g2_i1_coral   1.98672 0.04695340 0.4180430
TR10487|c0_g1_i1_coral   1.99810 0.04570594 0.4125186
TR1069|c0_g1_i1_coral    2.26510 0.02350656 0.3086533
TR10748|c0_g1_i1_coral   3.19820 0.00138287 0.0720091
TR10773|c0_g1_i1_coral   2.66639 0.00766715 0.1733954
TR10773|c1_g1_i1_coral   2.04411 0.04094219        NA
> dim(genes4heatmap)
[1] 866   6
> data4heatmap<-scaledcounts[row.names(scaledcounts)%in%row.names(genes4heatmap),]
> dim(data4heatmap)
[1] 866  78
> head(data4heatmap)
                       RI_B_01_14 RI_B_01_18 RI_B_01_22
TR10090|c0_g2_i1_coral    0.00000   3.468731   2.447866
TR10487|c0_g1_i1_coral   10.94714   5.203096   8.567532
TR1069|c0_g1_i1_coral     0.00000   0.000000   0.000000
TR10748|c0_g1_i1_coral    0.00000   0.000000   2.447866
TR10773|c0_g1_i1_coral    0.00000   6.070279   2.447866
TR10773|c1_g1_i1_coral    0.00000   2.601548   4.895733
                       RI_B_02_14 RI_B_02_18 RI_B_02_22
TR10090|c0_g2_i1_coral   3.772786    0.00000   0.000000
TR10487|c0_g1_i1_coral   0.000000    0.00000   6.648979
TR1069|c0_g1_i1_coral    7.545573    3.45517   6.648979
TR10748|c0_g1_i1_coral   0.000000    0.00000   0.000000
TR10773|c0_g1_i1_coral   3.772786    0.00000   0.000000
TR10773|c1_g1_i1_coral   0.000000    0.00000   2.216326
                       RI_B_03_14 RI_B_03_22 RI_B_04_14
TR10090|c0_g2_i1_coral   0.000000   3.818995   4.809473
TR10487|c0_g1_i1_coral   9.010379   5.091993   2.404737
TR1069|c0_g1_i1_coral    0.000000   0.000000   0.000000
TR10748|c0_g1_i1_coral   2.574394   0.000000   4.007894
TR10773|c0_g1_i1_coral   1.287197   0.000000   0.000000
TR10773|c1_g1_i1_coral   5.148788   1.272998   0.000000
                       RI_B_04_18 RI_B_04_22 RI_B_05_14
TR10090|c0_g2_i1_coral  3.6845136          0   0.570426
TR10487|c0_g1_i1_coral  4.5032943          0   9.126817
TR1069|c0_g1_i1_coral   0.0000000          0   0.000000
TR10748|c0_g1_i1_coral  2.8657328          0   1.711278
TR10773|c0_g1_i1_coral  0.4093904          0   0.000000
TR10773|c1_g1_i1_coral  0.0000000          0   0.285213
                       RI_B_05_18 RI_B_05_22 RI_B_06_14
TR10090|c0_g2_i1_coral   0.000000  2.4538305          0
TR10487|c0_g1_i1_coral   5.033716  0.8179435          0
TR1069|c0_g1_i1_coral    0.000000  0.0000000          0
TR10748|c0_g1_i1_coral   0.000000  0.0000000          0
TR10773|c0_g1_i1_coral   0.000000  0.0000000          0
TR10773|c1_g1_i1_coral   0.000000  0.8179435          0
                       RI_B_06_18 RI_B_06_22 RI_B_07_14
TR10090|c0_g2_i1_coral   4.827992          0   3.734168
TR10487|c0_g1_i1_coral   2.758853          0   5.227835
TR1069|c0_g1_i1_coral    0.000000          0   0.000000
TR10748|c0_g1_i1_coral   0.000000          0   2.987334
TR10773|c0_g1_i1_coral   0.000000          0   0.000000
TR10773|c1_g1_i1_coral   0.000000          0   0.000000
                       RI_B_07_18 RI_B_07_22 RI_W_01_18
TR10090|c0_g2_i1_coral   1.008773          0  12.257216
TR10487|c0_g1_i1_coral   5.043864          0   8.652152
TR1069|c0_g1_i1_coral    0.000000          0  10.094178
TR10748|c0_g1_i1_coral   0.000000          0   0.000000
TR10773|c0_g1_i1_coral   1.008773          0   7.931140
TR10773|c1_g1_i1_coral   0.000000          0   5.047089
                       RI_W_01_22 RI_W_02_14 RI_W_02_18
TR10090|c0_g2_i1_coral   7.743994   4.651361  4.9947759
TR10487|c0_g1_i1_coral   6.195195  16.279762  2.9968656
TR1069|c0_g1_i1_coral    9.292792   0.000000  0.0000000
TR10748|c0_g1_i1_coral   1.548799   4.651361  0.9989552
TR10773|c0_g1_i1_coral  17.036786   0.000000 14.9843278
TR10773|c1_g1_i1_coral  18.585585   0.000000 10.9885071
                       RI_W_02_22 RI_W_03_14 RI_W_03_18
TR10090|c0_g2_i1_coral   4.820288   3.044865   3.244480
TR10487|c0_g1_i1_coral   1.205072   7.307675   7.209956
TR1069|c0_g1_i1_coral    0.000000   0.000000   0.000000
TR10748|c0_g1_i1_coral   2.410144   2.435892   6.128462
TR10773|c0_g1_i1_coral   6.025360  23.140971  12.617422
TR10773|c1_g1_i1_coral   1.205072  10.352540   7.930951
                       RI_W_03_22 RI_W_04_14 RI_W_04_18
TR10090|c0_g2_i1_coral   1.581919    0.00000  7.4421015
TR10487|c0_g1_i1_coral  14.237275   17.10086  5.4575411
TR1069|c0_g1_i1_coral    0.000000    0.00000  0.0000000
TR10748|c0_g1_i1_coral   4.218452    0.00000  0.4961401
TR10773|c0_g1_i1_coral  29.001856    0.00000  1.9845604
TR10773|c1_g1_i1_coral   7.382291    0.00000  1.4884203
                       RI_W_05_14 RI_W_05_18 RI_W_05_22
TR10090|c0_g2_i1_coral   3.614931  10.107037   1.381659
TR10487|c0_g1_i1_coral   4.066797   4.042815   0.000000
TR1069|c0_g1_i1_coral    0.000000   0.000000   0.000000
TR10748|c0_g1_i1_coral   2.711198   1.010704   0.000000
TR10773|c0_g1_i1_coral   5.422396   2.021407   0.000000
TR10773|c1_g1_i1_coral   3.614931   3.032111   0.000000
                       RI_W_06_14 RI_W_06_18 RI_W_06_22
TR10090|c0_g2_i1_coral   3.133041   1.336966   7.790833
TR10487|c0_g1_i1_coral   4.177388  13.369662  10.016785
TR1069|c0_g1_i1_coral    0.000000   0.000000   0.000000
TR10748|c0_g1_i1_coral   3.133041   2.673932   2.225952
TR10773|c0_g1_i1_coral   5.221735   2.673932  10.016785
TR10773|c1_g1_i1_coral   1.044347   2.673932   3.338928
                       RI_W_07_14 RI_W_07_18 RI_W_07_22
TR10090|c0_g2_i1_coral   2.062318   1.118603   5.520462
TR10487|c0_g1_i1_coral   3.437196  13.423242   8.280694
TR1069|c0_g1_i1_coral    0.000000   0.000000   0.000000
TR10748|c0_g1_i1_coral   2.749757   2.237207   0.000000
TR10773|c0_g1_i1_coral   1.374879   2.237207   0.000000
TR10773|c1_g1_i1_coral   2.062318   3.355810   2.760231
                       VA_B_01_14 VA_B_01_18 VA_B_01_22
TR10090|c0_g2_i1_coral  10.204629   5.628251   5.690194
TR10487|c0_g1_i1_coral  10.204629   6.494135  10.242350
TR1069|c0_g1_i1_coral   33.165045   9.524732  17.639603
TR10748|c0_g1_i1_coral   1.275579   1.298827   5.121175
TR10773|c0_g1_i1_coral   6.377893   4.762366   2.845097
TR10773|c1_g1_i1_coral   8.929051   6.061193   6.259214
                       VA_B_02_14 VA_B_02_18 VA_B_02_22
TR10090|c0_g2_i1_coral   0.000000     0.0000   0.000000
TR10487|c0_g1_i1_coral   0.000000     0.0000  17.166789
TR1069|c0_g1_i1_coral   86.631891    44.0504  40.771123
TR10748|c0_g1_i1_coral  30.575962     0.0000   2.145849
TR10773|c0_g1_i1_coral   1.698665     0.0000   6.437546
TR10773|c1_g1_i1_coral   0.000000     2.5912   0.000000
                       VA_B_03_14 VA_B_03_18 VA_B_03_22
TR10090|c0_g2_i1_coral  10.929073   4.301848  3.5605530
TR10487|c0_g1_i1_coral  10.929073   7.886721  7.8332166
TR1069|c0_g1_i1_coral    0.000000   0.000000  0.0000000
TR10748|c0_g1_i1_coral   3.643024   7.886721  3.5605530
TR10773|c0_g1_i1_coral   0.000000   1.433949  0.7121106
TR10773|c1_g1_i1_coral   0.000000   3.584873  0.7121106
                       VA_B_04_14 VA_B_04_18 VA_B_04_22
TR10090|c0_g2_i1_coral  7.1085175   3.152383   0.000000
TR10487|c0_g1_i1_coral 15.1055996   4.053064   8.285065
TR1069|c0_g1_i1_coral   0.0000000   0.000000   0.000000
TR10748|c0_g1_i1_coral  2.6656940   0.000000   8.802882
TR10773|c0_g1_i1_coral  0.0000000   7.205447   8.285065
TR10773|c1_g1_i1_coral  0.8885647   8.556469   2.589083
                       VA_B_05_14 VA_B_05_18 VA_B_05_22
TR10090|c0_g2_i1_coral   1.399244  0.5528859   5.441030
TR10487|c0_g1_i1_coral   4.547541 17.1394640  21.764122
TR1069|c0_g1_i1_coral    0.000000  0.0000000   0.000000
TR10748|c0_g1_i1_coral   1.049433  1.6586578   3.627354
TR10773|c0_g1_i1_coral   1.399244  1.1057719   0.000000
TR10773|c1_g1_i1_coral   0.000000  4.4230875   0.000000
                       VA_B_06_14 VA_B_06_18 VA_B_06_22
TR10090|c0_g2_i1_coral   0.000000   4.206352   1.477470
TR10487|c0_g1_i1_coral   0.000000   8.412704   2.462449
TR1069|c0_g1_i1_coral   29.062864  16.825408   8.372327
TR10748|c0_g1_i1_coral   6.919730   0.000000   2.954939
TR10773|c0_g1_i1_coral   2.767892   0.000000   5.417388
TR10773|c1_g1_i1_coral   0.000000   2.523811   2.462449
                       VA_B_07_14 VA_B_07_18 VA_B_07_22
TR10090|c0_g2_i1_coral  1.4914137  15.552308   6.295498
TR10487|c0_g1_i1_coral  3.7285342   5.184103   8.393997
TR1069|c0_g1_i1_coral   0.0000000   0.000000   0.000000
TR10748|c0_g1_i1_coral  6.7113616   0.000000   4.196999
TR10773|c0_g1_i1_coral  1.4914137   2.962344   6.295498
TR10773|c1_g1_i1_coral  0.7457068   0.000000   4.196999
                       VA_W_01_14 VA_W_01_18 VA_W_02_14
TR10090|c0_g2_i1_coral   0.000000   3.866328  4.3614889
TR10487|c0_g1_i1_coral   6.699293   4.970993  1.7445956
TR1069|c0_g1_i1_coral    0.000000   0.000000  0.0000000
TR10748|c0_g1_i1_coral   2.871126   2.209330  0.8722978
TR10773|c0_g1_i1_coral   5.742251   1.104665  0.0000000
TR10773|c1_g1_i1_coral   0.000000   3.866328  0.0000000
                       VA_W_02_18 VA_W_03_14 VA_W_03_22
TR10090|c0_g2_i1_coral  13.082767  6.9966052   3.130966
TR10487|c0_g1_i1_coral  13.082767  3.1096023   9.392897
TR1069|c0_g1_i1_coral    0.000000  0.0000000   0.000000
TR10748|c0_g1_i1_coral   0.000000  0.7774006   3.757159
TR10773|c0_g1_i1_coral   3.924830  1.5548011   2.504773
TR10773|c1_g1_i1_coral   5.233107  0.7774006   2.504773
                       VA_W_04_14 VA_W_04_18 VA_W_04_22
TR10090|c0_g2_i1_coral   2.053504   7.705540 10.8488424
TR10487|c0_g1_i1_coral   3.593631  13.003099  1.4793876
TR1069|c0_g1_i1_coral    0.000000   0.000000  0.0000000
TR10748|c0_g1_i1_coral   6.673887   9.150329  7.3969380
TR10773|c0_g1_i1_coral   1.026752   0.000000  0.4931292
TR10773|c1_g1_i1_coral   1.026752   0.000000  0.0000000
                       VA_W_05_14 VA_W_05_18 VA_W_05_22
TR10090|c0_g2_i1_coral    0.00000   2.748941   7.427894
TR10487|c0_g1_i1_coral    0.00000   8.246822   8.665876
TR1069|c0_g1_i1_coral     0.00000   0.000000   0.000000
TR10748|c0_g1_i1_coral   14.61366   2.748941   9.903859
TR10773|c0_g1_i1_coral    0.00000   0.000000   0.000000
TR10773|c1_g1_i1_coral    0.00000   2.199153   1.237982
                       VA_W_06_14 VA_W_06_18 VA_W_06_22
TR10090|c0_g2_i1_coral   3.025641  0.8631729   0.000000
TR10487|c0_g1_i1_coral  10.085470  1.7263459  11.466093
TR1069|c0_g1_i1_coral    0.000000  0.0000000   0.000000
TR10748|c0_g1_i1_coral   2.017094  6.0422105   4.410036
TR10773|c0_g1_i1_coral   0.000000  1.7263459   0.000000
TR10773|c1_g1_i1_coral   2.017094  0.8631729   5.292043
                       VA_W_07_14 VA_W_07_18 VA_W_07_22
TR10090|c0_g2_i1_coral   5.517448   3.382824   2.842023
TR10487|c0_g1_i1_coral   7.093862   6.765648   3.789363
TR1069|c0_g1_i1_coral    0.000000   0.000000   0.000000
TR10748|c0_g1_i1_coral   0.000000   3.382824   1.894682
TR10773|c0_g1_i1_coral   0.000000   0.000000   0.000000
TR10773|c1_g1_i1_coral   0.000000   0.000000   0.000000
> 
> temp = as.matrix(rowMeans(data4heatmap))
> head(temp)
                           [,1]
TR10090|c0_g2_i1_coral 3.657565
TR10487|c0_g1_i1_coral 6.571698
TR1069|c0_g1_i1_coral  4.142052
TR10748|c0_g1_i1_coral 2.936423
TR10773|c0_g1_i1_coral 3.025158
TR10773|c1_g1_i1_coral 2.328759
> scaledmatrix<-matrix(data=temp, nrow=nrow(data4heatmap), ncol=ncol(data4heatmap), byrow=FALSE)
> data4heatmapscaled = data4heatmap/scaledmatrix
> head(data4heatmapscaled)
                       RI_B_01_14 RI_B_01_18 RI_B_01_22
TR10090|c0_g2_i1_coral   0.000000  0.9483717  0.6692613
TR10487|c0_g1_i1_coral   1.665801  0.7917431  1.3037015
TR1069|c0_g1_i1_coral    0.000000  0.0000000  0.0000000
TR10748|c0_g1_i1_coral   0.000000  0.0000000  0.8336218
TR10773|c0_g1_i1_coral   0.000000  2.0065992  0.8091699
TR10773|c1_g1_i1_coral   0.000000  1.1171391  2.1022922
                       RI_B_02_14 RI_B_02_18 RI_B_02_22
TR10090|c0_g2_i1_coral   1.031502  0.0000000  0.0000000
TR10487|c0_g1_i1_coral   0.000000  0.0000000  1.0117598
TR1069|c0_g1_i1_coral    1.821699  0.8341687  1.6052378
TR10748|c0_g1_i1_coral   0.000000  0.0000000  0.0000000
TR10773|c0_g1_i1_coral   1.247137  0.0000000  0.0000000
TR10773|c1_g1_i1_coral   0.000000  0.0000000  0.9517198
                       RI_B_03_14 RI_B_03_22 RI_B_04_14
TR10090|c0_g2_i1_coral  0.0000000  1.0441360  1.3149387
TR10487|c0_g1_i1_coral  1.3710885  0.7748368  0.3659232
TR1069|c0_g1_i1_coral   0.0000000  0.0000000  0.0000000
TR10748|c0_g1_i1_coral  0.8767109  0.0000000  1.3648899
TR10773|c0_g1_i1_coral  0.4254975  0.0000000  0.0000000
TR10773|c1_g1_i1_coral  2.2109576  0.5466423  0.0000000
                       RI_B_04_18 RI_B_04_22 RI_B_05_14
TR10090|c0_g2_i1_coral  1.0073680          0  0.1559579
TR10487|c0_g1_i1_coral  0.6852559          0  1.3888066
TR1069|c0_g1_i1_coral   0.0000000          0  0.0000000
TR10748|c0_g1_i1_coral  0.9759263          0  0.5827764
TR10773|c0_g1_i1_coral  0.1353286          0  0.0000000
TR10773|c1_g1_i1_coral  0.0000000          0  0.1224742
                       RI_B_05_18 RI_B_05_22 RI_B_06_14
TR10090|c0_g2_i1_coral  0.0000000  0.6708919          0
TR10487|c0_g1_i1_coral  0.7659688  0.1244646          0
TR1069|c0_g1_i1_coral   0.0000000  0.0000000          0
TR10748|c0_g1_i1_coral  0.0000000  0.0000000          0
TR10773|c0_g1_i1_coral  0.0000000  0.0000000          0
TR10773|c1_g1_i1_coral  0.0000000  0.3512357          0
                       RI_B_06_18 RI_B_06_22 RI_B_07_14
TR10090|c0_g2_i1_coral  1.3200019          0  1.0209437
TR10487|c0_g1_i1_coral  0.4198082          0  0.7955075
TR1069|c0_g1_i1_coral   0.0000000          0  0.0000000
TR10748|c0_g1_i1_coral  0.0000000          0  1.0173377
TR10773|c0_g1_i1_coral  0.0000000          0  0.0000000
TR10773|c1_g1_i1_coral  0.0000000          0  0.0000000
                       RI_B_07_18 RI_B_07_22 RI_W_01_18
TR10090|c0_g2_i1_coral  0.2758045          0   3.351196
TR10487|c0_g1_i1_coral  0.7675130          0   1.316578
TR1069|c0_g1_i1_coral   0.0000000          0   2.436999
TR10748|c0_g1_i1_coral  0.0000000          0   0.000000
TR10773|c0_g1_i1_coral  0.3334612          0   2.621728
TR10773|c1_g1_i1_coral  0.0000000          0   2.167287
                       RI_W_01_22 RI_W_02_14 RI_W_02_18
TR10090|c0_g2_i1_coral  2.1172541   1.271710  1.3656016
TR10487|c0_g1_i1_coral  0.9427084   2.477254  0.4560261
TR1069|c0_g1_i1_coral   2.2435236   0.000000  0.0000000
TR10748|c0_g1_i1_coral  0.5274440   1.584023  0.3401946
TR10773|c0_g1_i1_coral  5.6317019   0.000000  4.9532387
TR10773|c1_g1_i1_coral  7.9808953   0.000000  4.7186100
                       RI_W_02_22 RI_W_03_14 RI_W_03_18
TR10090|c0_g2_i1_coral  1.3178956  0.8324842  0.8870602
TR10487|c0_g1_i1_coral  0.1833730  1.1119920  1.0971223
TR1069|c0_g1_i1_coral   0.0000000  0.0000000  0.0000000
TR10748|c0_g1_i1_coral  0.8207755  0.8295438  2.0870501
TR10773|c0_g1_i1_coral  1.9917509  7.6495091  4.1708314
TR10773|c1_g1_i1_coral  0.5174739  4.4455171  3.4056552
                       RI_W_03_22 RI_W_04_14 RI_W_04_18
TR10090|c0_g2_i1_coral  0.4325062   0.000000  2.0347150
TR10487|c0_g1_i1_coral  2.1664531   2.602198  0.8304614
TR1069|c0_g1_i1_coral   0.0000000   0.000000  0.0000000
TR10748|c0_g1_i1_coral  1.4365953   0.000000  0.1689607
TR10773|c0_g1_i1_coral  9.5868908   0.000000  0.6560188
TR10773|c1_g1_i1_coral  3.1700530   0.000000  0.6391473
                       RI_W_05_14 RI_W_05_18 RI_W_05_22
TR10090|c0_g2_i1_coral  0.9883436  2.7633244  0.3777539
TR10487|c0_g1_i1_coral  0.6188351  0.6151858  0.0000000
TR1069|c0_g1_i1_coral   0.0000000  0.0000000  0.0000000
TR10748|c0_g1_i1_coral  0.9232995  0.3441955  0.0000000
TR10773|c0_g1_i1_coral  1.7924342  0.6681991  0.0000000
TR10773|c1_g1_i1_coral  1.5522989  1.3020286  0.0000000
                       RI_W_06_14 RI_W_06_18 RI_W_06_22
TR10090|c0_g2_i1_coral  0.8565921  0.3655346  2.1300602
TR10487|c0_g1_i1_coral  0.6356634  2.0344306  1.5242310
TR1069|c0_g1_i1_coral   0.0000000  0.0000000  0.0000000
TR10748|c0_g1_i1_coral  1.0669582  0.9106087  0.7580488
TR10773|c0_g1_i1_coral  1.7261033  0.8838986  3.3111614
TR10773|c1_g1_i1_coral  0.4484564  1.1482219  1.4337799
                       RI_W_07_14 RI_W_07_18 RI_W_07_22
TR10090|c0_g2_i1_coral  0.5638500  0.3058329   1.509327
TR10487|c0_g1_i1_coral  0.5230302  2.0425836   1.260054
TR1069|c0_g1_i1_coral   0.0000000  0.0000000   0.000000
TR10748|c0_g1_i1_coral  0.9364308  0.7618816   0.000000
TR10773|c0_g1_i1_coral  0.4544816  0.7395340   0.000000
TR10773|c1_g1_i1_coral  0.8855865  1.4410293   1.185280
                       VA_B_01_14 VA_B_01_18 VA_B_01_22
TR10090|c0_g2_i1_coral  2.7900066  1.5387973   1.555733
TR10487|c0_g1_i1_coral  1.5528148  0.9881975   1.558555
TR1069|c0_g1_i1_coral   8.0069110  2.2995199   4.258662
TR10748|c0_g1_i1_coral  0.4343988  0.4423160   1.744018
TR10773|c0_g1_i1_coral  2.1082846  1.5742538   0.940479
TR10773|c1_g1_i1_coral  3.8342522  2.6027562   2.687789
                       VA_B_02_14 VA_B_02_18 VA_B_02_22
TR10090|c0_g2_i1_coral  0.0000000   0.000000  0.0000000
TR10487|c0_g1_i1_coral  0.0000000   0.000000  2.6122305
TR1069|c0_g1_i1_coral  20.9152088  10.634922  9.8432176
TR10748|c0_g1_i1_coral 10.4126549   0.000000  0.7307695
TR10773|c0_g1_i1_coral  0.5615127   0.000000  2.1280034
TR10773|c1_g1_i1_coral  0.0000000   1.112696  0.0000000
                       VA_B_03_14 VA_B_03_18 VA_B_03_22
TR10090|c0_g2_i1_coral   2.988074  1.1761509  0.9734764
TR10487|c0_g1_i1_coral   1.663052  1.2001041  1.1919624
TR1069|c0_g1_i1_coral    0.000000  0.0000000  0.0000000
TR10748|c0_g1_i1_coral   1.240633  2.6858257  1.2125476
TR10773|c0_g1_i1_coral   0.000000  0.4740081  0.2353962
TR10773|c1_g1_i1_coral   0.000000  1.5393918  0.3057897
                       VA_B_04_14 VA_B_04_18 VA_B_04_22
TR10090|c0_g2_i1_coral  1.9435111  0.8618804   0.000000
TR10487|c0_g1_i1_coral  2.2985841  0.6167454   1.260719
TR1069|c0_g1_i1_coral   0.0000000  0.0000000   0.000000
TR10748|c0_g1_i1_coral  0.9078031  0.0000000   2.997825
TR10773|c0_g1_i1_coral  0.0000000  2.3818420   2.738722
TR10773|c1_g1_i1_coral  0.3815614  3.6742606   1.111786
                       VA_B_05_14 VA_B_05_18 VA_B_05_22
TR10090|c0_g2_i1_coral  0.3825615  0.1511623   1.487610
TR10487|c0_g1_i1_coral  0.6919888  2.6080725   3.311796
TR1069|c0_g1_i1_coral   0.0000000  0.0000000   0.000000
TR10748|c0_g1_i1_coral  0.3573847  0.5648565   1.235297
TR10773|c0_g1_i1_coral  0.4625357  0.3655254   0.000000
TR10773|c1_g1_i1_coral  0.0000000  1.8993321   0.000000
                       VA_B_06_14 VA_B_06_18 VA_B_06_22
TR10090|c0_g2_i1_coral  0.0000000   1.150042  0.4039490
TR10487|c0_g1_i1_coral  0.0000000   1.280142  0.3747052
TR1069|c0_g1_i1_coral   7.0165371   4.062094  2.0212992
TR10748|c0_g1_i1_coral  2.3565165   0.000000  1.0063056
TR10773|c0_g1_i1_coral  0.9149579   0.000000  1.7907788
TR10773|c1_g1_i1_coral  0.0000000   1.083758  1.0574082
                       VA_B_07_14 VA_B_07_18 VA_B_07_22
TR10090|c0_g2_i1_coral  0.4077614  4.2520938   1.721227
TR10487|c0_g1_i1_coral  0.5673624  0.7888529   1.277295
TR1069|c0_g1_i1_coral   0.0000000  0.0000000   0.000000
TR10748|c0_g1_i1_coral  2.2855567  0.0000000   1.429289
TR10773|c0_g1_i1_coral  0.4930036  0.9792364   2.081048
TR10773|c1_g1_i1_coral  0.3202164  0.0000000   1.802247
                       VA_W_01_14 VA_W_01_18 VA_W_02_14
TR10090|c0_g2_i1_coral  0.0000000  1.0570771  1.1924571
TR10487|c0_g1_i1_coral  1.0194159  0.7564245  0.2654711
TR1069|c0_g1_i1_coral   0.0000000  0.0000000  0.0000000
TR10748|c0_g1_i1_coral  0.9777629  0.7523882  0.2970613
TR10773|c0_g1_i1_coral  1.8981660  0.3651595  0.0000000
TR10773|c1_g1_i1_coral  0.0000000  1.6602522  0.0000000
                       VA_W_02_18 VA_W_03_14 VA_W_03_22
TR10090|c0_g2_i1_coral   3.576907  1.9129136  0.8560247
TR10487|c0_g1_i1_coral   1.990774  0.4731810  1.4292954
TR1069|c0_g1_i1_coral    0.000000  0.0000000  0.0000000
TR10748|c0_g1_i1_coral   0.000000  0.2647441  1.2795019
TR10773|c0_g1_i1_coral   1.297397  0.5139571  0.8279809
TR10773|c1_g1_i1_coral   2.247165  0.3338261  1.0755824
                       VA_W_04_14 VA_W_04_18 VA_W_04_22
TR10090|c0_g2_i1_coral  0.5614402   2.106741  2.9661383
TR10487|c0_g1_i1_coral  0.5468346   1.978651  0.2251150
TR1069|c0_g1_i1_coral   0.0000000   0.000000  0.0000000
TR10748|c0_g1_i1_coral  2.2727947   3.116148  2.5190299
TR10773|c0_g1_i1_coral  0.3394044   0.000000  0.1630094
TR10773|c1_g1_i1_coral  0.4409008   0.000000  0.0000000
                       VA_W_05_14 VA_W_05_18 VA_W_05_22
TR10090|c0_g2_i1_coral   0.000000  0.7515768   2.030831
TR10487|c0_g1_i1_coral   0.000000  1.2548999   1.318666
TR1069|c0_g1_i1_coral    0.000000  0.0000000   0.000000
TR10748|c0_g1_i1_coral   4.976688  0.9361528   3.372763
TR10773|c0_g1_i1_coral   0.000000  0.0000000   0.000000
TR10773|c1_g1_i1_coral   0.000000  0.9443452   0.531606
                       VA_W_06_14 VA_W_06_18 VA_W_06_22
TR10090|c0_g2_i1_coral  0.8272283  0.2359966   0.000000
TR10487|c0_g1_i1_coral  1.5346826  0.2626940   1.744769
TR1069|c0_g1_i1_coral   0.0000000  0.0000000   0.000000
TR10748|c0_g1_i1_coral  0.6869221  2.0576770   1.501839
TR10773|c0_g1_i1_coral  0.0000000  0.5706631   0.000000
TR10773|c1_g1_i1_coral  0.8661668  0.3706578   2.272473
                       VA_W_07_14 VA_W_07_18 VA_W_07_22
TR10090|c0_g2_i1_coral   1.508503  0.9248843  0.7770259
TR10487|c0_g1_i1_coral   1.079457  1.0295131  0.5766186
TR1069|c0_g1_i1_coral    0.000000  0.0000000  0.0000000
TR10748|c0_g1_i1_coral   0.000000  1.1520220  0.6452345
TR10773|c0_g1_i1_coral   0.000000  0.0000000  0.0000000
TR10773|c1_g1_i1_coral   0.000000  0.0000000  0.0000000
> 
> dim(data4heatmapscaled)
[1] 866  78
> 
> pairs.breaks <- seq(0, 3.0, by=0.1)
> length(pairs.breaks)
[1] 31
> mycol <- colorpanel(n=30, low="black", high="yellow") 
> 
> pdf(file="XXXXXX_byrow.pdf",7,7)
> heatmap.2(data.matrix(data4heatmapscaled), Rowv=T, Colv=F, dendrogram = c("row"), scale="none", keysize=1, breaks=pairs.breaks, col=mycol, trace = "none", symkey = F, density.info = "density", colsep=c(24), sepcolor=c("white"), sepwidth=c(.1,.1), margins=c(10,10), labRow=F)
> dev.off()
RStudioGD 
        2 
> 
> pdf(file="XXXXXX_bycolumn.pdf",7,7)
> heatmap.2(data.matrix(data4heatmapscaled), Rowv=T, Colv=T, dendrogram = c("col"), scale="none", keysize=1, breaks=pairs.breaks, col=mycol, trace = "none", symkey = F, density.info = "density", colsep=c(24), sepcolor=c("white"), sepwidth=c(.1,.1), margins=c(10,10), labRow=F)
> dev.off()
RStudioGD 
        2 
> heatmap.2(data.matrix(data4heatmapscaled), Rowv=T, Colv=F, dendrogram = c("row"), scale="none", keysize=1, breaks=pairs.breaks, col=mycol, trace = "none", symkey = F, density.info = "density", colsep=c(24), sepcolor=c("white"), sepwidth=c(.1,.1), margins=c(10,10), labRow=F)
Error in plot.new() : figure margins too large
> heatmap.2(data.matrix(data4heatmapscaled), Rowv=T, Colv=T, dendrogram = c("col"), scale="none", keysize=1, breaks=pairs.breaks, col=mycol, trace = "none", symkey = F, density.info = "density", colsep=c(24), sepcolor=c("white"), sepwidth=c(.1,.1), margins=c(10,10), labRow=F)
Error in .External.graphics(C_layout, num.rows, num.cols, mat, as.integer(num.figures),  : 
  invalid graphics state
> plotPCA(vstCounts[rownames(vstCounts)%in%row.names(genes4heatmap),], intgroup="Origin")
> plotPCA(vstCounts[rownames(vstCounts)%in%row.names(genes4heatmap),], intgroup="Origin")
> plotPCA(vstCounts[rownames(vstCounts)%in%row.names(genes4heatmap),], intgroup="Origin")
> plotPCA(vstCounts[rownames(vstCounts)%in%row.names(genes4heatmap),], intgroup="Origin_SymState")
> plotPCA(vstCounts[rownames(vstCounts)%in%row.names(genes4heatmap),], intgroup="Origin_SymState_Temp")
> pdf(file="866_RIvsVA_PCAv2.pdf",14, 14)
> plotPCA(vstCounts[rownames(vstCounts)%in%row.names(genes4heatmap),], intgroup="Origin")
> dev.off()
RStudioGD 
        2 
> prop.nullv3 <- apply(countsTable[rownames(countsTable)%in%row.names(genes4heatmap),], 2, function(x) 100*mean(x==0))
> barplot(prop.nullv3, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> pdf(file="ResNullCountsv2.pdf",14, 14)
> barplot(prop.nullv3, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> dev.off()
RStudioGD 
        2 
> barplot(prop.nullv3, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> distsv2<-dist(t(assay(vstCounts[rownames(vstCounts)%in%row.names(genes4heatmap),])))
> plot(hclust(distsv2))
> heatmap.2(as.matrix(distsv2), key=F, trace="none",
+           col=colorpanel(100, "black", "white"),
+           margin=c(10, 10))
> #### GOSeq analysis ####
> res<-resOrigin
> Annotations<-read.delim("Assembly_GoodCoralSymbiont_suffixed_totalannotated.txt")
> head(res)
log2 fold change (MLE): Origin VA vs RI 
Wald test p-value: Origin VA vs RI 
DataFrame with 6 rows and 6 columns
                        baseMean log2FoldChange
                       <numeric>      <numeric>
TR10083|c0_g2_i1_coral   5.36648     -0.2712427
TR10090|c0_g1_i1_coral   2.70436      1.1125117
TR10090|c0_g2_i1_coral   3.65756      0.9431346
TR10103|c0_g1_i1_coral   2.91279      0.0386643
TR10108|c0_g1_i1_coral   6.31144     -0.0179010
TR10132|c0_g1_i1_coral   9.26737     -0.2649903
                           lfcSE       stat    pvalue
                       <numeric>  <numeric> <numeric>
TR10083|c0_g2_i1_coral  0.446225 -0.6078616 0.5432793
TR10090|c0_g1_i1_coral  0.589306  1.8878328 0.0590484
TR10090|c0_g2_i1_coral  0.474719  1.9867203 0.0469534
TR10103|c0_g1_i1_coral  0.456720  0.0846565 0.9325345
TR10108|c0_g1_i1_coral  0.461958 -0.0387502 0.9690895
TR10132|c0_g1_i1_coral  0.677608 -0.3910675 0.6957473
                            padj
                       <numeric>
TR10083|c0_g2_i1_coral  0.865661
TR10090|c0_g1_i1_coral        NA
TR10090|c0_g2_i1_coral  0.418043
TR10103|c0_g1_i1_coral  0.984590
TR10108|c0_g1_i1_coral  0.992150
TR10132|c0_g1_i1_coral  0.921517
> sum(res$log2FoldChange!=0)
[1] 7659
> 
> genes<-as.integer(p.adjust(res$pvalue[res$log2FoldChange!=0 & !is.na(res$pvalue)], method="BH")<.05)
> names(genes)<-row.names(res[res$log2FoldChange!=0 & !is.na(res$pvalue),])
> table(genes)
genes
   0    1 
7533  116 
> 
> genes<-as.integer(res$pvalue[res$log2FoldChange!=0 & !is.na(res$pvalue)]<.05)
> names(genes)<-row.names(res[res$log2FoldChange!=0 & !is.na(res$pvalue),])
> table(genes)
genes
   0    1 
6783  866 
> 
> goterms<-strsplit(as.character(Annotations$GO), split=" // ")
> names(goterms)<-Annotations$ContigName
> 
> pwf<-nullp(genes, bias.data=Annotations[Annotations$ContigName%in%names(genes),"ContigLength"])
Warning message:
In pcls(G) : initial point very close to some inequality constraints
> GOGOGO<-goseq(pwf,gene2cat=goterms)
Using manually entered categories.
Calculating the p-values...
'select()' returned 1:1 mapping between keys
and columns
> GOGOGO$padj<-p.adjust(GOGOGO$over_represented_pvalue, method="fdr")
> 
> sum(GOGOGO$padj<0.2, na.rm=T)
[1] 3
> sum(GOGOGO$padj<0.1, na.rm=T)
[1] 0
> sum(GOGOGO$padj<0.05, na.rm=T)
[1] 0
> GOGOGO[GOGOGO$padj<0.05,]
[1] category                 over_represented_pvalue 
[3] under_represented_pvalue numDEInCat              
[5] numInCat                 term                    
[7] ontology                 padj                    
<0 rows> (or 0-length row.names)
> 
> GOTERM[["SOMEGOTERM"]]
NULL
> 
> EnGOS<-GOGOGO$category[p.adjust(GOGOGO$over_represented_pvalue, method="BH")<.05]
> 
> for(go in EnGOS){
+   print(GOTERM[[go]])
+   cat("--------------------------------------\n")}
> names(Annotations)
 [1] "ContigName"             
 [2] "ContigLength"           
 [3] "topnrMatch"             
 [4] "topnrEvalue"            
 [5] "topnrAlignmentLength"   
 [6] "topnrPercMatch"         
 [7] "nobadwordnrMatch"       
 [8] "nobadwordnrEvalue"      
 [9] "nobadwordnrAlignLength" 
[10] "nobadwordnrPercentMatch"
[11] "Uniprotmatch"           
[12] "X._identity"            
[13] "evalue"                 
[14] "ID"                     
[15] "Description"            
[16] "KEGG"                   
[17] "KEGGKO"                 
[18] "PFAM"                   
[19] "GO"                     
[20] "GOCC"                   
[21] "GOBP"                   
[22] "GOMF"                   
[23] "Keywords"               
> head(genes4heatmap)
log2 fold change (MLE): Origin VA vs RI 
Wald test p-value: Origin VA vs RI 
DataFrame with 6 rows and 6 columns
                        baseMean log2FoldChange
                       <numeric>      <numeric>
TR10090|c0_g2_i1_coral   3.65756       0.943135
TR10487|c0_g1_i1_coral   6.57170       0.727123
TR1069|c0_g1_i1_coral    4.14205       4.490291
TR10748|c0_g1_i1_coral   2.93642       1.787984
TR10773|c0_g1_i1_coral   3.02516       1.758477
TR10773|c1_g1_i1_coral   2.32876       1.292223
                           lfcSE      stat     pvalue
                       <numeric> <numeric>  <numeric>
TR10090|c0_g2_i1_coral  0.474719   1.98672 0.04695340
TR10487|c0_g1_i1_coral  0.363907   1.99810 0.04570594
TR1069|c0_g1_i1_coral   1.982381   2.26510 0.02350656
TR10748|c0_g1_i1_coral  0.559059   3.19820 0.00138287
TR10773|c0_g1_i1_coral  0.659498   2.66639 0.00766715
TR10773|c1_g1_i1_coral  0.632168   2.04411 0.04094219
                            padj
                       <numeric>
TR10090|c0_g2_i1_coral 0.4180430
TR10487|c0_g1_i1_coral 0.4125186
TR1069|c0_g1_i1_coral  0.3086533
TR10748|c0_g1_i1_coral 0.0720091
TR10773|c0_g1_i1_coral 0.1733954
TR10773|c1_g1_i1_coral        NA
> dim(genes4heatmap)
[1] 866   6
> 
> ResultsOutput<-cbind("ContigName"=row.names(genes4heatmap),genes4heatmap, Annotations[Annotations$ContigName%in%row.names(genes4heatmap),])
> dim(ResultsOutput)
[1] 866  30
> head(ResultsOutput)
DataFrame with 6 rows and 30 columns
              ContigName  baseMean log2FoldChange
             <character> <numeric>      <numeric>
1 TR10090|c0_g2_i1_coral   3.65756       0.943135
2 TR10487|c0_g1_i1_coral   6.57170       0.727123
3  TR1069|c0_g1_i1_coral   4.14205       4.490291
4 TR10748|c0_g1_i1_coral   2.93642       1.787984
5 TR10773|c0_g1_i1_coral   3.02516       1.758477
6 TR10773|c1_g1_i1_coral   2.32876       1.292223
      lfcSE      stat     pvalue      padj
  <numeric> <numeric>  <numeric> <numeric>
1  0.474719   1.98672 0.04695340 0.4180430
2  0.363907   1.99810 0.04570594 0.4125186
3  1.982381   2.26510 0.02350656 0.3086533
4  0.559059   3.19820 0.00138287 0.0720091
5  0.659498   2.66639 0.00766715 0.1733954
6  0.632168   2.04411 0.04094219        NA
              ContigName ContigLength
             <character>    <integer>
1 TR10090|c0_g2_i1_coral          772
2 TR10487|c0_g1_i1_coral         1007
3  TR1069|c0_g1_i1_coral          815
4 TR10748|c0_g1_i1_coral          516
5 TR10773|c0_g1_i1_coral          580
6 TR10773|c1_g1_i1_coral          586
              topnrMatch  topnrEvalue
             <character>  <character>
1 gnl|BL_ORD_ID|738431..  7.27758e-78
2 gnl|BL_ORD_ID|110398..  3.65321e-84
3 gnl|BL_ORD_ID|110400.. 9.23041e-133
4 gnl|BL_ORD_ID|110376..  2.29747e-78
5 gnl|BL_ORD_ID|110383..  2.14754e-64
6 gnl|BL_ORD_ID|110383..  1.33696e-65
  topnrAlignmentLength topnrPercMatch
           <character>    <character>
1                  258           0.53
2                  201           0.88
3                  271           0.73
4                  172           0.85
5                  206           0.55
6                  196           0.60
        nobadwordnrMatch nobadwordnrEvalue
             <character>       <character>
1 gnl|BL_ORD_ID|726506..       3.99079e-52
2 gnl|BL_ORD_ID|110398..       3.65321e-84
3 gnl|BL_ORD_ID|110400..      9.23041e-133
4 gnl|BL_ORD_ID|110376..       2.29747e-78
5 gnl|BL_ORD_ID|110383..       2.14754e-64
6 gnl|BL_ORD_ID|110383..       1.33696e-65
  nobadwordnrAlignLength nobadwordnrPercentMatch
             <character>             <character>
1                    264                    0.45
2                    201                    0.88
3                    271                    0.73
4                    172                    0.85
5                    206                    0.55
6                    196                    0.60
  Uniprotmatch X._identity      evalue
   <character> <character> <character>
1   A0A1X7UWJ8      40.927    1.82e-51
2       Q4R6F3      37.500    1.77e-06
3       Q8N2E2      31.022    1.60e-30
4   A0A2B4RJ64      70.690    9.57e-61
5   A0A2B4RML7      46.635    3.49e-44
6   A0A2B4RML7      47.847    2.78e-48
                ID            Description
       <character>            <character>
1 A0A1X7UWJ8_AMPQE Uncharacterized prot..
2      NGLY1_MACFA Peptide-N(4)-(N-acet..
3       VWDE_HUMAN von Willebrand facto..
4 A0A2B4RJ64_STYPI Uncharacterized prot..
5 A0A2B4RML7_STYPI Uncharacterized prot..
6 A0A2B4RML7_STYPI Uncharacterized prot..
           KEGG      KEGGKO                   PFAM
    <character> <character>            <character>
1       No_KEGG   No_KEGGKO       PF05585; DUF1758
2 mcf:101925902      K01456 PF04721; PAW,  PF094..
3    hsa:221806   No_KEGGKO           PF00094; VWD
4       No_KEGG   No_KEGGKO                   Pfam
5       No_KEGG   No_KEGGKO                   Pfam
6       No_KEGG   No_KEGGKO                   Pfam
                      GO                   GOCC
             <character>            <character>
1             GO:0004190                No_GOBP
2 GO:0005737 // GO:004.. glycoprotein catabol..
3 GO:0009986 // GO:000.. anatomical structure..
4             GO:0016021                No_GOBP
5             No_GOcodes                No_GOBP
6             No_GOcodes                No_GOBP
                    GOBP                   GOMF
             <character>            <character>
1 aspartic-type endope..                No_GOCC
2 metal ion binding (G.. cytoplasm (GO:000573..
3 signaling receptor b.. cell surface (GO:000..
4                No_GOMF integral component o..
5                No_GOMF                No_GOCC
6                No_GOMF                No_GOCC
                Keywords
             <character>
1 Complete proteome {E..
2 Acetylation;Cytoplas..
3 Alternative splicing..
4 Coiled coil {ECO:000..
5 Complete proteome {E..
6 Complete proteome {E..
> write.table(ResultsOutput, file="177OriginDEGswAnnotation.txt", quote=F, row.names=F, sep="\t")
> 



#9- Optional, also plot a PCA using only the genes with a pvalue<0.05 for the "origin" and "symstate" variables

#10- Even more optional, color code your symbols by temperature treatment as well as origin and symstate.
```

## Day13HW
```sh
#1- create an sbatch script to rm -r your sandbox/YOURNAME directory

[kcrid001@coreV3-23-046 sandboxes]$ cat SandboxRemovalKCrid.sh 
#!/bin/bash -l

#SBATCH -o KCridsandboxremoval.txt
#SBATCH -n 1
#SBATCH --mail-user=kcrid001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=KCridsandboxremoval

rm -r ./katiecrider
[kcrid001@coreV3-23-046 sandboxes]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes


#2- submit your sbatch script and add the entry to your logfile/readme

#3- scp your github logfile to the /cm/shared/courses/dbarshis/21AdvGenomics/archive with the name LASTNAME_FIRSTNAME_readme.md


scp README.md kcrid001@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/archive/Crider_Katie_readme.md



#4- scp the following files to your local computer
	scp YOURMIDASID@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/refassembly/15079_Apoc_hostsym.fasta ./
	scp YOURMIDASID@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/refassembly/15079_Apoc_hostsym.fasta.fai ./
	scp YOURMIDASID@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/dan/data/BAMS/RI_B_01/RI_B_01.bam ./
	scp YOURMIDASID@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/dan/data/BAMS/RI_B_01/RI_B_01.bam.bai ./
#5- launch IGV on your local machine and load in 15079_Apoc_hostsym.fasta as the "genome" and RI_B_01.bam as the input file
```
## Day13
```sh
#1- create an sbatch script to rm -r your sandbox/YOURNAME directory
#2- submit your sbatch script and add the entry to your logfile/readme

[kcrid001@turing1 sandboxes]$ cat SandboxRemovalKCrid.sh
#!/bin/bash -l

#SBATCH -o KCridsandboxremoval.txt
#SBATCH -n 1
#SBATCH --mail-user=kcrid001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=KCridsandboxremoval

rm -r ./katiecrider
[kcrid001@turing1 sandboxes]$ salloc
salloc: Pending job allocation 9284556
salloc: job 9284556 queued and waiting for resources
salloc: job 9284556 has been allocated resources
salloc: Granted job allocation 9284556
[kcrid001@coreV1-22-016 sandboxes]$ sbatch SandboxRemovalKCrid.sh
Submitted batch job 9284557
[kcrid001@coreV1-22-016 sandboxes]$ squeue -u kcrid001
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON) 
           9284557      main KCridsan kcrid001  R       0:01      1 coreV1-22-016 
           9284556      main       sh kcrid001  R       0:31      1 coreV1-22-016 

#3- scp your github logfile to the /cm/shared/courses/dbarshis/21AdvGenomics/archive with the name LASTNAME_FIRSTNAME_readme.md

(base) Katies-MacBook-Air-4:KatieCriderAdvancedGenomicsLog katiecrider$ scp README.md kcrid001@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/archive/Crider_Katie_readme.md
kcrid001@turing.hpc.odu.edu's password: 
README.md                                         100%  207KB   1.1MB/s   00:00 

#4- scp the following files to your local computer
(base) Katies-MacBook-Air-4:Genomics katiecrider$ mkdir day13
(base) Katies-MacBook-Air-4:Genomics katiecrider$ cd day13
(base) Katies-MacBook-Air-4:day13 katiecrider$ scp kcrid001@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/refassembly/15079_Apoc_hostsym.fasta ./
kcrid001@turing.hpc.odu.edu's password: 
15079_Apoc_hostsym.fasta                          100%   13MB  16.6MB/s   00:00    
(base) Katies-MacBook-Air-4:day13 katiecrider$ scp kcrid001@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/refassembly/15079_Apoc_hostsym.fasta.fai ./
kcrid001@turing.hpc.odu.edu's password: 
15079_Apoc_hostsym.fasta.fai                      100%  641KB   2.0MB/s   00:00    
(base) Katies-MacBook-Air-4:day13 katiecrider$ scp kcrid001@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/dan/data/BAMS/RI_B_01/RI_B_01.bam ./
kcrid001@turing.hpc.odu.edu's password: 
RI_B_01.bam                                       100%   44MB  17.5MB/s   00:02    
(base) Katies-MacBook-Air-4:day13 katiecrider$ scp kcrid001@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/dan/data/BAMS/RI_B_01/RI_B_01.bam.bai ./
kcrid001@turing.hpc.odu.edu's password: 
RI_B_01.bam.bai  


#5- launch IGV on your local machine and load in 15079_Apoc_hostsym.fasta as the "genome" and RI_B_01.bam as the input file

```
