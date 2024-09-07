
---

# Dinle Fonksiyonu

Bu basit `dinle` fonksiyonu, belirttiğiniz bir portu `nc` (Netcat) ile dinler. Fonksiyon, eğer port numarası verilmemişse, kullanıcıdan bir port numarası istemekte ve dinlemeye başlamaktadır. Bağlantı kesildiğinde bile dinleme otomatik olarak devam eder.

## Kullanım

### Fonksiyonun Tanımlanması

Fonksiyonu kullanabilmek için `.bashrc` veya `.zshrc` dosyanıza aşağıdaki satırı ekleyin:

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

Bu satırı ekledikten sonra terminali yeniden başlatın veya aşağıdaki komutları çalıştırın:
- **Bash**: `source ~/.bashrc`
- **Zsh**: `source ~/.zshrc`

### Komutların Kullanımı

#### 1. Port numarası vermeden kullanmak:
Eğer port numarası belirtmeden sadece `dinle` komutunu yazarsanız, sizden bir port numarası girmenizi ister.

```bash
dinle
```

Kullanıcıya şu mesaj gösterilir:
```bash
Lütfen bir port numarası girin!
Dinlemek istediğiniz portu girin: 
```

#### 2. Port numarasıyla kullanmak:
Port numarasını komutla beraber belirtebilirsiniz. Örneğin, 8080 portunu dinlemek için:

```bash
dinle 8080
```

Bu komut, Netcat ile belirtilen portu dinler:
```bash
nc -lvnp 8080 ile dinleniyor...
```

### Özellikler
- Kullanıcıdan port numarası alır veya doğrudan argüman olarak verilen portu kullanır.
- Dinleme kesildiğinde otomatik olarak yeniden başlar (sürekli dinleme modu).
- Hem Bash hem de Zsh ile uyumludur.

### Gereksinimler
- **Netcat** (`nc`): Dinleme işlemini gerçekleştirmek için sisteminizde `nc` kurulu olmalıdır.
  
Netcat'i kurmak için:
- **Ubuntu/Debian**: `sudo apt install netcat`
- **CentOS/Fedora**: `sudo yum install nc`

### Lisans
Bu proje MIT Lisansı ile lisanslanmıştır. Daha fazla bilgi için `LICENSE` dosyasına bakın.

---


