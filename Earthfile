FROM python:3

RUN pip install grpcio protobuf

WORKDIR /kvclient

code:
    COPY client.py .
    COPY github.com/earthly/earthly-example-proto:example+proto-py/py-pb/*.py .

lint:
    FROM +code
    RUN echo TODO

kvclient:
    FROM +code

kvclient-docker:
    FROM +kvclient
    ENTRYPOINT python3 client.py
    SAVE IMAGE as kvclient:latest

all:
    BUILD +lint
    BUILD +kvclient-docker
