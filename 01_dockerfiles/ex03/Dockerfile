#creating a docker-machine with more resources:
#	docker-machine create -d virtualbox --virtualbox-memory 4096 --virtualbox-cpu-count 2
#OR
#docker-machine stop Char && VBoxManage modifyvm Char --cpus 2 && VBoxManage modifyvm Char --memory 4096 && docker-machine start Char && eval $(docker-machine env Char)
#build with memory and cpu specified: docker build . -t gitlab -m 4g -c 3
#build image: docker build . -t gitlab 
#docker run --rm --privileged -it -p 80:80 -p 443:443 -p 2122:22 gitlab

FROM ubuntu:16.04
RUN apt-get -y update && apt-get -y upgrade && \
	apt-get -y install curl openssh-server ca-certificates postfix

RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh > script.deb.sh &&\
	bash script.deb.sh &&\ 
	apt-get -y install gitlab-ce

RUN EXTERNAL_URL="localhost"

RUN apt-get install -y tzdata && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /script.deb.sh

EXPOSE 443 80 22

RUN mkdir -p /etc/gitlab/ssl/ && openssl req -new -newkey rsa:2048 -days 365 \
	-nodes -x509 -subj "/C=FR/ST=Paris/L=Clichy/O=GlobalCorp/CN=localhost" -keyout /etc/gitlab/ssl/localhost.key \
	-out /etc/gitlab/ssl/localhost.crt && \
	echo "external_url 'https://localhost'" >> /etc/gitlab/gitlab.rb && \
	echo "letsencrypt['enable'] = false" >> /etc/gitlab/gitlab.rb && \
	echo "AuthorizedKeysFile      /var/opt/gitlab/.ssh/authorized_keys" >> /etc/ssh/sshd_config && \
	(/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure 

ENTRYPOINT service ssh start && (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl start && tail -f /dev/null
