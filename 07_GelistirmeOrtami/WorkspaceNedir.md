# Workspace Nedir?

**Workspace** üzerinde çalıştığın bir veya birden fazla kaynak, klasör ve projeyi aynı çalışma bağlamında bir araya getiren çalışma alanıdır.

"Workspace" Türkçede doğrudan **çalışma alanı** anlamına gelir.

En önemli nokta:
- Workspace, projelerini veya klasörlerini fiziksel olarak birleştirmek zorunda değildir. Asıl görevi, çalışırken ihtiyaç duyduğun kaynakları **aynı çalışma ortamında erişilebilir hale getirmektir.**

## Önce Temel Kavramları Ayıralım

Workspace'i anlamak için şu kavramları birbirinden ayırmak gerekir:
-   File
-   Folder
-   Project
-   Repository
-   Workspace
-   Working Directory
-   Context

Bunlar birbirleriyle ilişkili olabilir ama **aynı şey değildir.**

### 1.File / Dosya
En küçük seviyede gerçek dosyalar vardır.

``` 
    text
    Header.tsx
    package.json
    README.md
    theme-guide.md
    globals.css
```

Bir dosyanın içerisinde kod, yapılandırma, dokümantasyon veya başka
veriler bulunabilir.

### 2.Folder / Klasör

Dosyaları ve başka klasörleri düzenlemek için kullanılan fiziksel dosya
sistemi yapısıdır.

``` text
src/
├── components/
│   ├── Header.tsx
│   └── Footer.tsx
│
├── themes/
│   └── meridian/
│
└── app/
```

Windows'ta bunun fiziksel bir yolu olabilir: `C:\Users\Kullanici\Projects\ecommerce`. Buradaki `ecommerce`, bilgisayarındaki gerçek bir klasördür.

### 3.Project / Proje

**Project**, belirli bir amaç için geliştirdiğin yazılım bütünüdür. Örneğin `TravelMind AI`, `Portfolio`, `E-Commerce Store` birer proje olabilir.

Bir proje çoğu zaman bir klasörün içinde tutulur, ama kavramsal olarak ikisi aynı şey değildir:
 
```text
Folder  → Dosyaların fiziksel organizasyonu
Project → Geliştirdiğin yazılım/ürün
```

### 4.Repository / Repo

Repository, Git gibi bir versiyon kontrol sistemi tarafından takip
edilen kod tabanıdır.

``` text
ecommerce-store/
├── .git/
├── src/
├── docs/
├── package.json
└── README.md
```

Buradaki `.git` dizini, bu klasörün Git repository olarak yönetildiğini gösterir. Repository sayesinde `Değişiklik → Commit → Branch → Merge → Push / Pull` gibi işlemler yapılabilir.

**Project ile repository de birebir aynı kavram değildir.** Bir proje tek repository olabilir, ama büyük bir sistem birden fazla repository'den de oluşabilir:
 
```text
E-Commerce Sistemi
├── Store Repository
├── Admin Repository
└── Backend Repository
```

## Workspace Nedir?

Şimdi asıl kavrama gelelim. Diyelim ki bir e-ticaret sistemi üzerinde çalışıyorsun ve üç ayrı kod tabanın var: `ecommerce-store`, `ecommerce-admin`, `ecommerce-api`. Bunların her biri ayrı repository olabilir. Ancak yaptığın iş açısından üçünün de aynı sistemle ilişkisi vardır.
 
Bu durumda mantıksal bir çalışma alanı oluşturabilirsin:

``` text
┌──────────────────────────────────┐
│       E-COMMERCE WORKSPACE       │
│                                  │
│   ┌─────────┐   ┌─────────┐      │
│   │  STORE  │   │  ADMIN  │      │
│   └─────────┘   └─────────┘      │
│                                  │
│          ┌─────────┐             │
│          │   API   │             │
│          └─────────┘             │
└──────────────────────────────────┘
```

Burada:
- Store hâlâ ayrı proje olabilir.
- Admin hâlâ ayrı proje olabilir.
- API hâlâ ayrı repository olabilir.
- Git geçmişleri hâlâ birbirinden bağımsız olabilir.

Workspace sadece bunları **aynı çalışma ortamında erişilebilir hale
getirir.**

## Gerçek Hayat Benzetmesi

Workspace'i bir **çalışma masası** olarak düşün. Dolabında şu klasörler var: `Store`, `Admin`, `Backend`, `Portfolio`.
 
Bugün e-ticaret üzerinde çalışacaksın, masanın üzerine sadece ihtiyacın olanları koyuyorsun:

``` text
┌──────────────────────────────────┐
│          ÇALIŞMA MASASI          │
│                                  │
│   📁 Store      📁 Admin         │
│                                  │
│          📁 Backend              │
│                                  │
└──────────────────────────────────┘
```

`Portfolio` dolapta kalıyor çünkü şu an ihtiyacın yok.

Burada:

``` text
Çalışma masası = Workspace

Masanın üzerindeki klasörler = Workspace'e dahil ettiğin projeler/kaynaklar
```

Klasörleri aynı masaya koyman onları birbirine yapıştırmaz. **Workspace de tam olarak bunu yapar.**

## Workspace Fiziksel Bir Klasör Olmak Zorunda mı?

**Hayır.** Bu en önemli workspace özelliklerinden biridir.

Örneğin bilgisayarındaki klasörler fiziksel olarak üç farklı yerde bulunabilir:

``` text
C:\Projects\ecommerce-store

C:\Company\ecommerce-admin

D:\Documentation\ecommerce-docs
```

Bir araç bunları aynı workspace'e dahil ederek sana tek bir liste gibi gösterebilir:

``` text
E-Commerce Workspace
│
├── ecommerce-store
├── ecommerce-admin
└── ecommerce-docs
```

- **Workspace fiziksel konumdan çok mantıksal çalışma kapsamını ifade eder.**

## Workspace Birleştirme İşlemi Değildir
Diyelim ki `WORKSPACE` içine `Project-A` ve `Project-B`'yi ekledin. Bu şu anlama gelmez:

``` text
Project-A/
└── Project-B/
```

Workspace'e klasör eklemek:
- Dosyaları taşımaz veya kopyalamaz.
- Repository'leri, branch'leri veya Git geçmişlerini birleştirmez.
- Kodları otomatik aktarmaz.

Sadece **çalışma alanına dahil eder.**

Bu, VS Code gibi araçlarda oluşturduğun `.code-workspace` dosyası için de geçerlidir: bu dosya projelerin kendisini içermez, sadece hangi klasörlerin çalışma alanına dahil edileceğine dair bir referans listesi tutar — örneğin:
  
```json
{
  "folders": [
    { "path": "C:\\Projects\\ecommerce-store" },
    { "path": "C:\\Projects\\ecommerce-admin" }
  ]
}
```

## Single-Folder ve Multi-Root Workspace

Workspace tek klasörden de oluşabilir:
 
```text
WORKSPACE
└── ecommerce-store
    ├── src
    ├── docs
    ├── public
    └── package.json
```
 
Tek proje üzerinde çalışıyorsan çoğu zaman bu yeterlidir.
 
**Multi-root workspace** ise birden fazla bağımsız klasörün aynı çalışma alanında bulunmasıdır:
 
```text
WORKSPACE
│
├── ecommerce-store
│   ├── src
│   └── package.json
│
├── ecommerce-admin
│   ├── src
│   └── package.json
│
└── ecommerce-docs
    └── theme-guide.md
```
 
Bu yapı özellikle ilişkili birden fazla proje, frontend + backend, store + admin, eski proje + yeni proje, kod + dokümantasyon gibi durumlarda faydalıdır.

## Workspace ile Git Repository Arasındaki Fark

Diyelim ki workspace içerisinde iki repository var:

``` text
WORKSPACE
│
├── Store
│   ├── .git/
│   └── branch: tema/meridian
│
└── Admin
    ├── .git/
    └── branch: main
```

İkisi aynı workspace'te olsa bile `Store Git Repository ≠ Admin Git Repository`'dir. Store üzerinde çalıştırılan `git status`, yalnızca Store repository'sinin durumunu gösterir; Admin'in branch'i veya commit geçmişi bundan bağımsızdır.

- **Kural:** Workspace Git sınırlarını ortadan kaldırmaz.

## Workspace ile Monorepo Aynı Şey Değildir

Bir monorepo'da Store, Admin, UI ve Themes **aynı repository** içindedir:

``` text
ecommerce/
├── .git/
│
├── apps/
│   ├── store/
│   └── admin/
│
├── packages/
│   ├── ui/
│   └── themes/
│
└── package.json
```

Workspace ise üç ayrı repository'yi aynı çalışma alanında bir araya getirebilir:

``` text
WORKSPACE
├── store.git
├── admin.git
└── backend.git
```

Dolayısıyla: `Monorepo ≠ Workspace`, `Repository ≠ Workspace`, `Project ≠ Workspace`.

## Workspace ile Working Directory Farkı

Terminal açtığında terminalin o anda bulunduğu bir dizin vardır:

``` powershell
PS C:\Projects\ecommerce-store>
```

Bu, terminalin **working directory**'sidir. Ama workspace'in şöyle olabilir:

```text
WORKSPACE
├── ecommerce-store
├── ecommerce-admin
└── ecommerce-api
```

Terminal o anda yalnızca `ecommerce-store` içinde olabilir:
 
```text
Workspace          → Geniş çalışma alanı
Working Directory  → Terminalin şu anda bulunduğu dizin
```
 
**Neden önemli?** `npm run dev` gibi bir komut çalıştırdığında, hangi projenin çalışacağını büyük ölçüde terminalin bulunduğu dizin belirler.

## Workspace ile AI Context Aynı Şey Değildir

AI destekli kodlama araçlarında bu ayrım çok önemlidir. Workspace içinde 500 farklı dosya olması, AI'ın her cevapta bu 500 dosyanın tamamını aynı anda aktif olarak kullandığı anlamına gelmez.

```text
Workspace → AI aracının erişmesine izin verilen çalışma kapsamı.
            "Erişebileceğin alan burası."
 
Context   → AI'ın belirli bir görev sırasında gerçekten okuduğu,
            seçtiği veya modele sağlanan bilgiler bütünü.
            "Bu görev için şu anda kullandığın bilgi."
```
 
Örneğin:
 
```text
WORKSPACE
├── 500 dosya
│
└── CONTEXT
    ├── docs/theme-guide.md
    ├── themes/meridian/index.ts
    └── themes/meridian/theme.ts
```
 
**Kısa formül:** `Workspace = erişilebilir çalışma alanı`, `Context = o anda kullanılan bilgi`. **Workspace ≠ Context.**

## Workspace Farklı Araçlarda Farklı Anlamlara Gelebilir

"Workspace" genel bir yazılım kavramıdır ama her araç bunu kendi özelliklerine göre uygular.
 
**Kod editörü / IDE'de** workspace; projeleri, editör ayarlarını ve çalışma alanına özel yapılandırmaları kapsayabilir.
 
**AI kodlama aracında** workspace daha çok "AI'ın çalışabileceği kod alanı" anlamına yaklaşır. Ancak önemli bir ayrıntı var:
 
- Bir klasörün editörde workspace içinde görünmesi, kullandığın her AI aracının o klasöre otomatik olarak erişebileceği anlamına gelmez.
 
AI aracının izin sistemi, başlangıç dizini, güvenlik sınırları ve eklenen klasörleri algılama biçimi ayrıca kontrol edilmelidir.

## "Add Folder to Workspace" Ne Demektir?

**Add Folder to Workspace = Bir klasörü mevcut çalışma alanıma dahil et.**
 
Örneğin başlangıçta `WORKSPACE └── Store` varken, `Admin` klasörünü workspace'e eklersen sonuç şu olur:

```text
WORKSPACE
├── Store
└── Admin
```

Ama `Store └── Admin` şeklinde iç içe geçmiş bir yapı **olmaz.**

## VS Code Üzerinden Pratik Örnek
 
VS Code bu genel workspace mantığını **Multi-root Workspace** özelliğiyle uygular:
 
```text
File → Open Folder → Project-A
File → Add Folder to Workspace... → Project-B
```
 
Sonuç:
 
```text
WORKSPACE
├── Project-A
└── Project-B
```
 
Bu yapıyı daha sonra tekrar kullanmak istersen `File → Save Workspace As...` ile örneğin `ecommerce.code-workspace` dosyası oluşturabilirsin. Bu dosya, projelerin kendisini değil, "bu workspace açıldığında şu klasörleri çalışma alanına dahil et" bilgisini saklar.

## Ne Zaman Workspace Kullanmalıyım?
 
| Durum | Önerilen yapı |
|---|---|
| Tek proje üzerinde çalışıyorsan | `WORKSPACE └── Project` yeterlidir; gereksiz klasör eklemek işi karmaşıklaştırır. |
| Frontend + backend birlikte | `Fullstack Workspace ├── frontend └── backend` |
| Store + Admin birlikte inceleniyorsa | `E-Commerce Workspace ├── store └── admin` |
| Eski ve yeni kod karşılaştırılıyorsa | `Migration Workspace ├── old-project └── new-project` |
| Kod ve dokümantasyon ayrı klasörlerdeyse | `Theme Workspace ├── application └── documentation` |

## Örnek: Migration Workspace
 
Yeni yapı ile eski yapıyı karşılaştırmak istediğini düşün:
 
```text
MIGRATION WORKSPACE
│
├── NEW PROJECT
│   ├── docs/
│   │   └── new-theme-package-guide.md
│   ├── src/
│   └── themes/
│
└── OLD / REFERENCE PROJECT
    ├── src/
    └── themes/
```
 
Bu çalışma alanında şu tür bir akış izlenebilir:
 
```text
1. Yeni rehberi incele  →  2. Yeni yapıyı incele  →  3. Eski yapıyı incele
       →  4. İki yapıyı karşılaştır  →  5. Uyumsuzlukları çıkar
       →  6. Migration planı oluştur  →  7. Onaydan sonra implementasyon yap
```
 
Workspace burada araştırma ve karşılaştırmayı kolaylaştırır. Ancak yine: workspace'in iki klasörü içermesi, kullandığın AI aracının ikisine de otomatik olarak eriştiğini garanti etmez — AI aracının kendi erişim kapsamını ayrıca kontrol etmek gerekir.
 
## Workspace Kullanırken Dikkat Edilecekler
 
1. **Hangi projede işlem yaptığını bil.** Aynı isimli dosyalar olabilir (`Store/src/Header.tsx` vs `Admin/src/Header.tsx`) — yanlış projedeki dosyayı düzenlememeye dikkat et.
2. **Terminal konumunu kontrol et.** `C:\Projects\store>` ile `C:\Projects\admin>` aynı değildir; `npm install`, `npm run dev`, `git status` gibi komutlardan önce bulunduğun dizini kontrol et.
3. **Git repository sınırlarını unutma.** Aynı workspace'te olmaları, aynı Git repository oldukları anlamına gelmez — her repository'nin kendi branch ve commit geçmişi olabilir.
4. **Workspace'e gereksiz klasör ekleme.** Sadece Store üzerinde çalışıyorsan `Store, Admin, Backend, Portfolio, TravelMind, Random Tests` gibi ilgisiz projeleri aynı workspace'e doldurmak gerekli değildir.
5. **AI kullanıyorsan erişim sınırlarını kontrol et.** "Editörde görüyorum" demek "AI kesin erişebiliyor" demek değildir; kullandığın AI aracının workspace ve klasör erişim sistemini ayrıca kontrol et.
## Hızlı Karşılaştırma Tablosu
 
| Kavram | Ne demek? | Örnek |
|---|---|---|
| **File** | Gerçek dosya | `Header.tsx` |
| **Folder** | Dosyaları düzenleyen klasör | `src/components/` |
| **Project** | Geliştirdiğin yazılım/ürün | E-Commerce Store |
| **Repository** | Git tarafından takip edilen kod tabanı | `ecommerce-store.git` |
| **Workspace** | Bir veya daha fazla kaynağı aynı çalışma ortamında tutan alan | Store + Admin + Docs |
| **Working Directory** | Terminalin şu anda bulunduğu dizin | `C:\Projects\store` |
| **Context** | AI'ın o anda kullandığı bilgi | `theme-guide.md` + Meridian dosyaları |
| **Monorepo** | Birden fazla uygulama/paketin tek repository içinde yönetilmesi | `apps/store`, `apps/admin`, `packages/ui` |
 
## Sık Yapılan Yanlış Varsayımlar
 
- ❌ **"Workspace bir klasördür."** Her zaman değil — fiziksel klasörlerden oluşabilir ama kendisi mantıksal bir çalışma alanı da olabilir.
- ❌ **"İki projeyi workspace'e eklersem birleşir."** Hayır, projeler bağımsız kalabilir.
- ❌ **"Aynı workspace'teki projelerin Git branch'i aynıdır."** Hayır, her repository'nin kendi branch ve commit geçmişi olabilir.
- ❌ **"Workspace'teki her dosya AI'ın context'indedir."** Hayır, workspace erişilebilir alanı, context ise o anda kullanılan bilgiyi ifade eder.
- ❌ **"Terminal workspace'in tamamında çalışır."** Terminal belirli bir working directory içinde çalışır.
- ❌ **"Workspace monorepo demektir."** Hayır, workspace birden fazla bağımsız repository de içerebilir.
## Özet
 
Kavramların büyük resmi şöyle düşünülebilir (birebir her projede bu şekilde olmak zorunda değil, ilişkiyi anlamak için düşünsel bir model):
 
```text
                   WORKSPACE
                      │
          ┌───────────┼───────────┐
          │           │           │
        Store       Admin        Docs
          │           │           │
       ayrı repo    ayrı repo    kaynak
```
 
Zihinde tutulması gereken formüller:
 
```text
PROJECT            = geliştirdiğin şey
FOLDER             = dosyaların bulunduğu fiziksel yapı
REPOSITORY         = Git'in takip ettiği kod tabanı
WORKSPACE          = üzerinde birlikte çalışmak istediğin kaynakların çalışma alanı
WORKING DIRECTORY  = terminalin şu anda bulunduğu klasör
CONTEXT            = AI'ın o anda kullandığı bilgi
```
 
Workspace bu parçaların üzerinde **birlikte çalışmanı kolaylaştırır**, fakat onların teknik sınırlarını otomatik olarak ortadan kaldırmaz:
 
- **Workspace yeni bir proje oluşturmak veya projeleri birleştirmek değildir. Çalışırken ihtiyaç duyduğun bir veya birden fazla kaynağı aynı çalışma ortamında yönetmenin yoludur.**
 
**Ama workspace şunlar değildir:** proje birleştirme, Git merge, dosya taşıma, monorepo, terminal working directory, AI context.
 
### Mini Kontrol Listesi
 
Bir workspace oluşturmadan önce kendine şunları sor:
- Aynı görev için birden fazla proje veya klasöre ihtiyacım var mı?
- Bu klasörler birbiriyle ilişkili mi, ayrı Git repository mi?
- Terminalde hangi proje içinde çalıştığımı biliyor muyum?
- AI aracı kullanıyorsam hangi klasörlere gerçekten erişebildiğini biliyor muyum?
- Eski ve yeni kodu karşılaştırmam gerekiyor mu? Dokümantasyon başka bir klasörde mi?
Birden fazla sorunun cevabı **evet** ise multi-root / çok klasörlü bir workspace kullanmak faydalı olabilir. Bu ayrımları bildiğinde VS Code, Cursor, Claude Code ve diğer geliştirme araçlarında kullanılan "workspace" ifadelerini çok daha kolay yorumlayabilirsin.