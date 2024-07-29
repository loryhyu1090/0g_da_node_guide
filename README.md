# 0g_da_node_guide


![0G-bg-2](https://github.com/user-attachments/assets/b7c95ef3-638e-487f-bb2f-98b872e9d5af)

# Hardware Requirement
```
- Memory: 16 GB
- CPU: 8 cores
- Disk: 1 TB NVME SSD
- Bandwidth: 100 MBps for Download / Upload
```

# Installation
```
git clone https://github.com/0glabs/0g-da-node.git
cargo build --release
./dev_support/download_params.sh
```

# Configuration
Create a config.toml file and set the following field to proper values:
```
log_level = "info"

data_path = "./db/"

# path to downloaded params folder
encoder_params_dir = "params/" 

# grpc server listen address
grpc_listen_address = "0.0.0.0:34000"
# chain eth rpc endpoint
eth_rpc_endpoint = "https://rpc-testnet.0g.ai"
# public grpc service socket address to register in DA contract
# ip:34000 (keep same port as the grpc listen address)
# or if you have dns, fill your dns
socket_address = "<public_ip/dns>:34000"

# data availability contract to interact with
da_entrance_address = ""
# deployed block number of da entrance contract
start_block_number = 0

# signer BLS private key
signer_bls_private_key = ""
# signer eth account private key
signer_eth_private_key = ""

# whether to enable data availability sampling
enable_das = "false"
```

**Create a BLS private key:**
```
cargo run --bin key-gen
```

# Run
```
./target/release/server --config cargo.toml
```
