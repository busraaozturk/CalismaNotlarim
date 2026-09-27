# HTML Metadata ve Temel SEO
## Metadata Nedir?
**Metadata**, bir web sayfası hakkında ek bilgi sağlayan verilerdir.

HTML'de metadata bilgilerinin büyük bölümü <head> bölümünde bulunur. Bu bilgiler genellikle sayfanın ana içeriğinin bir parçası olarak kullanıcıya gösterilmez; tarayıcılar, arama motorları ve bazı sosyal medya platformları tarafından kullanılabilir.

Metadata sayesinde örneğin:
- Sayfanın karakter kodlaması,
- Mobil cihazlarda nasıl görüntüleneceği,
- Sayfanın başlığı ve açıklaması,
- Arama motorlarının sayfayı nasıl değerlendirebileceği,
- Tercih edilen URL,
- Sosyal medya paylaşım bilgilerinin nasıl oluşturulacağı

gibi bilgiler tanımlanabilir.

`Metadata'nın tamamı SEO amacıyla kullanılmaz. Bazı metadata bilgileri tareyıcı davranışı, bazıları arama motorlaro, bazıları ise sosyal platformları için önemlidir.`

## `<head>` Elementi
`<head>`, HTML belgesi hakkında bilgiler içeren bölümdür.

Temel bir HTML belgesi:
```
    <!DOCTYPE html> 
    <html lang="tr"> 
    <head> 
        <meta charset="UTF-8"> 
        <meta name="viewport" content="width=device-width, initial-scale=1.0" > 
        <title>HTML Öğrenme Notları</title> 
    </head> 
    
    <body> 
        <h1>HTML Öğrenme Notları</h1> 
    </body> 
    </html>
```

Burada:
```
    <html> 
    │ 
    ├── <head> 
    │   ├── charset 
    │   ├── viewport 
    │   |── title
    │   ├── description 
    │   ├── robots 
    │   ├── canonical 
    │   └── diğer metadata 
    │
    └── <body> 
        └── Kullanıcının gördüğü ana sayfa içeriği
```
şeklinde temel bir yapı bulunur.

`<head>` içerisindeki her element `<meta>` elementi değildir.

Örneğin:
```
    <title>...</title> 
    <meta name="description" content="..."> 
    <link rel="canonical" href="...">
```
üçü de `<head>` içerisinde bulunabilir ancak farklı HTML elementleridir.

## Temel `<head>` Yapıları
### Karakter Kodlaması - `charset`
Sayfanın hangi karakter kodlamasını kullandığını belirtir. Modern web sayfalarında genellikle `<meta charset="UTF-8">` kullanılır.

**UTF-8**; Türkçe karakterler dahil olmak üzere çok geniş bir karakter kümesini destekler.

Bu nedenle temel HTML yapısında `<head>` bölümünün başlarında bulunması iyi bir yaklaşımdır.

### Viewport
Viewport, özellikle mobil cihazlarda sayfanın görüntülenme davranışını belirlemek açısından önemlidir.

Yaygın kullanım:
```
    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0"
    >
```
Burada,

`width=device-width` sayfanın genişliğini cihazın ekran genişliğine göre ayarlar.
`initial-scale=1.0` sayfanın başlangıç zoom seviyesini belirtir.

Responsive web tasarımının doğru çalışması için temel `<head>` yapılarından biridir.

## `<title>` Elementi

`<title>`, web sayfasının başlığını belirtir.
```
    <title>HTML Öğrenme Notları | Frontend</title>
```
Tarayıcı sekmesinde kullanılmasının yanında arama motorları açısından da önemli bir bilgi kaynağıdır.

Örneğin, `<title>Ürünler</title>` yerine `<title>Kadın Kol Saatleri | Marka Adı</title>` sayfanın içeriğini daha açıklayıcı şekilde ifade eder.

### İyi Bir Title Nasıl Olmalıdır?

Title:
- Sayfanın içeriğini doğru anlatmalı,
- Açıklayıcı olmalı,
- Gereksiz yere uzun olmamalı,
- Diğer sayfalardan ayırt edilebilir olmalı,
- Anahtar kelimelerle yapay şekilde doldurulmamalıdır.

Örneğin, `<title>HTML Formları | Frontend Notları</title>` anlaşılır bir title örneğidir.

### Title Uzunluğu
SEO kaynaklarında sıklıkla yaklaşık 50–60 karakter önerisiyle karşılaşılabilir. Ancak bu kesin bir HTML veya Google kuralı değildir.

Arama motorları başlığın tamamını göstermek zorunda değildir ve arama sonuçlarındaki görünüm kullanılan cihaza, sorguya ve mevcut alana göre değişebilir. Bu nedenle karakter sayısını ezberlemek yerine, `Kısa, açıklayıcı, sayfaya özgü ve kullanıcıya anlamlı bir title yazmak` daha doğru bir yaklaşımdır.

### Sık Yapılan Title Hataları
- Tüm sayfalarda aynı title kullanmak,
- Çok genel title yazmak,
- Gereksiz uzun title kullanmak,
- Anahtar kelimeleri tekrar tekrar yazmak,
- Sayfanın içeriğiyle uyuşmayan title kullanmak.

## Meta Descriptiom
Meta description, sayfanın içeriğini açıklayan kısa bir metadata bilgisidir.
```
    <meta name="description" content="HTML öğrenmeye başlayanlar için hazırlanmış temel frontend çalışma notları." >
```

Arama motorları bu açıklamayı arama sonuçlarında snippet oluştururken kullanabilir. Ancak yazdığımız description'ın arama sonucunda **her zaman aynen gösterileceğinin garantisi yoktur.**  Arama motoru kullanıcının yaptığı sorguya göre sayfadaki başka bir metni de açıklama olarak gösterebilir.

### İyi Bir Meta Description Nasıl Olmalıdır?
Description:
- Sayfanın içeriğini doğru özetlemeli,
- Kullanıcı açısından anlaşılır olmalı,
- Sayfaya özgü olmalı,
- Gereksiz tekrar içermemeli,
- Doğal bir dille yazılmalıdır.

Örneğin:
```
    <meta
        name="description"
        content="Semantic HTML, formlar, tablolar ve erişilebilirlik konularını içeren başlangıç seviyesi HTML notları."
    >
```

### Description Uzunluğu
SEO çalışmalarında yaklaşık 140–160 karakter gibi önerilerle karşılaşılabilir. Ancak bu kesin bir sınır değildir. Asıl amaç belirli bir karakter sayısını doldurmak değil, sayfanın içeriğini kısa ve doğru şekilde açıklamaktır.

### Anahtar Kelime Kullanımı
Description içerisinde anahtar kelimenin mutlaka belirli sayıda kullanılması gerektiği şeklinde bir kural yoktur. Şunun gibi doğal olmayan tekrarlar yapılmamalıdır:
```
    HTML öğren, HTML dersleri, HTML notları,
    HTML eğitimi, HTML başlangıç...
```
Bunun yerine doğal bir açıklama tercih edilmelidir.

## Robots Meta
Robots meta etiketi, arama motorlarına sayfanın indekslenmesi ve bağlantıların değerlendirilmesi konusunda direktifler vermek için kullanılabilir.

Örneğin:
```
    <meta
        name="robots"
        content="index, follow"
    >
```

### `index`
Sayfanın arama motorunun indeksine alınabilmesine izin verir.

`<meta name="robots" content="index">`

### `noindex`
Sayfanın arama sonuçlarında indekslenmemesini ister.

`<meta name="robots" content="noindex">`

Özellikle `noindex` dşkkatlı kullanılmalıdır. Önemli bir sayfada yanlışlıkla kullanılması sayfanın arama sonuçlarından çıkarılmasına neden olabilir.

### `follow`
Sayfadaki bağlantıların arama motorları tarafından takip edilebilmesine izin verir.

`<meta name="robots" content="follow">`

### `nofollow`
Sayfadaki bağlantıların takip edilmemesi yönünde direktif verir.

`<meta name="robots" content="nofollow">`

Birlikte de kullanılabilir.

`<meta name="robots" content="noindex, nofollow">`

## Canonical URL
### Canonical Nedir?
Aynı veya çok benzer içeriğe birden fazla URL üzerinden ulaşılabildiği durumlarda tercih edilen URL'yi belirtmeye yardımcı olmak için canonical kullanılabilir.
```
    <link
        rel="canonical"
        href="https://example.com/products/watch"
    >
```

Canonical bir `<meta>` etiketi değildir. `<link>` elementidir ve `<head>` içerisinde kullanılır.

### Canonical Neden Kullanılır?
Örneğin aşağıdaki URL'lerin aynı ürünü gösterdiğini düşünelim:
```
    /products/watch
    /products/watch?ref=instagram
    /products/watch?color=black
```
Benzer veya aynı içerik farklı URL'lerden erişilebilir durumda olabilir. Tercih edilen temel URL; `https://example.com/products/watch` ise sayfada `<link rel="canonical" href="https://example.com/products/watch">` kullanılabilir.

Bu, arama motoruna: `Bu içerik için tercih edilen URL budur.` bilgisini sağlar.

Canonical güçlü bir sinyaldir ancak arama motorunun bu URL'yi seçmesini yüzde yüz zorunlu hale getiren bir komut olarak düşünülmemelidir.

### Self-Referencing Canonical

Bir sayfanın canonical adresinin kendisini göstermesine **self-referencing canonical** denir.

Örneğin sayfanın adresi, `https://example.com/products/watch` ise <link rel="canonical" href="https://example.com/products/watch">` kullanılabilir. Bu yaklaşım canonical URL'nin açıkça belirtilmesini sağlar.

### Canonical URL Nasıl Yazılmalıdır?
Canonical için genellikle mutlak URL kullanılması tercih edilir:
```
    <link
        rel="canonical"
        href="https://example.com/products/watch"
    >
```
URL'nin sitenin gerçek URL yapısıyla tutarlı olması gerekir.

Örneğin:
```
    http / https
    www / non-www
    slash / non-slash
```
gibi URL farklılıklarında site genelinde tutarlı bir yapı bulunmalıdır.

### Canonical ve Redirect Aynı Şey Değildir
Canonical ile yönlendirme birbirinden farklıdır.
| Canonical     | Redirect      |
|---------------|---------------|
|Mevcut sayfa açık kalabilir | Kullanıcı başka URL'ye yönlendirilir |
|Tercih edilen URL hakkında arama motoruna sinyal verir | Tarayıcıya başka bir URL'ye gitmesini söyler|
|Benzer/duplicate URL durumlarında kullanılabilir | URL taşıma/değiştirme gibi durumlarda kullanılabilir |

Örneğin: Cannonical
```
    /products/watch?ref=instagram

        ↓ tercih edilen

    /products/watch
```
kullanıcı ilk URL'de kalabilir.

Redirect'te ise:
```
    /eski-url
        ↓
    301 Redirect
        ↓
    /yeni-url
```
tarayıcı yeni adrese gider.

### Backend'e Geçerken
Redirect ve HTTP durum kodları backend tarafında çok daha önemli hale gelir.

Örneğin:
```
    200 → Başarılı istek 
    301 → Kalıcı yönlendirme 
    302 → Geçici yönlendirme 
    404 → Kaynak bulunamadı
```

### Sık Yapılan Cannonical Hataları
- Tüm sayfalarda aynı canonical URL'yi kullanmak,
- Yanlış sayfayı canonical göstermek,
- HTTP/HTTPS tutarsızlığı,
- Yanlış domain kullanmak,
- URL yapısında tutarsızlık oluşturmak,
- Birbiriyle ilgisiz içerikleri canonical ile ilişkilendirmek.

## Sayfa Dili
### `lang`
Sayfanın temel dili `<html>` elementi üzerinde belirtilir.

Türkçe : `<html lang="tr">`
İngilizce : `<html lang="en">`

`lang` bir meta etiketi değildir. Sayfanın dilinin tarayıcılar ve yardımcı teknolojiler tarafından anlaşılmasına yardımcı olur ve erişilebilirlik açısından da önemlidir.

## Çok Dilli Sayfalarda `hreflang`
Aynı içeriğin farklı dil veya bölge sürümleri bulunuyorsa `hreflang` kullanılabilir.

Örneğin:
```
    <link rel="alternate" hreflang="tr" href="https://example.com/tr/" > 
    <link rel="alternate" hreflang="en" href="https://example.com/en/" >
```

Bu yapı arama motorlarının farklı dil sürümleri arasındaki ilişkiyi anlamasına yardımcı olur. `hreflang`, özellikle çok dilli veya çok bölgeli web sitelerinde önem kazanır. Bölgesel dil kodları, `<x-default>`, cannonical-hreflang ilişkileri gibi daha ileri kullanım senaryoları bulunmaktadır.

## Sosyal Medya Metadata
SEO Metadata ile sosyal medya paylaşım metadata'sı aynı amaçla kullanılmaz. Bir sayfa sosyal medya veya mesajlaşma platformlarında paylaşıldığında başlık, açıklama ve görsel içeren bir önizleme gösterilebilir. Bu bilgileri kontrol etmeye yardımcı olmak için farklı metadata standartları kullanılabilir.

### Open Graph
Open Graph metadata, bir sayfanın paylaşım önizlemesi hakkında bilgi sağlayabilir.

Temel örnek:
```
    <meta property="og:title" content="HTML Öğrenme Notları" > 
    <meta property="og:description" content="Frontend öğrenmeye başlayanlar için hazırlanmış HTML çalışma notları." > 
    <meta property="og:image" content="https://example.com/images/html-notlari.jpg" > 
    <meta property="og:url" content="https://example.com/html" > 
    <meta property="og:type" content="website" >
```

Buradaki temel özellikler:
```
    og:title → Paylaşım başlığı 
    og:description → Paylaşım açıklaması 
    og:image → Paylaşım görseli 
    og:url → İçeriğin URL'si 
    og:type → İçerik türü
```

Open Graph doğrudan bir Google ranking etiketi olarak düşünülmemelidir. Temel amacı paylaşım önizlemelerine metadata sağlamaktır.

### Twitter / X Card
Twitter/X üzerinde paylaşım önizlemeleri için Card metadata kullanılabilir.

Örneğin:
```
    <meta name="twitter:card" content="summary_large_image" > 
    <meta name="twitter:title" content="HTML Öğrenme Notları" > 
    <meta name="twitter:description" content="Frontend öğrenmeye başlayanlar için HTML çalışma notları." > 
    <meta name="twitter:image" content="https://example.com/images/html-notlari.jpg" >
```

Burada temel amaç sosyal medya paylaşımının nasıl sunulacağı hakkında platforma bilgi sağlamaktır.

## Favicon
Favicon, web sitesini temsil eden küçük simgedir. Tarayıcı sekmelerinde ve bazı diğer arayüzlerde kullanılabilir.

Örneğin:
```
    <link rel="icon" href="/favicon.ico">
```
PNG gibi farklı formatlar da kullanılabilir:
```
    <link rel="icon" type="image/png" href="/favicon.png">
```

Favicon bir meta etiketi değildir; `<link>` elementi kullanılarak tanımlanır.

## SEO'da Yanlış Anlaşılan Meta Etiketleri
Her `<meta>` etiketi Google sıralamasını etkileyen bir SEO etiketi değildir.

### Meta Keywords
Eskiden anahtar kelimeleri belirtmek amacıyla kullanılan:
```
    <meta
        name="keywords"
        content="html, css, javascript"
    >
```

Google web arama sıralamasında meta keywords bilgisini kullanmaz. Bu nedenle modern Google SEO çalışmaları için gerekli bir etiket olarak değerlendirilmemelidir.

### Author
```
    <meta
        name="author"
        content="Büşra Öztürk"
    >
```
sayfanın yazarı hakkında metadata sağlayabilir.

Ancak bunu `Google sıralamamı yükselten SEO etiketi` olarak değerlendirmek doğru değildir. Bir metadata bilgisinin anlamlı olması ile doğrudan ranking faktörü olması aynı şey değildir.

### Generator
Bazı sistemler sayfanın hangi yazılım tarafından oluşturulduğunu belirtmek için:
```
    <meta
        name="generator"
        content="..."
    >
```
kullanabilir. Bu da doğrudan SEO sıralaması sağlayan bir meta etiketi değildir.

### `http-equiv="refresh"`
Şu yapı:
```
    <meta
        http-equiv="refresh"
        content="5;url=https://example.com"
    >
```
belirli bir süre sonra başka sayfaya geçiş yapmak için kullanılabilir. Ancak URL yönlendirmelerinde genel olarak uygun HTTP redirect yöntemleri tercih edilmelidir.

## Structured Data / Schema Bu Konunun Neresinde?
Structured Data, meta etiketlerinden farklı bir konudur. Arama motorlarına sayfadaki içeriğin türü ve özellikleri hakkında yapılandırılmış bilgi sağlamaya yardımcı olur.

Örneğin:
```
    Product
    Article
    Breadcrumb
    Organization
    Event
```
gibi içerikler için structured data kullanılabilir.

Modern web uygulamalarında sıkça **JSON-LD** formatıyla karşılaşılır.

Örneğin genel görünümü:
```
    <script type="application/ld+json">
    {
        ...
    }
    </script>
```
şeklindedir.

Ancak Structured Data; `Meta tag konusu değildir.` Kendi kuralları ve kullanım senaryoları bulunduğu için **Structured Data / Schema.org / JSON-LD** başlığı altında ayrıca incelenmesi daha doğrudur.

## Temel SEO ve Metadata Hataları
HTML tarafında sık karşılaşılan hatalar şunlardır:

### Tüm sayfalarda aynı title kullanmak

`<title>Web Sitesi</title>` yerine sayfanın içeriğini açıklayan farklı title'lar kullanılmalıdır.

### Meta description'ı tüm sayfalarda kopyalamak
Her sayfanın içeriğine uygun açıklama oluşturmak daha doğru bir yaklaşımdır.

### Yanlışlıkla `noindex` kullanmak
```
    <meta
        name="robots"
        content="noindex"
    >
```
önemli bir sayfada kullanılırsa sayfanın arama sonuçlarında bulunmasını engelleyebilir.

### Bütün sayfalarda aynı canonical kullanmak
Her sayfanın canonical yapısı gerçek URL ve içerik ilişkisine göre oluşturulmalıdır.

### Meta keywords'e gereğinden fazla önem vermek
```
    <meta
        name="keywords"
        content="..."
    >
```
modern Google web arama sıralaması için gerekli değildir.

### SEO amacıyla anahtar kelimeleri tekrar etmek
Metadata kullanıcı ve sayfa içeriği düşünülerek doğal biçimde yazılmalıdır.

### Sosyal medya metadata'sını SEO ranking faktörü sanmak
Open Graph ve Twitter/X Card'ın temel amacı sosyal medya paylaşım önizlemeleridir.

## Tam Bir `<head>` Örneği
Şimdi öğrendiğimiz temel yapıları bir araya getirelim:
```
<!DOCTYPE html> 
<html lang="tr"> 
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title> HTML Öğrenme Notları | Frontend </title>
        <meta name="description" content="HTML öğrenmeye başlayanlar için hazırlanmış temel frontend çalışma notları">
        <meta name="robots" content="index, follow">
        <link rel="canonical" href="https://example.com/html">
        <link rel="icon" href="/favicon.ico">

        <!-- Open Graph --> 
        <meta property="og:title" content="HTML Öğrenme Notları"> 
        <meta property="og:description" content="Frontend öğrenmeye başlayanlar için hazırlanmış HTML çalışma notları.">
        <meta property="og:image" content="https://example.com/images/html-notlari.jpg"> 
        <meta property="og:url" content="https://example.com/html"> 
        <meta property="og:type" content="website">

        <!-- Twitter / X --> 
        <meta name="twitter:card" content="summary_large_image"> 
        <meta name="twitter:title" content="HTML Öğrenme Notları"> 
        <meta name="twitter:description" content="Frontend öğrenmeye başlayanlar için HTML çalışma notları."> 
        <meta name="twitter:image" content="https://example.com/images/html-notlari.jpg">
    </head>
    <body> 
        <h1>HTML Öğrenme Notları</h1> 
    </body>
</html>
```

Bu örnekte bütün metadata'nın aynı amaçla kullanılmadığına dikkat etmek gerekir:

```
    charset → Karakter kodlaması 
    viewport → Mobil görüntüleme 
    title → Sayfa başlığı 
    description → Sayfa açıklaması 
    robots → Arama motoru direktifleri 
    canonical → Tercih edilen URL 
    favicon → Site simgesi 
    Open Graph → Paylaşım metadata'sı Twitter / X Card ↓ Platform paylaşım metadata'sı
```

## Kısa Kontrol Listesi
Bir HTML sayfasının `<head>` bölümünü hazırlarken temel olarak şunları kontrol edebiliriz:
- `<html>` üzerinde doğru lang değeri var mı?
- `charset="UTF-8" `tanımlandı mı?
- Viewport tanımlandı mı?
- Sayfaya özgü ve anlamlı `<title>` var mı?
- Gerekliyse sayfaya özgü meta description var mı?
- Robots direktifleri doğru mu?
- Canonical URL doğru mu?
- Çok dilli yapı varsa `hreflang` doğru mu?
- Favicon tanımlandı mı?
- Sosyal paylaşım önemliyse Open Graph bilgileri mevcut mu?
- Gerekiyorsa Twitter/X Card bilgileri mevcut mu?
- Metadata içerisinde gereksiz anahtar kelime tekrarları var mı?
- Sayfanın metadata bilgileri gerçek içeriği doğru şekilde temsil ediyor mu?

## Kısaca
HTML metadata yalnızca SEO'dan ibaret değildir. `<head>` içerisinde tarayıcı, arama motoru ve sosyal platformlar için farklı amaçlara hizmet eden bilgiler bulunabilir. Temel ilişkiyi şöyle düşünebiliriz:
```
    <head>
    │
    ├── Tarayıcı
    │   ├── charset
    │   ├── viewport
    │   └── favicon
    │
    ├── Sayfa Bilgisi
    │   ├── title
    │   └── description
    │
    ├── Arama Motorları
    │   ├── robots
    │   ├── canonical
    │   └── hreflang
    │
    └── Sosyal Platformlar
        ├── Open Graph
        └── Twitter / X Card
```

Bu konunun temel prensibi şudur:
`Metadata'yı yalnızca arama motorları için değil; sayfanın ne olduğunu, nasıl yorumlanması gerektiğini ve farklı sistemlerde nasıl temsil edileceğini açıklayan HTML bilgisinin bir parçası olarak düşünmeliyiz.`