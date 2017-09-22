From beevelop/ionic

MAINTAINER zhangzhuang 
RUN apt-get -qq install -y vim  && \
    mkdir  /opt/apps/  && \
    cd /opt/apps  && \
    ionic start myApp01 blank && \
    ionic start myApp02 tabs  && \
    ionic start myApp03 sidemenu  && \
    cd myApp03  && \
    ionic cordova platform add android  && \
    ionic cordova build android 
    
