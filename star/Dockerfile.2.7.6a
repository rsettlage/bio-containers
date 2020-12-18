FROM ubuntu:20.04

LABEL maintainer="rsettlag@vt.edu" \
      description="Dockerfile providing the STAR sequencing read aligner" \
      org.label-schema.vcs-url="https://github.com/rsettlage/bio-containers"

ENV PATH="/STAR/bin/Linux_x86_64_static:${PATH}"

RUN apt update \
  && apt install -y git vim zlib1g-dev build-essential

RUN git clone https://github.com/alexdobin/STAR.git \
  && cd STAR/source \
  && make STARstatic

CMD STAR

