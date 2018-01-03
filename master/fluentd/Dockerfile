FROM fluent/fluentd:v0.14-onbuild

RUN gem install fluent-plugin-route                      \
                --no-rdoc                                \
                --no-ri                                  \
                --version 1.0.0

RUN apk add --update --virtual .build-deps               \
        sudo build-base ruby-dev                      && \
    sudo gem install                                     \
         fluent-plugin-elasticsearch                  && \
    sudo gem sources --clear-all                         \
    apk del .build-deps                               && \
    rm -rf /var/cache/apk/*                              \
           /home/fluent/.gem/ruby/2.3.0/cache/*.gem
