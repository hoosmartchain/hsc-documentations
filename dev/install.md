# 快速安装

## 安装依赖 (以 Ubuntu 20.04.2 LTS 为例)
Make 

    sudo apt install build-essential

Go-lang [official guidence](https://golang.org/doc/install)

    wget https://golang.org/dl/go1.16.3.linux-amd64.tar.gz
    sudo tar -C /usr/local -xzf go1.16.3.linux-amd64.tar.gz
    export PATH=$PATH:/usr/local/go/bin
    go version

## 获取HSC源码
git clone https://github.com/hoosmartchain/hoo-smartchain.git

## 编译
```
cd /path/to/hoo-smartchain
make geth
ls ./build/bin
sudo cp ./build/bin/geth /usr/local/bin/

```

## 检查
```
geth version
```
<!-- 
## 网络接入
程序启动默认接入`mainnet`，如需接入公共测试网，可添加`option` `--testnet`。 -->
