FROM pytorch/pytorch:2.0.1-cuda11.7-cudnn8-runtime

ENV DEBIAN_FRONTEND=noninteractive
SHELL ["/bin/bash", "-c"]

# apt install
RUN apt-get update && apt-get upgrade -y
RUN apt-get update --fix-missing && apt-get install -y --no-install-recommends\     
    build-essential \
    software-properties-common \
    build-essential \
    libfreetype6-dev \
    libgdal-dev \
    htop \
    && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* 

RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y libgl1-mesa-dev

# install dependencies
COPY env/requirements.txt /tmp/requirements.txt
RUN pip3 install --upgrade pip setuptools
RUN pip3 install -r /tmp/requirements.txt && \
    rm -rf /tmp/requirements.txt

# workspace
ENV PYTHONPATH $PYTHONPATH:/workspace
ENV PATH /opt/conda/bin:$PATH
WORKDIR /workspace/