from buildbot/buildbot-worker:master

user root
run echo "deb http://apt.dockerproject.org/repo ubuntu-trusty main" \
          > /etc/apt/sources.list.d/docker.list \
      && apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 \
          --recv-keys 58118E89F3A912897C070ADBF76221572C52609D \
      && DEBIAN_FRONTEND=noninteractive \
      && apt-get update \
      && apt-get install -y apt-transport-https \
      && apt-get install -y ca-certificates \
      && apt-get install -y curl \
      && apt-get install -y docker-engine \
      && apt-get install -y sudo \
      && groupadd -r buildbot \
      && useradd -r -g buildbot buildbot \
      && rm -rf /var/lib/apt/lists/*
run echo 'buildbot ALL=NOPASSWD: ALL' >> /etc/sudoers

run curl -L https://github.com/docker/compose/releases/download/1.8.0/\
docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose; \
chmod +x /usr/local/bin/docker-compose

user buildbot
