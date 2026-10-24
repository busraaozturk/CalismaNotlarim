# SEO Nedir?
Bir web sitesi yayına alındığında kullanıcıların o siteye ulaşmasının en yaygın yollarından biri arama motorlarıdır. Kullanıcı Google'a `kadın deri çanta` yazdığında hangi sayfaların, hangi sırayla gösterileceğine arama motoru karar verir.

**SEO (Search Engine Optimization)**, Türkçede **Arama Motoru Optimizasyonu**, bir web sitesinin arama motorları tarafından **bulunabilmesi, anlaşılabilmesi ve ilgili aramalarda kullanıcılara gösterilebilmesi** için yapılan çalışmaların bütünüdür.

Bu notta SEO'nun ne olduğunu ve arama motorlarının nasıl çalıştığını kavramsal olarak inceleyeceğiz. SEO için HTML tarafında kullanılan `title`, `meta description`, `robots`, `canonical` gibi yapılar **04_HTML/15_HTMLMetadataTemelSEO.md** notunda ayrıntılı olarak anlatılmaktadır.
```
    SEO Nedir?
    │
    ├── 1. Arama Motoru Nasıl Çalışır?
    │   ├── Tarama (Crawling)
    │   ├── İndeksleme (Indexing)
    │   └── Sıralama (Ranking)
    │
    ├── 2. robots.txt
    │
    ├── 3. sitemap.xml
    │
    ├── 4. SEO Türleri
    │   ├── Teknik SEO
    │   ├── On-Page SEO
    │   └── Off-Page SEO
    │
    ├── 5. Sayfa Deneyimi ve Core Web Vitals
    │
    ├── 6. SEO ve Frontend Geliştirici
    │
    └── 7. SEO Araçları
```

## SEO Neden Önemlidir?
Arama sonuçlarında kullanıcıların büyük çoğunluğu ilk sayfadaki, özellikle de ilk sıralardaki sonuçlara tıklar. Bir sayfa ne kadar iyi hazırlanmış olursa olsun arama motoru tarafından bulunamıyor veya anlaşılamıyorsa kullanıcılara ulaşması zorlaşır.

Arama sonuçlarındaki ziyaretçiler iki şekilde gelebilir:
```
    Arama Sonuçları
    │
    ├── Organik sonuçlar
    │   └── Arama motorunun kendi değerlendirmesiyle sıraladığı sonuçlar
    │       → SEO (Search Engine Optimization)
    │
    └── Reklam sonuçları
        └── "Sponsorlu" olarak işaretlenen, ücret ödenen sonuçlar
            → SEA (Search Engine Advertising)
```
SEO, organik sonuçlarla ilgilenir. Reklamdan farklı olarak tıklama başına ücret ödenmez ancak sonuçları zaman içinde ve yavaş yavaş görülür.

## 1. Arama Motoru Nasıl Çalışır?
Arama motorlarının çalışma mantığı genel olarak üç aşamada düşünülebilir:
```
    Tarama (Crawling)
          ↓
    İndeksleme (Indexing)
          ↓
    Sıralama ve Sunma (Ranking / Serving)
```

### Tarama — Crawling
Arama motorları, web'i dolaşan ve sayfaları ziyaret eden programlar kullanır. Bunlara **crawler**, **bot** veya **spider** denir. Google'ın crawler'ı **Googlebot** olarak adlandırılır.

Crawler yeni sayfaları genellikle şu yollarla bulur:
- Daha önce bildiği sayfalardaki **bağlantıları (`<a href>`) takip ederek,**
- Site sahibinin sunduğu **sitemap.xml** dosyası üzerinden,
- Search Console gibi araçlarla doğrudan bildirilen adreslerden.

Burada HTML açısından önemli bir nokta vardır:
```
    <a href="/urunler">Ürünler</a>
    → Crawler bu bağlantıyı bulup takip edebilir.

    <div onclick="goTo('/urunler')">Ürünler</div>
    → Gerçek bir bağlantı olmadığı için takip edilmeyebilir.
```
Bu nedenle sayfalar arasındaki geçişler gerçek `<a>` elementleriyle yapılmalıdır. Bu konu **04_HTMLdeBaglantilarveNavigasyon** notundaki `<a>` ve `<button>` ayrımıyla da doğrudan ilişkilidir.

**- JavaScript ile Oluşturulan İçerik**

Google, sayfaları tarayıcıya benzer şekilde çalıştırarak (render ederek) JavaScript ile oluşturulan içeriği de görebilir. Ancak bu işlem ek kaynak gerektirdiği için gecikebilir ve her arama motoru aynı başarıyla yapamaz. Önemli içeriğin sunucudan gelen HTML'de hazır bulunması daha güvenilirdir. Next.js gibi framework'lerin sunduğu **Server Side Rendering** bu açıdan da avantaj sağlar.

### İndeksleme — Indexing
Taranan sayfa analiz edilir ve arama motorunun büyük veritabanına, yani **indeksine** eklenip eklenmeyeceğine karar verilir.

Bu aşamada arama motoru:
- Sayfanın başlığını, başlık hiyerarşisini ve metin içeriğini,
- Görsellerin `alt` metinlerini,
- Sayfanın dilini,
- Aynı içeriğin başka bir URL'de bulunup bulunmadığını (canonical),
- Sayfanın indekslenmeye izin verip vermediğini (`noindex`)

değerlendirir.

**Taranan her sayfa indekse eklenmez.** Kalitesiz, kopya veya `noindex` ile işaretlenmiş sayfalar indekse alınmayabilir. İndekste olmayan bir sayfa arama sonuçlarında **hiç görünmez.**

### Sıralama ve Sunma — Ranking / Serving
Kullanıcı bir arama yaptığında arama motoru indeksindeki sayfalar arasından en uygun olanları seçer ve sıralar.

Sıralamada yüzlerce sinyal kullanılır. Bunların tamamı açıklanmaz ancak temel olarak şu sorular önemlidir:
```
    İçerik, kullanıcının aradığı şeye cevap veriyor mu?
    İçerik güvenilir ve kaliteli mi?
    Başka siteler bu sayfaya bağlantı veriyor mu?
    Sayfa hızlı ve mobil cihazlarda kullanışlı mı?
    Site güvenli (HTTPS) mi?
```

Ayrıca Google sayfaları sıralarken öncelikli olarak sayfanın **mobil sürümünü** değerlendirir. Buna **mobile-first indexing** denir. Bu nedenle mobil görünümde eksik olan içerik, sıralamada da eksik kabul edilebilir.

## 2. `robots.txt`
`robots.txt`, sitenin kök dizininde bulunan ve crawler'lara **sitenin hangi bölümlerini taramaları gerektiğini** bildiren düz metin dosyasıdır.
```
    https://example.com/robots.txt
```

Örnek bir `robots.txt`:
```
    User-agent: *
    Disallow: /admin/
    Disallow: /sepet/

    Sitemap: https://example.com/sitemap.xml
```
Burada:
```
    User-agent: *          → Kural tüm crawler'lar için geçerlidir.
    Disallow: /admin/      → /admin/ ile başlayan adresler taranmasın.
    Sitemap: ...           → Site haritasının adresi.
```

**- Önemli: `robots.txt` Tarama İçindir, İndeksleme İçin Değil**

`robots.txt` ile engellenen bir sayfa, başka sitelerden bağlantı alıyorsa yine de arama sonuçlarında (içeriği olmadan) görünebilir.
```
    robots.txt Disallow      → "Bu sayfayı tarama."
    <meta name="robots" content="noindex"> → "Bu sayfayı indeksleme."
```
Hatta bir sayfa `robots.txt` ile engellenirse crawler sayfayı hiç açamayacağı için içindeki `noindex` etiketini de **göremez.** Bir sayfanın arama sonuçlarında görünmemesi isteniyorsa `noindex` kullanılmalı ve sayfanın taranmasına izin verilmelidir.

**- `robots.txt` Bir Güvenlik Önlemi Değildir**

`robots.txt` herkese açık bir dosyadır ve yalnızca bir **ricadır.** İyi niyetli crawler'lar bu kurallara uyar ancak kötü niyetli botlar uymak zorunda değildir. Gizli kalması gereken sayfalar `robots.txt` ile değil, **giriş/yetkilendirme** ile korunmalıdır. Hatta `Disallow: /gizli-panel/` yazmak bu adresin varlığını herkese duyurmak anlamına gelir.

## 3. `sitemap.xml`
**Site haritası (sitemap)**, sitedeki önemli sayfaların listesini arama motorlarına sunan bir XML dosyasıdır.
```
    <?xml version="1.0" encoding="UTF-8"?>
    <urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
        <url>
            <loc>https://example.com/</loc>
            <lastmod>2026-10-01</lastmod>
        </url>
        <url>
            <loc>https://example.com/urunler</loc>
            <lastmod>2026-10-20</lastmod>
        </url>
    </urlset>
```
Burada:
```
    <loc>     → Sayfanın tam adresi
    <lastmod> → Sayfanın son değiştirilme tarihi
```
Sitemap özellikle:
- Çok sayıda sayfası olan,
- Yeni yayınlanmış ve henüz bağlantı almamış,
- Sayfaları birbirine az bağlantı veren

siteler için faydalıdır. Sitemap'te bir sayfanın bulunması o sayfanın indeksleneceğini **garanti etmez**; arama motoruna yalnızca bir yol haritası sunar.

Sitemap adresi `robots.txt` içerisinde belirtilebilir veya Google Search Console üzerinden gönderilebilir. Next.js gibi framework'ler sitemap dosyasını otomatik oluşturmayı da destekler.

## 4. SEO Türleri
SEO çalışmaları genellikle üç başlık altında incelenir:
```
    SEO
    │
    ├── Teknik SEO
    │   └── Site arama motorları tarafından taranabiliyor ve indekslenebiliyor mu?
    │
    ├── On-Page SEO (Sayfa İçi)
    │   └── Sayfanın içeriği ve HTML yapısı doğru ve anlaşılır mı?
    │
    └── Off-Page SEO (Sayfa Dışı)
        └── Site, web üzerinde ne kadar güvenilir ve referans alınan bir kaynak?
```

### Teknik SEO
Sitenin altyapısıyla ilgilidir. Örneğin:
- `robots.txt` ve `sitemap.xml` dosyalarının doğru hazırlanması,
- HTTPS kullanılması,
- Sayfaların hızlı yüklenmesi,
- Mobil uyumluluk,
- Doğru HTTP durum kodları (taşınan sayfalar için `301`, olmayan sayfalar için `404`),
- Kopya içerikler için `canonical` kullanılması,
- Anlaşılır ve temiz URL yapısı.

HTTP durum kodları **01_TemelKonular/HttpNedir.md** notunda ayrıntılı olarak incelenmektedir.

URL yapısına örnek:
```
    Anlaşılır:  https://example.com/kadin/deri-canta
    Karmaşık:   https://example.com/index.php?cat=12&id=8841
```

### On-Page SEO
Sayfanın kendi içeriği ve HTML yapısıyla ilgilidir. Frontend geliştiricinin en çok katkı sağladığı alandır.
- Her sayfa için benzersiz ve açıklayıcı `<title>`,
- Sayfayı özetleyen `meta description`,
- Tek ve anlamlı bir `<h1>` ile doğru başlık hiyerarşisi,
- Semantic HTML (`header`, `nav`, `main`, `article`...),
- Görsellerde anlamlı `alt` metinleri,
- Açıklayıcı bağlantı metinleri ("buraya tıklayın" yerine "iade koşullarını inceleyin"),
- Site içi bağlantılar (internal links),
- Kullanıcının sorusuna gerçekten cevap veren kaliteli içerik.

### Off-Page SEO
Sitenin dışında gerçekleşen ve sitenin güvenilirliğini etkileyen faktörlerdir. En bilineni **backlink**, yani başka sitelerin bizim sitemize verdiği bağlantılardır.

Güvenilir ve konuyla ilgili sitelerden gelen bir bağlantı, arama motoruna "bu içerik referans alınmaya değer" sinyali verir. Ancak bağlantı satın almak veya anlamsız sitelerden toplu bağlantı almak arama motorlarının kurallarına aykırıdır ve cezaya yol açabilir.

## 5. Sayfa Deneyimi ve Core Web Vitals
Arama motorları yalnızca içeriğe değil, kullanıcının sayfada nasıl bir deneyim yaşadığına da bakar. Google bu deneyimi ölçmek için **Core Web Vitals** adını verdiği üç temel metrik kullanır:
```
    LCP (Largest Contentful Paint)
    └── Sayfadaki en büyük görünür içerik ne kadar sürede yüklendi?
        → Yükleme hızı

    INP (Interaction to Next Paint)
    └── Kullanıcı bir butona bastığında sayfa ne kadar hızlı tepki verdi?
        → Etkileşim hızı

    CLS (Cumulative Layout Shift)
    └── Sayfa yüklenirken içerikler beklenmedik şekilde kaydı mı?
        → Görsel kararlılık
```
Bu metriklerin birçoğu doğrudan HTML ile ilişkilidir:
```
    LCP → Ana görsele fetchpriority="high", diğerlerine loading="lazy"
          (05_HTMLdeGorsellerveMedya)
          Script'lerde defer kullanmak (18_HTML'eJavaScriptEklemek)

    CLS → Görsellere width ve height vermek
          (05_HTMLdeGorsellerveMedya)
```
Core Web Vitals sıralamada bir sinyal olsa da içeriğin kalitesinin önüne geçmez. Çok hızlı ancak kullanıcının aradığı cevabı vermeyen bir sayfa üst sıralarda yer almaz.

## 6. SEO ve Frontend Geliştirici
SEO genellikle pazarlama ekibinin işi gibi düşünülse de birçok temel SEO gereksinimi doğrudan frontend geliştiricinin yazdığı koda bağlıdır.
```
    Frontend Geliştirici
    │
    ├── Semantic HTML ve doğru başlık hiyerarşisi
    ├── title, meta description, canonical, robots (15_HTMLMetadataTemelSEO)
    ├── Paylaşım metadata'sı (16_OpenGraphNedir)
    ├── Structured Data (17_StructuredDataSchemaorg ve JSON-LD)
    ├── Görsellerde alt metni ve performans
    ├── Gerçek <a> bağlantıları
    ├── Erişilebilirlik (14_HTML'deErişilebilirlik)
    └── Sayfa hızı ve mobil uyumluluk
```
Erişilebilirlik ve SEO arasında güçlü bir ilişki vardır. Ekran okuyucunun bir sayfayı anlamasını kolaylaştıran semantic yapı, `alt` metinleri ve anlamlı bağlantılar arama motorunun sayfayı anlamasını da kolaylaştırır.

## 7. SEO Araçları
**- Google Search Console**

Google'ın ücretsiz aracıdır. Sitenin:
- Hangi sayfalarının indekslendiğini,
- Hangi aramalarda göründüğünü ve kaç tıklama aldığını,
- Tarama ve indeksleme hatalarını,
- Core Web Vitals sonuçlarını

gösterir. Sitemap da bu araç üzerinden gönderilebilir.

**- Lighthouse**

Chrome Geliştirici Araçları (F12) içerisinde bulunur. Sayfanın performans, erişilebilirlik, en iyi uygulamalar ve temel SEO puanlarını ölçer ve iyileştirme önerileri sunar. **PageSpeed Insights** aynı ölçümleri web üzerinden yapar.

**- `site:` Araması**

Google'da `site:example.com` şeklinde arama yapılarak sitenin hangi sayfalarının indekste olduğu kabaca görülebilir.

## SEO Hakkında Yanlış Bilinenler
**1. "SEO hemen sonuç verir."**

SEO çalışmalarının etkisi genellikle haftalar veya aylar içinde görülür. Yeni bir sayfanın taranması, indekslenmesi ve sıralamada yerini bulması zaman alır.

**2. "Doğru meta etiketleriyle ilk sıraya çıkılır."**

Meta etiketleri arama motorunun sayfayı doğru anlamasına ve sonuçta düzgün görünmesine yardımcı olur. Ancak sıralamayı belirleyen asıl unsur içeriğin kalitesi ve kullanıcının aramasına verdiği cevaptır. `meta keywords` etiketi ise Google tarafından sıralamada kullanılmaz.

**3. "Anahtar kelimeyi ne kadar çok tekrar edersem o kadar iyi."**

Anahtar kelimeyi doğal olmayan şekilde tekrar etmek (**keyword stuffing**) arama motorlarının kurallarına aykırıdır ve sıralamaya zarar verebilir. İçerik arama motoru için değil, kullanıcı için yazılmalıdır.

**4. "Sitemap'e eklenen her sayfa indekslenir."**

Sitemap bir öneridir; indekslemeyi garanti etmez.

**5. "robots.txt ile sayfayı arama sonuçlarından kaldırırım."**

`robots.txt` taramayı engeller. Sayfanın sonuçlarda görünmemesi için `noindex` kullanılmalıdır.

**6. "SEO bir kez yapılır ve biter."**

İçerikler, rakipler ve arama motorlarının algoritmaları sürekli değiştiği için SEO sürekli takip ve iyileştirme gerektirir.

## Kısaca Özet
- **SEO**, bir sitenin arama motorlarında bulunabilmesi, anlaşılabilmesi ve ilgili aramalarda gösterilebilmesi için yapılan çalışmalardır.
- Arama motorları sayfaları **tarar (crawl)**, uygun gördüklerini **indeksler (index)** ve arama yapıldığında **sıralar (rank).**
- Crawler sayfaları bağlantılar ve sitemap üzerinden bulur; bu yüzden gerçek `<a href>` bağlantıları önemlidir.
- `robots.txt` **taramayı**, `noindex` **indekslemeyi** kontrol eder. İkisi aynı şey değildir.
- `robots.txt` bir güvenlik önlemi değildir.
- `sitemap.xml` sitenin önemli sayfalarını arama motorlarına listeler ancak indekslemeyi garanti etmez.
- SEO; **teknik**, **sayfa içi (on-page)** ve **sayfa dışı (off-page)** olarak üç başlıkta incelenebilir.
- **Core Web Vitals** (LCP, INP, CLS) sayfa deneyimini ölçer ve birçoğu doğrudan HTML ile iyileştirilebilir.

Temel akış:
```
    Kullanıcı için kaliteli içerik
            +
    Arama motorunun tarayıp anlayabileceği doğru HTML yapısı
            +
    Hızlı, güvenli ve mobil uyumlu bir site
            ↓
    Arama sonuçlarında görünürlük
```

SEO'nun HTML tarafındaki uygulamaları için:
- **04_HTML/15_HTMLMetadataTemelSEO.md** → title, meta description, robots, canonical, hreflang
- **04_HTML/16_OpenGraphNedir.md** → Paylaşım metadata'sı
- **04_HTML/17_StructuredDataSchemaorg ve JSON-LD.md** → Yapısal veri
