# Running the Miden node locally

### Setup

1. **Install Miden node:**
  
```sh
cargo install miden-node --locked 
```

2. **In the root of the miden-tutorials directory, run the following:**

```sh
miden-node make-genesis \
  --inputs-path  node/config/genesis.toml \
  --output-path node/storage/genesis.dat

cd node/storage
miden-node start \
--config node/config/miden-node.toml \
node
```

### Reset

Use the following command to reset the Miden node:

```sh
rm -rf rust-client/store.sqlite3 
rm -rf node/storage/accounts
rm -rf node/storage/blocks
```

### 🚀 How to Deploy

Build & Run with Docker

```sh
docker build -t miden-node .
docker run -d --name miden-node -p 57291:57291 -p 48046:48046 -p 28943:28943 miden-node
```

OR Use Docker Compose

```sh
docker compose up -d
# or
DOCKER_BUILDKIT=0 docker compose up -d
```

### ✅ Verify the Node is Running

```sh
curl http://localhost:57291
```
