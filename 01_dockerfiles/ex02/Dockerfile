FROM	ruby:latest

MAINTAINER alamy <alamy@student.42.fr>

RUN		apt-get update && \ 
		apt-get install -y build-essential libpq-dev nodejs && \
		gem install rails && \ 
		apt-get install -y mysql-client postgresql-client sqlite3

ONBUILD RUN bundle install
ONBUILD EXPOSE	3000
ONBUILD COPY /opt/app
ONBUILD WORKDIR	/opt/app

#docker build -t alamy/debian:latest $PWD

#FROM ruby:latest

#RUN mkdir -p /opt/app
#WORKDIR /opt/app

#RUN apt-get update && \
 #   apt-get install -y nodejs && \
  #  apt-get install -y sqlite3 && \
   # gem install rails && \
    #rm -rf /var/lib/apt/lists/*

#COPY . /opt/app

#EXPOSE 3000

#ONBUILD RUN bundle install && \
 #           rake db:migrate && \
  #          rake db:seed 