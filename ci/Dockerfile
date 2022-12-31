
#retrieve main docker image

FROM  yoedistro/yoe-build:buster 

ARG BOARD=stratix10

# Proxies





#setting up main directory
RUN mkdir -p /home/build/yocto
WORKDIR /home/build/yocto
RUN cd /home/build/yocto


#cloning

RUN git clone -b honister http://git.yoctoproject.org/poky
RUN git clone -b honister http://git.yoctoproject.org/meta-intel-fpga

#Setting up yocto
RUN source poky/oe-init-build-env ./build
RUN ls build
RUN pwd
RUN echo 'MACHINE = "'$BOARD'"' >> build/conf/local.conf
RUN echo 'BBLAYERS += " ${TOPDIR}/../meta-intel-fpga "' >> build/conf/bblayers.conf


#Building
RUN bash -c "source poky/oe-init-build-env ./build;  bitbake core-image-minimal" 



