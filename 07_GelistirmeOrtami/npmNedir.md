# npm Nedir?
**npm**, Javascript ve Node.js ekosisteminde kullanılan paket yönetim sistemidir.

npm 3 temel parçadan oluşur:
- **npm Registry:** Paketlerin yayımlandığı çevrim içi kayıt sistemi
- **npm CLI:** Terminalde kullandığımız komut satırı aracı
- **npm web sitesi:** Paketleri araştırabildiğimiz ve hesapları yönetebildiğimiz web sitesi

Geliştirme sırasında `npm install` gibi komutlarla kullandığımız bölüm, npm’in **CLI aracıdır**. npm’in resmî açıklamasına göre registry, CLI ve web sitesi aynı npm ekosisteminin farklı parçalarıdır.

## npm Ne İşe Yarar?
npm temel olarak:
- Projeye paket ekler.
- Paketleri kaldırır.
- Bağımlılıkları yükler.
- Paket sürümlerini yönetir.
- package.json içindeki scriptleri çalıştırır.
- Paketlerin kayıtlarını günceller.
- Projeyi başka bir bilgisayarda yeniden kurmaya yardımcı olur.

Örneğin projeye Zod paketini eklemek için:
```
    npm install zod
```
komutu kullanılır.

Burada:
- **npm:** Kullanılan package manager
- **install:** Yapılacak işlem
- **zod:** Yüklenecek paket anlamına gelir.

## npm ve Node.js ilişkisi
npm ve Node.js aynı şey değildir.

| Araç    | Görevi                                                           |
| ------- | ---------------------------------------------------------------- |
| Node.js | JavaScript kodunun bilgisayarda veya sunucuda çalışmasını sağlar |
| npm     | JavaScript paketlerini ve proje komutlarını yönetir              |

Node.js kurulduğunda npm de genellikle birlikte kurulur. Bu nedenle çoğu durumda npm’i ayrıca kurmamız gerekmez. Resmî npm kurulum belgesi Node.js ve npm sürümlerinin aşağıdaki komutlarla kontrol edilebileceğini belirtir.

Node.js sürümünü kontrol etmek için: `node -v`

npm sürümünü kontrol etmek için: `npm -v`

Örnek çıktı:
```
    v20.14.0
    10.7.0
```

Bu iki aracın sürümleri birbirinden farklıdır. Çünkü Node.js ve npm ayrı araçlardır.

## npm Bir Paketi Nasıl Yükler?
Örneğin şu komutu çalıştıralım:
```
    npm install zod
```

npm genel olarak şu işlemleri gerçekleştirir:
- Zod paketini registry üzerinde bulur.
- Uygun paket sürümünü belirler.
- Paketin ihtiyaç duyduğu alt bağımlılıkları bulur.
- Paket dosyalarını projeye yükler.
- Bağımlılığı `package.json` dosyasına kaydeder.
- Kesin kurulum sonucunu `package-lock.json` dosyasına kaydeder.

Paket dosyaları varsayılan npm kurulumunda genellikle `node_modules` klasöründe bulunur.

```
proje/
├── node_modules/
├── package.json
└── package-lock.json
```

Bu üç yapının temel görevleri şöyledir:
| Yapı                | Görevi                                              |
| ------------------- | --------------------------------------------------- |
| `package.json`      | Projenin bağımlılıklarını ve komutlarını tanımlar   |
| `package-lock.json` | npm’in belirlediği kesin paket sürümlerini kaydeder |
| `node_modules`      | İndirilen paket dosyalarını barındırır              |

`package-lock.json`, aynı bağımlılık ağacının farklı kurulumlarda tekrar oluşturulmasına yardımcı olur ve proje deposuna gönderilmesi amaçlanır. 

## Temel npm Komutları
### Projedeki paketleri yüklemek
```
    npm install
```
Kısa biçimi:
```
    npm i
```

Bu komut, mevcut projedeki `package.json` ve lock dosyası bilgilerini kullanarak gerekli paketleri yükler.

Genellikle şu durumlarda çalıştırılır:
- Proje GitHub’dan ilk kez indirildiğinde,
- node_modules klasörü bulunmadığında,
- Projenin bağımlılıkları değiştiğinde.

### Yeni bir paket eklemek
```
    npm install paket-adi
```

Örnek:
```
    npm install zod
```

Bu paket varsayılan olarak `dependencies` alanına eklenir:
```
{
  "dependencies": {
    "zod": "^4.0.0"
  }
}
```

### Geliştirme Bağımlılığı Eklemek

Yalnızca geliştirme sürecinde kullanılan bir paket için `--save-dev` veya kısa biçimiyle `-D` kullanılır:
```
    npm install --save-dev paket-adi
```
Kısa kullanımı:
```
    npm install -D paket-adi
```
Örnek:
```
    npm install -D eslint
```

Bu paket `devDependencies` alanına eklenir:
{
  "devDependencies": {
    "eslint": "^9.0.0"
  }
}

### Paket Kaldırmak
```
    npm uninstall paket-adi
```

Örnek:
```
    npm uninstall zod
```
Bu işlem:
- Paketi kurulu bağımlılıklardan kaldırır.
- `package.json` kaydını günceller.
- `package-lock.json` dosyasını günceller.

Dolayısıyla paketi yalnızca `node_modules` içinden elle silmek yerine `npm uninstall` kullanılmalıdır.

### Paketleri Güncellemek
```
    npm update
```

Bu komut paketleri, `package.json` içinde izin verilen sürüm aralıkları doğrultusunda günceller.

Belirli bir paketi güncellemek için:
```
    npm update paket-adi
```

Her güncelleme doğrudan uygulanmamalıdır. Özellikle büyük projelerde değişiklikler incelenmeli ve proje tekrar test edilmelidir.

### npm ile Script Çalıştırmak
npm yalnızca paket yüklemek için kullanılmaz. package.json içinde tanımlanan proje komutlarını da çalıştırır.

Örnek:
```
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "lint": "eslint ."
  }
}
```

Bu scriptler şu şekilde çalıştırılır: 
```
    npm run dev
    npm run build
    npm run lint
```

Komutun çalışma mantığı şöyledir:
```
    npm run dev
            ↓
    package.json içindeki "dev" scriptini bulur
            ↓
    next dev komutunu çalıştırır
```

Projede tanımlanmış scriptleri görmek için `npm run` kullanılabilir.

## npm install ve npm ci Farkı
Günlük geliştirme sırasında genellikle, `npm install` kullanılır.

Otomatik test, deployment ve CI/CD ortamlarında ise sıklıkla `npm ci` komutuyla karşılaşılır.

Temel fark:
| Komut         | Kullanım amacı                                        |
| ------------- | ----------------------------------------------------- |
| `npm install` | Günlük geliştirme ve bağımlılık ekleme                |
| `npm ci`      | Lock dosyasına bağlı temiz ve tekrarlanabilir kurulum |

`npm ci` mevcut bağımlılık kayıtlarını değiştirmek için değil, projeyi lock dosyasına göre temiz şekilde kurmak için kullanılır.

Başlangıç sebiyesinde şu ayrımı bilmek yeterlidir:
`Geliştirirken genellikle **npm install**, otomatik kurulum sistemlerinde genellikle **npm ci** kullanılır.`

## Yerel ve Global Kurulum
### Yerel Kurulum
Varsayılan paket kurulumu yereldir:
```
    npm install zod
```

Paket yalnızca mevcut projeye eklenir. Uygulama içinde kullanılacak paketler genellikle bu şekilde kurulmalıdır.

### Global Kurulum
Bir paketi bilgisayar genelinde komut olarak kullanmak için `-g` seçeneği kullanılabilir:
```
    npm install -g paket-adi
```

Ancak her paketi global kurmak doğru değildir. Projeye ait React, Next.js, Zod veya ESLint gibi paketler genellikle yerel kurulmalıdır.

Temel kural:
```
    Projeye ait paketler **yerel**, bilgisayar genelinde kullanılacak komut satırı araçları gerektiğinde **global** kurulur.
```

## npx Nedir?
`npx`. bir paketin sunduğu komutu global olarak yüklemek zorunda kalmadan çalıştırmaya yardımcı olur.

Örneğin yeni bir Next.js projesi oluştururken `npx create-next-app@latest` kullanılabilir.

Burada paket bilgisayara kalıcı bir global araç olarak eklenmek zorunda değildir. `npx`, ilgili komutu çalıştırır.

Kısa ayrım:
| Araç  | Görevi                                  |
| ----- | --------------------------------------- |
| `npm` | Paketleri kurar ve yönetir              |
| `npx` | Paketlerin sunduğu komutları çalıştırır |

## npm ile Yeni Proje Bilgisi Oluşturmak
Boş bir klasörde `package.json` oluşturmak için: 
```
    npm init
```
kullanılır.

Sorular sorulmadan varsayılan değerlerle oluşturmak için:
```
    npm init -y
```
kullanılabilir.

Bu komutu `package.json` konusunda gördüğümüz için burada tekrar ayrıntılandırmamıza gerek yoktur.

## Sık Kullanılan npm Komutları
| Komut                      | Görevi                                                  |
| -------------------------- | ------------------------------------------------------- |
| `npm -v`                   | npm sürümünü gösterir                                   |
| `npm init`                 | `package.json` oluşturur                                |
| `npm install`              | Projenin paketlerini yükler                             |
| `npm install paket-adi`    | Projeye paket ekler                                     |
| `npm install -D paket-adi` | Geliştirme bağımlılığı ekler                            |
| `npm uninstall paket-adi`  | Paketi kaldırır                                         |
| `npm update`               | Uygun paket güncellemelerini yapar                      |
| `npm run`                  | Tanımlı scriptleri listeler                             |
| `npm run dev`              | `dev` scriptini çalıştırır                              |
| `npm run build`            | `build` scriptini çalıştırır                            |
| `npm ci`                   | Lock dosyasına göre temiz kurulum yapar                 |
| `npm audit`                | Bağımlılıklardaki bilinen güvenlik sorunlarını denetler |

## npm Kullanırken Dikkat Edilmesi Gerekenler
- npm komutları projenin `package.json` dosyasının bulunduğu klasörde çalıştırılmalıdır.
- Projeye ait paketler gereksiz yere global kurulmamalıdır.
- `package-lock.json` dosyası silinmemeli ve GitHub’a gönderilmelidir.
- `node_modules` klasörü GitHub’a gönderilmemelidir.
- npm kullanılan projede Yarn veya pnpm komutları karıştırılmamalıdır.
- Paket güncellemelerinden sonra proje test edilmelidir.
- `npm audit fix --force` gibi zorlayıcı komutlar ne değiştirdiği anlaşılmadan çalıştırılmamalıdır.

Özellikle bir projede `package-lock.json` bulunuyorsa bu genellikle projenin npm il yönetildiğini gösterir.

# Kısa Özet
`npm;` JavaScript paketlerini yüklemek, kaldırmak, güncellemek ve proje scriptlerini çalıştırmak için kullanılan bir package manager’dır.

Temel çalışma ilişkisi şöyledir:
```
    npm
    ├── package.json dosyasını okur
    ├── registry üzerinden paketleri bulur
    ├── paketleri projeye yükler
    ├── package-lock.json dosyasını günceller
    └── proje scriptlerini çalıştırır
 ```

En sık kullanılan komutlar:
```
    npm install
    npm install paket-adi
    npm install -D paket-adi
    npm uninstall paket-adi
    npm run dev
    npm run build
```

Unutmamamız gereken temel cümle:

`npm, Node.js’in kendisi değildir; Node.js projelerindeki paketleri ve proje komutlarını yöneten araçtır.`