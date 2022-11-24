VERSION 0.6
FROM python:3

RUN pip install grpcio protobuf pycodestyle

WORKDIR /kvclient

code:
    COPY client.py .
    COPY github.com/earthly/earthly-example-proto:main+proto-py/py-pb/*.py .

lint:
    FROM +code
    RUN pycodestyle client.py

kvclient-docker:
    FROM +code
    SAVE IMAGE kvclient:latest

all:
    BUILD +lint
    BUILD +kvclient-docker
