🖥️ 0G NODE (ONE CLICK COMMAND)

1. ALL INSTALLTION :

sudo apt-get update && sudo apt-get upgrade -y && sudo apt install curl iptables build-essential git wget lz4 jq make protobuf-compiler cmake gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev screen ufw -y && curl https://sh.rustup.rs -sSf | sh -s -- -y && source $HOME/.cargo/env && rustc --version && wget https://go.dev/dl/go1.24.3.linux-amd64.tar.gz && \
sudo rm -rf /usr/local/go && \
sudo tar -C /usr/local -xzf go1.24.3.linux-amd64.tar.gz &&  
rm go1.24.3.linux-amd64.tar.gz && \
echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc && \
source ~/.bashrc && go version && git clone https://github.com/0glabs/0g-storage-node.git && cd 0g-storage-node && git checkout v1.1.0 && git submodule update --init && cargo build --release && rm -rf $HOME/0g-storage-node/run/config.toml && curl -o $HOME/0g-storage-node/run/config.toml https://raw.githubusercontent.com/Naveenrawde3/0G-LABS-STORAGE-NODE-RUN-GUIDE-BY-NTEK/main/config.toml && nano $HOME/0g-storage-node/run/config.toml


🛠 2. SETUP A SYSTEM SERVICE
sudo tee /etc/systemd/system/zgs.service > /dev/null <<EOF
[Unit]
Description=ZGS Node
After=network.target

[Service]
User=$USER
WorkingDirectory=$HOME/0g-storage-node/run
ExecStart=$HOME/0g-storage-node/target/release/zgs_node --config $HOME/0g-storage-node/run/config.toml
Restart=on-failure
RestartSec=10
LimitNOFILE=65535

[Install]
WantedBy=multi-user.target
EOF


3. START SERVICE (PART 2)
sudo systemctl daemon-reload && sudo systemctl enable zgs && sudo systemctl start zgs

4. 🧪 SNAPSHORT COMMAND : 4.78M Block Snapshot 🫰 

sudo systemctl stop zgs

rm -rf $HOME/0g-storage-node/run/db/flow_db

wget https://github.com/Mayankgg01/0G-Storage-Node-Guide/releases/download/v1.0/flow_db.tar.xz \
  -O $HOME/0g-storage-node/run/db/flow_db.tar.xz && \
  tar -xJvf $HOME/0g-storage-node/run/db/flow_db.tar.xz -C $HOME/0g-storage-node/run/db/


sudo systemctl restart zgs

47
