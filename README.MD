## How to run ARIMA?
- 1. `ssh -i id-rsa cloud@141.5.109.198`
- 2. create new `screen` by this command `screen -s arima_screen_name`, if you want to check result you have to go in `screen`
  - 2.1 `screen -ls` - list of screen
  - 2.2 `screen a`
3. `docker ps ` - get list of running docker and take docker id to enter
4. `docker exec -it {docker_id} bash` - enter inside of docker
5. move R1, R2 to the /Oncology/INPUT/ `mv /shared_folder/...R1..fastq.qz /Oncology/INPUT/`
6. then run this command when you are in /Oncology folder
```
bash run_Arima-Oncology-Pipeline-singularity-v0.3.sh -I /Oncology/INPUT/P1574_DNA_01_DHL4_HiChIP_S1_R1_001.fastq.gz,/Oncology/INPUT/P1574_DNA_01_DHL4_HiChIP_S1_R2_001.fastq.gz -o /Oncology/OUTPUT/
```
## How can I move folders?
- 1. `ssh -i id-rsa cloud@141.5.109.198`
- 3. check job is done or not
  - 2.1 `screen -list` - to get id and
  - 2.2 `screen -r {id of screen}` 
  - 2.3 if you see `job is finished`, you can start doing step 4, otherwise use `ctrl+a+d` to deattach from screen, and job will continue in background
- 4. move OUTPUT folder to the shared folder in docker
```
mv /Oncology/OUTPUT/ /shared_folder/OUTPUT/Farage/
```
- 5. clean OUTPUT folder
```
rm -rf /Oncology/OUTPUT
```
- 6. then close `screen` by using `exit` command multiple times until you exit ssh


## How to check if the job is done?
1. `ssh -i id-rsa cloud@141.5.109.198`
2. use `htop`, and if CPU usage is high, it means that job is still running in background.


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




