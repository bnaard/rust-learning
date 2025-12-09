FROM texlive/texlive:latest

# installing utils 
RUN apt-get update && \
    apt-get -y install --no-install-recommends \
    git \
    inkscape \
    tree \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# install Rust and some useful components
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
ENV PATH="/root/.cargo/bin:${PATH}"
RUN rustup component add rustfmt clippy
