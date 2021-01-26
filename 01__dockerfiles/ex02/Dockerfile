FROM ruby:latest

ENV PORT 3000

EXPOSE $PORT

RUN mkdir -p /opt/

WORKDIR /opt/

RUN gem install rails bundler
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update -qq && apt-get install -yf nodejs yarn
RUN rails new app

WORKDIR /opt/app/

RUN bundle update
RUN bundle install

ONBUILD RUN rake db:migrate
ONBUILD RUN rake db:seed