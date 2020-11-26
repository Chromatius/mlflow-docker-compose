FROM python:3.7-slim-buster

RUN apt-get update && apt-get install -y \
  tree

# Install python packages
RUN pip install mlflow psycopg2-binary

RUN mkdir -p /mlflow/mlruns

WORKDIR /mlflow

ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8

RUN echo "export LC_ALL=$LC_ALL" >> /etc/profile.d/locale.sh
RUN echo "export LANG=$LANG" >> /etc/profile.d/locale.sh

COPY start.sh ./start.sh
RUN chmod +x ./start.sh

ENTRYPOINT ["./start.sh"]