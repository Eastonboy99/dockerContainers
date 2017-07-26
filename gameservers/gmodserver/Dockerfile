FROM ubuntu:16.04

RUN dpkg --add-architecture i386
RUN apt-get update -y 
RUN DEBIAN_FRONTEND=noninteractive apt-get install mailutils postfix curl wget file bzip2 gzip unzip bsdmainutils python util-linux ca-certificates tmux lib32gcc1 libstdc++6 libstdc++6:i386 lib32tinfo5 binutils -y

RUN adduser --system gmodserver

RUN mkdir /mnt/game
RUN chown -R gmodserver: /mnt/game

USER gmodserver
WORKDIR /mnt/game

RUN wget -N --no-check-certificate https://gameservermanagers.com/dl/linuxgsm.sh && chmod +x linuxgsm.sh && bash linuxgsm.sh gmodserver

RUN /bin/bash ./gmodserver auto-install
USER root
RUN DEBIAN_FRONTEND=noninteractive apt-get install gdb -y

USER gmodserver

# RUN yes | /bin/bash ./gmodserver debug
RUN /bin/bash ./gmodserver start
RUN /bin/bash ./gmodserver monitor

ENTRYPOINT ["./gmodserver"]

CMD ["console"]