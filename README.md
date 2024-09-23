
# HEMI
![image](https://github.com/user-attachments/assets/c8b01d22-9fed-4fb5-beaa-5076a3e621e5)

### Discord : https://discord.gg/hemixyz

### Gereksinimler:
-------------------
### RAM : 2 GB
### Storage : 50 GB
### CPU : 2 Core

### Sunucumuzu güncelliyoruz
```
sudo apt update
sudo apt install git make
```
###  Kurulumuzu yapıyoruz
```
cd
git clone https://github.com/hemilabs/heminetwork.git
cd heminetwork
make deps
make install
```
### Cüzdan oluşturalım
```
cd bin
./keygen -secp256k1 -json -net="testnet" > ~/popm-address.json

```
### Aşağıdaki komutla cüzdan bilgilerimizi alalım
```
nano ~/popm-address.json
```
### Public hash bizim dc de faucetten token isteyeceğimiz adresimiz.Bu bilgileri mutlaka saklayın
### Faucetten tokenlerimizi aldıysak devam edelim
### Servis dosyası oluşturuyoruz. Private key yazan yer kendi priv keyinizi yazmayı unutmayın !!!
```
sudo tee /etc/systemd/system/popmd.service <<EOF
[Unit]
Description=Popmd Service
After=network.target

[Service]
Type=simple
User=root
WorkingDirectory=/root/heminetwork
ExecStart=/root/heminetwork/bin/popmd
Environment="POPM_BTC_PRIVKEY=private yaz"
Environment="POPM_STATIC_FEE=50"
Environment="POPM_BFG_URL=wss://testnet.rpc.hemi.network/v1/ws/public"
Restart=always

[Install]
WantedBy=multi-user.target
EOF
```
### Artık başlatıyoruz
```
sudo systemctl daemon-reload
sudo systemctl enable popmd
sudo systemctl start popmd
```
### Loglarımızı kontrol edelim
```
sudo journalctl -u popmd -fo cat
```
### Loglarınız bu şekilde görüyorsanız her şey yolunda demktir
![image](https://github.com/user-attachments/assets/556859a7-041b-4702-99d0-a04bff4a54de)
### Bu rehber kıymetli hocamız molla202 nin hazırladığı kodlar ile oluşturulmuştur. Kendisine  teşekkürler 🙏





