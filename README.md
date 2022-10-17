
## Please replace current `v1.4.2` or `v1.4.3-patch` by `v1.4.3`
- No chain halt (consensus) required
- Apply it ASAP

> Stop your current daemon (bcnad or Cosmovisor) 
```
sudo service bcnad stop || sudo service cosmovisor stop
```

> Make a copy of the bd files:
```
copy -R $HOME/.bcna/data $HOME/.bcna/data_update
``` 

> Another important step to make: add this text to `.bcna/config/app.toml`
```
# IAVLDisableFastNode enables or disables the fast node feature of IAVL. 
# Default is true.
iavl-disable-fastnode = false
```

# Instructions for compile the source
```
git clone https://github.com/BitCannaGlobal/bcna-patch.git
cd bcna-patch
git checkout 1.4.3-2-g9f1b06d
make build
build/bcna version 
 >> should be `1.4.3-2-g9f1b06d` 

### For Cosmovisor:
```
cp ~/.bcna/cosmovisor/current/bin/bcnad ~/.bcna/cosmovisor/current/bin/bcna_downgrade #for fast downgrade 
mv build/bcnad  ~/.bcna/cosmovisor/current/bin/
sudo service cosmovisor restart
sudo journalctl -fu cosmovisor #check the logs
```

### For BCNAD daemon:
```
sudo cp $(which bcnad) ~/bcna_downgrade #for fast downgrade
sudo mv build/bcnad $(which bcnad)
sudo service bcnad restart
sudo journalctl -fu bcnad #check the logs
```


# Instructions for download (bcnad & cosmovisor) 

```
wget https://github.com/BitCannaGlobal/bcna-patch/releases/download/v1.4.3/bcna_linux_amd64.tar.gz
rm  -rf ./bcna_linux_amd64.tar.gz  # delete old versions, check also bcnad in this folder
tar zxvf bcna_linux_amd64.tar.gz
./bcnad version
 >> result should be `1.4.3`
```
### For Cosmovisor:
```
cp ~/.bcna/cosmovisor/current/bin/bcnad ~/.bcna/cosmovisor/current/bin/bcna_downgrade #for fast downgrade 
mv ./bcnad  ~/.bcna/cosmovisor/current/bin/
sudo service cosmovisor restart
sudo journalctl -fu cosmovisor #check the logs
```

### For BCNAD daemon:
```
sudo cp $(which bcnad) ~/bcna_downgrade #for fast downgrade
sudo mv ./bcnad $(which bcnad)
sudo service bcnad restart
sudo journalctl -fu bcnad #check the logs
```

