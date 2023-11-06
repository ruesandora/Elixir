# Elixir

# Neden kuruyorum?

> Maliyet harcamıyorum, hali hazırda olan sunucularıma yerleştirdim node'u

> Donanım oldukça düşük

> Ödül açıklaması yok ama bekliyorum şahsen.

> Son olarak metriklerdeki validatör sayılarının gerçek olmadığından eminim.

#

> Önemli linkler: [Duyuru](https://t.me/RuesAnnouncement) - [Sohbet](https://t.me/RuesChat) -  [WP Kanalı](https://whatsapp.com/channel/0029VaBcj7V1dAw1H2KhMk34) - [Discord](https://discord.gg/elixirprotocol)


# Donanım
```
1 vCPU  - 2 RAM - 30 GB SSD, Ubuntu
```

# Kurulum

```console
# cihaz güncelleme
sudo apt update -y && sudo apt upgrade -y

# docker kurulumu
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done


sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Tek komut
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo docker run hello-world
```

```console
# Dockerfile indirelim:
wget https://files.elixir.finance/Dockerfile
# Bu aşamada HİÇ kullanılmamış ve kullanmayacağımız bir metamask account oluşturalım.

# içersine girelim
nano Dockerfile
# İçersinde ki Validatör ismi, private key ve cüzdan adresi güncelleyelim.

# Tilkimask Private key alma: Sağdan üç nokta => Hesap bilgileri => Özel anahtarı al
# Bilgilerimizi doldurduktan sonra sunucumuzda CTRL X Y ENTER ile kaydedebiliriz.
```

# Node başlatma

```console
# image oluşturalım:
docker build . -f Dockerfile -t elixir-validator

# Node calıştırma:
screen -S elixir
docker run -it --name ev elixir-validator
```

# Validator

> Son olarak [Buradan](https://dashboard.elixir.finance/) cüzdanınızı bağlayın ve 1000 elixir token claim edin.

> Sonra min. 100 token olmak uzere stake edin bır kısmını ve son olarak Enroll diyerek validatör başlatıyoruz.

> Aşağıda twitter ve discord bağlayarak rolünüzüde almayı unutmayın.

> Ledearboardda cüzdan aratarak node'unuzu görebilirsiniz fakat şu an pek çalıştığı söylenemez.

> Aynı zamanda metrics kısmıda çalışmıyor düzeltirler yakında takip ederiz.

<img width="1105" alt="Ekran Resmi 2023-11-06 15 09 36" src="https://github.com/ruesandora/Elixir/assets/101149671/e7326b21-b19c-460a-b405-8b04156b2831">












