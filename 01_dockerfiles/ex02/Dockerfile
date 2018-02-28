FROM	ruby

EXPOSE	3000
WORKDIR	/opt/app

RUN		apt-get update -qq && \ 
		apt-get install -y build-essential libpq-dev nodejs && \
		gem install bundler && \
		