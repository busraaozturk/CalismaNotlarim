# 📚 Web Geliştirme Çalışma Notları

> Yazılım geliştirme öğrenme yolculuğundaki önemli kavramlar ve pratikler hakkında detaylı notlar.

## 📖 İçindekiler

1. [Temel Konular](#01-temel-konular)
2. [Git & Github](#02-git--github)
3. [CSS](#03-css)
4. [HTML](#04-html)
5. [JavaScript](#05-javascript)
6. [Next.js](#06-nextjs)
7. [Geliştirme Ortamı](#07-geliştirme-ortamı)
8. [Diğer](#diğer)

---

## 01. Temel Konular

Web geliştirmede ihtiyaç duyulan temel kavramları, internet altyapısını ve yazılım süreçlerini anlamak.

- [**Tarayıcı Kavramları**](01_TemelKonular/TarayıcıKavramları.md) - URL yazıldığında olanlar, tarayıcı motorları, rendering süreci, veri depolama yöntemleri ve geliştirici araçları
- [**HTTP Nedir?**](01_TemelKonular/HttpNedir.md) - İstemci-sunucu iletişimi, istek-yanıt yapısı, HTTP metotları, durum kodları ve HTTPS
- [**Domain Name Nedir?**](01_TemelKonular/DomainName.md) - Alan adı yapısı, DNS, TLD, SLD ve subdomain kavramları
- [**Hosting Nedir?**](01_TemelKonular/HostingNedir.md) - Web barındırmanın çalışma biçimi, hosting türleri ve seçim kriterleri
- [**SEO Nedir?**](01_TemelKonular/SEONedir.md) - Arama motorlarının çalışma mantığı, robots.txt, sitemap.xml, SEO türleri ve Core Web Vitals
- [**Test Güdümlü Geliştirme (TDD)**](01_TemelKonular/TestGudumluGelistirme%28TDD%29.md) - Red-Green-Refactor döngüsü ve TDD’nin frontend’de kullanımı
- [**Yazılım Yaşam Döngüsü (SDLC)**](01_TemelKonular/YazilimYasamDongusu%28SDLC%29.md) - Planlama, analiz, tasarım, geliştirme, test, yayınlama, bakım aşamaları ve SDLC modelleri

---

## 02. Git & Github

Sürüm kontrol sistemi ve işbirliği araçlarının kullanımı.

- [**Git & Github Nedir?**](02_Git%26Github/Git%26GithubNedir.md) - Git ve GitHub’ın temel kavramları
- [**Git Çoklu Hesap Rehberi**](02_Git%26Github/GitCokluHesapRehberi.md) - Aynı bilgisayarda birden fazla Git hesabı yönetimi
- [**Gitignore Nedir?**](02_Git%26Github/GitignoreNedir.md) - Versiyon kontrolünden dosya hariç tutma
- [**GitLab Nedir?**](02_Git%26Github/GitLabNedir.md) - GitLab platformu ve temel kullanım alanları

---

## 03. CSS

Web tasarımı ve stil oluşturmaya yönelik notlar.

- [**00 - CSS Temelleri**](03_CSS/00_CSSTemelleri.md) - CSS'in görevi, HTML'e dahil edilmesi ve temel sözdizimi
- [**01 - CSS Seçiciler (Selectors)**](03_CSS/01_CSSSeçiciler%28Selectors%29.md) - Element, class, id, attribute, pseudo-class ve kombinatör seçicileri
- [**02 - Cascade ve Specificity**](03_CSS/02_CascadeveSpecificity.md) - Çakışan kuralların hangi sırayla ve önceliğe göre uygulandığı
- [**03 - CSS Renkler (Colors)**](03_CSS/03_CSSRenkler%28Colors%29.md) - Renk değerleri ve renk formatları
- [**04 - CSS Birimler ve Fonksiyonlar**](03_CSS/04_CSSBirimlerveFonksiyonlar.md) - Mutlak ve göreceli birimler, CSS fonksiyonları
- [**05 - CSS Box Model**](03_CSS/05_CSSBoxModeli.md) - Content, padding, border, margin ve box-sizing
- [**06 - CSS Display**](03_CSS/06_CSSDisplay.md) - Block, inline, inline-block ve diğer display değerleri
- [**07 - CSS Positioning**](03_CSS/07_CSSPositioning.md) - static, relative, absolute, fixed ve sticky konumlandırma
- [**08 - CSS Flexbox**](03_CSS/08_CSSFlexbox.md) - Tek boyutlu yerleşim ve hizalama
- [**09 - CSS Grid**](03_CSS/09_CSSGrid.md) - İki boyutlu satır-sütun yerleşim sistemi
- [**10 - CSS Tipografi**](03_CSS/10_CSSTipografi.md) - Yazı tipi, boyut, kalınlık, satır yüksekliği ve metin düzeni
- [**11 - CSS Arka Planlar**](03_CSS/11_CSSArkaPlanlar.md) - Arka plan rengi, görseli, konumu, boyutu ve gradient

**PDF Notlar**

- [**Responsive Design**](03_CSS/MediaQuery.pdf) - Media queries ve responsive tasarım teknikleri
- [**CSS Birimler**](03_CSS/piksel%20-%20em%20-%20rem%201.pdf) - px, em, rem birimleri ve kullanım alanları
- [**Liste Yapıları**](03_CSS/ul-li%28Liste%29Yapısı.pdf) - HTML listeleri ve CSS stillemesi

---

## 04. HTML

HTML'in temel yapısı, semantik elementler, formlar, medya, erişilebilirlik ve SEO.

- [**00 - HTML Temelleri**](04_HTML/00_HTMLTemelleri.md) - Markup dili, element/tag/attribute, yorumlar, whitespace, sayfa iskeleti ve CSS/JS ekleme
- [**01 - Anlamsal HTML Yapısı**](04_HTML/01_AnlamsalHTMLYapisi.md) - header, nav, main, section, article, aside ve footer
- [**02 - Başlık Hiyerarşisi**](04_HTML/02_BaşlıkHiyerarşisi.md) - h1–h6 kullanımı ve doğru başlık sıralaması
- [**03 - Metin Etiketleri**](04_HTML/03_HTMLdeMetinEtiketleri.md) - p, br, hr, vurgu etiketleri, pre, code/kbd/samp, div/span, değişiklik ve alıntı etiketleri
- [**04 - Bağlantılar ve Navigasyon**](04_HTML/04_HTMLdeBaglantilarveNavigasyon.md) - href, target, sayfa içi bağlantılar, mailto/tel ve a-button farkı
- [**05 - Görseller ve Medya**](04_HTML/05_HTMLdeGorsellerveMedya.md) - img, alt, loading, fetchpriority, figure, picture, video, track (altyazı) ve audio
- [**06 - Listeler**](04_HTML/06_HTML'deListeler.md) - Sıralı, sırasız, iç içe ve açıklama listeleri
- [**07 - Tablolar**](04_HTML/07_HTML'deTablolar.md) - Tablo yapısı, thead/tbody/tfoot, caption, scope, colspan ve rowspan
- [**08 - HTML Formları**](04_HTML/08_HTMLFormları.md) - form, input türleri, dosya yükleme, label, select, textarea, form doğrulama ve sınırlılıkları
- [**09 - Global Attributes**](04_HTML/09_HTMLGlobalAttriubutes.md) - id, class, title, lang, hidden, tabindex, data-* ve style
- [**10 - Etkileşimli ve Yardımcı Elementler**](04_HTML/10_HTMLEtkilesimliYardimciElementler.md) - details, summary, dialog, progress, meter ve output
- [**11 - Embedded Content**](04_HTML/11_HTMLEmbeddedContent.md) - iframe, sandbox, CSP, embed ve object
- [**12 - Responsive Images**](04_HTML/12_HTMLResponsiveImages.md) - srcset, sizes, picture ve art direction
- [**13 - Entities ve Özel Karakterler**](04_HTML/13_HTMLEntitiesveÖzelKarakterler.md) - Karakter referansları ve &nbsp; kullanımı
- [**14 - Erişilebilirlik (A11y)**](04_HTML/14_HTML'deErişilebilirlik.md) - Semantic HTML, klavye kullanımı, formlar, tablolar ve ARIA
- [**15 - Metadata ve Temel SEO**](04_HTML/15_HTMLMetadataTemelSEO.md) - title, meta description, robots, canonical, hreflang ve favicon
- [**16 - Open Graph (OG)**](04_HTML/16_OpenGraphNedir.md) - Sosyal medya paylaşım kartları ve Twitter / X Card
- [**17 - Structured Data, Schema.org ve JSON-LD**](04_HTML/17_StructuredDataSchemaorg%20ve%20JSON-LD.md) - Yapısal veri ve schema türleri
- [**18 - HTML'e JavaScript Eklemek**](04_HTML/18_HTML'eJavaScriptEklemek.md) - script yerleşimi, defer, async, type="module" ve noscript
---

## 05. JavaScript

JavaScript programlama dili temelleri ve yöntemleri.

- [**Array Fonksiyonları**](05_JavaScript/array_function.md) - Dizi manipülasyon yöntemleri
  - `filter()` - Şart uygun elemanları filtreleme
  - `map()` - Dizinin her elemanında işlem yapma
  - `sort()` - Diziyi sıralama

---

## 06. Next.js

Modern React framework ve server-client mimarisi.

- [**Server Component Nedir?**](06_Next.js/ServerClientComponent/01_ServerComponentNedir.md) - Server-side rendering ve bileşenleri
- [**Client Component Nedir?**](06_Next.js/ServerClientComponent/02_ClientComponentNedir.md) - Client-side işlemleri ve bileşenleri
- [**Birlikte Çalışma Mimarisi**](06_Next.js/ServerClientComponent/03_BirlikteCalismaMimarisi.md) - Server ve Client bileşenlerin etkileşimi
- [**Server & Client Component Karşılaştırması**](06_Next.js/ServerClientComponent/04_Server%26ClientComponent_Table.md) - Detaylı tablo ve farklar
- [**Data Fetch Mantığı**](06_Next.js/ServerClientComponent/05_DataFetchMantığı.md) - Next.js'de veri çekme yöntemleri
- [**React Kaynakları**](06_Next.js/React.pdf) - React kütüphanesi ve öğrenme materyalleri
- [**Örnek Dosyalar**](06_Next.js/next.js_example/) - index, list ve state HTML örnekleri

---

## 07. Geliştirme Ortamı

Paket yönetimi, bağımlılıklar ve JavaScript geliştirme araçları.

- [**Workspace Nedir?**](07_GelistirmeOrtami/WorkspaceNedir.md) - Çalışma alanı kavramı ve kullanım amacı
- [**Package Manager Nedir?**](07_GelistirmeOrtami/PackageManager.md) - Paket yöneticilerinin görevi
- [**Paket Nedir?**](07_GelistirmeOrtami/PaketNedir.md) - Paketin yapısı ve içeriği
- [**Bağımlılık (Dependency) Nedir?**](07_GelistirmeOrtami/BagimlilikNedir.md) - Projelerin dış paketlerle ilişkisi
- [**package.json Nedir?**](07_GelistirmeOrtami/PackagejsonNedir.md) - Projenin temel tanımlama dosyası
- [**npm Nedir?**](07_GelistirmeOrtami/npmNedir.md) - npm Registry, CLI ve temel komutlar
- [**Yarn Nedir?**](07_GelistirmeOrtami/yarnNedir.md) - Yarn paket yöneticisi
- [**pnpm Nedir?**](07_GelistirmeOrtami/pnpmNedir.md) - pnpm paket yöneticisi
- [**npm, Yarn ve pnpm Karşılaştırması**](07_GelistirmeOrtami/npm-Yarn-pnpmKarsilastirmasi.md) - Üç paket yöneticisinin farkları
- [**Bun Nedir?**](07_GelistirmeOrtami/BunNedir.md) - Runtime, package manager ve diğer araçları bir arada sunan Bun

---

## Diğer

- [**Prisma Nedir?**](PrismaNedir.md) - TypeScript/Node.js projeleri için ORM aracı

---

## 🚀 Başlama

Bu notlar öğrenme ve referans amaçlı kullanılan içeriklerden oluşmaktadır. Web'in nasıl çalıştığını anlamak için **01. Temel Konular** ile başlayıp ardından **HTML → CSS → JavaScript** sırasıyla ilerleyebilirsiniz. Her bölümdeki notlar numara sırasına göre okunacak şekilde hazırlanmıştır.

---

**Son Güncelleme:** Ekim 2026
