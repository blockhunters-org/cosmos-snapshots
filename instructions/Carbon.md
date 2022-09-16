# Sync Source Testnet using snapshot 


### Stop Source service

`systemctl stop carbon.service`  

Remove old data in directory `~/.carbon/data`

```
rm -rf ~/.carbon/data; \
mkdir -p ~/.carbon/data; \
cd ~/.carbon/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://dl.carbon.bh.rocks/  | egrep -o ">carbon.*tar" | tr -d ">"); \
wget -O - https://dl.carbon.bh.rocks/${SNAP_NAME} | tar xf -
```
![alt text](https://github.com/blockhunters-org/cosmos-snapshots/blob/main/2021-01-20_14-19.png?raw=true)

Start service and check logs  
```
systemctl start carbon.service; \
tail -f /var/log/carbon/*.log
```
