# Bun Nedir?
Bun, JavaScript ve TypeScript projeleri için geliştirilmiş çok amaçlı bir geliştirme aracıdır.

npm, Yarn ve pnpm yalnızca package manager olarak kullanılırken Bun daha geniş bir yapıya sahiptir.

Bun içerisinde şunlar bulunur:
| Özellik            | Görevi                                        |
| ------------------ | --------------------------------------------- |
| JavaScript runtime | JavaScript ve TypeScript kodlarını çalıştırır |
| Package manager    | Paketleri yükler ve yönetir                   |
| Script runner      | `package.json` scriptlerini çalıştırır        |
| Test runner        | Otomatik testleri çalıştırır                  |
| Bundler            | Proje dosyalarını dağıtıma hazırlar           |

En kısa tanımıyla:

`Bun; Node.js, package manager, test aracı ve bundler görevlerini tek bir sistemde birleştirmeyi amaçlayan JavaScript araç setidir.`

Bun'ın resmi belgeleri de onu Javascript ve TypeScript uygulamaları için bütünleşik bir araç seti olarak tanımlanır.

## Bun Yalnızca Package Manager Mıdır?
Hayır. Bun’ı npm, Yarn ve pnpm’den ayıran temel nokta budur.
```
    npm  → Package manager
    Yarn → Package manager
    pnpm → Package manager
    Bun  → Runtime + Package manager + Test runner + Bundler
```

Node.js bir JavaScript runtime'dır. npm ise Node.js projelerindeki paketleri yönetir.

Bun, bu iki görevi tek araçta sunabilir; `bun index.ts`

Bu komut TypeScript dosyasını çalıştırabilir.
```
    bun install
```

Bu komut ise projenin paketlerini yükler.

## Bun Package Manager
Bun’ın package manager bölümü, npm Registry’de yayımlanan paketlerle çalışabilir.

Örneğin Zod paketini Bun ile projeye ekleyebiliriz: `bun add zod``

Bun, mevcut bir package.json dosyasını okuyabilir ve bağımlılıkları proje içine yükleyebilir. Paketler genellikle node_modules klasörüne kurulur.

```
proje/
├── node_modules/
├── package.json
└── bun.lock
```

## Temel Bun Komutları
### Bun Sürümünü Kontrol Etmek
`bun --version`

### Projenin Bağımlılıklarını Yüklemek
`bun install`

Bu komut package.json içindeki bağımlılıkları yükler.

### Yeni Paket Eklemek
`bun add paket-adi`

Örnek: `bun add zod` 

Paket varsayılan olarak dependencies alanına eklenir.

### Geliştirme Bağımlılığı Eklemek
`bun add --dev paket-adi``

Kısa kullanımları; `bun add -d paket-adi` veya `bun add -D paket-adi``

Örnek: `bun add -D eslint``

Bu paket devDependencies alanına eklenir.

### Paket Kaldırmak
`bun remove paket-adi`

Örnek: `bun remove zod`

### Paket Güncellemek
`bun update`

Belirli bir paketi güncellemek için; `bun update zod`

## Bun ile Script Çalıştırmak
Aşağıdaki scriptlerin package.json içinde bulunduğunu düşünelim:
```
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "lint": "eslint ."
  }
}
```

Bun ile scriptler şu şekilde çalıştırılabilir:
```
    bun run dev
    bun run build
    bun run lint
```

Kısa kullanım da mümkündür; `bun dev`

Ancak komutun ne çalıştırdığı konusunda açıklık sağlamak için `bun run dev` kullanımı daha anlaşılırdır.

## bunx Nedir?
bunx, bir paketin komutunu projeye kalıcı bağımlılık olarak eklemeden çalıştırmayı sağlar.

Örnek: `bunx create-next-app@latest``

Temel karşılıkları şöyledir:
| Package manager | Geçici komut çalıştırma |
| --------------- | ----------------------- |
| npm             | `npx`                   |
| Yarn            | `yarn dlx`              |
| pnpm            | `pnpm dlx`              |
| Bun             | `bunx`                  |

## bun.lock Dosyası
Bun'ın güncel lock dosyasının adı: `bun.lock``

Bu dosya, Bun'ın belirlediği kesin bağımlılık sürümlerini kaydeder ve Github'a gönderilmelidir.

Eski Bun projelerinde şu dosya görülebilir: `bun.lockb`

`bun.lockb`, eski ikili lock dosyası biçiimidir. Güncel Bun sürümleri metin tabanlı bun.lock dosyasını kullanır.

| Bun sürümü/proje yapısı | Lock dosyası |
| ----------------------- | ------------ |
| Güncel Bun projeleri    | `bun.lock`   |
| Eski Bun projeleri      | `bun.lockb`  |

## Bun'ın Diğer Özellikleri
### TypeScript Çalıştırmak
Bun, TypeScript dosyalarını doğrudan çalıştırabilir: `bun run index.ts`

Aynı şekilde .tsx dosyalarını da çalıştırabilir: `bun run index.tsx`

### Test çalıştırmak
Bun kendi test aracını sunar: `bun test`

### Projeyi Derlemek
Bun'ın bundler özelliği şu komutla kullanılabilir: `bun build ./src/index.ts`

Bu özellikler Bun'ın yalnızca olmadığını gösterir.

## Bun, Node.js'in Yerine Kullanılabilir Mi?
Bun, Node.js’e alternatif bir JavaScript runtime olarak geliştirilmiştir. Birçok Node.js API’si ve npm paketiyle uyumlu çalışmayı amaçlar.

Ancak Node.js uyumluluğu devam eden bir geliştirme alanıdır. Bu nedenle Node.js için geliştirilmiş her proje Bun ile kesin olarak sorunsuz çalışacak diye düşünülmemelidir.

Burada iki farklı kullanım ayrılmalıdır:
- Bun’ı yalnızca paketleri yüklemek için kullanmak
- Uygulamayı Bun runtime üzerinde çalıştırmak

Bir proje Bun ile paketlerini yükleyebilir ancak üretim ortamında Node.js üzerinde çalışmaya devam edebilir. Runtime değiştirmek daha kapsamlı bir karardır ve projenin test edilmesini gerektirir.

## Bun Kullanırken Dikkat Edilmesi Gerekenler
- Bun yalnızca package manager değildir.
- Mevcut bir projede package manager izinsiz değiştirilmemelidir.
- bun.lock Git ile takip edilmelidir.
- node_modules GitHub’a gönderilmemelidir.
- Node.js için geliştirilmiş projelerin Bun uyumluluğu test edilmelidir.
- Projede npm, Yarn, pnpm ve Bun lock dosyaları karıştırılmamalıdır.

Lock dosyasına göre kullanılan araç anlaşılabilir:
```
    package-lock.json → npm
    yarn.lock         → Yarn
    pnpm-lock.yaml    → pnpm
    bun.lock          → Bun
```

# Kısa Özet
Bun; Javascript ve Typescript projeleri için runtime, package manager, test runner ve bundler özelliklerini bir arada sunan araçtır.

Temel komutları:
| Komut               | Görevi                           |
| ------------------- | -------------------------------- |
| `bun --version`     | Bun sürümünü gösterir            |
| `bun install`       | Projenin bağımlılıklarını yükler |
| `bun add zod`       | Yeni bağımlılık ekler            |
| `bun add -D eslint` | Geliştirme bağımlılığı ekler     |
| `bun remove zod`    | Paketi kaldırır                  |
| `bun update`        | Paketleri günceller              |
| `bun run dev`       | Proje scriptini çalıştırır       |
| `bunx paket-adi`    | Paket komutunu geçici çalıştırır |
| `bun test`          | Testleri çalıştırır              |
| `bun build`         | Dosyaları paketler               |

Unutmamamız gereken temel ayrım:
```
    npm, Yarn ve pnpm package manager'dır; Bun ise package manager özelliği de bulunan daha kapsamlı bir JavaScript ara setidir.
```