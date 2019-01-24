FROM ruby:2.4-alpine

RUN apk add --update build-base postgresql-dev tzdata

# throw errors if Gemfile has been modified since Gemfile.lock
# RUN bundle config --global frozen 1

# RUN gem install rails -v '5.1.6'

WORKDIR /usr/src/app