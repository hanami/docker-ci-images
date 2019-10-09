FROM ruby:2.6

RUN apt-get update -y
RUN apt-get install -y locales

# Set timezone to UTC by default
RUN ln -sf /usr/share/zoneinfo/Etc/UTC /etc/localtime

# Use unicode
RUN locale-gen C.UTF-8 || true
ENV LANG=C.UTF-8

RUN apt-get install -y build-essential sqlite3 wget chrpath libssl-dev libxft-dev libfreetype6 libfreetype6-dev libfontconfig1 libfontconfig1-dev

ENV PHANTOM_JS="phantomjs-2.1.1-linux-x86_64"
ENV OPENSSL_CONF=/etc/ssl/
RUN wget https://github.com/hanami/hanami/raw/master/vendor/$PHANTOM_JS.tar.bz2 \
    && tar -xvjf $PHANTOM_JS.tar.bz2 \
    && mv $PHANTOM_JS /usr/local/share \
    && ln -sf /usr/local/share/$PHANTOM_JS/bin/phantomjs /usr/local/bin \
    && phantomjs --version
