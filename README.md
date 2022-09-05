# Docker image of SWASH model with MPI (for parallel or serial runs)
https://swash.sourceforge.io/

## 1a) Pull the docker image from DockerHub then go to 2)
docker pull simonwp/swash:801_mpi

## or 1b) build docker image locally on your machine (with swash version 8.01)
sudo docker build -f Dockerfile_MPI -t swash:801_mpi .

## 2)To start the docker
sudo docker run -it swash:801_mpi

## 3)To run one of the test case to check install
cd ./testcases/l12bbbar/

swashrun -input l12bbb01.sws -mpi 3 # use 3 processors

swashrun -input l12bbb01.sws -mpi 1 # to use only one processor

## To run one of your SWASH model 
Mount the folder you want to see inside the docker container 
like this  : 

docker run -it -v /path/swash_run:/swash_run_in_docker swash:801_mpi
cd swash_run_in_docker

## >>>Now start your simulation !

##### Notes to push image to dockerhub
docker tag swash:801_mpi simonwp/swash:801_mpi # tag local image with correct dockerhub name 

docker push simonwp/swash:801_mpi              # push image to docker hub

##### Thanks to Ioannis Karmpadakis for sharing his own dockerfile that served as a basis for this MPI version 
https://github.com/ikarmpadakis/swash/blob/master/Docker/Dockerfile
