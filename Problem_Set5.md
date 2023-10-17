# MGJW Problem Set 5


## Part 1

### Blast
* Go to assembly page on NCBI. **How many assembled genomes are available for S. aureus on GenBank and RefSeq?**
* Go to the genome page of S. aureus and then press on Genome Assembly and Annotation report and then search for strain N315. Press on the accession number NC_002745.2 (GCF_000009645.1). Now let's try to download a fasta file*. Press on send to and then select file and then select fasta. This should download the fasta file. Do the same step but for strain Newman (NC_009641.1; GCF_000010465.1).
> *Optionally, use [ncbi-datasets](https://www.ncbi.nlm.nih.gov/datasets/docs/v2/download-and-install/) to download both genomes right from the command line:
```
datasets download genome accession GCF_000009645.1  GCF_000010465.1
```

* Move these two files to MGJW
* Make a nucleotide blast database of both files. Check the name of the files and then concatenate them similar to the commands below. **You will need to modify these commands based on the files' names.**
```
conda activate blast
cat genome3.fasta genome4.fasta > genomes_3_4_combined.fasta
makeblastdb -in genomes_3_4_combined.fasta -title two_staph_blast_db -dbtype nucl
blastn -query Two_genes.fasta -db genomes_3_4_combined.fasta -outfmt '6 qseqid sacc evalue qcovs pident' -out Two_genes_output.txt
less Two_genes_output.txt
```

### Mlst
Let's type a S. aureus genome!
```
conda activate mlst
cd ~/MGJW/problem_set4/abricate_genomes
mlst --scheme saureus genome3.fasta
```
**What is the Sequence Type (ST) of this genome?**

You can also run mlst with multiple genomes at once using the *. When using *, make sure that all of the input files are assemblies as mlst works only with contig files.

Additionally, you can redirect the output of the above command to a new file instead of printing it to the screen. This is useful when you are working with many isolates and/or need the report for downstream processing. Let's try it:

```
mlst abricate_genomes/*.fasta > mlst_report.tsv
```

Let's take a look at the report:
```
less mlst_report.tsv
```


## Part 2 for Session 6 Readiness
You will need to install Snippy for Session 6.

[snippy](https://github.com/tseemann/snippy)
```
mamba create -n snippy -c bioconda snippy
conda activate snippy
snippy
```
## Bash Script
[Looping by Qianxuan (Sean) She](https://github.com/qianxuans/MGJW_LoopingScript)
