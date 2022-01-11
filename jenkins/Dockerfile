FROM jenkins/jenkins:latest

## 현재 유저권한으로
USER $USER

## docker 설치 
RUN curl -s https://get.docker.com/ | sh

## docker-compose 설치
RUN curl -L "https://github.com/docker/compose/releases/download/1.28.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && \
    chmod +x /usr/local/bin/docker-compose && \
    ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

## dcs 툴 설치
RUN curl -sL bit.ly/ralf_dcs -o ./dcs && \
    chmod 755 dcs && \
    mv dcs /usr/local/bin/dcs

## zulu jdk 11 설치
RUN apt-get update && apt-get -y install software-properties-common && \
    apt-add-repository 'deb http://repos.azulsystems.com/ubuntu stable main' && \
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 0xB1998361219BD9C9 && \
    apt-get update && apt-get -y install zulu-11

## docker group 에 jenkins 추가 
RUN usermod -aG docker jenkins