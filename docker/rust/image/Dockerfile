ARG RUST_VERSION=1.63.0
# https://hub.docker.com/_/rust
FROM rust:${RUST_VERSION}-slim-bullseye

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    # Development tools.
    git sudo \
    # Install required packages for `cargo-edit`.
    libssl-dev pkg-config \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN rustup component add rls rust-analysis rust-src rustfmt clippy \
    && cargo install cargo-edit cargo-watch

ARG RUST_UID=1000
ARG RUST_GID=1000
ARG RUST_USERNAME=rust_template_user
ARG RUST_GROUPNAME=rust_template_user
ARG RUST_PASSWORD=rust_template_user

# Add user and group.
RUN groupadd -g ${RUST_GID} ${RUST_GROUPNAME} \
    && useradd -m -s /bin/bash -u ${RUST_UID} -g ${RUST_GID} ${RUST_USERNAME} \
    && echo "${RUST_USERNAME}:${RUST_PASSWORD}" | chpasswd \
    && echo "${RUST_USERNAME}   ALL=(ALL:ALL) ALL" > "/etc/sudoers.d/${RUST_GROUPNAME}" \
    && chmod 0440 "/etc/sudoers.d/${RUST_GROUPNAME}"
USER ${RUST_UID}:${RUST_GID}
