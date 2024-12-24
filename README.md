# spheron-fizz-node-setup
Fizz Node kurulumu için basit bir rehber
# Spheron Fizz Node Kurulum Rehberi

Spheron Network'ün Fizz Node'unu kurdum ve test ettim. Sorunsuz bir şekilde puan kazanıyorum. Aşağıda, bu nodu nasıl kurabileceğinize dair rehber bulunmaktadır.

## Donanım Gereksinimleri
- **Sunucu:** 4 vCPU, 8 GB RAM

---

## Kurulum

1. [Fizz](https://fizz.spheron.network/) web sitesine giderek cüzdanınızı bağlayın.
2. Gerekli adımları tamamladıktan sonra node kurulum sayfasına geçin.
3. Lokasyonunuza yakın bir sağlayıcı seçin ve setup dosyasını indirin.

### Gerekli Komutlar
Aşağıdaki komutları sırasıyla sunucunuzda çalıştırın:

#### Docker ve Swap Kurulumu
```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io
sudo systemctl start docker
sudo systemctl enable docker
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo fallocate -l 4096M /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```

#### Setup Script Çalıştırma
```bash
chmod +x /root/fizzup.sh
screen -S fizz
bash /root/fizzup.sh
```

#### Log Kontrolü
```bash
docker compose -f ~/.spheron/fizz/docker-compose.yml logs -f
```

---

## Görseller
### Bağlantı Ekranı
![Bağlantı Ekranı](https://github.com/user-attachments/assets/717f26b1-4a10-475f-ba9b-f5e488127e06)

### Setup Ekranı
![Setup Ekranı](https://github.com/user-attachments/assets/c1bde16d-56c4-4da1-920a-113d6aba9a44)

---

## Notlar
- Eksik veya hatalı bir adım görürseniz geri bildirim bırakabilirsiniz.
- Rehber güncellenmeye devam edecektir.


