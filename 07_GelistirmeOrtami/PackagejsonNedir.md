# Package.json Dosyası Nedir?
**package.json**, Javascript ve Node.js projelerinin temel tanımlama dosyasıdır.

Projenin:
- Adını ve sürümünü
- Çalıştırabilir komutlarını
- Doğrudan bağımlılıklarını
- Kullanacağı package manager'ı
- Çalışma ortamıyla ilgili bazı bilgileri kaydeder

En temel tanımıyla:
`package.json, projenin kimlik bilgilerini, çalışma komutlarını ve paket ihtiyaçlarını tanımlayan dosyadır. `

## package.json Neden Kullanılır?
Bir JavaScript projesi React, Next.js, Zod veya TypeScript gibi farklı paketlere ihtiyaç duyabilir.

`package.json`, projenin hangi paketlere ihtiyaç duyduğunu kaydeder. Package manager da bu dosyayı okuyarak gerekli paketleri belirler.

Ayrıca projeyi çalıştırmak, geliştirmek, kontrol etmek veya üretime hazırlamak için kullanılan komutlar da bu dosyada tanımlanabilir.

Bu sayede:
- Projenin ihtiyaç duyduğu paketler takip edilir.
- Proje komutları ortak bir yerde tutulur.
- Ekip üyeleri aynı komutları kullanabilir.
- Proje başka bir bilgisayarda yeniden kurulabilir.
- Kullanılması gereken package manager belirtilebilir.

## package.json Nerede Bulunur?
`package.json` genellikle projenin ana dizininde, yani kök kalsöründe bulunur.

Örnek bir proje yapısı:
```
e-ticaret-projesi/
├── public/
├── src/
├── package.json
├── yarn.lock
├── next.config.ts
└── tsconfig.json
```

Burada `package.json`, `src` ve `public` klasörleriyle aynı ana dizinde bulunur.

## Temel Bir package.json Örneği
Bir Next.js projesinde aşağıdakine benzer bir `package.json` dosyası bulunabilir:
```
{
  "name": "e-ticaret-projesi",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "eslint ."
  },
  "dependencies": {
    "next": "^16.0.0",
    "react": "^19.0.0",
    "react-dom": "^19.0.0",
    "zod": "^4.0.0"
  },
  "devDependencies": {
    "typescript": "^5.0.0",
    "eslint": "^9.0.0"
  },
  "engines": {
    "node": ">=20"
  },
  "packageManager": "yarn@4.18.0"
}
```

Şimdi bu örnekte bulunan temel alanları inceleyelim.

### 1. name
Projenin veya paketin adını belirtir.
```
{
    "name: "e-ticaret-pojesi"
}
```

Paket adlarında genellikle:
- Küçük harf kullanılır
- Boşluk kullanılmaz
- Kelimeler kısa çizgiyle ayrılır
- Açıklayıcı bir isim tercih edilir

Uygun Örnek : `e-ticaret-projesi`
Uygun Olmayan Örnek : `E Ticaret Projesi`

### 2. version
Projenin veya paketin sürümünü belirtir.
```
{
    "version" : "1.0.0"
}
```

### 3. private
Projenin yanlışlıkla npm Registry üzerinde yayımlanmasını önlemeye yardımcı olur.
```
  {
    "private" : true
  }
```
Bu alan özellikle npm üzerinde paket olarak yayımlanması planlanmayan web uygulamalarında kullanılır.

`private: true` :
- Github reposunu private yapmaz
- Kaynak kodunu gizlemez
- Projenin erişim izinlerini değiştirmez

Yalnızca projenin yanlışlıkla paket olarak yayımlanmasını engellemeye yönelik bir ayardır.

### 4. scripts
Projede kullanılan terminal komutlarının kısa isimlerle tanımlandığı alandır.
```
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "eslint ."
  }
}
```

Bu örnekte:
| Script  | Görevi                             |
| ------- | ---------------------------------- |
| `dev`   | Geliştirme ortamını başlatır       |
| `build` | Projeyi üretim ortamına hazırlar   |
| `start` | Hazırlanmış uygulamayı çalıştırır  |
| `lint`  | Kod kalitesi kontrolünü çalıştırır |

npm kullanılıyorsa `dev`scripti şu şekilde çalıştırılır:
```
  npm run dev
```

Yarn kullanıyorsa:
```
  yarn dev
```

pnpm kullanıyorsa:
```
  pnpm dev
```

Packahe manager'lar farklı olsa da çalıştırılan `dev` komutu aynı `package.json` dosyasından okunur.

**Script Adları Zorunlu Mudur?**
`dev`, `build`, `start` ve `lint` yaygın olarak kullanılan script adlarıdır. Ancak geliştirici projeye özel scriptler de tanımlayabilir.
```
{
  "scripts": {
    "dev": "next dev",
    "typecheck": "tsc --noEmit",
    "check": "eslint . && tsc --noEmit"
  }
}
```

Bu scriptler terminalden çalıştırılabilir:
```
  npm run typecheck
  npm run check
```

Script kullanmak, uzun proje komutlarının kısa ve ortak isimlerle çalıştırılmasını sağlar.

### 5. dependencies
Uygulamaların çalışmak için ihtiyaç duyduğu doğrudan paketlerin kaydedildiği alanıdır.
```
{
  "dependencies": {
    "next": "^16.0.0",
    "react": "^19.0.0",
    "zod": "^4.0.0"
  }
}
```
Burada:
- Sol tarafta paketin adı
- Sağ tarafta sürüm bilgisi bulunur.

`Uygulamanın çalışmasıyla ilgili doğrudan bağımlılıklar bu alanda kaydedilir.`

### 6. devDependencies
Projenin geliştirilmesi ve kontrol edilmesi sırasında kullanılan paketlerin kaydedildiği alandır.

```
{
  "devDependencies": {
    "typescript": "^5.0.0",
    "eslint": "^9.0.0"
  }
}
```

Örneğin TypeScript ve EsLint geliştirme sürecinde kullanıldığı için genellikle bu alanda bulunur.

Temel ayrım:
- `dependencies`: Uygulamanın çalışmasıyla ilgili paketler
- `devDependencies`: Geliştirme ve kontrol sorasında kullanılan paketler

### 7. engines
Projenin çalışması için beklenen çalışma ortamı sürümünü belirtir.

```
{
  "engines": {
    "node": ">=20"
  }
}
```

Bu örnekte projenin Node.js 20 veya daha yeni bir sürümle çalışması beklendiği belirtilir.

engines alanı sürümü otomatik olarak yüklemez veya değiştirmez. Kullanılan araca ve proje ayarlarına göre uyarı verilmesini ya da kurulumun sınırlandırılmasını sağlayabilir.

### 8. packageManager
Projede kullanılması beklenen package manager’ı ve sürümünü belirtir.
```
{
  "packageManager": "yarn@4.18.0"
}
```

Bu kayıt:
- Projede Yarn kullanılacağını,
- Beklenen Yarn sürümünün 4.18.0 olduğunu belirtir.

Başka örnekler:
```
{
  "packageManager": "npm@11.0.0"
}

{
  "packageManager": "pnpm@10.0.0"
}
```

Bu alan özellikle ekip projelerinde herkesin aynı package manager ve sürümle çalışmasına yardımcı olur.

**`engines` ve `packageManager` farkı**
Bu iki alan benzer görünse de farklı amaçlara sahiptir:
| Alan             | Görevi                                                              |
| ---------------- | ------------------------------------------------------------------- |
| `engines`        | Projenin beklediği Node.js gibi çalışma ortamı sürümlerini belirtir |
| `packageManager` | Projede kullanılacak package manager’ı ve sürümünü belirtir         |

Birlikte kullanım örneği:
```
{
  "engines": {
    "node": ">=20"
  },
  "packageManager": "yarn@4.18.0"
}
```

Bu projede Node.js 20 veya daha yeni bir sürüm ve Yarn 4.18.0 kullanılması beklenir.

## package.json Yazım Kuralları
package.json, JSON biçiminde yazılır. Bu nedenle JSON kurallarına uygun olmalıdır.

**Anahtarlar ve metinler çift tırnakla yazılır**

Doğru:
```
{
  "name": "ornek-proje"
}
```

Yanlış:
```
{
  name: 'ornek-proje'
}
```

**Alanlar virgülle ayrılır**

Doğru:
```
{
  "name": "ornek-proje",
  "version": "1.0.0"
}
```

Yanlış:
```
{
  "name": "ornek-proje"
  "version": "1.0.0"
}
```
**Son alandan sonra virgül kullanılmaz**

Doğru:
```
{
  "name": "ornek-proje",
  "version": "1.0.0"
}
```

Yanlış:
```
{
  "name": "ornek-proje",
  "version": "1.0.0",
}
```

**Standart JSON içerisinde yorum yazılmaz**
Aşağıdaki kullanım geçersizdir:
```
{
  "name": "ornek-proje",
  // Proje sürümü
  "version": "1.0.0"
}
```

Açıklamalar için README.md gibi dokümantasyon dosyaları kullanılmalıdır.

## package.json Nasıl Oluşturulur?
npm kullanılarak yeni bir `package.json` dosyası oluşturulabilir:
```
  npm init
```

Bu komut proje hakkındaki bilgileri sırayla sorar:

Varsayılan bilgilerle hızlıca oluşturmak için aşağıdaki gibi kullanılabilir.
```
  npm init -y
```

Next.js gibi proje oluşturma araçları kullanıldığında `package.json` genellikle otomatik olarak oluşturulur.

## package.json manuel olarak düzenlenebilir mi?

Evet. package.json normal bir metin dosyasıdır ve manuel olarak düzenlenebilir.

Örneğin yeni bir script eklenebilir:
```
{
  "scripts": {
    "dev": "next dev",
    "typecheck": "tsc --noEmit"
  }
}
```

Ancak paket ekleme ve kaldırma işlemlerinin package manager komutlarıyla yapılması daha doğru olur. Çünkü package manager gerekli proje dosyalarını birlikte günceller.

Ayrıca bir paketi yalnızca package.json dosyasına yazmak, paketin dosyalarını bilgisayara indirmez. Paketlerin kurulması için package manager’ın kurulum işlemi de çalıştırılmalıdır.

## package.json GitHub’a gönderilir mi?

Evet. package.json Git ile takip edilmeli ve GitHub’a gönderilmelidir.

Çünkü bu dosya projenin:
- Paket ihtiyaçlarını,
- Scriptlerini,
- Çalışma ortamı beklentilerini,
- Package manager bilgisini taşır.

package.json sayesinde projeyi GitHub’dan indiren başka bir geliştirici, projenin ihtiyaçlarını görebilir ve gerekli paketleri yeniden kurabilir.

## İlişkili Dosyalarla Temel Farkı

package.json, lock dosyası ve node_modules aynı görevi yapmaz.
| Yapı           | Temel görevi                                   |
| -------------- | ---------------------------------------------- |
| `package.json` | Projenin ihtiyaçlarını ve komutlarını tanımlar |
| Lock dosyası   | Belirlenen paket sürümlerini kaydeder          |
| `node_modules` | Yüklenen paket dosyalarını barındırır          |

Lock dosyaları ve node_modules klasörü sonraki konularda ayrı ayrı incelenecektir.

## Kısa Özet
package.json, Javascript projesinini temel tanımlama dosyasıdır.

En önemli alanları şunlardır:
| Alan              | Görevi                                            |
| ----------------- | ------------------------------------------------- |
| `name`            | Projenin veya paketin adını belirtir              |
| `version`         | Sürüm bilgisini belirtir                          |
| `private`         | Yanlışlıkla paket olarak yayımlanmasını önler     |
| `scripts`         | Proje komutlarını tanımlar                        |
| `dependencies`    | Çalışma bağımlılıklarını kaydeder                 |
| `devDependencies` | Geliştirme bağımlılıklarını kaydeder              |
| `engines`         | Beklenen çalışma ortamını belirtir                |
| `packageManager`  | Kullanılacak package manager ve sürümünü belirtir |

Unutulmaması gereken temel cümle:

`package.json paketlerin kodlarını saklamaz; projenin ihtiyaç duyduğu paketleri, komutları ve temel çalışma bilgilerini kaydeder.`