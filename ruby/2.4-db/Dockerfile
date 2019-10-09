FROM ruby:2.4

RUN apt-get update -y
RUN apt-get install -y locales

# Set timezone to UTC by default
RUN ln -sf /usr/share/zoneinfo/Etc/UTC /etc/localtime

# Use unicode
RUN locale-gen C.UTF-8 || true
ENV LANG=C.UTF-8

RUN apt-get install -y build-essential sqlite3 default-mysql-client

RUN wget -q https://www.postgresql.org/media/keys/ACCC4CF8.asc -O - | APT_KEY_DONT_WARN_ON_DANGEROUS_USAGE=1 apt-key add -
RUN sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ stretch-pgdg main" >> /etc/apt/sources.list.d/pgdg.list'
RUN apt-get update -y
RUN apt install -y postgresql-client
