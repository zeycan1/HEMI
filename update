```
systemctl stop popmd
cd
mv heminetwork heminetworkydk
wget https://github.com/hemilabs/heminetwork/releases/download/v0.4.3/heminetwork_v0.4.3_linux_amd64.tar.gz
tar -xzvf heminetwork_v0.4.3_linux_amd64.tar.gz
mv heminetwork_v0.4.3_linux_amd64 heminetwork
chmod +x /root/heminetwork/bfgd
chmod +x /root/heminetwork/bssd
chmod +x /root/heminetwork/btctool
chmod +x /root/heminetwork/extool
chmod +x /root/heminetwork/hemictl
chmod +x /root/heminetwork/keygen
chmod +x /root/heminetwork/popmd
chmod +x /root/heminetwork/tbcd
```
```
sudo tee /etc/systemd/system/popmd.service <<EOF
[Unit]
Description=Popmd Service
After=network.target

[Service]
Type=simple
User=root
WorkingDirectory=/root/heminetwork
ExecStart=/root/heminetwork/popmd
Environment="POPM_BTC_PRIVKEY=private yaz"
Environment="POPM_STATIC_FEE=50"
Environment="POPM_BFG_URL=wss://testnet.rpc.hemi.network/v1/ws/public"
Restart=always

[Install]
WantedBy=multi-user.target
EOF
```
```
systemctl daemon-reload && systemctl restart popmd && journalctl -u popmd -fo cat
```
