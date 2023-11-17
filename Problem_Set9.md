# MGJW Problem set 9
## Metagenomics
### Using Sunbeam
1. Pull the docker image: `docker pull qianxuanshe/mgjw-sep2023-s9:latest`
2. Run the docker image in an interactive mode: `docker run -it qianxuanshe/mgjw-sep2023-s9:latest`
3. Download the k2_standard_08gb_20231009 database: `bash download_db.sh`
4. Create a new Sunbeam project: `sunbeam init sunbeam_demonstration --data_fp /MGJW_metagenomics/reads`
5. Replace the sunbeam_config.yml: `cp sunbeam_config.yml /MGJW_metagenomics/sunbeam_demonstration`
6. Run Sunbeam: `sunbeam run --profile sunbeam_demonstration/ all_classify`
7. You can use the [R script](Shotgun_Sunbeam_demonstration.Rmd) to replicate the results shared by Dr. Ceylan Tanes
#### Notes
1. Turn on "Rosetta for x86/amd64 emulation on Apple silicon" in Docker settings if you are using M1 or M2 Apple CPUs.
2. Allocate 16GB RAM in the Docker settings.
3. The results will be under /MGJW_metagenomics/sunbeam_demonstration/sunbeam_output
