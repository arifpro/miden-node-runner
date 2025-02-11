# Use the Rust official image as the base
FROM rust:latest

# Install system dependencies for Clang, LLVM, SQLite3, pkg-config, and build tools
RUN apt-get update && apt-get install -y \
  clang \
  llvm \
  libsqlite3-dev \
  pkg-config \
  build-essential \
  && rm -rf /var/lib/apt/lists/*

# Set environment variables for Clang and SQLite3
ENV LIBCLANG_PATH=/usr/lib/llvm-14/lib
ENV LIBSQLITE3_SYS_BUNDLING=1
ENV PKG_CONFIG_PATH=/usr/lib/pkgconfig

# Set working directory
WORKDIR /app

# Copy the project files (including the config folder)
COPY . /app/

# List the contents of /app to verify the copy
RUN ls -l /app/

# Install Miden Node
RUN cargo install miden-node --locked

# Expose necessary ports
EXPOSE 57291 48046 28943

# Initialize and start the node
CMD sh -c "miden-node make-genesis --inputs-path config/genesis.toml --output-path storage/genesis.dat && cd storage && miden-node start --config config/miden-node.toml node"

# # Build the project
# RUN cargo build --release

# # Expose necessary ports
# EXPOSE 57291 48046 28943

# # Start the Miden node using the config files from your config folder
# CMD ["./target/release/miden-node", "start", "--config", "config/miden-node.toml", "node"]
