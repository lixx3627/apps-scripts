# Description
This repo contains miscellaneous stand-alone scripts for working with PacBio Data

## getJobData.py
### Dependencies
 - pbcommand
### Usage
    $ python getJobData.py -h
    usage: getJobData.py [-h] [-o,--outDir OUTDIR] [-n,--names] [--host HOST]
                         [--port PORT]
                         jobNumber [dataName [dataName ...]]
    
    Get job outputs from smrtlink datastore
    
    positional arguments:
      jobNumber           SMRT Link job number
      dataName            name of datasetset to get. default None. (use -n to see
                          available names)
    
    optional arguments:
      -h, --help          show this help message and exit
      -o,--outDir OUTDIR  output destination directory. default cwd
      -n,--names          print names of available items in datastore. default
                          False
      --host HOST         smrtlink host name. default smrtlink
      --port PORT         smrtlink services port. default 8081
### Examples
-Print description and paths to output files
    $ python getJobData.py --host smrtlink-release --port 9091 -n 12258
    Amplicon Consensus Report               /pbi/analysis/smrtlink/release/smrtsuite/userdata/jobs_root/012/012258/tasks/pbreports.tasks.amplicon_analysis_consensus-0/consensus_report.json
    Consensus Sequence Statistics           /pbi/analysis/smrtlink/release/smrtsuite/userdata/jobs_root/012/012258/tasks/pbcoretools.tasks.gather_csv-1/file.csv
    Chimeric/Noise Sequences by barcode     /pbi/analysis/smrtlink/release/smrtsuite/userdata/jobs_root/012/012258/tasks/pbcoretools.tasks.split_laa_fastq-0/chimera_fastq.gz
    Consensus Amplicons                     /pbi/analysis/smrtlink/release/smrtsuite/userdata/jobs_root/012/012258/tasks/pbcoretools.tasks.split_laa_fastq-0/consensus_fastq.gz
    Input Molecule Report CSV               /pbi/analysis/smrtlink/release/smrtsuite/userdata/jobs_root/012/012258/tasks/pbcoretools.tasks.gather_csv-2/file.csv
    Consensus Amplicons                     /pbi/analysis/smrtlink/release/smrtsuite/userdata/jobs_root/012/012258/tasks/pbcoretools.tasks.gather_fastq-1/file.fastq
    LAA Input Report                        /pbi/analysis/smrtlink/release/smrtsuite/userdata/jobs_root/012/012258/tasks/pbreports.tasks.amplicon_analysis_input-0/amplicon_input_report.json
    Chimeric/Noise Sequences                /pbi/analysis/smrtlink/release/smrtsuite/userdata/jobs_root/012/012258/tasks/pbcoretools.tasks.gather_fastq-2/file.fastq
    Master Log                              /pbi/analysis/smrtlink/release/smrtsuite/userdata/jobs_root/012/012258/logs/master.log
    Analysis Log                            /pbi/analysis/smrtlink/release/smrtsuite/userdata/jobs_root/012/012258/logs/pbsmrtpipe.log
-Copy outputs to local directory
    $ python getJobData.py --host smrtlink-release --port 9091 12258 'Amplicon Consensus Report' 'Input Molecule Report CSV' -o /my/output/directory
    'Amplicon Consensus Report'             =>      /my/output/directory/consensus_report.json
    'Input Molecule Report CSV'             =>      /my/output/directory/file.csv

Disclaimer
THIS WEBSITE AND CONTENT AND ALL SITE-RELATED SERVICES, INCLUDING ANY DATA, ARE PROVIDED "AS IS," WITH ALL FAULTS, WITH NO REPRESENTATIONS OR WARRANTIES OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING, BUT NOT LIMITED TO, ANY WARRANTIES OF MERCHANTABILITY, SATISFACTORY QUALITY, NON-INFRINGEMENT OR FITNESS FOR A PARTICULAR PURPOSE. YOU ASSUME TOTAL RESPONSIBILITY AND RISK FOR YOUR USE OF THIS SITE, ALL SITE-RELATED SERVICES, AND ANY THIRD PARTY WEBSITES OR APPLICATIONS. NO ORAL OR WRITTEN INFORMATION OR ADVICE SHALL CREATE A WARRANTY OF ANY KIND. ANY REFERENCES TO SPECIFIC PRODUCTS OR SERVICES ON THE WEBSITES DO NOT CONSTITUTE OR IMPLY A RECOMMENDATION OR ENDORSEMENT BY PACIFIC BIOSCIENCES.