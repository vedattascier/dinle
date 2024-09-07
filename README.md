Port Dinleme Scripti
Bu README, dinle isimli bir fonksiyonun nasıl kurulacağı ve kullanılacağı hakkında bilgi vermektedir. Bu fonksiyon, belirli bir portu dinlemek için nc (Netcat) komutunu kullanır ve port üzerinde gelen bağlantıları sürekli olarak dinler.

Kurulum
Bash ve Zsh Shell'leri için Fonksiyon Ekleyin:

dinle fonksiyonunu hem ~/.bashrc hem de ~/.zshrc dosyalarınıza eklemeniz gerekiyor. Bu, bash ve zsh shell'lerinde fonksiyonu kullanabilmenizi sağlar.

Aşağıdaki komutları çalıştırarak fonksiyonu her iki dosyaya da ekleyebilirsiniz:

bash
Kodu kopyala
echo 'dinle() { if [ -z "$1" ]; then echo -n "Dinlemek istediğiniz portu girin: "; read port; else port=$1; fi; echo "nc -lvnp $port ile dinleniyor..."; while true; do nc -lvnp $port; done; }' >> ~/.zshrc
echo 'dinle() { if [ -z "$1" ]; then echo -n "Dinlemek istediğiniz portu girin: "; read port; else port=$1; fi; echo "nc -lvnp $port ile dinleniyor..."; while true; do nc -lvnp $port; done; }' >> ~/.bashrc
Shell Yeniden Başlatma veya Yükleme:

Değişikliklerin etkili olabilmesi için shell oturumunuzu kapatıp açmanız veya aşağıdaki komutlarla konfigürasyon dosyalarını yeniden yüklemeniz gerekmektedir:

bash
Kodu kopyala
source ~/.bashrc
source ~/.zshrc
Kullanım
Fonksiyonu kullanmak için terminalde dinle komutunu çağırabilirsiniz. İki kullanım şekli vardır:

Port Numarası Sağlayarak:

Belirli bir portu dinlemek için port numarasını doğrudan belirtebilirsiniz:

bash
Kodu kopyala
dinle 1234
Bu komut, 1234 numaralı portu dinlemeye başlar.

Port Numarası Girmeden:

Port numarası belirtmezseniz, fonksiyon sizden bir port numarası girmenizi isteyecektir:

bash
Kodu kopyala
dinle
Komut çalıştıktan sonra port numarasını girmeniz istenecek ve girilen port numarası dinlenmeye başlanacaktır.

Gereksinimler
Netcat (nc) komutunun sistemde yüklü olması gerekir. Çoğu Linux dağıtımında bu paket önceden yüklenmiştir. Yüklemek için aşağıdaki komutu kullanabilirsiniz:

bash
Kodu kopyala
sudo apt-get install netcat
Lisans
Bu proje MIT Lisansı altında lisanslanmıştır. Daha fazla bilgi için Lisans Dosyasına göz atabilirsiniz.
