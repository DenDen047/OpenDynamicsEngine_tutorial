FROM dorowu/ubuntu-desktop-lxde-vnc


# init
RUN apt-get update && apt-get upgrade -y

# ODE (http://szmlb.hatenablog.com/entry/2014/12/29/234455)
# RUN apt-get install -y automake libtool freeglut3-dev

WORKDIR /opt
RUN apt-get install -y wget
RUN wget https://bitbucket.org/odedevs/ode/downloads/ode-0.16.tar.gz
RUN tar xzvf ode-0.16.tar.gz
WORKDIR /opt/ode-0.16
RUN ./configure \
  --with-trimesh=opcode \
  --enable-new-trimesh \
  --enable-shared  \
  --enable-release \
  --with-x \
  --enable-double-precision \
  --with-libccd
RUN make
RUN make install

RUN cp -r include/drawstuff /usr/local/include/
RUN cp drawstuff/src/.libs/libdrawstuff.* /usr/local/lib
RUN ldconfig

