## Katie Crider's Advanced Genomics Log (Spring 2021)

## Day 02 Exercises: 2021-01-22
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
(base) Katies-MacBook-Air-4:KatieCriderAdvancedGenomicsLog katiecrider$ git commit -m ‘updating notebook with day02 exercises’
(base) Katies-MacBook-Air-4:KatieCriderAdvancedGenomicsLog katiecrider$ git push -u origin main

```

## Day 03 Exercises/Day 2 HW: 1/27/21
``` sh
#exercises day03 / Day02HW:

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
