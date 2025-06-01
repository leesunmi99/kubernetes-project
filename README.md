# kubernetes-project


## Vagrant 설치
mkdir cicd
cd cicd

# Vagrant 스크립트 다운로드
curl -O https://raw.githubusercontent.com/k8s-1pro/install/main/ground/cicd-server/vagrant-2.4.3/Vagrantfile

# Rocky Linux Repo 세팅
curl -O https://raw.githubusercontent.com/k8s-1pro/install/main/ground/cicd-server/vagrant-2.4.3/rockylinux-repo.json
vagrant box add rockylinux-repo.json

# Vagrant Vbguest 및 Disk Plugin 설치 
vagrant plugin install vagrant-vbguest vagrant-disksize

# Vagrant 실행
vagrant up
