FROM deeppavlov/deeppavlov:1.2.0

RUN apt-get update && apt-get install git -y

ARG COMMIT=0.13.0
ARG CONFIG
ARG SERVICE_PORT
ARG SRC_DIR
ARG TOP_N

ENV COMMIT=$COMMIT
ENV CONFIG=$CONFIG
ENV SERVICE_PORT=$SERVICE_PORT
ENV TOP_N=$TOP_N

COPY ./annotators/fact_retrieval_rus/requirements.txt /src/requirements.txt
RUN pip install -r /src/requirements.txt

RUN pip install git+https://github.com/deeppavlov/DeepPavlov.git@${COMMIT}

COPY $SRC_DIR /src

WORKDIR /src

CMD gunicorn  --workers=1 --timeout 500 server:app -b 0.0.0.0:8130

