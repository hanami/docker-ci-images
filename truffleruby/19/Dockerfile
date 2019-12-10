# Thanks to @chrisseaton https://github.com/oracle/truffleruby/issues/1449#issuecomment-550331141
FROM ubuntu:18.04
RUN apt-get update
RUN apt-get install -y locales
RUN locale-gen en_US.UTF-8
ENV LANG=en_US.UTF-8
RUN apt-get install -y curl
RUN apt-get install -y libz-dev
RUN apt-get install -y libssl-dev
RUN apt-get install -y make
WORKDIR /test
RUN useradd -ms /bin/bash test
RUN chown test /test
USER test
RUN curl -OL https://github.com/graalvm/graalvm-ce-builds/releases/download/vm-19.3.0/graalvm-ce-java11-linux-amd64-19.3.0.tar.gz
RUN mkdir /test/graalvm
RUN tar -zxf graalvm-ce-java11-linux-amd64-19.3.0.tar.gz -C /test/graalvm --strip-components=1
RUN /test/graalvm/bin/gu install org.graalvm.ruby | tee install.log
# RUN grep 'The Ruby openssl C extension needs to be recompiled on your system to work with the installed libssl' install.log
# RUN grep '/jre/languages/ruby/lib/truffle/post_install_hook.sh' install.log
# RUN /test/graalvm/jre/languages/ruby/lib/truffle/post_install_hook.sh
ENV PATH=/test/graalvm/bin:$PATH
RUN ruby --version
RUN ruby --jvm --version
RUN ruby --native --version
CMD bash
