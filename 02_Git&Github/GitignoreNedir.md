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

## En Çok Kullanılan .gitignore Örnekleri
### Node.js / React Projesi
```
    node_modules/
    dist/
    .env
```

### ASP.NET Core / MVC Projesi
```
    bin/
    obj/
    .vs/
    appsettings.Development.json
```

### Visual Studio Ignore
```
    .vs/
    *.user
    *.suo
```

## .gitignore Güvenlik İçin de Önemlidir
Bazı dosyalarda şunlar olabilir:
- API Key
- Database şifresi
- JWT secret
- Connection string

**Örnek:**
```
    {
        "ConnectionString": "Server=..."
    }
```

Bunlar yanlışlıkla GitHub’a gönderilirse:
- güvenlik açığı oluşur
- veritabanı ele geçirilebilir
- API kullanım hakkı çalınabilir

Bu yüzden:
```
    .env
    appsettings.Development.json
```
çok önemlidir.

## .gitignore Çalışma Mantığı

Git yalnızca:
- henüz takip edilmeyen dosyalarda .gitignore kurallarını uygular.

Yani:

**Şu durum önemli:**

Dosya daha önce Git’e eklenmişse:
```
    git add .
```
ile track edilmişse, sonradan `.gitignore` içine yazmak yeterli olmaz.

## Daha Önce Eklenen Dosyayı Ignore Etme
**Örneğin:**
```
    node_modules/
```
ekledin ama klasör daha önce commit edilmiş.

Şu komutu kullanmalısın:
```
    git rm -r --cached node_modules
```
Sonra:
```
    git commit -m "Remove node_modules"
```

## Wildcard Kullanımı
`.gitignore` içinde özel karakterler kullanılabilir.

### Tüm `.log` dosyalarını ignore et
```
    *.log
```

**Örnek:**
```
    error.log
    app.log
```

### Tüm `bin` klasörlerini ignore et
```
    **/bin/
```

### Belirli dosyayı ignore etme
```
    !important.txt
```

**! işareti:** ignore etme demektir.

## `.gitignore` ve Takım Çalışması
Takım projelerinde çok önemlidir.

Çünkü herkesin:
- IDE ayarı farklıdır
- işletim sistemi farklıdır
- geçici dosyaları farklıdır

`.gitignore` sayesinde:
- gereksiz çakışmalar önlenir
- temiz repo oluşur
- herkes aynı yapıda çalışır

## Gerçek Hayatta En Kritik Kullanım Alanları
### 1.`node_modules`
En yaygın kullanım. Çünkü:
```
    npm install
```
ile yeniden oluşturulabilir.

### 2.Build Dosyaları
Örnek:
```
    dist/
    build/
```
Çünkü bunlar derleme çıktısıdır.

### 3.IDE Dosyaları
Visual Studio:
```
    .vs/
```
VS Code:
```
    .vscode/
```

### 4.Environment Dosyaları
```
    .env
```
Çünkü gizli bilgiler içerir.

## `.gitignore` Dosyası Nasıl Oluşturulur?
Manuel oluşturulabilir.
```
    .gitignore
```
Başında nokta olması önemlidir.

## GitHub Hazır `.gitignore` Şablonları
Github birçok teknoloji için hazır şablon sunar.
Örneğin:
- Node
- React
- ASP.NET
- Python
- Java

Bunlar standart kuralları içerir.

Örnek ASP.NET `.gitignore`:
```
    bin/
    obj/
    .vs/
    *.user
```

## İyi Bir .gitignore Nasıl Olmalı?
İyi bir .gitignore: 
- Gereksiz dosyaları dışlamalı
- Gizli bilgileri korumalı
- Repoyu temiz tutmalı
- Takım çalışmasını kolaylaştırmalı
- Büyük klasörleri engellemeli

## Gerçek Bir ASP.NET Core MVC .gitignore Örneği
```
# Build folders
bin/
obj/

# Visual Studio
.vs/
*.user
*.suo

# Logs
*.log

# Environment files
appsettings.Development.json

# Node modules
node_modules/

# Publish folder
publish/
```

## Özet
`.gitignore`:

- Git’in hangi dosyaları takip ETMEMESİ gerektiğini söyler
- Projeyi temiz tutar
- Güvenlik sağlar
- Gereksiz dosyaları engeller
- Takım çalışmalarını kolaylaştırır

## Kısaca Akılda Kalacak Şekilde
**Git:**
```
    “Dosyaları takip ederim.”
```
**.gitignore:**
```
    “Şunları takip etme.”
```

## Öğrenmen Gereken En Kritik Nokta
Yeni başlayanların en büyük hatası:
```
    git add .
```
komutunu çalıştırmadan önce .gitignore hazırlamamaktır.

Bu yüzden profesyonel akış genelde şöyledir:
1. Projeyi oluştur
2. .gitignore oluştur
3. git init
4. git add .
5. commit at

Bu sıra çok önemlidir.