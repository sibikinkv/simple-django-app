FROM python:3.8-slim-buster

ARG APP_HOME=/src

WORKDIR $APP_HOME

RUN apt update \
	&& apt install -y netcat \
	&& rm -rf /var/lib/apt/lists/*

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN mkdir $APP_HOME/static

RUN pip install --upgrade pip
COPY ./requirements.txt .
RUN pip install -r requirements.txt

COPY ./entrypoint.sh .
RUN sed -i 's/\r$//g' entrypoint.sh

COPY . .

ENTRYPOINT ["/src/entrypoint.sh"]