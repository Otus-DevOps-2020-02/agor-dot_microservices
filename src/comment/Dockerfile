FROM alpine:3.7
ENV BUILD_PACKAGES curl-dev ruby-dev build-base
ENV RUBY_PACKAGES ruby ruby-io-console ruby-bundler
RUN apk add $BUILD_PACKAGES bash && \
    apk add $RUBY_PACKAGES && \
    rm -rf /var/cache/apk/*

ENV APP_HOME /app
RUN mkdir "$APP_HOME"
WORKDIR $APP_HOME

ADD Gemfile* $APP_HOME/
RUN bundle install
ADD . $APP_HOME

ENV COMMENT_DATABASE_HOST comment_db
ENV COMMENT_DATABASE comments

CMD ["puma"]
