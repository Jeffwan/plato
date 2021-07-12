FROM ubuntu:18.04

RUN apt update && apt install -y default-jdk libgomp1 libnuma-dev

# bazel-bin is soft link which docker doesn't supports. Copy real files to bazel-bin-copy
COPY bazel-bin-copy/example /code
COPY data /data
COPY 3rd/ /3rd
COPY scripts /scripts
