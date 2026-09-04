# Workspace Nedir? Sıfırdan Detaylı Rehber

> **Amaç:** Bu rehber, "workspace" kavramını daha önce hiç kullanmamış
> biri için sıfırdan açıklar.\
> Workspace'in klasör, proje, repository, working directory ve AI
> context kavramlarından farkını; birden fazla projeyi aynı çalışma
> alanında nasıl tutabileceğini ve hangi durumlarda kullanmanın mantıklı
> olduğunu anlatır.

------------------------------------------------------------------------

## 1. Workspace'i Tek Cümlede Anlayalım

**Workspace = üzerinde çalıştığın bir veya birden fazla kaynak, klasör
ve projeyi aynı çalışma bağlamında bir araya getiren çalışma alanıdır.**

"Workspace" Türkçede doğrudan **çalışma alanı** anlamına gelir.

En önemli nokta:

> Workspace, projelerini veya klasörlerini fiziksel olarak birleştirmek
> zorunda değildir.\
> Asıl görevi, çalışırken ihtiyaç duyduğun kaynakları **aynı çalışma
> ortamında erişilebilir hale getirmektir.**

------------------------------------------------------------------------

# 2. Önce Temel Kavramları Ayıralım

Workspace'i anlamak için şu kavramları birbirinden ayırmak gerekir:

-   File
-   Folder
-   Project
-   Repository
-   Workspace
-   Working Directory
-   Context

Bunlar birbirleriyle ilişkili olabilir ama **aynı şey değildir.**

------------------------------------------------------------------------

## 2.1 File --- Dosya

En küçük seviyede gerçek dosyalar vardır.

Örneğin:

``` text
Header.tsx
package.json
README.md
theme-guide.md
globals.css
```

Bir dosyanın içerisinde kod, yapılandırma, dokümantasyon veya başka
veriler bulunabilir.

------------------------------------------------------------------------

## 2.2 Folder --- Klasör

Dosyaları ve başka klasörleri düzenlemek için kullanılan fiziksel dosya
sistemi yapısıdır.

Örneğin:

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

Windows'ta bunun fiziksel bir yolu olabilir:

``` text
C:\Users\Kullanici\Projects\ecommerce
```

Buradaki `ecommerce`, bilgisayarındaki gerçek bir klasördür.

------------------------------------------------------------------------

## 2.3 Project --- Proje

**Project**, belirli bir amaç için geliştirdiğin yazılım bütünüdür.

Örneğin:

``` text
TravelMind AI
Portfolio
E-Commerce Store
E-Commerce Admin
```

birer proje olabilir.

Bir proje çoğu zaman bir klasörün içinde tutulur:

``` text
ecommerce-store/
├── src/
├── public/
├── docs/
├── package.json
└── README.md
```

Ancak kavramsal olarak:

``` text
Folder  → Dosyaların fiziksel organizasyonu
Project → Geliştirdiğin yazılım/ürün
```

şeklinde düşünmek daha doğrudur.

------------------------------------------------------------------------

## 2.4 Repository --- Repo

Repository, Git gibi bir versiyon kontrol sistemi tarafından takip
edilen kod tabanıdır.

Örneğin:

``` text
ecommerce-store/
├── .git/
├── src/
├── docs/
├── package.json
└── README.md
```

Buradaki `.git` dizini, bu klasörün Git repository olarak yönetildiğini
gösterir.

Repository sayesinde:

``` text
Değişiklik
    ↓
Commit
    ↓
Branch
    ↓
Merge
    ↓
Push / Pull
```

gibi işlemler yapılabilir.

### Önemli

**Project ile repository de birebir aynı kavram değildir.**

Bir proje tek repository olabilir.

Ama büyük bir sistem:

``` text
E-Commerce Sistemi
├── Store Repository
├── Admin Repository
└── Backend Repository
```

şeklinde birden fazla repository'den de oluşabilir.

------------------------------------------------------------------------

# 3. Workspace Nedir?

Şimdi asıl kavrama gelelim.

Diyelim ki bir e-ticaret sistemi üzerinde çalışıyorsun ve üç ayrı kod
tabanın var:

``` text
ecommerce-store
ecommerce-admin
ecommerce-api
```

Bunların her biri ayrı repository olabilir.

Ancak yaptığın iş açısından üçünün de aynı sistemle ilişkisi vardır.

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

-   Store hâlâ ayrı proje olabilir.
-   Admin hâlâ ayrı proje olabilir.
-   API hâlâ ayrı repository olabilir.
-   Git geçmişleri hâlâ birbirinden bağımsız olabilir.

Workspace sadece bunları **aynı çalışma ortamında erişilebilir hale
getirir.**

------------------------------------------------------------------------

# 4. Gerçek Hayat Benzetmesi

Workspace'i bir **çalışma masası** olarak düşün.

Dolabında şu klasörler var:

``` text
📁 Store
📁 Admin
📁 Backend
📁 Portfolio
```

Bugün e-ticaret üzerinde çalışacaksın.

Masanın üzerine şunları koyuyorsun:

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

Masanın üzerindeki klasörler
= Workspace'e dahil ettiğin projeler/kaynaklar
```

Klasörleri aynı masaya koyman onları birbirine yapıştırmaz.

**Workspace de tam olarak bunu yapar.**

------------------------------------------------------------------------

# 5. Workspace Fiziksel Bir Klasör Olmak Zorunda mı?

**Hayır.**

Bu en önemli workspace özelliklerinden biridir.

Örneğin bilgisayarındaki klasörler şöyle olabilir:

``` text
C:\Projects\ecommerce-store

C:\Company\ecommerce-admin

D:\Documentation\ecommerce-docs
```

Fiziksel olarak üç farklı yerde bulunuyorlar.

Bir araç bunları aynı workspace'e dahil ederek sana şöyle gösterebilir:

``` text
E-Commerce Workspace
│
├── ecommerce-store
├── ecommerce-admin
└── ecommerce-docs
```

Yani:

> **Workspace fiziksel konumdan çok mantıksal çalışma kapsamını ifade
> eder.**

------------------------------------------------------------------------

# 6. Workspace Birleştirme İşlemi Değildir

Bu konu özellikle önemlidir.

Diyelim ki:

``` text
WORKSPACE
├── Project-A
└── Project-B
```

oluşturdun.

Bu şu anlama **gelmez:**

``` text
Project-A/
└── Project-B/
```

Aynı şekilde:

``` text
Project-A'daki kod
        +
Project-B'deki kod
        ↓
tek proje
```

şeklinde bir işlem gerçekleşmez.

Workspace'e klasör eklemek:

-   Dosyaları taşımaz.
-   Dosyaları kopyalamaz.
-   Repository'leri birleştirmez.
-   Branch'leri birleştirmez.
-   Git geçmişlerini birleştirmez.
-   Kodları otomatik aktarmaz.

Sadece **çalışma alanına dahil eder.**

------------------------------------------------------------------------

# 7. Single-Folder ve Multi-Root Workspace

Workspace tek klasörden de oluşabilir.

## Single-Folder Workspace

``` text
WORKSPACE
└── ecommerce-store
    ├── src
    ├── docs
    ├── public
    └── package.json
```

Tek proje üzerinde çalışıyorsan çoğu zaman bu yeterlidir.

------------------------------------------------------------------------

## Multi-Root Workspace

Birden fazla bağımsız klasörün aynı çalışma alanında bulunmasıdır.

``` text
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

Bu yapı özellikle:

-   ilişkili birden fazla proje,
-   frontend + backend,
-   store + admin,
-   eski proje + yeni proje,
-   kod + dokümantasyon

gibi durumlarda faydalıdır.

------------------------------------------------------------------------

# 8. Workspace ile Git Repository Arasındaki Fark

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

İkisi aynı workspace'te olsa bile:

``` text
Store Git Repository ≠ Admin Git Repository
```

Store üzerinde yapılan:

``` bash
git status
```

işlemi Store repository'sinin durumunu gösterir.

Admin'in branch'i veya commit geçmişi bundan bağımsızdır.

### Kural

> **Workspace Git sınırlarını ortadan kaldırmaz.**

------------------------------------------------------------------------

# 9. Workspace ile Monorepo Aynı Şey Değildir

Bir monorepo şöyle olabilir:

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

Burada Store, Admin, UI ve Themes **aynı repository** içerisindedir.

Bu bir **monorepo** örneğidir.

Workspace ise şöyle de olabilir:

``` text
WORKSPACE
├── store.git
├── admin.git
└── backend.git
```

Burada üç ayrı repository aynı workspace içerisinde bulunabilir.

Dolayısıyla:

``` text
Monorepo  ≠ Workspace
Repository ≠ Workspace
Project    ≠ Workspace
```

------------------------------------------------------------------------

# 10. Workspace ile Working Directory Farkı

Terminal açtığında terminalin o anda bulunduğu bir dizin vardır.

Örneğin:

``` powershell
PS C:\Projects\ecommerce-store>
```

Buradaki:

``` text
C:\Projects\ecommerce-store
```

terminalin **working directory**'sidir.

Ama workspace'in şöyle olabilir:

``` text
WORKSPACE
├── ecommerce-store
├── ecommerce-admin
└── ecommerce-api
```

Terminal o anda yalnızca:

``` text
ecommerce-store
```

içerisinde olabilir.

Dolayısıyla:

``` text
Workspace
   ↓
Geniş çalışma alanı

Working Directory
   ↓
Terminalin şu anda bulunduğu dizin
```

### Neden önemli?

Şu komutu çalıştırdığında:

``` bash
npm run dev
```

hangi projenin çalışacağını büyük ölçüde terminalin bulunduğu dizin
belirler.

------------------------------------------------------------------------

# 11. Workspace ile AI Context Aynı Şey Değildir

AI destekli kodlama araçlarında bu ayrım çok önemlidir.

Diyelim workspace içerisinde:

``` text
WORKSPACE
├── src/
├── docs/
├── tests/
├── public/
└── 500 farklı dosya
```

bulunuyor.

Bu, AI'ın her cevapta 500 dosyanın tamamını aynı anda aktif olarak
kullandığı anlamına gelmez.

## Workspace

AI aracının erişmesine izin verilen çalışma kapsamı olabilir.

``` text
WORKSPACE
        ↓
"Erişebileceğin alan burası."
```

## Context

AI'ın belirli bir görev sırasında gerçekten okuduğu, seçtiği veya modele
sağlanan bilgiler bütünüdür.

``` text
CONTEXT
       ↓
"Bu görev için şu anda kullandığın bilgi."
```

Örneğin:

``` text
WORKSPACE
├── 500 dosya
│
└── CONTEXT
    ├── docs/theme-guide.md
    ├── themes/meridian/index.ts
    └── themes/meridian/theme.ts
```

### Kısa formül

``` text
Workspace = erişilebilir çalışma alanı
Context   = o anda kullanılan bilgi
```

> **Workspace ≠ Context**

------------------------------------------------------------------------

# 12. Workspace Farklı Araçlarda Farklı Anlamlara Gelebilir

"Workspace" genel bir yazılım kavramıdır ancak her araç bunu kendi
özelliklerine göre uygular.

## Kod editörü / IDE

Workspace şunları kapsayabilir:

``` text
Workspace
├── Project A
├── Project B
├── editör ayarları
└── çalışma alanına özel yapılandırmalar
```

------------------------------------------------------------------------

## AI kodlama aracı

Workspace daha çok:

``` text
AI'ın çalışabileceği kod alanı
```

anlamına yaklaşabilir.

Ancak önemli bir ayrıntı vardır:

> Bir klasörün editörde workspace içerisinde görünmesi, kullandığın her
> AI aracının o klasöre otomatik olarak erişebileceği anlamına gelmez.

AI aracının:

-   izin sistemi,
-   başlangıç dizini,
-   güvenlik sınırları,
-   eklenen klasörleri algılama biçimi

ayrıca kontrol edilmelidir.

------------------------------------------------------------------------

# 13. "Add Folder to Workspace" Ne Demektir?

Artık genel kavramı bildiğimize göre bu ifade çok daha kolaydır:

> **Add Folder to Workspace = Bir klasörü mevcut çalışma alanıma dahil
> et.**

Örneğin başlangıçta:

``` text
WORKSPACE
└── Store
```

var.

`Admin` klasörünü workspace'e eklersen:

``` text
WORKSPACE
├── Store
└── Admin
```

olur.

Ama:

``` text
Store
└── Admin
```

olmaz.

------------------------------------------------------------------------

# 14. Aynı Workspace'te Birden Fazla Proje Nasıl Tutulur?

Genel mantık şöyledir:

### Başlangıç

``` text
WORKSPACE
└── Project-A
```

### İkinci klasörü dahil et

``` text
+ Project-B
```

### Sonuç

``` text
WORKSPACE
├── Project-A
└── Project-B
```

Araç multi-root workspace destekliyorsa bu iki klasörü aynı çalışma
ortamında gösterebilir.

------------------------------------------------------------------------

# 15. VS Code Üzerinden Pratik Örnek

VS Code bu genel workspace mantığını **Multi-root Workspace**
özelliğiyle uygular.

Önce ana klasörü açabilirsin:

``` text
File
→ Open Folder
→ Project-A
```

Daha sonra:

``` text
File
→ Add Folder to Workspace...
→ Project-B
```

Sonuç:

``` text
WORKSPACE
├── Project-A
└── Project-B
```

Workspace yapısını daha sonra tekrar kullanmak istiyorsan:

``` text
File
→ Save Workspace As...
```

ile örneğin:

``` text
ecommerce.code-workspace
```

dosyası oluşturabilirsin.

Bu dosya projelerinin kendisini içermez.

Temel olarak:

> "Bu workspace açıldığında şu klasörleri çalışma alanına dahil et."

bilgisini saklar.

------------------------------------------------------------------------

# 16. Workspace Dosyası Projeleri Kopyalamaz

Örneğin:

``` text
ecommerce.code-workspace
```

oluşturdun.

Bu dosyanın içinde bütün Store ve Admin kodlarının kopyası bulunmaz.

Mantıksal olarak buna benzer referanslar tutulabilir:

``` json
{
  "folders": [
    {
      "path": "C:\\Projects\\ecommerce-store"
    },
    {
      "path": "C:\\Projects\\ecommerce-admin"
    }
  ]
}
```

Yani workspace dosyası bir çeşit:

``` text
Çalışma alanı tanımı
```

olarak düşünülebilir.

------------------------------------------------------------------------

# 17. Ne Zaman Workspace Kullanmalıyım?

## Tek projede çalışıyorsan

Çoğu zaman:

``` text
WORKSPACE
└── Project
```

yeterlidir.

Gereksiz yere başka klasörleri eklemek çalışma alanını
karmaşıklaştırabilir.

------------------------------------------------------------------------

## Frontend + Backend üzerinde birlikte çalışıyorsan

``` text
Fullstack Workspace
├── frontend
└── backend
```

mantıklıdır.

------------------------------------------------------------------------

## Store + Admin birlikte incelenecekse

``` text
E-Commerce Workspace
├── store
└── admin
```

mantıklıdır.

------------------------------------------------------------------------

## Eski ve yeni kodu karşılaştırıyorsan

``` text
Migration Workspace
├── old-project
└── new-project
```

çok kullanışlı olabilir.

------------------------------------------------------------------------

## Kod ve dokümantasyon farklı klasörlerdeyse

``` text
Theme Workspace
├── application
└── documentation
```

kullanılabilir.

------------------------------------------------------------------------

# 18. Meridian Gibi Bir Migration İşinde Örnek

Örneğin yeni yapı ile eski yapıyı karşılaştırmak istediğini düşün.

``` text
MERIDIAN MIGRATION WORKSPACE
│
├── NEW PROJECT
│   ├── docs/
│   │   └── new-theme-package-guide.md
│   │
│   ├── src/
│   └── themes/
│
└── OLD / REFERENCE PROJECT
    ├── src/
    └── themes/
        └── meridian/
```

Bu çalışma alanında şu tür bir görev yürütülebilir:

``` text
1. Yeni theme package rehberini incele
             ↓
2. Main'den gelen yeni yapıyı incele
             ↓
3. Meridian'ın mevcut yapısını incele
             ↓
4. İki yapıyı karşılaştır
             ↓
5. Uyumsuzlukları çıkar
             ↓
6. Migration planı oluştur
             ↓
7. Onaydan sonra implementasyon yap
```

Workspace burada araştırma ve karşılaştırmayı kolaylaştırır.

Ancak yine:

> Workspace'in iki klasörü içermesi, kullandığın AI aracının ikisine de
> otomatik olarak eriştiğini garanti etmez. AI aracının kendi erişim
> kapsamını ayrıca kontrol etmek gerekir.

------------------------------------------------------------------------

# 19. Workspace Kullanırken Dikkat Edilecekler

## 1 --- Hangi projede işlem yaptığını bil

Aynı isimli dosyalar olabilir:

``` text
Store/src/Header.tsx
Admin/src/Header.tsx
```

Yanlış projedeki dosyayı düzenlememeye dikkat et.

------------------------------------------------------------------------

## 2 --- Terminal konumunu kontrol et

Örneğin:

``` powershell
PS C:\Projects\store>
```

ile:

``` powershell
PS C:\Projects\admin>
```

aynı değildir.

`npm install`, `npm run dev`, `git status` gibi komutlardan önce
bulunduğun dizini kontrol et.

------------------------------------------------------------------------

## 3 --- Git repository sınırlarını unutma

Aynı workspace'te olmaları aynı Git repository oldukları anlamına
gelmez.

``` text
Workspace
├── Repo A
└── Repo B
```

iki ayrı Git geçmişi olabilir.

------------------------------------------------------------------------

## 4 --- Workspace'e gereksiz klasör ekleme

Çalıştığın görev için gerekli alanları eklemek daha düzenlidir.

Örneğin sadece Store üzerinde çalışıyorsan:

``` text
Store
Admin
Backend
Portfolio
TravelMind
Random Tests
```

gibi ilgisiz projeleri aynı workspace'e doldurmak gerekli değildir.

------------------------------------------------------------------------

## 5 --- AI kullanıyorsan erişim sınırlarını kontrol et

Şunu varsayma:

``` text
Editörde görüyorum
       ↓
AI kesin erişebiliyor
```

Bunun yerine kullandığın AI aracının workspace ve klasör erişim
sistemini ayrıca kontrol et.

------------------------------------------------------------------------

# 20. Kavramların Büyük Resmi

``` text
┌───────────────────────────────────────────────┐
│                  WORKSPACE                    │
│                                               │
│  ┌─────────────────────────────────────────┐  │
│  │          PROJECT / REPOSITORY           │  │
│  │                                         │  │
│  │   ┌───────────────┐                     │  │
│  │   │    FOLDER     │                     │  │
│  │   │               │                     │  │
│  │   │   ┌──────┐    │                     │  │
│  │   │   │ FILE │    │                     │  │
│  │   │   └──────┘    │                     │  │
│  │   └───────────────┘                     │  │
│  └─────────────────────────────────────────┘  │
│                                               │
│  ┌─────────────────────────────────────────┐  │
│  │          PROJECT / REPOSITORY           │  │
│  │             ...                         │  │
│  └─────────────────────────────────────────┘  │
└───────────────────────────────────────────────┘
```

Bu çizim birebir her projede böyle olmak zorunda değildir; kavramların
ilişkisini anlamak için düşünsel bir modeldir.

------------------------------------------------------------------------

# 21. Hızlı Karşılaştırma Tablosu

  -----------------------------------------------------------------------
  Kavram                  Ne demek?               Örnek
  ----------------------- ----------------------- -----------------------
  **File**                Gerçek dosya            `Header.tsx`

  **Folder**              Dosyaları düzenleyen    `src/components/`
                          klasör                  

  **Project**             Geliştirdiğin           E-Commerce Store
                          yazılım/ürün            

  **Repository**          Git tarafından takip    `ecommerce-store.git`
                          edilen kod tabanı       

  **Workspace**           Bir veya daha fazla     Store + Admin + Docs
                          kaynağı aynı çalışma    
                          ortamında tutan alan    

  **Working Directory**   Terminalin şu anda      `C:\Projects\store`
                          bulunduğu dizin         

  **Context**             Özellikle AI'ın o anda  `theme-guide.md` +
                          kullandığı bilgi        Meridian dosyaları

  **Monorepo**            Birden fazla            `apps/store`,
                          uygulama/paketin tek    `apps/admin`,
                          repository içinde       `packages/ui`
                          yönetilmesi             
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 22. Sık Yapılan Yanlış Varsayımlar

### ❌ "Workspace bir klasördür."

Her zaman değil.

Workspace fiziksel klasörlerden oluşabilir ama kendisi mantıksal bir
çalışma alanı da olabilir.

### ❌ "İki projeyi workspace'e eklersem birleşir."

Hayır.

Projeler bağımsız kalabilir.

### ❌ "Aynı workspace'teki projelerin Git branch'i aynıdır."

Hayır.

Her repository'nin kendi branch ve commit geçmişi olabilir.

### ❌ "Workspace'teki her dosya AI'ın context'indedir."

Hayır.

Workspace erişilebilir alanı, context ise o anda kullanılan bilgiyi
ifade eder.

### ❌ "Terminal workspace'in tamamında çalışır."

Terminal belirli bir working directory içerisinde çalışır.

### ❌ "Workspace monorepo demektir."

Hayır.

Workspace birden fazla bağımsız repository de içerebilir.

------------------------------------------------------------------------

# 23. Zihinde Tutulması Gereken En Önemli Formüller

``` text
PROJECT
= geliştirdiğin şey
```

``` text
FOLDER
= dosyaların bulunduğu fiziksel yapı
```

``` text
REPOSITORY
= Git'in takip ettiği kod tabanı
```

``` text
WORKSPACE
= üzerinde birlikte çalışmak istediğin kaynakların çalışma alanı
```

``` text
WORKING DIRECTORY
= terminalin şu anda bulunduğu klasör
```

``` text
CONTEXT
= AI'ın o anda kullandığı bilgi
```

------------------------------------------------------------------------

# 24. En Önemli Sonuç

Workspace'i şu şekilde düşün:

``` text
                   WORKSPACE
                      │
          ┌───────────┼───────────┐
          │           │           │
        Store       Admin        Docs
          │           │           │
       ayrı repo    ayrı repo    kaynak
```

Workspace bu parçaların üzerinde **birlikte çalışmanı kolaylaştırır**,
fakat onların teknik sınırlarını otomatik olarak ortadan kaldırmaz.

> **Workspace yeni bir proje oluşturmak veya projeleri birleştirmek
> değildir. Çalışırken ihtiyaç duyduğun bir veya birden fazla kaynağı
> aynı çalışma ortamında yönetmenin yoludur.**

------------------------------------------------------------------------

# 25. Mini Kontrol Listesi

Bir workspace oluşturmadan önce kendine şunları sor:

-   Aynı görev için birden fazla proje veya klasöre ihtiyacım var mı?
-   Bu klasörler birbirleriyle ilişkili mi?
-   Bunlar ayrı Git repository mi?
-   Terminalde hangi proje içinde çalıştığımı biliyor muyum?
-   AI aracı kullanıyorsam hangi klasörlere gerçekten erişebildiğini
    biliyor muyum?
-   Eski ve yeni kodu karşılaştırmam gerekiyor mu?
-   Dokümantasyon başka bir klasörde mi?

Birden fazla sorunun cevabı **evet** ise multi-root / çok klasörlü bir
workspace kullanmak faydalı olabilir.

------------------------------------------------------------------------

## Kısa Özet

``` text
Workspace
│
├── Tek proje olabilir
│
├── Birden fazla proje olabilir
│
├── Birden fazla repository içerebilir
│
├── Farklı fiziksel konumlardaki klasörleri bir araya getirebilir
│
└── Araçlara göre farklı özellikler kazanabilir
```

**Ama workspace:**

``` text
≠ proje birleştirme
≠ Git merge
≠ dosya taşıma
≠ monorepo
≠ terminal working directory
≠ AI context
```

Bu ayrımları bildiğinde VS Code, Cursor, Claude Code ve diğer geliştirme
araçlarında kullanılan "workspace" ifadelerini çok daha kolay
yorumlayabilirsin.
