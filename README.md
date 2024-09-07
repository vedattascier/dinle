

### Fonksiyonun Eklenmesi

`dinle` fonksiyonunu `.zshrc` dosyanıza eklemek için şu komutu kullanabilirsiniz:

```bash
echo 'dinle() {
    if [ -z "$1" ]; then
        echo -n "Dinlemek istediğiniz portu girin: "
        read port
    else
        port=$1
    fi
    echo "nc -lvnp $port ile dinleniyor..."
    
    # CTRL+C sinyalini yakalayıp fonksiyonu sonlandırıyoruz
    trap "echo Dinleme durduruluyor...; exit 0" SIGINT
    
    while true; do
        nc -lvnp $port
        # Netcat oturumu kapandıktan sonra kısa bir bekleme süresi ekliyoruz
        sleep 1
    done
}' >> ~/.zshrc
```

### Güncellenmiş `README.md`

```markdown
# Dinle Fonksiyonu

Bu basit `dinle` fonksiyonu, belirttiğiniz bir portu `nc` (Netcat) ile dinler. Fonksiyon, port numarası verilmediğinde kullanıcıdan bir port numarası ister ve dinlemeye başlar. Dinleme kesildiğinde bile otomatik olarak devam eder.

## Kurulum

Fonksiyonu `.zshrc` dosyanıza eklemek için aşağıdaki adımları takip edebilirsiniz:

1. Terminali açın ve aşağıdaki komutu çalıştırın:

    ```bash
    echo 'dinle() {
        if [ -z "$1" ]; then
            echo -n "Dinlemek istediğiniz portu girin: "
            read port
        else
            port=$1
        fi
        echo "nc -lvnp $port ile dinleniyor..."
        
        # CTRL+C sinyalini yakalayıp fonksiyonu sonlandırıyoruz
        trap "echo Dinleme durduruluyor...; exit 0" SIGINT
        
        while true; do
            nc -lvnp $port
            # Netcat oturumu kapandıktan sonra kısa bir bekleme süresi ekliyoruz
            sleep 1
        done
    }' >> ~/.zshrc
    ```

2. Değişikliklerin etkili olması için terminalinizi yeniden başlatın veya `.zshrc` dosyasını yeniden yükleyin:

    ```bash
    source ~/.zshrc
    ```

## Kullanım

Fonksiyonu kullanarak belirli bir portu dinlemek için aşağıdaki komutları kullanabilirsiniz:

### Port Numarası Vermeden Kullanmak

Port numarası belirtmeden `dinle` komutunu yazdığınızda, sizden bir port numarası girmenizi ister:

```bash
dinle
```

Ekranda şu mesajı göreceksiniz:

```
Dinlemek istediğiniz portu girin:
```

### Port Numarasıyla Kullanmak

Port numarasını doğrudan belirterek dinlemek için:

```bash
dinle 8080
```

Bu komut, belirtilen portu Netcat ile dinler ve terminalde şu mesajı gösterir:

```
nc -lvnp 8080 ile dinleniyor...
```

## Özellikler

- Kullanıcıdan port numarası alır veya doğrudan argüman olarak verilen portu kullanır.
- Dinleme kesildiğinde otomatik olarak yeniden başlar (sürekli dinleme modu).
- `zsh` shell'i ile uyumludur.

## Gereksinimler

- **Netcat (nc)**: Dinleme işlemini gerçekleştirmek için sisteminizde netcat kurulu olmalıdır.

Netcat'i kurmak için:

- Ubuntu/Debian: `sudo apt install netcat`
- CentOS/Fedora: `sudo yum install nc`

## Lisans

Bu proje MIT Lisansı ile lisanslanmıştır. Daha fazla bilgi için `LICENSE` dosyasına bakın.
```

Bu README dosyası, kullanıcıların fonksiyonu `.zshrc` dosyasına nasıl ekleyeceklerini ve nasıl kullanacaklarını açıklar. Ayrıca, fonksiyonun `Ctrl+C` ile düzgün bir şekilde sonlanmasını sağlar.
