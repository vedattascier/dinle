
Elbette! İşte GitHub için `README.md` dosyanızın taslağı:

```markdown
# Dinle Fonksiyonu

Bu proje, belirli bir portu dinlemek için Netcat (nc) kullanmanıza olanak tanıyan basit bir bash fonksiyonunu içerir. Fonksiyon, port numarası belirtmeden çalıştırıldığında kullanıcıdan bir port numarası girmesini ister ve belirli bir portu sürekli olarak dinler. Bağlantı kesildiğinde bile dinleme otomatik olarak devam eder.

## Kurulum

Fonksiyonu kullanabilmek için `.bashrc` veya `.zshrc` dosyanıza aşağıdaki kodu ekleyin:

```bash
dinle() {
    if [ -z "$1" ]; then
        echo "Lütfen bir port numarası girin!"
        echo -n "Dinlemek istediğiniz portu girin: "
        read port
    else
        port=$1
    fi
    echo "nc -lvnp $port ile dinleniyor..."
    while true; do
        nc -lvnp $port
    done
}
```

Daha sonra terminalinizi yeniden başlatın veya aşağıdaki komutlardan birini çalıştırın:

- Bash: `source ~/.bashrc`
- Zsh: `source ~/.zshrc`

## Kullanım

### Port numarası vermeden kullanmak

Sadece `dinle` komutunu yazarak, port numarasını girmeniz istenir:

```bash
dinle
```

### Port numarasıyla kullanmak

Belirli bir port numarasını argüman olarak vererek dinleyebilirsiniz. Örneğin, 8080 portunu dinlemek için:

```bash
dinle 8080
```

## Özellikler

- Kullanıcıdan port numarası alır veya doğrudan verilen portu kullanır.
- Dinleme kesildiğinde otomatik olarak yeniden başlar.
- Hem Bash hem de Zsh ile uyumludur.

## Gereksinimler

Netcat (nc) kurulu olmalıdır. Netcat'i kurmak için:

- Ubuntu/Debian: `sudo apt install netcat`
- CentOS/Fedora: `sudo yum install nc`

## Lisans

Bu proje MIT Lisansı ile lisanslanmıştır. Daha fazla bilgi için [LICENSE](LICENSE) dosyasına bakabilirsiniz.

## Katkıda Bulunanlar

- [Vedat Taşçıer](https://github.com/vedattascier)

## İletişim

Herhangi bir sorun, öneri veya katkı için [Vedat Taşçıer](https://github.com/vedattascier) ile iletişime geçebilirsiniz.
```

Bu `README.md` dosyası, fonksiyonun kurulumu, kullanımı, gereksinimler ve lisans bilgilerini kapsar. GitHub projelerinde standart olarak bulunan bölümlerle uyumludur. Kendi GitHub profilinizi ve iletişim bilgilerinizi eklemeyi unutmayın!
