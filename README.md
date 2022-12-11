# StrideNode
A simple guide

#!/bin/bash  
exists()  
{  
  command -v "$1" >/dev/null 2>&1  
}  
if exists curl; then  
echo ''  
else  
  sudo apt update && sudo apt install curl -y < "/dev/null"  
fi  
bash_profile=$HOME/.bash_profile  
if [ -f "$bash_profile" ]; then  
    . $HOME/.bash_profile  
fi  
sleep 1 && curl -s https://api.nodes.guru/logo.sh | bash && sleep 1  
  
  
if [ ! $STRIDE_NODENAME ]; then  
read -p "Enter node name: " STRIDE_NODENAME  
echo 'export STRIDE_NODENAME='\"${STRIDE_NODENAME}\" >> $HOME/.bash_profile  
fi  
echo 'source $HOME/.bashrc' >> $HOME/.bash_profile  
. $HOME/.bash_profile  
sleep 1  
cd $HOME  
sudo apt update  
sudo apt install make clang pkg-config libssl-dev build-essential git jq ncdu bsdmainutils htop -y < "/dev/null"  
  
echo -e '\n\e[42mInstall Go\e[0m\n' && sleep 1  
cd $HOME  
wget -O go1.18.4.linux-amd64.tar.gz https://golang.org/dl/go1.18.4.linux-amd64.tar.gz  
rm -rf /usr/local/go && tar -C /usr/local -xzf go1.18.4.linux-amd64.tar.gz && rm go1.18.4.linux-amd64.tar.gz  
echo 'export GOROOT=/usr/local/go' >> $HOME/.bash_profile  
echo 'export GOPATH=$HOME/go' >> $HOME/.bash_profile  
echo 'export GO111MODULE=on' >> $HOME/.bash_profile  
echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> $HOME/.bash_profile && . $HOME/.bash_profile  
go version  
  
echo -e '\n\e[42mInstall software\e[0m\n' && sleep 1 
rm -rf $HOME/stride   
git clone https://github.com/Stride-Labs/stride.git  
cd stride  
git checkout cf4e7f2d4ffe2002997428dbb1c530614b85df1b  
make build  
mv $HOME/stride/build/strided /usr/local/bin/  
sleep 1  
strided init "$STRIDE_NODENAME" --chain-id=STRIDE-TESTNET-4 --overwrite
PEER="29acbb3b3b9fa880944741c32617826cba44a624@78.47.214.203:26656,165f6cba877d71f0ad1c8ee6392beea35e04cb78@95.217.155.136:16656,390ff948ffbb9ad1793c3de91bf457750f3279b6@65.108.71.92:54356,aeabaf90afbe6321f2e8a33ddc5aebf2963f6efd@65.108.238.183:36656,328d459d21f82c759dda88b97ad56835c949d433@78.47.222.208:26639,ad4c545a806e151fe3cdd7e418b5544bc14a36d6@158.247.230.103:26656,d76de995b7c611e3edd651b828fd01f242015740@45.77.33.208:26656,23573e96a23292e97ce42a03260799f2a20415b6@88.198.39.43:26736,6c933f3ff3e529852e958f40c5d3c82296504e50@158.247.231.72:26656,3f1d13d7b9d499ca2c4647b844dab1d3a3f2a6ab@212.162.153.56:26656,dd93bd24192d8d3151264424e44b0f213d2334dc@162.55.173.64:26656,54a11c47658ebd5dcbd70eb3c62197b439482d3f@116.202.236.115:21016,d6e423fbd610dae4f0966cfed5b47165b4548582@45.91.168.197:26656,95ee745023b21aee6aa62c46352724b5f32240cd@161.97.91.70:16656,8deab2e38cd0a02bf2572340b6e082c59d856bae@2.59.156.145:26656,e4a2f835dc501cec2e87bac9b3365ff21bb87851@45.32.126.218:26656,8ff255af7f4d13429af028184a917093cddb92ff@185.216.75.46:16656,57fea82e70f8ffef72a3d09021796a52c43685d8@65.108.206.56:16656,abb29071e552fb1cd8ecae886c50ac3471a170c3@164.68.125.90:26656,01806f822366b27c4f63502eeec689abedb20438@38.242.128.46:16656,3b44079def8ad2dd8cbb14ce562957b5057b4e7b@65.108.204.115:26656,89fc167903c6f8afd519cbc8cc1542ac6467f911@135.181.133.248:11656,6cd4368f972c8e70f39f159804d2b0c89d603b7b@115.73.213.74:26656,c311f95b9c644c484671a096fc53297d4d5ae82e@86.48.2.178:26656,3983015b094e92c88b31250454c2093b39fe87c6@134.122.100.79:26656,866bb1cbc21bf1f1fd524717d536c1020bd26c45@49.12.237.93:26656,1a8a12acb9d68cfceef15826aa8183a755f038c1@159.65.81.42:26656,59e0c79c8c30ccd03e2f3d61d4f40b5f75223cd5@45.32.119.215:26656,375bf00a82d55f02ec6e44974a6848a4e8af8016@149.102.146.46:26656,45380044a09852b7fac0c6bc4da625128118fd04@45.77.241.50:26656,12090dadc2c6b1b90a4a2f77259f107a36c17242@65.108.249.29:16656,f0c7aaa7bcd159e4fe2775abc5968e3548af866d@34.135.153.30:16656,fcdda87767645df851c5405d9bb8601330a469c6@51.75.135.46:16656,d339b9a6df1b3f85f9da48134f59882456de1301@147.182.232.40:26656,e718e156dbc1b6644653debece7552de9a3f670f@185.220.205.98:16656,673cd2e8df973b8c10b1a460bd846e31b228373c@135.181.73.170:26757,9443ac82d9c5220e489e14be1335a871b9f6c552@178.62.122.192:26656,9988473a72d06d3eedec4eabafa677295015ce8e@65.108.137.92:26656,acc291258810e829db87a8babfa22cf82e217caa@141.147.7.113:26656,3aef99f334355ca0935855b72a5f8da23ded22a9@178.62.38.35:26656,8071611b00cacb8d6a71c1916b9045f70fc3b0ca@135.181.202.21:16656,8acff5bc80a9d286721d540047c53f7ad0d54f2b@95.216.153.211:16656,5387b1a0bef6fd279db6ab19ad64c4c117a45745@194.163.149.116:26656,1600b794c3727e5848efa593e16339789bad6320@116.203.41.7:16656,96cbb011ccd1573e0044a47b59b714ed03e5c4d5@65.21.147.17:16656,23b28771770bed1e9e30ba27d8d1d63d98549265@65.21.159.63:16656,d6d45352df7a280225ff4a7e1d43659090ee85ef@49.12.214.194:26656"  
SEED="d2ec8f968e7977311965c1dbef21647369327a29@seedv2.poolparty.stridenet.co:26656"  
sed -i.bak "s/^persistent_peers *=.*/persistent_peers = \"$PEER\"/;" $HOME/.stride/config/config.toml 
sed -i "s/^seeds *=.*/seeds = \"$SEED\"/;" $HOME/.stride/config/config.toml  
#PRUNING CONFIG  
sed -i "s/pruning *=.*/pruning = \"custom\"/g" $HOME/.stride/config/app.toml  
sed -i "s/pruning-keep-recent *=.*/pruning-keep-recent = \"100\"/g" $HOME/.stride/config/app.toml  
sed -i "s/pruning-interval *=.*/pruning-interval = \"10\"/g" $HOME/.stride/config/app.toml  
sed -i.bak -e "s/indexer *=.*/indexer = \"null\"/g" $HOME/.stride/config/config.toml  
wget -O $HOME/.stride/config/genesis.json https://raw.githubusercontent.com/Stride-Labs/testnet/main/poolparty/genesis.json  
strided tendermint unsafe-reset-all  
wget -O $HOME/.stride/config/addrbook.json https://api.nodes.guru/stride_addrbook.json  
echo -e '\n\e[42mRunning\e[0m\n' && sleep 1  
echo -e '\n\e[42mCreating a service\e[0m\n' && sleep 1  
  
echo "[Unit]  
Description=Strided Node  
After=network.target  
  
[Service]  
User=$USER  
Type=simple  
ExecStart=$(which strided) start  
Restart=on-failure  
LimitNOFILE=65535  
  
[Install]  
WantedBy=multi-user.target" > $HOME/strided.service  
sudo mv $HOME/strided.service /etc/systemd/system  
sudo tee <<EOF >/dev/null /etc/systemd/journald.conf  
Storage=persistent  
EOF  
echo -e '\n\e[42mRunning a service\e[0m\n' && sleep 1  
sudo systemctl restart systemd-journald  
sudo systemctl daemon-reload  
sudo systemctl enable strided  
sudo systemctl restart strided  
  
echo -e '\n\e[42mCheck node status\e[0m\n' && sleep 1  
if [[ `service strided status | grep active` =~ "running" ]]; then  
  echo -e "Your stride node \e[32minstalled and works\e[39m!"  
  echo -e "You can check node status by the command \e[7mservice strided status\e[0m"  
  echo -e "Press \e[7mQ\e[0m for exit from status menu"  
else  
  echo -e "Your stride node \e[31mwas not installed correctly\e[39m, please reinstall."  
fi  
