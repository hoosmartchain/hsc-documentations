# Install

## Install dependencies (Ubuntu 20.04.2 LTS)
Make 

    sudo apt install build-essential

Go-lang [official guidence](https://golang.org/doc/install)

    wget https://golang.org/dl/go1.16.3.linux-amd64.tar.gz
    sudo tar -C /usr/local -xzf go1.16.3.linux-amd64.tar.gz
    export PATH=$PATH:/usr/local/go/bin
    go version

## Clone HSC source code
git clone https://github.com/hoosmartchain/hoo-smartchain.git

## Make
```
cd /path/to/hoo-smartchain
make geth
ls ./build/bin
sudo cp ./build/bin/geth /usr/local/bin/

```

## Check version
```
geth version
```
<!-- 
## 网络接入
程序启动默认接入`mainnet`，如需接入公共测试网，可添加`option` `--testnet`。 -->
