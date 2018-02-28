FROM	ruby:latest

MAINTAINER alamy <alamy@student.42.fr>

RUN		apt-get update -qq && \ 
		apt-get install -y build-essential libpq-dev nodejs && \
		gem install rails && \ 
		apt-get install -y mysql-client postgresql-client sqlite3

ONBUILD RUN bundle install
ONBUILD EXPOSE	3000
ONBUILD COPY /opt/app
ONBUILD WORKDIR	/opt/app

CMD ruby