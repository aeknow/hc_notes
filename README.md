# Debian12下安装运行 Aeternity Hyperchains 测试网节点
Ubuntu 22.04之后的操作应该类似。

目前看起来已经能将超链挂载到AE的POW主网正常运行；感谢AE社区的支持鞭策，特别是"௸故事༊ོོོ࿆如酒の࿆೨"大佬的支持。

如有问题，请加微信：aeknow 交流

## 一、极简测试模式
### 1.安装节点运行环境，需要openssl 1.x版本支持：
```shell
sudo apt -y install git autoconf build-essential cmake erlang libsodium-dev libgmp-dev
wget https://www.openssl.org/source/openssl-1.1.1o.tar.gz
tar zxf openssl-1.1.1o.tar.gz
cd openssl-1.1.1o
./config
make
sudo make install
```
### 2.直接可用的配置文件
- [aeternity.yaml](./aeternity.yaml)
- [hc_liu_accounts.json](./hc_liu_accounts.json)
- [hc_liu_contracts.json](./hc_liu_contracts.json)

### 3.下载并解压缩节点文件
下载当前最新版本：https://github.com/aeternity/aeternity/releases/download/v7.3.0-rc6/aeternity-bundle-v7.3.0-rc6-ubuntu-x86_64.tar.gz

```shell
tar zxf aeternity-bundle-v7.3.0-rc6-ubuntu-x86_64.tar.gz
```

### 4.复制配置文件到对应目录
将aeternity.yaml放在launch同一目录，将hc_liu_accounts.json以及hc_liu_contracts.json复制到./data/aecore这个目录；即可运行：
```shell
bin/aeternity console
```

### 5.检查超链运行状态
浏览器打开：http://127.0.0.1:3013/v3/status
即可查看当前节点运行状态，类似：
```json
{
  "difficulty": 0,
  "genesis_key_block_hash": "kh_v6jnz9ka1hEWTgFxbgXYDPm2CDzMtk5GVVpBTWs8ykt4BGKZP",
  "hashrate": 0,
  "listening": true,
  "network_id": "hc_liu",
  "node_revision": "39c4b40491332ffe3ca8358377a2b68e6ecc0424",
  "node_version": "7.3.0-rc6",
  "peer_connections": {
    "inbound": 0,
    "outbound": 0
  },
  "peer_count": 0,
  "peer_pubkey": "pp_2pevEb9NeLdxqsMncojLHKCnQFhKMxB4GUBKeRVKTXH7P4tLbQ",
  "pending_transactions_count": 0,
  "protocols": [
    {
      "effective_at_height": 0,
      "version": 6
    }
  ],
  "solutions": 0,
  "sync_progress": 100,
  "syncing": false,
  "top_block_height": 474,
  "top_key_block_hash": "kh_hF5wiHFdA5njiyo2QidcbBz8KmTBjT2Sks9kPYfYKnsg7Q4Qo",
  "uptime": "23m:48s.108"
}
```

运行一段时间后（>30分钟），超链就会提交pin tx到父链上去；如：https://testnet.aescan.io/transactions/th_2HAatj4b7Mr7PKJcVX7AqM9dAKFcFKcjJF7HL6rdqHvV9N6oPi

### 6.相关辅助工具
- 超链新手工具：https://github.com/aeternity/hyperchain-starter-kit
- sdk：https://github.com/aeternity/aepp-sdk-js

## 二、生产部署 
部署到ae pow主网需要理解具体的各种参数设置，回头单独整理成文。
