FROM centos:7
RUN mkdir /incoming /input
WORKDIR /
CMD ["/bin/bash"]