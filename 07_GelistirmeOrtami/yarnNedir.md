# Yarn Nedir?
Yarn, Javascript ve Node.js projelerinde kullanılan bir `package manager`’dır.

npm gibi Yarn'da:
- Paketleri yükler,
- Paketleri kaldırır,
- Bağımlılıkları yönetir,
- Proje scriptlerini çalıştırır,
- Paket sürümlerinin tutarlı kalmasına yardımcı olur.

En kısa tanımıyla:
```
    Yarn, npm'e alternatif olarak kullanılabilen bir JavaScript package manager'dır.
```

Yarn farklı bir package manager olsa da paketleri çoğunlukla npm Registry üzerinden indirir. Yani npm Registry’de bulunan `react`, `next`, `zod` veya `swiper` gibi paketler Yarn ile de kurulabilir.

```
    yarn add zod
```

## Yarn Neden Kullanılır?
Yarn; paket kurulumlarının güvenilir, hızlı ve ekip içinde tutarlı şekilde yapılmasına yardımcı olmak amacıyla geliştirilmiştir.

Modern Yarn ayrıca:
- Proje bazında Yarn sürümü belirleme,
- Farklı paket kurulum yöntemleri,
- Workspace desteği,
- Gelişmiş önbellekleme,
- Plug’n’Play kullanımı

gibi özellikler sunar.

Ancak temel kullanım bakımından npm ile aynı ihtiyacı karşılar: `Projenin paketlerini ve bağımlılıklarını yönetmek.`

## Yarn ve npm İlişkisi
Yarn ve npm aynı araç değildir, ancak aynı tür işi yaparlar.

| Özellik        | npm                     | Yarn                    |
| -------------- | ----------------------- | ----------------------- |
| Araç türü      | Package manager         | Package manager         |
| Paket ekleme   | `npm install zod`       | `yarn add zod`          |
| Paket kaldırma | `npm uninstall zod`     | `yarn remove zod`       |
| Lock dosyası   | `package-lock.json`     | `yarn.lock`             |
| Registry       | Genellikle npm Registry | Genellikle npm Registry |

Bir paketin npm Registry’den indirilmesi, projede mutlaka npm kullanıldığı anlamına gelmez. Yarn da aynı registry’deki paketleri indirebilir.

## Yarn Classic ve Modern Yarn
Yarn öğrenirken bilinmesi gereken en önemli konulardan biri sürüm ayrımıdır.

Yarn'ın iki temel dönemi vardır:

### 1. Yarn Classic
Yarn'ın `1.x` sürümleridir.

Örnek: `Yarn 1.22.22`

Yarn Classic daha eski proje ve eğitimlerde sıkça görülebilir.

### 2. Modern Yarn
Yaen'ın `2.x` ve sonraki sürümleridir.

Örnek: `Yarn 4.18.0`

Modern Yarn; yeni yapılandırma seçenekleri, farklı kurulum yöntemleri ve gelişmiş workspace özellikleri sunar. Resmî Yarn belgeleri mümkün olan projelerde Classic sürümden Modern Yarn’a geçilmesini önerir.

| Yarn sürümü           | Adlandırma   |
| --------------------- | ------------ |
| Yarn `1.x`            | Yarn Classic |
| Yarn `2.x` ve sonrası | Modern Yarn  |

## Yarn 1 ile Yarn 4 Neden Karşılaştırılmamalıdır?
Yarn 1 ve Yarn 4 aynı aracın farklı ana sürümleridir; ancak komutları, yapılandırmaları ve kurulum davranışları arasında önemli farklılıklar bulunabilir.

Örneğin projede:
```
{
  "packageManager": "yarn@4.18.0"
}
```
yazıyorsa bu proje Yarn 4.18.0 ile çalıştırılmak üzere yapılandırılmıştır.

Bilgisayarda global olarak:
```
    Yarn 1.22.22
```
bulunması, projede beklenen sürümle uyuşmaz.

Benim daha önce yaşadığım durum buydu:
```
    Projede beklenen Yarn 4.18.0
    Bilgisayarda çalışan: Yarn 1.22.22
```

Bu uyuşmazlık:
- Komutların farklı davranmasına,
- Yapılandırmaların okunmamasına,
- Paket kurulumunun başarısız olmasına,
- Yanlış lock dosyası değişikliklerine neden olabilir.

`Bir projede yalnızca 'Yarn kurulu mu?' sorusuna değil, 'Doğru Yarn sürümü kullanılıyor mu?' sorusuna da bakılmalıdır.`

## Yarn Sürümü Nasıl Kontrol Edilir?
Terminalde şu komut çalıştırılır:
```
    yarn --version
```

Kısa biçimi: `yarn -v`

Örnek çıktı: `4.18.0`

Projede beklenen sürüm ise `package.json` içinden kontrol edilebilir:
```
{
  "packageManager": "yarn@4.18.0"
}
```

Terminalde görünen sürümle `package.json` içindeki sürümün uyumlu olması gerekir.

## Yarn ve Corepack İlişkisi
Modern Yarn projelerinde Yarn sürümünün proje bazında yönetilmesi için Corepack kullanılabilir.

Corepack, `package.json` içindeki şu alanı okuyabilir:
```
    {
    "packageManager": "yarn@4.18.0"
    }
```

Böylece proje için gerekli Yarn sürümünün kullanılmasına yardımcı olur.

Yarn'ın resmi belgeleri, Yarn'ı `npm install -g yarn` komutuyla global olarak kurmak yerine proje bazlı sürüm yönetimi için Corepack kullanılmasını önerir. Bunun nedeni package manager sürümünün de proje bağımlılıkları gibi sabitlenebilmesidir.

Corepack'i etkinleştirmek için genellikle `corepack enable` kullanılır.

Corepack sistemde bulunmuyorsa önce şu komut gerekebilir:
```
    npm install -g corepack
```

Ardından `corepack enable` çalıştırılabilir.

`Corepack, projenin ihtiyaç duyduğu Yarn sürümünün kullanılmasına yardımcı olur.`

## Temel Yarn Komutları
### Projenin Paketlerini Yüklemek
```
    yarn install
```

Modern Yarn' da yalnızca `yarn` yazmak da kurulum işlemini başlatır. Resmi Yarn rehberine göre `yarn`, `yarn install` komutunun kısa karşılığıdır.

Bu komut genellikle:
- Proje Github'dan indirildiğinde,
- Bağımlılıklar eksik olduğunda,
- Projenin paket kayıtları değiştiğinde çalıştırılır.

### Yeni Paket Eklemek
```
    yarn add paket-adi
```

Örnek:
```
    yarn add zod
```
Paket normal olarak `dependencies`alanına eklenir:
```
    {
        "dependencies": {
            "zod": "^4.0.0"
        }
    }
```

Yarn'da paket eklemek için `install` değil, `add` kullanılır: `yarn add zod`

Resmî Yarn belgelerine göre `yarn add`, paketi `package.json` dosyasındaki uygun bağımlılık alanına ekler.

### Geliştirme Bağımlılığı Eklemek
```
    yarn add --dev paket-adi
```

Kısa kullanımı: `yarn add -D paket-adi`

Örnek:
```
    yarn add -D eslint
```

Bu paket `devDependencies` alanına eklenir:
```
    {
        "devDependencies": {
            "eslint": "^9.0.0"
        }
    }
```

### Paket Kaldırmak
`yarn remove paket-adi`

Örnek:
```
    yarn remove zod
```

Bu işlem paketi kaldırır ve ilgili proje kayıtlarını günceller.

### Paket Güncellemek
Modern Yarn'da bir paketi güncellemek için:
```
    yarn up paket-adi
```

Örnek:
```
    yarn up zod
```

Proje genelindeki uygun paketleri güncellemek için; `yarn up "*"` kullanılabilir.

Burada sürüm farkına dikkat edilmelidir:
| Sürüm        | Yaygın güncelleme komutu |
| ------------ | ------------------------ |
| Yarn Classic | `yarn upgrade`           |
| Modern Yarn  | `yarn up`                |

Bu Yarn sürümünün neden kontrol edilmesi gerektiğine iyi bir örnektir.

## Yarn ile Script Çalıştırmak
`package.json` dosyasında şu scriptlerin bulunduğunu düşünelim:
```
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "lint": "eslint ."
  }
}
```

Yarn ile bu scriptler şu şekilde çalıştırılabilir:
```
yarn dev
yarn build
yarn lint
```

Uzun kullanım biçimi de geçerlidir: `yarn run dev`

Yani `yarn dev` ile `yarn run dev`aynı scripti çalıştırır.

## yarn.lock Dosyası
Yarn, paket kurulumlarının sonucunu `yarn.lock` dosyasında kaydeder.
```
    proje/
    ├── package.json
    ├── yarn.lock
    └── src/
```

Temel ayrım şöyledir:
| Dosya          | Görevi                                              |
| -------------- | --------------------------------------------------- |
| `package.json` | Projenin istediği bağımlılıkları belirtir           |
| `yarn.lock`    | Yarn’ın belirlediği kesin kurulum sonucunu kaydeder |


`yarn.lock`:
- Elle düzenlenmemelidir.
- Git ile takip edilmelidir.
- Github'a gönderilmemelidir.
- Aynı projede `package-lock.json` ile karıştırılmamalıdır.
Projede `yarn.lock` bulunması, o projenin Yarn ile yönetildiğini gösteren önemli işaretlerden biridir.

## Yarn Her Zaman `node_modules` Oluşturur mu?
Hayır. Bu durum Yarn'ın sürümüne ve proje ayarlarına bağlıdır.

Yarn Classic genellikle `node_modules` kullanır:
```
proje/
├── node_modules/
├── package.json
└── yarn.lock
```

Modern Yarn ise farklı kurulum yöntemlerini destekler:
- `node_modules`
- Plug'n'Play
- pnpm benzeri kurulum modeli

Resmi Yarn belgelerine göre Modern Yarn bu farklı kurulum stratejilerini destekler.

## Plug’n’Play nedir?
Plug’n’Play, kısa adıyla PnP, paketlerin klasik `node_modules` yapısı yerine Yarn tarafından oluşturulan bir bağlantı dosyası üzerinden bulunmasını sağlayan yöntemdir.

PnP kullanan projede şu dosya görülebilir: `.pnp.cjs`

Bu nedenle modern bir Yarn projesinde `node_modules` klasörünün bulunmaması her zaman paketlerin kurulmadığı anlamına gelmez.

Proje node_modules kullanacak şekilde ayarlanmışsa .yarnrc.yml içinde aşağıdaki yapı bulunabilir:
```
    nodeLinker: node-modules
```

Başlangıç seviyesinde şu bilgiyi bilmek yeterlidir:

`Yarn Classic genellikle node_modules kullanır; Modern Yarn ise proje ayarına göre node_modules veya Pnp kullanabilir.`

## Yarn Yapılandırma Dosyaları
Modern Yarn projelerinde şu yapılarla karşılaşılabilir:
```
    .yarnrc.yml
    .yarn/
    .pnp.cjs
    yarn.lock
```

| Yapı          | Temel görevi                                               |
| ------------- | ---------------------------------------------------------- |
| `yarn.lock`   | Paketlerin kurulum sonucunu kaydeder                       |
| `.yarnrc.yml` | Yarn ayarlarını tutar                                      |
| `.yarn/`      | Projeye ait Yarn dosyalarını veya önbelleği barındırabilir |
| `.pnp.cjs`    | PnP kullanılıyorsa paket bağlantılarını tanımlar           |

Her Yarn projesinde bu yapıların tamamının bulunması zorunlu değildir.

## `yarn dlx` Nedir?
Modern Yarn'da bir paketin komutunu projeye kalıcı bağımlılık olarak eklemeden çalıştırmak için `yarn dlx paket-adi` kullanılabilir.

Örnek:
```
    yarn dlx create-next-app
```

Bu kullanım npm'deki `npx`komutuna benzer:
| npm             | Modern Yarn          |
| --------------- | -------------------- |
| `npx paket-adi` | `yarn dlx paket-adi` |

Bu komut sürekli kullanılacak proje bağımlılıkları için değil, tek seferlik araç çalıştırma işlemleri için uygundur.

## Temel Yarn Komutları
| Komut                   | Görevi                                      |
| ----------------------- | ------------------------------------------- |
| `yarn --version`        | Yarn sürümünü gösterir                      |
| `yarn`                  | Projenin bağımlılıklarını yükler            |
| `yarn install`          | Projenin bağımlılıklarını yükler            |
| `yarn add paket-adi`    | Yeni bağımlılık ekler                       |
| `yarn add -D paket-adi` | Geliştirme bağımlılığı ekler                |
| `yarn remove paket-adi` | Paketi kaldırır                             |
| `yarn up paket-adi`     | Modern Yarn’da paketi günceller             |
| `yarn dev`              | `dev` scriptini çalıştırır                  |
| `yarn build`            | `build` scriptini çalıştırır                |
| `yarn dlx paket-adi`    | Bir paket komutunu geçici olarak çalıştırır |

## Yarn Kullanırken Dikkat Edilmesi Gerekenler
- Önce `yarn --version` ile kullanılan sürüm kontrol edilmelidir.
- `package.json` içindeki packageManager alanı incelenmelidir.
- Yarn 1 ile Yarn 4 aynı kabul edilmemelidir.
- Yarn kullanılan projede npm komutları çalıştırılmamalıdır.
- `yarn.lock` dosyası silinmemeli ve GitHub’a gönderilmelidir.
- Modern Yarn projesinde `node_modules` bulunmaması hemen hata olarak değerlendirilmemelidir.
- Yarn’ın global eski sürümü yerine proje için belirlenen sürüm kullanılmalıdır.
- Paket değişikliklerinden sonra oluşan `yarn.lock` değişikliği de commit edilmelidir.

Özellikle şu iki lock dosyası aynı projede birlikte oluşturulmamalıdır:
```
    yarn.lock
    package-lock.json
```

Bu durum npm ve Yarn'ın aynı projede karışık kullanıldığına işaret edebilir.

# Kısa Özet
Yarn, JavaScript projelerindeki paketleri ve bağımlılıkları yöneten bir package manager’dır.

npm ile aynı temel ihtiyacı karşılar ancak komutları ve bazı çalışma özellikleri farklıdır.

En önemli bilgiler:
```
    Yarn 1.x             → Yarn Classic
    Yarn 2 ve sonrası    → Modern Yarn
    Yarn lock dosyası    → yarn.lock
    Paket ekleme         → yarn add
    Paket kaldırma       → yarn remove
    Script çalıştırma    → yarn dev
    Sürüm kontrolü       → yarn --version
```

Yarn hakkında özellikle unutulmaması gereken nokta şudur:
```
    Projede Yarn kullanılması tek başına yeterli değildir; projenin beklediği doğru Yarn sürümü kullanılmalıdır.
```