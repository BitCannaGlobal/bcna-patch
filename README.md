
## Please replace current v1.4.2 or v1.4.3-patch by v1.4.3
- No chain halt (consensus) required
- Apply it ASAP


## Instructions (bcnad & cosmovisor) 
:eyes: Download the binary to your local computer and upload to your validator server.

```
wget https://github.com/BitCannaGlobal/bcna-patch/releases/download/v1.4.3/bcna_linux_amd64.tar.gz
rm  -rf ./bcna_linux_amd64.tar.gz  # delete old versions, check also bcnad in this folder
tar zxvf bcna_linux_amd64.tar.gz
./bcnad version
 >> result should be `v1.4.3`
```
### For Cosmovisor:
```
mv ./bcnad  ~/.bcna/cosmovisor/current/bin/
sudo service cosmovisor restart
sudo journalctl -fu cosmovisor #check the logs
```

### For BCNAD daemon:
```
sudo mv ./bcnad $(which bcnad)
sudo service bcnad restart
sudo journalctl -fu bcnad #check the logs
```

