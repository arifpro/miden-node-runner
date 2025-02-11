# Use the Rust official image as the base
FROM rust:latest

# Set working directory
WORKDIR /app

# Install Miden Node
RUN cargo install miden-node --locked

# Copy configuration files
COPY config config
COPY storage storage

# Expose necessary ports
EXPOSE 57291 48046 28943

# Initializing the node
CMD miden-node make-genesis --inputs-path config/genesis.toml --output-path storage/genesis.dat

# Start the node
CMD miden-node start --config config/miden-node.toml node
