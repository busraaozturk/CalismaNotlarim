# Structured Data, Schema.org ve JSON-LD
Bir web sayfasına baktığımızda içeriğin ne anlama geldiğini çoğu zaman kolayca anlayabiliriz.
Örneğin bir ürün sayfasında: 
- Siyah Kol Saati
- 12500TL
- Stokta
- 4.7 yıldız 

bilgilerini gördüğümüzde bunun:
- Bir ürün adı
- Ürün fiyatı
- Stok durumu
- Değerlendirme puanı

olduğunu anlayabiliriz.

Ancak arama motorlarının bu bilgilerin anlamını daha açık ve standart bir biçimde anlayabilmesi için **Structed Data (Yapılandırılmış Veri)** kullanılabilir.

## Structured Data Nedir?
**Structured Data**, bir web sayfasındaki içeriğin ne anlama geldiğini makinelerin daha kolay anlayabileceği standart bir yapıyla açıklayan verilerdir.

Örneğin sayfada;
```
    <h1>Siyah Kol Saati</h1>
    <p>12.500 TL</p>
```
bulunduğunu düşünelim.

Bir kullanıcı bunun ürün adı ve diyat olduğunu sayfanın bağlamından anlayabilir. Structured Data ile ise bu bilgiler açıkça aşağıdaki şekilde tanımlanabilir:
```
    Bu bir Product 
    │ 
    ├── name 
    │   └── Siyah Kol Saati 
    │ 
    └── offers 
        └── price 
            └── 12500
```

Temel amaç; `Sayfadaki verilerin **anlamını ve aralarındaki** ilişkileri makinelere standart biçimde açıklamaktır.`

## Structured Data Neden Kullanılır?
Arama motorları HTML içeriğini zaten analiz edebilir. Structed Data'nın amacı arama motorlarına `Bu metni tahmin etmeye çalışma, bu veri bir ürünün fiyatıdır.` gibi daha açık ve standart bilgiler sağlamaktır.

Örneğin, "Siyah Kol Saati" tek başına yalnızca bir metindir. Structured Data içerisinde: `"name":"Siyah Kol Saati` olaran tanımladığında bu değerin ilgili nesnenin adı olduğu belirtilmiş olur.

Structed Data özellikle:
- Ürünler
- Makaleler
- Organizasyonlar
- Etkinlikler
- Breadcrumb yapıları
- Tarifler

gibi belirli içerik türlerini tanımlamak için kullanılabilir.

Arama motorları destekledikleri yapılandırılmış verileri, uygun durumlarda arama sonuçlarındaki gelişmiş görünümler içinde kullanabilir.

Ancak: `Structured Data eklemek, sayfanın mutlaka özel veya zengin bir arama sonucu görünümü kazanacağı anlamına gelmez.`

## Schema.org Nedir?
Structured Data yazarken ortak bir kelime dağarcığına ihtiyaç vardır. Burada **Schema.org** devreye girer. 

**Schema.org;** web üzerindeki varlıkları ve özelliklerini tanımlamak için kullanılan ortak bir vocabulary yani **şema sözlüğü** sunar.

Örneğin:
```
    Product 
    Article 
    Organization 
    Person 
    Event 
    BreadcrumbList 
    Recipe
```

```
    Bir ürün için **product** kullanabiliriz.
    Bir makale için **article** kullanabiliriz.
    Bir organizasyon için **Organization** kullanılabilir.
```

Basitçe aşağıdaki şekilde düşünebiliriz:
```
    Structured Data 
        │ 
        ├── Veriyi yapılandırma yaklaşımı 
        │ 
        ▼ 
    Schema.org 
        │ 
        └── Kullanabileceğimiz türler ve özellikler için sözlük
```

## JSON-JD Nedir?
Schema.org bize **hangi kavramları ve özellikleri kullanabileceğimizi** söyler. Bunları HTML sayfasına aktarmanın ise farklı yöntemleri vardır. Bunlardan biri ve web sayfalarında çok sık karşılaşacağımız yöntem **JSON-LD** yani, **JavaScript Obkect Notiation for Linked Data** formatıdır.

Örneğin:
```
    <script type="application/ld+json"> { 
        "@context": "https://schema.org", 
        "@type": "Product", 
        "name": "Siyah Kol Saati" }
    </script>
```

Bu kod kullanıcıya sayfanın normal içeriği olarak gösterilmez. Makinelerin okuyabileceği yapılandırılmış veri sağlar.

## Structured Data, Schema.org ve JSON-LD Aynı Şey mi?
Hayır. Bu üç kavram birbirleriyle ilişkili olsa da aynı şeyi ifade etmez.

```
    Structured Data
    |
    |   Sayfadaki bilgileri yapılandırılmış 
    |   biçimde açıklama yaklaşımı
    |
    ▼
    Schema.org
    |
    |   Kullanacağımız türleri ve 
    |   özellikleri tanımlayan sözlük
    |
    ▼
    JSON-LD
        |
        |   Bu veriyi sayfaya ekleyebileceğimiz
        |   formatlardan biri
        ▼
        <script type="application/ld+json">
```

Kısaca:
| Kavram            | Görevi    |
|-------------------|-----------|
| Structed Data     | Veriyi anlamlı ve yapılandırılmış şekilde tanımlamak |
| Schema.org        | Türleri ve özellikleri sağlayan ortak sözlük  |
|Json-LD            | Structured Data'yı ifade etme yöntemlerinden biri |

Bu ayrımı anlamak konunun en öenmli noktalarından biridir.

## JSON-LD HTML'e Nasıl Eklenir?
**JSON-LD**: `<script type="application/ld+json">` elementi içerisinde yazılır.

Örneğin:
```
    <script type="application/ld+json"> 
    { 
        "@context": "https://schema.org", 
        "@type": "Product", 
        "name": "Siyah Kol Saati" 
    } 
    </script>
```

Buradaki `type="application/ld+json"` script içeriğinin normal JavaScript değil, **JSON-LD** verisi olduğunu belirtir. Bu nedenle içerisine `const product = {};` gibi normal JavaScript kodları yazılmaz.

## `@context` Nedir?
JDON-LD örneklerinde genellikle `"@context": "https://schema.org"` ile karşılaşırız. Bu ifade kullanılan terimlerin hangi vocabulary bağlamında yorumlanacağını belirtir.

Schema.org kullanıyorsak, `"@context" : "https://schema.org"` şeklinde tanımlarız. Başlangıç seviyesinde bunu şöyle düşünebiliriz:
```
    @context
        ↓
    Bu JSON-LD içerisindeki kavramları 
    hangi sözlüğe göre yorumlamalısın?
        ↓
    Schema.org
```

## `@type` Nedir?
`@type` tanımladığımız şeyin türünü belirtir.

Örneğin: `"@type" : "Product"` şu anlama gelir: **Bu veri bir ürünü tanımlıyor.**

Makale için: `"@type" : "Article"`

Organizasyon için: `"@type" : "Organization"` kullanılabilir.

Temel mantık:
```
    @context → Hangi sözlük?
    @type → Bu şey nedir?
```

## Product Schema Örneği
Bir e-ticaret ürün sayfasını düşünelim. Sayfada BULUNUYOR OLABİLİR:
```
    <h1>Siyah Kol Saati</h1>
    <p>12.500TL<P>
```

Buna karşılık yapılandırılmış veri örneği şöyle olabilir:
```
    <script type="application/ld+json"> 
    { 
        "@context": "https://schema.org", 
        "@type": "Product", 
        "name": "Siyah Kol Saati", 
        "description": "Siyah deri kayışlı kol saati.", 
        "sku": "WATCH-001", 
        "offers": { 
            "@type": "Offer", 
            "price": "12500", 
            "priceCurrency": "TRY", 
            "availability": "https://schema.org/InStock" 
            } 
        } 
    </script>
```

Burada aşağıdaki gibi bir yapı vardır:
```
    Product 
    │ 
    ├── name 
    │ 
    ├── description 
    │ 
    ├── sku 
    │ 
    └── offers 
        │ 
        ├── price 
        ├── priceCurrency 
        └── availability
```

## İç İçe Veri Yapıları
Structured Data her zaman düz bir yapı değildir. Örneğin bir ürünün `Product` bilgisi vardır. Bu ürünün ayrıca `offer` bilgisi bulunabilir.

Bu nedenle bu şekilde iç içe nesneler kullanılabilir.
```
    { 
        "@type": "Product", 
        "name": "Siyah Kol Saati", 
        "offers": { 
            "@type": "Offer", 
            "price": "12500", 
            "priceCurrency": "TRY" 
        } 
    }
```

Mantık:
```
    Product
    │
    └── offers
          │
          └── Offer
               │
               ├── price
               └── priceCurrency
```
Bu sayede yalnızca **değerleri değil, değerlerin birbirleriyle ilişkilerini** de açıklayabiliriz.

## Article Schema
Blog veya makale sayfasında `Article` kullanılabilir.

Örneğin:
```
    <script typr="application/ld+json">
    {
        "@context": "https://schema.org", 
        "@type": "Article", 
        "headline": "Semantic HTML Nedir?", 
        "datePublished": "2026-09-25", 
        "author": { 
            "@type": "Person", 
            "name": "Yazar Adı" 
        }
    }
    </script>
```

Burada:
```
    Article
    │
    ├── headline
    ├── datePublished
    │
    └── author
        │
        └── Person
            └── name
```
ilişkisi kurulmuştur.

## Organization Schema
Bir şirket veya organizasyon hakkında yapılandırılmış veri sunmak için `Organization` kullanılabilir.

Basit örnek:
```
    <script type="application/ld+json"> 
    { 
        "@context": "https://schema.org", 
        "@type": "Organization", 
        "name": "Örnek Teknoloji", 
        "url": "https://example.com" 
    } 
    </script>
```
Burada tanımlanan varlığın **Organization** olduğu belirtilir. Ardından bu organizasyona ait bilgiler property'ler aracılığıyla tanımlanır.

## BreadcrumbList 
Breadcrumb yapısını HTML tarafında şöyle kullanabiliriz: `Ana Sayfa > Saatler > Siyah Kol Saati` Bu navigasyon yapısı Structured Data ile de ifade edilebilir.

Örneğin:
```
    <script type="application/ld+json"> 
    { 
        "@context": "https://schema.org", 
        "@type": "BreadcrumbList", 
        "itemListElement": [ 
            { 
                "@type": "ListItem", 
                "position": 1, 
                "name": "Ana Sayfa", 
                "item": "https://example.com/" 
            }, 
            { 
                "@type": "ListItem", 
                "position": 2, 
                "name": "Saatler", 
                "item": "https://example.com/saatler" 
            }, 
            { 
                "@type": "ListItem", 
                "position": 3, 
                "name": "Siyah Kol Saati" 
            } 
        ] 
    } 
    </script>
```

Burada aşağıdaki şekilde sıralı bir yapı oluşturulur.
```
    BreadcrumbList 
    │ 
    └── itemListElement 
        │ 
        ├── ListItem → 1 
        ├── ListItem → 2 
        └── ListItem → 3
```

## Her Sayfaya Aynı Schema Eklenir Mi?
Hayır. Structured Data sayfanın **gerçek içeriğine uygun** olmalıdır.

Örneğin:
```
    Ürün Detay Sayfası → Product
    Makale Sayfası → Article
    Breafcrumb bulunan sayfa → BreadcrumbList
    Organizasyon hakkında uygun sayfa/veri → BreadcrumbList
```

Bu nedenle: `Her sayfaya Product ekle` gibi bir **yaklaşım doğru değildir.**

Structured Data'nın temel prensibi: `Sayfada gerçekten bulunan içeriği doğru tür ve özelliklerle tanımlamaktır.`

## Sayfada Olmayan Bilgiyi Schema'ya Eklemek
Structured Data ile kullanıcıya gösterilen içerik arasında tutarlılık önemlidir. Örneğin ürün sayfasında fiyat `12.500 TL`olarak gösteriliyorsa Structured Data içerisinde `"price" : "9999"` gibi farklı bir fiyat verilmemelidir.

Aynı şekilde sayfada bulunmayan:
- Sahte değerlendirme,
- Yanlış stok bilgisi,
- Gerçek olmayan fiyat,
- İlgisiz ürün bilgileri eklenmemelidir.

Doğru mantık:
```
    Kullanıcının gördüğü içerik
        ↓
    Structured Data
        ↓
    Aynı gerçek içeriği açıklamalı
```
Structured Data görünmeyen bir SEO metni deposu değildir.

## Structured Data Bir Ranking Garantisimidir?
Hayır. Structured Data kullanmak:
```
    Schema ekledim.
            ↓
    Google'da kesin yükselirim
```
anlamına gelmez.

Aynı şekilde:
```
    Schema ekledim
            ↓
    Arama sonucunda kesin zengin görünüm çıkar.
```
sonucu da garanti değildir.

Structured Data'nın görevi içeriğin anlamını standart biçimde açıklamaktır. 

## Structured Data ve Open Graph Farkı
Bu iki konu zaman zaman karıştırılabilir. Open Graph'ı daha önce ayrı olarak incelemiştik.

Örneğin: `<meta property="og:title" content="Siyah Kol Saati" >`

Open Graph özellikle içeriğin sosyal platformlarda paylaşılırken nasıl temsil edileceğiyle ilişkilidir.

Structured Data ise:
```
    <script type="application/ld+json"> 
    { 
        "@context": "https://schema.org", 
        "@type": "Product", 
        "name": "Siyah Kol Saati" 
    } 
    </script>
```
şeklinde içeriğin yapısal anlamını ifade eder.

Temel fark:
| Open Graph                          | Structured Data                                     |
|-------------------------------------|-----------------------------------------------------|
|Sosyal paylaşım temsilinde kullanılır|İçeriğin makine tarafından anlaşılmasını yapılandırır|
|`meta` etiketleriyle kullanılır      |Örneğin JSON-LD ile kullanılabilir                   |
|`og:*` property'leri                 |Schema.org türleri ve özellikleri                    |

Birbirlerinin yerine geçmezler.

## Structured Data ve Metadata Aynı Şey mi?
Tam olarak değil. Daha önce:
```
    <title>...</title>

    <meta
        name="description"
        content="..."
    >

    <link
        rel="canonical"
        href="..."
    >
```
gibi metadata yapılarını gördük.

Structured Data ise içeriğin anlamını ve ilişkilerini daha ayrıntılı biçimde tanımlayabilir.

Örneğin:
```
    Product
    │
    ├── name
    ├── brand
    ├── sku
    └── offers
        ├── price
        ├── currency
        └── availability
```
gibi bir veri modeli oluşturabilir.

Dolayısıyla Structured Data'yı: `Metadata'nın aynısı` olarak düşünmemek gerekir.

## JSON-LD ve Normal JavaScript Farkı
İkisi de `<script>` içerisinde görülebildiği için başlangıçta karıştırılabilir.

Normal JavaScript:
```
    <script>
        const productName = "Siyah Kol Saati";

        console.log(productName);
    </script>
```
JSON-LD:
```
    <script type="application/ld+json">
    {
        "@context": "https://schema.org",
        "@type": "Product",
        "name": "Siyah Kol Saati"
    }
    </script>
```
JSON-LD içerisinde normal JavaScript komutları çalıştırmıyoruz.

Yani:
```
    <script> → JavaScript kodu
    <script type="application/ld+json"> → JSON-LD structured data
```
ayrımını bilmek önemlidir.

## Dinamik Sitelerde Structured Data
Gerçek projelerde ürün bilgileri çoğu zaman HTML içerisinde sabit yazılmaz. Backend veya API'den gelebilir.

Örneğin:
```
    Backend / API
        │
        ▼
    Product
    │
    ├── Name
    ├── Price
    ├── Currency
    └── Stock
        │
        ├──────────────► Sayfadaki ürün bilgileri
        │
        └──────────────► Structured Data
```
Buradaki önemli nokta aynı gerçek veri kaynağının kullanılmasıdır. Örneğin ürün fiyatı backend'den `12.500 TL` geliyorsa hem kullanıcıya gösterilen fiyat hem Structured Data içerisindeki fiyat aynı güncel veriden üretilmelidir.

Bu yaklaşım verilerin birbirinden kopmasını engeller.

## Structured Data Nasıl Kontrol Edilir?
Structured Data ekledikten sonra yalnızca `"Kod yazıldı, tamam."` dememek gerekir. Kontrol edilmelidir. Özellikle iki farklı kontrol türü önemlidir.

### Sözdizimi ve Schema Kontrolü
Yapının geçerli olup olmadığı kontrol edilebilir.

Örneğin:
```
    @type doğru mu?
    Property doğru mu?
    JSON geçerli mi?
    Beklenen değerler var mı?
```
### Arama Motoru Özelliği Kontrolü
Bir arama motorunun belirli bir rich result özelliği için gereken şartların karşılanıp karşılanmadığı ayrıca kontrol edilebilir.

Bu iki kontrol tamamen aynı şey değildir.

Bir yapı Schema.org açısından anlamlı olabilir fakat belirli bir arama motoru özelliği için gereken tüm alanları karşılamıyor olabilir.

## Structured Data Test Araçları
Pratikte iki tür kaynak özellikle kullanışlıdır:

### Schema.org Validator
Schema.org yapısının kontrol edilmesine yardımcı olur.

### Google Rich Results Test
Google'ın desteklediği zengin arama sonucu türleri açısından sayfanın Structured Data yapısını kontrol etmeye yardımcı olur.

Buradaki önemli ayrım:
```
    Schema.org → Veri modelinin / vocabulary'nin kendisi
    Arama motoru dokümantasyonu → Belirli arama özelliklerinde hangi yapıların desteklendiği
```
Bu nedenle gerçek projelerde yalnızca örnek kod kopyalamak yerine kullanılan schema türünün güncel dokümantasyonu kontrol edilmelidir.

## Structured Data Nerede Bulunmalı?
JSON-LD `<script type="application/ld+json">` ile sayfanın HTML belgesine eklenir.

Örneğin `<head>` içerisinde bulunabilir:
```
    <head>

        <title>Siyah Kol Saati</title>

        <script type="application/ld+json">
        {
            "@context": "https://schema.org",
            "@type": "Product",
            "name": "Siyah Kol Saati"
        }
        </script>

    </head>
```
Ancak burada asıl önemli konu yalnızca fiziksel konumu değildir.

Daha önemli olan:
- İlgili sayfada bulunması,
- Doğru veriyi içermesi,
- Sayfanın gerçek içeriğiyle eşleşmesi gibi kurallardır.

## Structured Data'da Sık Yapılan Hatalar
Structured Data kullanırken özellikle şu hatalardan kaçınılmalıdır:

### Her Sayfaya Aynı Schema'yı Eklemek
```
    Ana Sayfa
    Ürün Sayfası        →   Product
    Kategori
    Blog
```
doğru değildir. Schema sayfanın içeriğine uygun olmalıdır.

### Sayfada Olmayan Bilgiyi Ekleme
Örneğin gerçekte değerlendirme yokken `"ratingValue" : "5"` gibi sahte bilgi eklenmemelidir.

### Eski veya Yanlış Fiyat Göndermek
Sayfa: 12.500 TL

Schema: 10.000 TL olmamalıdır.

### JSON-LD İçerisine JavaScript Yazmak
Yanlış:
```
    <script type="application/ld+json">
    const product = {
        name: "Saat"
    };
    </script>
```
JSON-LD bloğu geçerli JSON-LD/JSON yapısında olmalıdır.

### Schema.org ile Google Gereksinimlerini Aynı Şey Sanmak
Schema.org'da bir property bulunması:
```
    Google bunu mutlaka rich result için kullanır.
```
anlamına gelmez.

Kullanılan arama motorunun güncel dokümantasyonu ayrıca kontrol edilmelidir.

### Schema Eklemeyi SEO Garantisi Sanmak
Structured Data faydalı bir anlamlandırma mekanizmasıdır ancak tek başına sıralama veya rich result garantisi değildir.

## Gerçek Bir Ürün Sayfası Örneği
HTML içeriğimiz:
```
    <article> 
        <h1>Siyah Kol Saati</h1> 
        <p> Siyah deri kayışlı klasik kol saati. </p> 
        <p> 12.500 TL </p> 
        <p> Stokta </p> 
    </article>
```
Aynı gerçek ürün için Structured Data:
```
    <script type="application/ld+json"> 
    { 
        "@context": "https://schema.org", 
        "@type": "Product", 
        "name": "Siyah Kol Saati", 
        "description": "Siyah deri kayışlı klasik kol saati.", 
        "sku": "WATCH-001", 
        "offers": { 
            "@type": "Offer", 
            "price": "12500", 
            "priceCurrency": "TRY", 
            "availability": "https://schema.org/InStock" 
        } 
    } 
    </script>
```

Burada iki farklı kullanıcı vardır:
```
    Sayfadaki HTML → İnsanların gördüğü içerik
    Structured Data → Makinelere içeriğin yapısını ve anlamını açıklayan veri
```
Ancak ikisi **aynı gerçek içeriği temsil eder.**

## Hangi Schema Türlerini Bilmeliyim?
Schema.org içerisinde çok sayıda tür bulunmaktadır. Bunların tamamını ezberlemek gerekli değildir.Frontend geliştirirken özellikle şu isimlerle karşılaşmak yeterli bir başlangıçtır:
```
    Product 
    Article 
    Organization 
    Person 
    BreadcrumbList 
    Event 
    Recipe
```

Projeye göre başka türlerle de karşılaşılabilir. Burada amaç: `Bütün Schema.org vocabulary'sini ezberlemek değil, ihtiyaç olduğunda doğru schema türünü araştırıp uygulayabilmektir.`

## Kontrol Listesi
Structured Data eklerken şu soruları sorabiliriz:
- Sayfa gerçekten bu schema türüne uygun mu?
- `@context` doğru mu?
- `@type` içeriği doğru temsil ediyor mu?
- Structured Data gerçek sayfa içeriğiyle eşleşiyor mu?
- Fiyat, stok veya diğer dinamik bilgiler güncel mi?
- Kullanıcıya gösterilmeyen sahte bilgiler eklenmiş mi?
- JSON geçerli mi?
- İç içe nesnelerin ilişkileri doğru mu?
- Schema.org dokümantasyonu kontrol edildi mi?
- Arama motorunun ilgili özellik için güncel gereksinimleri kontrol edildi mi?
- Structured Data test edildi mi?

## Kısaca Özet
Konunun temel ilişkisini şöyle düşünebiliriz:
```
    Web Sayfasındaki İçerik
            ↓
    Structured Data
            ↓
        Achema.org
            ↓
        JSON-LD
            ↓
    <script type="application/ld+json">
```

Kavramların görevleri:
```
    Structured Data → Veriyi anlamlı ve yapılandırılmış şekilde açıklama yaklaşımı
    Schema.org → Kullanılacak türleri ve özellikleri tanımlayan sözlük
    JSON-LD → Bu veriyi ifade edebileceğimiz formatlardan biri
```

Örneğin:
```
    Product 
    │ 
    ├── name 
    ├── description 
    ├── sku 
    │ 
    └── offers 
        │ 
        └── Offer 
            ├── price 
            ├── priceCurrency 
            └── availability
```

Bu konudaki en önemli nokta:
```
    Structured Data, arama motorlarını kandırmak için eklenen görünmez SEO metni değildir. Sayfada gerçekten bulunan içeriğin anlamını, türünü ve ilişkilerini makinelerin anlayabileceği standart bir yapıyla açıklamanın yoludur.
```

Bu nedenle doğru yaklaşım:

`Önce gerçek ve doğru sayfa içeriği → ardından bu içeriği doğru Structured Data ile tanımlamak.`
