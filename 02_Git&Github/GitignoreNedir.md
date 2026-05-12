# .gitignore Nedir?

## Git Nedir?

Bir projede yazdığımız kodların geçmişini takip etmek için kullanılan sisteme Git denir.

Git sayesinde:
- Kod değişikliklerini kayıt altına alırız
- Eski sürümlere dönebiliriz
- Takım halinde çalışabiliriz
- Hangi dosyada ne değişti görebiliriz

Örneğin:
```
    git add .
    git commit -m "Login ekranı eklendi"
```
dediğimizde Git proje dosyalarını takip etmeye başlar.

## Problem Nerede Başlıyor?
Bir projede sadece kod dosyaları olmaz.

Şunlar da oluşur:
- Geçici dosyalar
- Derleme çıktıları
- Cache dosyaları
- IDE ayarları
- Kullanıcıya özel ayarlar
- Şifre veya gizli bilgiler
- Binlerce bağımlılık dosyası

Örneğin:
```
    node_modules/
    bin/
    obj/
    .vs/
```
Bu dosyaların Git'e gönderilmesi çoğu zaman:
- gereksizdir,
- projeyi şişirir,
- güvenlik riski oluşturur,
- ekip içinde sorun çıkarır.

İşte burasa `.gitignore` devreye girer.

## .gitignore Nedir?
`.girignore`, Git'e ***"Bu dosya ve klasörleri takip etme."*** dememizi sağlayan özel bir dosyadır.

Git bu dosyadaki kuralları okur ve belirtilen dosyaları versiyon kontrolüne dahil etmez.

## .gitignore Neden Kullanılır?
**Amaç:**
- Gereksiz veya özel dosyaların Git'e yüklenmesini engellemektir.

## .gitignore Kullanılmazsa Ne Olur?
**Örnek Senaryo**

Bir React projesi düşünelim.

Projede şunlar var:
```
    node_modules/
    src/
    public/
    package.json
```

`node_modules` klasörü:
- tüm npm paketlerini içerir
- binlerce dosya barındırır
- tekrar üretilebilir

Eğer `.gitignore` kullanılmazsa:
```
    git add.
```
komutu `node_modules` klasörünü de Git'e ekler.

Sonuç:
- Repo aşırı büyür
- Push işlemi yavaşlar
- GitHub limit sorunları oluşabilir
- Takım arkadaşların gereksiz dosyaları indirir

## .gitignore Dosyası Nerede Bulunur?
Genellikle proje kök dizininde bulunur.

Örnek:
```
    MyProject/
    │
    ├── .gitignore
    ├── package.json
    ├── src/
    └── public/
```

## .gitignore Dosya Yapısı
İçerisine hangi dosyaların ignore edileceği yazılır.

**Örnek:**
```
    node_modules/
    bin/
    obj/
    .env
```

**Anlamları:**
| Kural           | Açıklama                              |
| --------------- | ------------------------------------- |
| `node_modules/` | npm paket klasörünü ignore et         |
| `bin/`          | build çıktısını ignore et             |
| `obj/`          | geçici derleme dosyalarını ignore et  |
| `.env`          | gizli environment dosyasını ignore et |
