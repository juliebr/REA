FROM ruby:2.5

# throw errors if Gemfile has been modified since Gemfile.lock
RUN bundle config --global frozen 1



WORKDIR /usr/src/sinatra

COPY simple-sinatra/* ./

RUN bundle install


EXPOSE 9292

CMD bundle exec rackup