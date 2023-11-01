# Microbial Genomics Journey Workshop 2023
## Session 7: Pangenome analysis
The pangenome of a microbial species is the total set of genes present in all members of that species. It is typically much larger than the genome of any single member of the species. The pangenome can be divided into two categories: the core genome and the accessory genome.<br/>

The core genome is the set of genes that are present in all members of the species. These genes are essential for the basic functions and survival of the microorganisms and are typically conserved due to their importance.<br/>

The accessory genome (also known as the dispensable or flexible genome) is the set of genes that are present in some, but not all, members of the species. It is typically more variable than the core genome. These genes can provide additional capabilities or adaptations to specific environments, such as resistance to antibiotics, virulence factors, or metabolic pathways. The accessory genome contributes to the genomic diversity and ecological success of a species.<br/>

In some cases, more categories are included:<br/>

Shell genes: These genes are present in a moderate number of strains within a species, making them more frequent than cloud genes but less conserved than core genes.<br/>

Cloud genes: These genes are present in only a few strains within a species and are the least conserved genes in the pangenome. Cloud genes can represent recent acquisitions of genetic material, such as through horizontal gene transfer.<br/>

The pangenome can be used to study the evolution of microbial species, to identify genes that are important for particular functions, and to develop new methods for microbial diagnostics and therapeutics.<br/>

Here are some examples of how the pangenome has been used in research:

* To study the evolution of microbial species: The pangenome can be used to compare the genomes of different strains of a species
* To identify genes that have been gained or lost over time. This can help to understand how the species has adapted to different environments.
* To identify genes that are important for particular functions:
* To develop new methods for microbial diagnostics and therapeutics: The pangenome can be used to identify genes that are unique to particular strains of a species. This can help to develop new methods for diagnosing and treating microbial infections.

## Roary
[Roary](http://sanger-pathogens.github.io/Roary/) is a tool designed to quickly build large-scale pan genomes for prokaryote populations, consisting of hundreds or thousands of isolates. It identifies core and accessory genes, enabling researchers to gain insights into the genetic structure of prokaryotic genomes. Roary can allow efficient analysis on a standard desktop without sacrificing accuracy. It will give different outputs which can be explored and understood from the explanation available from roary website.

### Conda:
```
conda activate roary
cd ~/MGJW
mkdir roary_results
cd roary_results
roary ../gff/*.gff
```
**gff files and folder are available in the problem set 6 dataset**

### Docker:
#### Pull the docker image
```
docker pull qianxuanshe/mgjw-sep2023-s7:latest
```
#### Run the docker image
```
docker run -it qianxuanshe/mgjw-sep2023-s7
```
#### Make the directory for roary output, and go to the directory
```
mkdir roary_results
cd roary_results
```
#### Run Roary
```
roary ../gff/*.gff
```
## Panaroo
Panaroo(https://gtonkinhill.github.io/panaroo/#/) is a graph based pangenome clustering tool that is able to account for many of the sources of error introduced during the annotation of prokaryotic genome assemblies.

### Docker:
#### Pull the docker image
```
docker pull qianxuanshe/mgjw-sep2023-s7-panaroo:latest
```
#### Run the docker image
```
docker run -it qianxuanshe/mgjw-sep2023-s7-panaroo
```
#### Make the directory for panaroo output
```
mkdir panaroo_results
```

#### Run Panaroo
```
panaroo -i /session7/gff/*.gff -o panaroo_results --clean-mode strict
```

## Scoary
[Scoary](https://github.com/AdmiralenOla/Scoary) is a tool that uses Roary's gene_presence_absence.csv file and a user-created traits file to calculate associations between accessory genome genes and traits. It generates a list of genes ranked by the strength of association for each trait.
### Conda:
```
scoary -p 1 -g op_roary/gene_presence_absence.csv -t traits.csv
```
### Docker
#### Run the same docker image(qianxuanshe/mgjw-sep2023-s7).
Ignore this step if you don't exit the docker image.
```
docker run -it qianxuanshe/mgjw-sep2023-s7
```
#### Run Scoary
```
scoary -p 1 -g /session7/roary_results/gene_presence_absence.csv -t traits.csv
```


## Further Readings
* [roary](https://academic.oup.com/bioinformatics/article/31/22/3691/240757)
* [Scoary](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-016-1108-8)
* [Panaroo](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-020-02090-4)
