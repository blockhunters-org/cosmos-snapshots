# Sync Source Testnet using snapshot 


### Stop Source service

`systemctl stop source.service`  

Remove old data in directory `~/.source/data`

```
rm -rf ~/.source/data; \
mkdir -p ~/.source/data; \
cd ~/.source/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s http://snap.source.bh.rocks/  | egrep -o ">source.*tar" | tr -d ">"); \
wget -O - http://snap.source.bh.rocks/${SNAP_NAME} | tar xf -
```
![alt text](https://github.com/blockhunters-org/cosmos-snapshots/blob/main/2021-01-20_14-19.png?raw=true)

Start service and check logs  
```
systemctl start source.service; \
journalctl -u source.service -f --no-hostname
```
