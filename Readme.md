This is a centos + mysql + xtrabackup docker container to restore Bahmni mysql backup
ON HOST - 
cd /root
git clone https://github.com/Pasayadaan/bahmni-mysql-restore.git
cd bahmni-mysql-restore
tar -xvf backuptest.tgz
docker build -t <repo name> .
docker images
docker run -e container_name=bahmni -v /root/bahmni-mysql-restore:/data/openmrs -it --privileged=true --security-opt seccomp:unconfined --cap-add=SYS_ADMIN -d --name bahmni <image> /usr/sbin/init
docker exec -it bahmni
  
In Container
bahmni --help
bahmni -i local restore --restore_type=db --options=bahmni_reports --strategy=pitr   --restore_point=20201219131551_full

