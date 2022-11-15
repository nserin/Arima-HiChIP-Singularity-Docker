## How to run ARIMA?
1. `ssh -i id-rsa cloud@141.5.109.198`
2. create new `screen` by this command screen -s arima_screen_name, if you want to check result you have to go in `screen`
  2.1 `screen -ls` - list of screen
  2.2 `screen a`
3. `docker ps ` - get list of running docker and take docker id to enter
4. `docker exec -it {docker_id} bash` - enter inside of docker


# How to create new docker with host network
```
docker run -it --network host -v /home/cloud/shared_folder/:/shared_folder/ --name arima_oncology --privileged arimaxiang/arima_oncology:0.3
```

# How to install singularity in docker, (it should be installed in docker)
https://stackoverflow.com/a/66978973

# Download .sif file
(it would be better to download file in host server not in docker)
```
wget ftp://ftp-arimagenomics.sdsc.edu/pub/ARIMA_Oncology_Pipeline/Arima-Oncology-Pipeline-singularity-v0.2.sif shared_folder
```

# Run Mapping inside the docker
```
bash run_Arima-Oncology-Pipeline-singularity-v0.3.sh -I /Oncology/INPUT/P1574_DNA_01_DHL4_HiChIP_S1_R1_001.fastq.gz,/Oncology/INPUT/P1574_DNA_01_DHL4_HiChIP_S1_R2_001.fastq.gz -o /Oncology/OUTPUT/
```




