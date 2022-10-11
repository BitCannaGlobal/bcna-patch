
## Please replace current v1.4.2 by v1.4.3
- No chain halt (consensus) required
- Apply it ASAP
- **Source code can't be disclosed by the moment**


## Instructions (bcnad & cosmovisor) 
```
rm  -rf ./bcna_linux_amd64.tar.gz  # delete old versions, check also bcnad in this folder
wget https://github.com/BitCannaGlobal/bcna-patch/releases/download/v1.4.3-patch/bcna_linux_amd64.tar.gz
tar zxvf bcna_linux_amd64.tar.gz
./bcnad version --long --output json |jq .commit 
   >>>>> output should be >>>> "94bfd1b95655df23ec5617b06aadf80f90917521"
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

## Sha256SUM
`05c896fc389f9c08c1beb8e55490bb5d171c8373b951ba54ccff4cbd484ff3ef bcna_linux_amd64.tar.gz`

Other versions, check the attached `release_checksum`
