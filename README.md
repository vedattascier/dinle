# Port Dinleme Scripti

Bu proje, `dinle` isimli bir fonksiyon sağlar. Bu fonksiyon, belirli bir portu dinlemek için `nc` (Netcat) komutunu kullanır ve port üzerindeki gelen bağlantıları sürekli olarak dinler.

## Kurulum

### Bash ve Zsh Shell'leri İçin Fonksiyon Ekleyin

Aşağıdaki komutları terminalinize girerek `dinle` fonksiyonunu bash ve zsh shell'lerine ekleyebilirsiniz:

```bash
echo 'dinle() { if [ -z "$1" ]; then echo -n "Dinlemek istediğiniz portu girin: "; read port; else port=$1; fi; echo "nc -lvnp $port ile dinleniyor... (Ctrl+C ile durdurabilirsiniz)"; nc -lvnp $port; echo "Dinleme durduruldu."; }' >> ~/.bashrc

```

 ```bash
echo 'dinle() { if [ -z "$1" ]; then echo -n "Dinlemek istediğiniz portu girin: "; read port; else port=$1; fi; echo "nc -lvnp $port ile dinleniyor... (Ctrl+C ile durdurabilirsiniz)"; nc -lvnp $port; echo "Dinleme durduruldu."; }' >> ~/.zshrc
```

### Shell Yeniden Başlatma veya Yükleme

Değişikliklerin etkili olabilmesi için shell oturumunuzu kapatıp açmanız veya konfigürasyon dosyalarını yeniden yüklemeniz gerekmektedir. Aşağıdaki komutları kullanarak bu işlemi gerçekleştirebilirsiniz:

```bash
source ~/.bashrc
```
```bash
source ~/.zshrc
```

## Kullanım

Fonksiyonu kullanmak için terminalde `dinle` komutunu çağırabilirsiniz. İki kullanım şekli vardır:

1. **Port Numarası Sağlayarak:**

   Belirli bir portu dinlemek için port numarasını doğrudan belirtebilirsiniz:

   ```bash
   dinle 2121
   ```

   Bu komut, 2121 numaralı portu dinlemeye başlar.

2. **Port Numarası Girmeden:**

   Port numarası belirtmezseniz, fonksiyon sizden bir port numarası girmenizi isteyecektir:

   ```bash
   dinle
   ```

   Komut çalıştıktan sonra port numarasını girmeniz istenecek ve girilen port numarası dinlenmeye başlanacaktır.

## Gereksinimler

- Netcat (`nc`) komutunun sistemde yüklü olması gerekir. Çoğu Linux dağıtımında bu paket önceden yüklenmiştir. Yüklemek için aşağıdaki komutu kullanabilirsiniz:

   ```bash
   sudo apt-get install netcat
   ```

## Lisans

Bu proje MIT Lisansı altında lisanslanmıştır. Daha fazla bilgi için [Lisans Dosyasına](LICENSE) göz atabilirsiniz.

