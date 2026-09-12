# pnpm Nedir?
**pnpm**, Javascript ve Node.js projelerinde kullanılan bir package manager'dır.

npm ve Yarn gibi pnpm de:
- Projenin bağımlılıklarını yükler.
- Yeni paket ekler.
- Kullanılmayan paketleri kaldırır.
- Paketleri günceller.
- `package.json` içindeki scriptleri çalıştırır.
- Paketlerin sürüm bilgilerini lock dosyasında saklar.

En kısa tanımıyla:
`pnpm, paketleri disk alanını daha verimli kullanacak şekilde yöneten bir JavaScript package manager’dır.`

## pnpm'in npm ve Yarn'dan Temel Farkı Nedir?
pnpm’in öne çıkan farkı, aynı paketlerin dosyalarını her projeye yeniden kopyalamak yerine bilgisayardaki ortak bir depoda saklamasıdır.

Bu ortak depoya `store` adı verilir.

Örneğin bilgisayarımızda üç farklı proje olduğunu düşünelim:
```
    Proje A → React kullanıyor
    Proje B → React kullanıyor
    Proje C → React kullanıyor
```

Geleneksel yöntemde React dosyalarının her proje için ayrı bir kopyası bulunabilir.

pnpm ise aynı paket sürümünü ortak store içinde bir defa saklar ve projeleri bu dosyalara bağlar:
```
pnpm store
└── React dosyaları
    ├── Proje A bağlantısı
    ├── Proje B bağlantısı
    └── Proje C bağlantısı
```

Böylece aynı paket sürümü farklı projelerde kullanıldığında dosyaların tekrar tekrar indirilmesi ve saklanması azaltılır.

Resmî pnpm belgelerine göre paketler içerik tabanlı ortak bir store içinde saklanır ve projelere hard link yöntemiyle bağlanır. Bu yaklaşım disk kullanımını azaltabilir ve paket kurulumlarını hızlandırabilir.

## Store Nedir?
Store, pnpm'in indirdiği paket dosyalarını bilgisayarda ortak olarak sakladığı alandır.

Store konumunu görmek için `pnpm store path` komutu kullanılabilir.

Basitleştirilmiş çalışma şekli şöyledir:
```
Registry
   ↓
pnpm store
   ↓
Projenin node_modules yapısı
```

Bir paket store içinde zaten bulunuyorsa pnpm aynı dosyaları yeniden indirmek yerine mevcut dosyalardan yararlanabilir.

Ancak store ortak olsa da her projenin hangi pakete ve sürüme ihtiyaç duyduğu yine kendi:
- `package.json`
- `pnpm-lock.json`

dosyalarıyla belirlenir.

## pnpm `node_modules` Kullanır Mı?
Evet. pnpm varsayılan olarak node_modules klasörü oluşturur ancak bu klasörün yapısı npm ve Yarn Classic’e göre farklıdır.

Örnek:
```
    proje/
    ├── node_modules/
    │   └── .pnpm/
    ├── package.json
    └── pnpm-lock.yaml
```

pnpm paketleri ortak store ile proje arasında **hard link** ve **symbolic link** bağlantıları kullanarak düzenler.

Bu teknik terimlerin temel anlamı şöyledir:
- **Hard link:** Aynı dosya içeriğine diskte tekrar kopya oluşturmadan ulaşılmasını sağlar.
- **Symbolic link:** Bir dosya veya klasöre yönlendiren bağlantıdır.

Başlangıç seviyesinde şu bilgi yeterlidir:

`pnpm paketleri yine projede kullanılabilir hâle getirir; ancak her paketin tüm dosyalarını her projeye yeniden kopyalamamaya çalışır.``

## pnpm Neden Daha Katı Bir Bağımlılık Yapısı Kullanır?
pnpm’in oluşturduğu `node_modules` yapısında proje genellikle yalnızca `package.json` dosyasında açıkça belirtilen doğrudan bağımlılıklara erişir.

Örneğin projemizde yalnızca `paket-a` kayıtlı olsun:
```
{
  "dependencies": {
    "paket-a": "^1.0.0"
  }
}
```

`paket-a`, kendi içinde `paket-b` kullanıyor olabilir:
```
    Proje
    └── paket-a
        └── paket-b
```

Bizim projemiz `paket-b`yi doğrudan kullanacaksa onu ayrıca bağımlılık olarak eklemelidir:
```
    pnpm add paket-b
```
Bu yaklaşım, projede açıkça tanımlanmamış paketlerin yanlışlıkla kullanılmasını azaltır.

Resmî pnpm belgeleri, varsayılan yapıda yalnızca doğrudan bağımlılıkların node_modules köküne bağlandığını belirtir.

## pnpm Sürümü Nasıl Kontrol Edilir?
Terminalde; `pnpm --version` veya `pnpm -v` kullanılır.

Örnek çıktı; `10.0.0``

Projede beklenen pnpm sürümü `package.json` içinde belirtilebilir:
```
    {
    "packageManager": "pnpm@10.0.0"
    }
```
Terminalde çalışan sürümle projenin beklediği sürümün uyumlu olması önemlidir.

pnpm sürümlerinin Node.js uyumluluğu değişebildiği için kurulum yaparken kullanılan Node.js sürümü de kontrol edilmelidir.

## Temel pnpm Komutları
### Projenin Bağımlılıklarını Yüklemek
`pnpm install`

Kısa biçimi; `pnpm i`

Bu komut projenin bağımlılıklarını yükler ve gerekli kurulum yapısını oluşturur.

Genellikle:
- Proje Github'dan indirildiğinde,
- `node_modules` bulunmadığında,
- Bağımlılıklar değiştiğinde çalıştırılır.

### Yeni Paket Eklemek
`pnpm add paket-adi`

Örnek: `pnpm add zod``

Bu işlem Zod’u `dependencies` alanına ekler:
```
    {
    "dependencies": {
        "zod": "^4.0.0"
    }
    }
```

### Geliştirme Bağımlılığı Eklemek
`pnpm add --save-dev paket-adi``

Kısa kullanımı; `pnpm add -D paket-adi``

Örnek: `pnpm add -D eslint``

Paket devDependencies alanına eklenir:
```
    {
        "devDependencies": {
            "eslint": "^9.0.0"
        }
    }
```
-D seçeneğinin paketi devDependencies alanına eklediği resmî pnpm komut belgesinde de belirtilir.

### Paket Kaldırmak
`pnpm remove paket-adi`

Örnek: `pnpm remove zod`

Kısa biçimi de kullanılabilir; `pnpm rm zod``

Bu işlem paket kaydını ve ilgili kurulum bilgilerini günceller.

### Paket Güncellemek
`pnpm update paket-adi`

Kısa biçimi: `pnpm up paket-adi`

Örnek: `pnpm up zod`

Tüm uygun bağımlılıkları güncellemek için `pnpm update` kullanılabilir.

Paket güncellendikten sonra proje test edilmelidir.

## pnpm ile Script Çalıştırmak
Aşağıdaki scriptlerin `package.json` içinde tanımlı olduğunu düşünelim:
```
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "lint": "eslint ."
  }
}
```

Scriptler şu şekilde çalıştırılabilir; `pnpm run dev`

Kısa kullanım; `pnpm dev`

Diğer örnekler: 
```
    pnpm build
    pnpm lint
```

Yani `pnpm run dev`ve `pnpm dev` aynı dev scriptini çalıştırır.

## pnpm-lock.yaml Dosyası
pnpm'in oluşturduğu lock dosyasının adı; `pnpm-lock.yaml`

Örnek proje yapısı:
```
proje/
├── node_modules/
├── package.json
├── pnpm-lock.yaml
└── src/
```

Temel görevi:
| Dosya            | Görevi                                              |
| ---------------- | --------------------------------------------------- |
| `package.json`   | Projenin bağımlılık ihtiyaçlarını belirtir          |
| `pnpm-lock.yaml` | pnpm’in belirlediği kesin kurulum sonucunu kaydeder |

- Elle düzenlenmemelidir.
- Git ile takip edilmelidir.
- GitHub'a gönderilmelidir.
- Paket değişiklikleriyle birlikte commit edilmelidir.

Projede `pnpm-lock.yaml` bulunması, o projenin pnpm ile yönetildiğini gösteren temel işaretlerden biridir.

## Sık Kullanılan pnpm Komutları
| Komut                   | Görevi                                  |
| ----------------------- | --------------------------------------- |
| `pnpm -v`               | pnpm sürümünü gösterir                  |
| `pnpm install`          | Projenin bağımlılıklarını yükler        |
| `pnpm add paket-adi`    | Yeni bağımlılık ekler                   |
| `pnpm add -D paket-adi` | Geliştirme bağımlılığı ekler            |
| `pnpm remove paket-adi` | Paketi kaldırır                         |
| `pnpm update`           | Paketleri günceller                     |
| `pnpm run dev`          | `dev` scriptini çalıştırır              |
| `pnpm build`            | `build` scriptini çalıştırır            |
| `pnpm store path`       | Ortak store konumunu gösterir           |
| `pnpm dlx paket-adi`    | Paket komutunu geçici olarak çalıştırır |

## pnpm Kullanırken Dikkat Edilmesi Gerekenler
- Projede pnpm-lock.yaml bulunuyorsa pnpm kullanılmalıdır.
- Aynı projede npm, Yarn ve pnpm komutları karıştırılmamalıdır.
- pnpm-lock.yaml dosyası GitHub’a gönderilmelidir.
- node_modules klasörü GitHub’a gönderilmemelidir.
- Paketi doğrudan kullanacaksak package.json içinde bağımlılık olarak tanımlamalıyız.
- pnpm’in bağlantılı node_modules yapısı elle değiştirilmemelidir.
- package.json içindeki packageManager alanı kontrol edilmelidir.
- pnpm sürümünün kullanılan Node.js ve proje sürümüyle uyumlu olması gerekir.

Aynı projede aşağıdaki lock dosyalarının birlikte bulunması package manager'ların karıştırıldığına işaret edebilir:
```
    package-lock.json
    yarn.lock
    pnpm-lock.yaml
```

Projenin yalnızca seçilen package manager'a ait lock dosyasını kullanması gerekir.

# Kısa Özet
pnpm, JavaScript projelerindeki paketleri ve bağımlılıkları yöneten bir package manager’dır.

npm ve Yarn’dan ayrılan temel özelliği, paket dosyalarını ortak bir store içinde saklayarak projeler arasında tekrar kullanmasıdır.
```
    Paket Registry
        ↓
    Ortak pnpm store
        ↓
    Projenin node_modules yapısı
```

Temel pnpm bilgileri:
Lock dosyası          → pnpm-lock.yaml
Paket yükleme         → pnpm install
Paket ekleme          → pnpm add
Geliştirme paketi     → pnpm add -D
Paket kaldırma        → pnpm remove
Paket güncelleme      → pnpm update
Script çalıştırma     → pnpm dev
Geçici komut          → pnpm dlx

Unutulmaması gereken temel cümle:

`pnpm aynı paket dosyalarını her projede yeniden saklamak yerine ortak bir store üzerinden kullanarak disk alanını daha verimli yönetir.