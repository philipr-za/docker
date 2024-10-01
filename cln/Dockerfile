FROM ubuntu:22.04
RUN apt-get update && apt-get install -y \
    build-essential \
    curl \
    wget \
    libssl-dev \
    zlib1g-dev \
    libbz2-dev \
    libreadline-dev \
    libsqlite3-dev \
    libffi-dev \
    libncurses5-dev \
    libncursesw5-dev \
    xz-utils \
    liblzma-dev \
    autoconf automake git libtool libgmp-dev net-tools zlib1g-dev libsodium-dev gettext libprotobuf-c-dev protobuf-compiler protobuf-compiler-grpc libgrpc++-dev pkg-config vim jq \
    valgrind libpq-dev cppcheck libsecp256k1-dev lowdown lnav sudo

# Python Stuff
RUN apt-get install -y python3 python3-venv python3-dev python3-pip python3-mako 
RUN python3 --version
RUN pip --version
RUN pip install --upgrade pip
RUN pip install wheel
RUN pip install --user poetry
RUN pip install --user mistune==0.8.4
RUN pip install --user mrkd==0.2.0
RUN pip install pytest
RUN pip install mako
RUN pip install grpcio-tools

# Rust stuff
RUN curl https://sh.rustup.rs -sSf | bash -s -- -y
ENV PATH="/root/.local/bin:/root/.cargo/bin:${PATH}"
RUN rustup default 1.74
RUN echo "[safe]\n	directory = *" > /root/.gitconfig

# Elements
RUN cd /tmp/
RUN wget https://github.com/ElementsProject/elements/releases/download/elements-23.2.1/elements-23.2.1-x86_64-linux-gnu.tar.gz
RUN tar -xf elements-23.2.1-x86_64-linux-gnu.tar.gz
RUN mv "elements-23.2.1"/bin/* "/usr/local/bin"
RUN rm -rf elements-23.2.1-x86_64-linux-gnu.tar.gz elements-23.2.1

# Bitcoin
RUN wget https://bitcoincore.org/bin/bitcoin-core-27.1/bitcoin-27.1-x86_64-linux-gnu.tar.gz
RUN tar -xf bitcoin-27.1-x86_64-linux-gnu.tar.gz
RUN mv "bitcoin-27.1"/bin/* "/usr/local/bin"
RUN rm -rf bitcoin-27.1-x86_64-linux-gnu.tar.gz bitcoin-27.1

# Including Custom built CLN stuff 
COPY ./lightning-cli /usr/local/bin/
COPY ./lightningd /usr/local/bin/
COPY ./lightning-hsmtool /usr/local/bin/
COPY ./c-lightning /usr/local/libexec/c-lightning

WORKDIR /root/
