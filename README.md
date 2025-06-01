CI/CD 서버를 위한 vagrant 설치 및 Jenkins 초기 세팅 

# Vagrant 설치 - cicd-server

📁 디렉토리 생성 및 이동

```bash
mkdir cicd
cd cicd
```



⬇️ Vagrant 스크립트 다운로드

```bash
curl -O https://raw.githubusercontent.com/k8s-1pro/install/main/ground/cicd-server/vagrant-2.4.3/Vagrantfile
```

Rocky Linux Repo 세팅
```bash
curl -O https://raw.githubusercontent.com/k8s-1pro/install/main/ground/cicd-server/vagrant-2.4.3/rockylinux-repo.json
vagrant box add rockylinux-repo.json
```
Vagrant Vbguest 및 Disk Plugin 설치 
```bash
vagrant plugin install vagrant-vbguest vagrant-disksize
```
Vagrant 실행
```bash
vagrant up
```



# Jenkins 초기 세팅

