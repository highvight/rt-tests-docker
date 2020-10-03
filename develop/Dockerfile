FROM ubuntu:latest

RUN apt-get update && \
    apt-get install --no-install-recommends build-essential libnuma-dev git -y && \
    git clone -b stable/v1.0 git://git.kernel.org/pub/scm/utils/rt-tests/rt-tests.git && \
    cd rt-tests && \
    make all && \
    make install

RUN mkdir /rt-tests/out && \
    touch /rt-tests/out/latencies.txt

WORKDIR "/rt-tests"

ENTRYPOINT ["cyclictest", "--duration=1m", "--histofall=10000", "--histfile=out/latencies.txt"]
CMD ["--help"]

