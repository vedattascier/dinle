<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dinle Fonksiyonu</title>
</head>
<body>
    <h1>Dinle Fonksiyonu</h1>
    <p>
        Bu basit <code>dinle</code> fonksiyonu, belirttiğiniz bir portu <code>nc</code> (Netcat) ile dinler.
        Fonksiyon, eğer port numarası verilmemişse, kullanıcıdan bir port numarası istemekte ve dinlemeye başlamaktadır.
        Bağlantı kesildiğinde bile dinleme otomatik olarak devam eder.
    </p>

    <h2>Kullanım</h2>

    <h3>Fonksiyonun Tanımlanması</h3>
    <p>Fonksiyonu kullanabilmek için <code>.bashrc</code> veya <code>.zshrc</code> dosyanıza aşağıdaki satırı ekleyin:</p>
    <pre><code>dinle() {
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
    </code></pre>

    <p>Bu satırı ekledikten sonra terminali yeniden başlatın veya aşağıdaki komutları çalıştırın:</p>
    <ul>
        <li><strong>Bash:</strong> <code>source ~/.bashrc</code></li>
        <li><strong>Zsh:</strong> <code>source ~/.zshrc</code></li>
    </ul>

    <h3>Komutların Kullanımı</h3>

    <h4>1. Port numarası vermeden kullanmak:</h4>
    <p>Eğer port numarası belirtmeden sadece <code>dinle</code> komutunu yazarsanız, sizden bir port numarası girmenizi ister.</p>
    <pre><code>dinle
    </code></pre>

    <p>Kullanıcıya şu mesaj gösterilir:</p>
    <pre><code>Lütfen bir port numarası girin!
Dinlemek istediğiniz portu girin:
    </code></pre>

    <h4>2. Port numarasıyla kullanmak:</h4>
    <p>Port numarasını komutla beraber belirtebilirsiniz. Örneğin, 8080 portunu dinlemek için:</p>
    <pre><code>dinle 8080
    </code></pre>

    <p>Bu komut, Netcat ile belirtilen portu dinler:</p>
    <pre><code>nc -lvnp 8080 ile dinleniyor...
    </code></pre>

    <h2>Özellikler</h2>
    <ul>
        <li>Kullanıcıdan port numarası alır veya doğrudan argüman olarak verilen portu kullanır.</li>
        <li>Dinleme kesildiğinde otomatik olarak yeniden başlar (sürekli dinleme modu).</li>
        <li>Hem Bash hem de Zsh ile uyumludur.</li>
    </ul>

    <h2>Gereksinimler</h2>
    <p><strong>Netcat</strong> (<code>nc</code>): Dinleme işlemini gerçekleştirmek için sisteminizde <code>nc</code> kurulu olmalıdır.</p>
    <p>Netcat'i kurmak için:</p>
    <ul>
        <li><strong>Ubuntu/Debian:</strong> <code>sudo apt install netcat</code></li>
        <li><strong>CentOS/Fedora:</strong> <code>sudo yum install nc</code></li>
    </ul>

    <h2>Lisans</h2>
    <p>Bu proje MIT Lisansı ile lisanslanmıştır. Daha fazla bilgi için <code>LICENSE</code> dosyasına bakın.</p>
</body>
</html>
