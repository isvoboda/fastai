FROM nvidia/cuda:10.0-base-ubuntu18.04

ENV LC_ALL C.UTF-8
ENV LANG C.UTF-8

RUN apt-get update && apt-get install -y\
    libnvtoolsext1 \
    python3 \
    python3-pip \
    python3-dev && \
rm -rf /var/lib/apt/lists/*

RUN python3 -m pip install pipenv
WORKDIR /app/env
COPY torch-1.0.0-cp36-cp36m-linux_x86_64.whl torch-1.0.0-cp36-cp36m-linux_x86_64.whl
# RUN wget https://download.pytorch.org/whl/cu100/torch-1.0.0-cp36-cp36m-linux_x86_64.whl
COPY Pipfile /app/env/Pipfile
COPY Pipfile.lock /app/env/Pipfile.lock
RUN pipenv install --system --deploy && rm torch-1.0.0-cp36-cp36m-linux_x86_64.whl
