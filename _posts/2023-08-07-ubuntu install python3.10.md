## UBUNTU:

```
# os update
apt-get update

# install depends
apt-get install -y --no-install-recommends \
  build-essential \
  curl \
  libffi-dev \
  libssl-dev \
  zlib1g-dev \
  liblzma-dev \
  libbz2-dev \
  libreadline-dev \
  libsqlite3-dev

# download python package
wget https://www.python.org/ftp/python/3.10.0/Python-3.10.0.tgz \
    && tar -xvf Python-3.10.0.tgz \
    && cd Python-3.10.0 \
    && ./configure --enable-optimizations \
    && make altinstall

# install pip package manager
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py \
    && python3.10 get-pip.py

# create env
python3.10 -m venv /py && \
  /py/bin/pip install --upgrade pip && \
  /py/bin/pip install --no-cache-dir -r /tmp/requirements.txt && \
  rm /tmp/requirements.txt
```

## Docker:
```
FROM ubuntu:latest
COPY ./requirements.txt /tmp/requirements.txt
COPY ./app /app
COPY ./scripts /scripts

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        build-essential \
        curl \
        libffi-dev \
        libssl-dev \
        zlib1g-dev \
        liblzma-dev \
        libbz2-dev \
        libreadline-dev \
        libsqlite3-dev

RUN wget https://www.python.org/ftp/python/3.10.0/Python-3.10.0.tgz \
    && tar -xvf Python-3.10.0.tgz \
    && cd Python-3.10.0 \
    && ./configure --enable-optimizations \
    && make altinstall

RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py \
    && python3.10 get-pip.py

RUN python3.10 -m venv /py && \
  /py/bin/pip install --upgrade pip && \
  /py/bin/pip install --no-cache-dir -r /tmp/requirements.txt && \
  rm /tmp/requirements.txt
```
