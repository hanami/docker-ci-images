FROM ruby:2.3

RUN apt-get update -y
RUN apt-get install -y locales

# Set timezone to UTC by default
RUN ln -sf /usr/share/zoneinfo/Etc/UTC /etc/localtime

# Use unicode
RUN locale-gen C.UTF-8 || true
ENV LANG=C.UTF-8

RUN apt-get install -y build-essential nodejs default-jre
