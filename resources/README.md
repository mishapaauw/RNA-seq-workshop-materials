## Arabidopsis RNA-seq reads

For this workshop, we use reads from ENA project [PRJEB13938](https://www.ebi.ac.uk/ena/browser/view/PRJEB13938). 

Download the reads from one sample:

```bash
curl ftp://ftp.sra.ebi.ac.uk/vol1/fastq/ERR140/009/ERR1406259/ERR1406259.fastq.gz --output ERR1406259.fastq.gz
```

Then, create three different subsampling datasets from this one sample. They will be treated as different 'samples' in the tutorial:

```bash
seqkit sample -s 123 -p 0.1 ERR1406259.fastq.gz| seqkit head -n 50000 > sample1.fastq.gz
seqkit sample -s 124 -p 0.1 ERR1406259.fastq.gz| seqkit head -n 50000 > sample2.fastq.gz
seqkit sample -s 125 -p 0.1 ERR1406259.fastq.gz| seqkit head -n 50000 > sample3.fastq.gz
```

Create one sample with only bad quality reads, using the `-R` option of `seqkit`:

```bash
seqkit seq -R 15 ERR1406259.fastq.gz | seqkit head -n 50000 > sample4.fastq.gz
```

Remove the full read set, we don't need this in the repository:

```bash
rm ERR1406259.fastq.gz 
```

## Software used

* [seqkit](https://bioinf.shenwei.me/seqkit/) version 2.10.1.
