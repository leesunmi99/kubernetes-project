CI/CD 서버를 위한 vagrant 설치 및 Jenkins 초기 세팅 과정입니다. 

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
만약 오류시 ```vagrant destroy```를 사용해서 삭제 후 재설치 


# Jenkins 초기 세팅
### 초기 비밀번호 확인 (VM에서)
```bash
cat /var/lib/jenkins/secrets/initialAdminPassword
```

### 전역 설정 (System Configuration > tools)
JDK installations
Name: jdk-17
JAVA_HOME: java-17-openjdk-17.0.15.0.6-2.el8.x86_64/bin/java
```bash
# java 명령어 실행 위치 확인 
readlink -f $(which java)
export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-17.0.15.0.6-2.el8.x86_64
export PATH=$JAVA_HOME/bin:$PATH
```

Gradle installations
name: gradle-7.6.1
GRADLE_HOME: /opt/gradle/gradle-7.6.1


# Docker login
단, 이는 급하게 CI/CD 서버를 구축할 때만 사용한다. 
```bash
chmod 666 /var/run/docker.sock
usermod -aG docker jenkins
su - jenkins -s /bin/bash
docker login
```


# Master Node 의 인증서 복사 (CI/CD 로그인 - Jenkins)
```bash
scp root@192.168.56.30:/root/.kube/config ~/.kube
```
