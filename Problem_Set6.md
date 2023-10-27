# MGJW Problem Set 6

## Part 1
### Download needed files
* To follow the steps here, you need to download this file from this dropbox URL [problem_set6.tar.gz](https://www.dropbox.com/s/hyjuujea5y0wd2c/problem_set6.zip?dl=0) and put it in MGJW or using `wget -O problem_set6.tar.gz https://www.dropbox.com/s/hyjuujea5y0wd2c/problem_set6.zip?dl=0 --no-check-certificate`
* If you downloaded the file from the web and not using `wget`, you will need to move it to MGJW `mv ~/Downloads/problem_set6.tar.gz ~/MGJW`.
* Unarchive the file `tar -xf problem_set6.tar.gz -C ./`

### Snippy through a Docker image
To use the docker image:
1. Download the docker hub desktop at https://www.docker.com/get-started/ (choose the correct version for different systems and specs).
2. Install and open the docker hub desktop(no need to sign in if just use the docker image)
open the terminal, and pull the docker image for session 6 using:
```
docker pull qianxuanshe/mgjw-sep2023-s6:latest
```
3. We can check current local images using the docker hub desktop or in terminal using
```
docker images
```
4. To use the image using a container created with random name (can easily be found and deleted in Docker Desktop)
```
docker run -it qianxuanshe/mgjw-sep2023-s6
```
5. there are 2 directories in the image. one is problem_set6, another is session6. The files needed in the class or the problem set are in the directories.
6. You can simply now follow the steps in the next section. **You do not need to activate an environment before using the tools in a docker image**. Use `ls` to know what the folders are in your docker image and then move between the different folders for the problem set.

### Snippy
Let's produce a core snp alignment for multiple Staphylococcus aureus genomes. These genomes are from the North American and South American parallel epidemics of USA300. We will need to use [Snippy](https://github.com/tseemann/snippy) which finds SNPs between a reference genome and your NGS sequence reads or assembled genomes. We will use `V2200_PEB.fna.gz` as a reference. To simplify running the 4 isolate sequences (contigs) against the same reference, we can use the [snippy-multi](https://github.com/tseemann/snippy#using-snippy-multi). This script requires a tab separated input file as follows, and can handle paired-end reads, single-end reads, and assembled contigs. We will a homemade script `snippy_convert_list_input_tab.py` to produce the tab-separated file that `snippy-multi` needs.

```
conda activate snippy
cd ~/MGJW/problem_set6/genomes
ls > ../files_list.txt
cd ..
chmod +x snippy_convert_list_input_tab.py
./snippy_convert_list_input_tab.py files_list.txt snippy_tab_list.txt
snippy-multi snippy_tab_list.txt --ref V2200_PEB.fna > runme.sh
chmod +x runme.sh
./runme.sh
```

## Part 2 for Session 7 Readiness
You will need to install Roary, Scoary, Panaroo for Session 7. The installation for roary and panaroo are challenging so do not get frustrated if they do not work.

* [Roary](https://github.com/sanger-pathogens/Roary)
```
mamba create -n roary -c bioconda roary
conda activate roary
roary -h
```
If you have a problem with the Rule module, you may need to run `cpan File::Find::Rule module`

* [Scoary](https://github.com/AdmiralenOla/Scoary)
```
mamba create -n scoary -c bioconda scoary
conda activate scoary
scoary -h
```
* [Panaroo](https://gtonkinhill.github.io/panaroo/#/)
```
cd MGJW/
mamba create -n panaroo python=3.9.16
conda activate panaroo
mamba install -c conda-forge biopython networkx gffutils joblib tqdm peewee
mamba install -c bioconda python-edlib cd-hit mafft
git clone https://github.com/gtonkinhill/panaroo
cd panaroo/
python3 setup.py install
panaroo -h
```
## part 3
[Visualizing Your SNPs](https://github.com/ahmedmagds/Microbial-Genomics-Journey-Workshop-2023/blob/main/snipit.md)
