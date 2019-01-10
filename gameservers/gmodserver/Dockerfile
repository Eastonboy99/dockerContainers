FROM ubuntu:16.04

RUN dpkg --add-architecture i386
RUN apt-get update -y 
RUN DEBIAN_FRONTEND=noninteractive apt-get install mailutils postfix curl wget file bzip2 gzip unzip bsdmainutils python util-linux ca-certificates tmux lib32gcc1 libstdc++6 libstdc++6:i386 lib32tinfo5 binutils gdb sudo -y
RUN usermod -aG sudo gmodserver
RUN adduser --system gmodserver
RUN echo "gmodserver ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers
RUN echo "gmodserver:gmodserver" | chpasswd
RUN mkdir /mnt/game
RUN chown -R gmodserver: /mnt/game

USER gmodserver
WORKDIR /mnt/game

RUN wget -N --no-check-certificate https://raw.githubusercontent.com/Eastonboy99/LinuxGSM/master/linuxgsm.sh && chmod +x linuxgsm.sh && bash linuxgsm.sh gmodserver

RUN /bin/bash ./gmodserver auto-install

# USER gmodserver
# RUN echo "#!/bin/bash" >> ./gmodserverScript.sh
# RUN echo "su -c '/mnt/game/gmodserver start' gmodserver" >> ./gmodserverScript.sh
# RUN chmod +x ./gmodserverScript.sh
# RUN ./gmodserverScript.sh
# RUN yes | /bin/bash ./gmodserver debug
# RUN /bin/bash ./gmodserver start
# RUN /bin/bash ./gmodserver monitor
# WORKDIR /tmp
# RUN DEBIAN_FRONTEND=noninteractive apt install libevent-dev build-essential git autotools-dev automake pkg-config ncurses-dev -y
# RUN DEBIAN_FRONTEND=noninteractive apt remove tmux -y
# RUN git clone https://github.com/tmux/tmux.git --branch 2.0 --single-branch
# WORKDIR /tmp/tmux
# RUN ./autogen.sh
# RUN ./configure
# RUN make -j4
# RUN make install
# RUN make clean
# WORKDIR /mnt/game
USER gmodserver
RUN ./gmodserver start


ENTRYPOINT ["./gmodserver"]

CMD ["console"]