# How to run
#
# docker run -d \
#       -v /etc/localtime:/etc/localtime:ro \
#       -v /tmp/.X11-unix:/tmp/.X11-unix \
#       -e DISPLAY=unix$DISPLAY \
#       --cap-add NET_RAW \
#       --cap-add NET_ADMIN \
#       --net host \
#       --name wireshark \
#       r2dkennobi/wireshark
#
# References: 
# - http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/
FROM ubuntu:16.04
LABEL maintainer "Kenny Yokoyama <kenny.yokoyama@shield.ai>"

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
  && apt-get install -y software-properties-common --no-install-recommends \
  && add-apt-repository ppa:wireshark-dev/stable \
  && apt-get update && apt-get install -y wireshark libcap2-bin \
  && rm -rf /var/lib/apt/lists/*


# Even in Docker, want to capture as non-root user
ENV HOME /home/wireshark
RUN useradd --create-home --home-dir $HOME wireshark \
  && chown -R wireshark:wireshark $HOME \
  && usermod -a -G wireshark wireshark

RUN chown root:wireshark /usr/bin/dumpcap \
  && setcap 'CAP_NET_RAW,CAP_NET_ADMIN=eip' /usr/bin/dumpcap

USER wireshark

WORKDIR wireshark

ENTRYPOINT ["wireshark"]
