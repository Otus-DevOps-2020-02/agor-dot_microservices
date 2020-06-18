FROM alpine:3.7
ENV BUILD_PACKAGES curl-dev ruby-dev build-base
ENV RUBY_PACKAGES ruby ruby-io-console ruby-bundler
RUN apk add --no-cache $BUILD_PACKAGES && \
    apk add --no-cache $RUBY_PACKAGES && \

ENV APP_HOME /app
RUN mkdir "$APP_HOME"

WORKDIR $APP_HOME
COPY Gemfile* $APP_HOME/
RUN bundle install
COPY . $APP_HOME

ENV POST_SERVICE_HOST post
ENV POST_SERVICE_PORT 5000
ENV COMMENT_SERVICE_HOST comment
ENV COMMENT_SERVICE_PORT 9292

CMD ["puma"]
