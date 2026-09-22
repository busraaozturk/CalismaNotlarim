# OPEN GRAPH (OG)
## Open Graph Nedir?
**Open Graph(OG),** bbir web sayfası başka bir platformda paylaşıldığında sayfa hakkında yapılandırılmış bilgiler sağlayan bir metadata protokolüdür.

Örneğin bir bağlantı paylaşıldığında:
```
    Başlık
    Açıklama
    Görsel
    URL
    İçerik Türü
```
gibi bilgilerin tanımlanmasına yardımcı olur.

Open Graph etiketleri HTML belgesinin `<head>` bölümüne yazılır. Temel bir örnek:
```
    <head> 
        <meta property="og:title" content="HTML Öğrenme Notları"> 
        <meta property="og:description" content="Frontend öğrenmeye başlayanlar için hazırlanmış HTML çalışma notları."> 
        <meta property="og:image" content="https://example.com/images/html-notlari.jpg"> 
        <meta property="og:url" content="https://example.com/html"> 
        <meta property="og:type" content="website"> 
    </head>
```

Open Graph, ilk olarak Facebook tarafından geliştirilmiştir ve günümüzde web sayfalarının paylaşım metadata'sını tanımlamak amacıyla yaygın şekilde kullanılmaktadır.

## Open Graph Neden Kullanılır?
Bir bağlantının paylaşım önizlemesi oluşturulurken platformların sayfa hakkında bilgi edinmesi gerekir. Open Graph sayesinde geliştirici sayfa hakkında açık metadata sağlayabilir.

Örneğin:
```
    Web Sayfası 
        │ 
        ▼ 
    <head> 
        │ 
        ├── og:title 
        ├── og:description 
        ├── og:image 
        ├── og:url 
        └── og:type 
        │ 
        ▼    
    Paylaşım Platformu 
        │ 
        ▼ 
    Bağlantı Önizlemesi
```

Open Graph kullanılmadığında platform, paylaşım için gerekli bilgileri sayfanın diğer bölümlerinden çıkarmaya çalışabilir. Bu nedenle Open Graph kullanmak, paylaşım bilgilerinin daha kontrollü tanımlanmasını sağlar.

## Open Graph ve SEO İlişkisi
Open Graph'ın temel amacı **arama motoru sıralaması değil, paylaşım metadata'sıdır.**

Bu nedenle:
```
    <title>
    <meta name="description">
            ↓
    Arama sonucu ve sayfa metadata'sı
```
ile:
```
    og:title
    og:description
    og:image
        ↓
    Sosyal/paylaşım önizlemesi
```
aynı şey değildir.

Open Graph etiketleri doğrudan Google sıralamasını yükselten SEO etiketleri olarak düşünülmemelidir. Ancak iyi hazırlanmış paylaşım bilgileri bağlantının kullanıcıya daha anlaşılır ve düzenli sunulmasına yardımcı olabilir.

`Open Graph = paylaşım metadata'sı`

## Temel Open Graph Özellikleri
Open Graph protokolünün temel özellikleri şunlardır:
```
    Open Graph 
    │ 
    ├── og:title 
    ├── og:type 
    ├── og:image 
    └── og:url
```

Bunlara ek olarak uygulamalarda sıklıkla:
```
    og:description 
    og:site_name 
    og:locale
```
gibi özelliklerle de karşılaşılır.

## `og:title`
`og:title`, içeriğin paylaşım başlığını belirtir.
```
    <meta property="og:title" content="HTML Öğrenme Notları" >
```
Örneğin sayfanın HTML title'ı:
```
    <title>HTML Öğrenme Notları | Frontend Çalışmaları</title>
```

iken Open Graph başlığı:
```
    <meta property="og:title" content="HTML Öğrenme Notları" >
```
olabilir.

### `og:title`ve `<title>` Aynı mı?
Hayır. İkisi benzer bilgiler içerebilse de farklı amaçlara hizmet eder.
```
    <title> → HTML belgesinin başlığı 
    og:title → İçeriğin Open Graph başlığı
```
Aynı metni kullanmaları mümkündür ancak zorunlu değildir.

### İyi Bir `og:title`
Başlık:
- İçeriği doğru açıklamalı,
- Anlaşılır olmalı,
- Gereksiz şekilde uzun olmamalı,
- Yanıltıcı olmamalıdır.

Kesin bir karakter sayısını ezberlemek yerine paylaşım ortamında anlaşılır ve kısa bir başlık oluşturmak daha doğru bir yaklaşımdır.

## `og:description`
`og:description`, paylaşılan içeriğin kısa açıklamasını belirtir.
```
    <meta
        property="og:description"
        content="Frontend öğrenmeye başlayanlar için hazırlanmış HTML çalışma notları."
    >
```
Kullanıcıya bağlantının içeriği hakkında kısa bilgi vermek amacıyla kullanılabilir.

### İyi Bir `og:description`
Açıklama:
- İçeriği doğru özetlemeli,
- Kısa ve anlaşılır olmalı,
- Gereksiz anahtar kelime tekrarları içermemeli,
- Yanıltıcı olmamalıdır.

Burada da kesin bir karakter sınırını kural olarak kabul etmek yerine içeriğin doğru ve anlaşılır biçimde açıklanmasına odaklanmak daha uygundur.

## `og:image`
`og:image`, içerikle ilişkilendirilen paylaşım görselini belirtir.
```
    <meta
        property="og:image"
        content="https://example.com/images/html-notlari.jpg"
    >
```
Paylaşım kartının en dikkat çekici bölümlerinden biri genellikle görseldir. Bu nedenle kullanılan görsel:
- İçerikle ilgili olmalı,
- Yeterli kalitede olmalı,
- İnternet üzerinden erişilebilir olmalı,
- Uygun en-boy oranına sahip olmalıdır.

### Görsel URL'si
Görsel için tam URL kullanılması güvenli ve taşınabilir bir yaklaşımdır.

Örneğin:
```
    <meta
        property="og:image"
        content="https://example.com/images/html-notlari.jpg"
    >
```
Bu kullanım:
```
    <meta
        property="og:image"
        content="/images/html-notlari.jpg"
    >
```
gibi relative bir adres kullanmaktan daha açıktır.

### `og:image:width` ve `og:image:height`
Görselin genişlik ve yükseklik bilgileri ayrıca belirtilebilir.
```
    <meta
        property="og:image:width"
        content="1200"
    >

    <meta
        property="og:image:height"
        content="630"
    >
```
Bu metadata, görsel hakkında platforma ek bilgi sağlar. `1200 × 630` gibi boyutlarla uygulamada sık karşılaşılabilir ancak bunu Open Graph protokolünün bütün platformlar için zorunlu tek boyutu olarak düşünmemek gerekir. Hedeflenen platformun güncel görsel gereksinimleri ayrıca kontrol edilmelidir.

### `og:image:alt`
Görsel için alternatif açıklama bilgisi sağlanabilir.
```
    <meta
        property="og:image:alt"
        content="HTML çalışma notlarını gösteren kapak görseli"
    >
```
Bu açıklama görselin neyi temsil ettiğini ifade etmelidir.

### Görsel İçin Ek Özellikler
Gerekli durumlarda görsel hakkında başka bilgiler de tanımlanabilir. 

Örneğin: `<meta propert="og:image:type" content="image/jpeg">`

Böylece Open Graph görselinin türü hakkında ek bilgi sağlanabilir.

## `og:url`
`og:url`, Open Graph nesnesinin URL'sini belirtir.
```
    <meta
        property="og:url"
        content="https://example.com/html"
    >
```
Örneğin kullanıcı şu adres üzerinden sayfaya gelmiş olabilir: `https://example.com/html?utm_source=social`

Ancak sayfanın temel adresi: `https://example.com/html`

ise Open Graph URL'si buna göre tanımlanabilir: `<meta property="og:url" content="https://example.com/html">`

## `og:url` ve Canonical Aynı Şey mi?
Hayır. Benzer URL mantıklarıyla karşılaşılabilse de farklı sistemlere hizmet ederler.
```
    canonical → Arama motorlarına tercih edilen URL hakkında sinyal verir.
    
    og:url → Open Graph nesnesinin URL'sini tanımlar.
```
Örneğin:
```
    <link
        rel="canonical"
        href="https://example.com/html"
    >

    <meta
        property="og:url"
        content="https://example.com/html"
    >
``` 
Çoğu standart sayfada bunların aynı temel URL'yi göstermesi mantıklı olabilir. Ancak kavramsal olarak birbirlerinin yerine geçmezler.

## `og:type`
`og:type`, içeriğin türünü belirtir. Temel bir web sayfası için; `<meta property="og:type" content="website">` kullanılabilir.

Farklı içerik türlerinde farklı Open Graph türleriylr karşılaşılabilir. Örneğin:
```
    website 
    article 
    profile 
    video.* 
    music.*
```
`og:type` seçilirken gerçek içeriğin türüne uygun değer kullanılmalıdır.

## Article İçerikleri
Bir blog yazısı veya makale gibi içerikte, `<meta property="og:type" content="article">` kullanılabilir. Article türüne özel ek özellikler de bulunur.

Örneğin:
```
    <meta property="article:published_time" content="2026-09-22T10:00:00+03:00">
    <meta property="article:modified_time" content="2026-09-22T14:30:00+03:00">
    <meta property="article:author" content="https://example.com/authors/example">
    <meta property="article:section" content="Frontend">
    <meta property="article:tag" content="HTML">
```
Bunlar her web sayfasında kullanılacak özellikler değildir. İçerik gerçekten article türündeyse değerlendirilmelidir.

## `og:site_name`
`og:site_name`, içeriğin ait olduğu sitenin adını belirtmek için kullanılabilir.
```
    <meta property="og:site_name" content="Frontend Notları">
```
Burada:
```
    og:title → İçeriğin başlığı
    og:site_name → İçeriğin bulunduğu sitenin adı
```
şeklinde bir ayrım vardır.

## `og:locale`
`og:locale`, içeriğin dil ve bölge bilgisini belirtmek için kullanılabilir.

Örneğin:
```
    <meta property="og:locale" content="tr_TR">
```

İngilizce ABD içeriği için:
```
    <meta property="og:locale" content="en_US">
```

Genel yapı `dil_BÖLGE` şeklindedir.

### Alternatif Diller
İçeriğin başka dil/bölge sürümleri bulunuyorsa, `<meta property="og:locale:alternate" content="en_US">` gibi alternatif locale bilgileri de sağlanabilir.

Birden fazla alternatif varsa özellik birden fazla kez kullanılabilir.
```
    <meta property="og:locale:alternate" content="en_US">
    <meta property="og:locale:alternate" content="de_DE">
```

## Video ve Ses İçerikleri
Open Graph yalnızca metin ve görsel metadata'sından oluşmaz. Video ve ses içerikleri için de özellikler bulunmaktadır.

### Video

Örneğin:
```
    <meta property="og:video" content="https://example.com/video.mp4">
    <meta property="og:video:type" content="video/mp4">
    <meta property="og:video:width" content="1280">
    <meta property="og:video:height" content="720">
```

### Audio
Ses içeriği için, `<meta property="og:audio" content="https://example.com/audio.mp3">` gibi özelliklerle karşılaşılabilir. Bunlar temel web sayfalarının tamamında gerekli değildir. İçerik türüne göre kullanılır.

## Open Graph Nasıl Çalışır?
Genel mantığı şu şekilde düşünebiliriz:
```
Kullanıcı bir URL paylaşır
          │
          ▼
Platform URL'yi inceler
          │
          ▼
HTML belgesini alır
          │
          ▼
<head> içerisindeki
Open Graph metadata'sını okur
          │
          ▼
Başlık / açıklama / görsel
gibi bilgileri değerlendirir
          │
          ▼
Paylaşım önizlemesi oluşturulur
```

Burada önemli bir nokta vardır, `Open Graph metadata'sını yazmak, her platformun paylaşım kartını tamamen aynı şekilde göstereceği anlamına gelmez.` Platformlar kendi görüntüleme kurallarını uygulayabilir.

## Cache Mantığı
Paylaşım platformları bir URL'yi her görüntülemede yeniden okumak yerine daha önce elde ettikleri bilgileri bir süre saklayabilir. Buna `cache` denir.

Örneğin:
```
    <meta property="og:image" content="https://example.com/images/old.jpg">
```
daha sonra:
```
    <meta property="og:image" content="https://example.com/images/new.jpg">
```
olarak değiştirilmiş olsun.

Kod doğru olmasına rağmen platform bir süre, `old.jpg` görselini göstermeye devam edebilir.

Bu durumda sorun her zaman HTML kodundan kaynaklanmaz; platformun önceden aldığı metadata'yı önbellekte tutması da sebep olabilir.

## Twitter / X Card ve Open Graph
Twitter/X için ayrıca Card metadata'sı ile karşılaşabiliriz.

Örneğin:
```
    <meta name="twitter:card"content="summary_large_image">
    <meta name="twitter:title" content="HTML Öğrenme Notları">
    <meta name="twitter:description" content="Frontend öğrenmeye başlayanlar için HTML çalışma notları.">
    <meta name="twitter:image" content="https://example.com/images/html-notlari.jpg">
```
Burada önemli fark syntax'ta da görülebilir.

Open Graph:
```
    <meta property="og:title" content="HTML Öğrenme Notları">
```

Twitter/X Card:
```
    <meta name="twitter:title" content="HTML Öğrenme Notları">
```

Yani:
```
    Open Graph
    property="og:*"

    Twitter/X Card
    name="twitter:*"
```
şeklinde farklı metadata yapılarıyla karşılaşırız. Platformların hangi fallback davranışlarını kullandığı zaman içinde değişebileceğinden, uygulama geliştirirken ilgili platformun güncel dokümantasyonu kontrol edilmelidir.

## `twitter:card`
Kart türünü belirtir.

Örneğin: `<meta name="twitter:card" content="summary_large_image">`

Yaygın kart türlerinden bazıları:
```
    summary
    summary_large_image
    player
    app
```

Her kart türünün kullanım amacı ve gereksinimleri farklı olabilir.

## Twitter/X İçin Diğer Metadata

### twitter:title

`<meta name="twitter:title" content="HTML Öğrenme Notları">`

### twitter:description
`<meta name="twitter:description" content="Frontend öğrenmeye başlayanlar için HTML çalışma notları.">`

### twitter:image
`<meta name="twitter:image" content="https://example.com/images/html-notlari.jpg">`
 
Projede Twitter/X paylaşım önizlemeleri önemliyse platformun güncel Card dokümantasyonu üzerinden desteklenen özellikler ayrıca kontrol edilmelidir.

## Open Graph ve Twitter/X Card Aynı Şey mi?
Hayır. İkisi farklı metadata sistemleridir.
```
    Paylaşım Metadata'sı
    │
    ├── Open Graph
    │   ├── og:title
    │   ├── og:description
    │   ├── og:image
    │   ├── og:url
    │   └── og:type
    │
    └── Twitter / X Card
        ├── twitter:card
        ├── twitter:title
        ├── twitter:description
        └── twitter:image
```
Bir projede ikisinin birlikte kullanılması mümkündür.

## Open Graph ve Schema Aynı Şey mi?
Hayır. Open Graph ile Structured Data / Schema farklı amaçlara sahiptir.

| Yapı              | Temel Amaç        |
|-------------------|-------------------|
|`<title>`          | HTML belgesinin başlığı| 
|Meta description   | Sayfa hakkında açıklayıcı metadata |
|Open Graph         | Paylaşım metadata'sı|
|Twitter/X Card     | X/Twitter paylaşım metadata'sı|
|Structured Data    | İçeriğin yapısını makine tarafından anlaşılabilir şekilde ifade etmek|

Örneğin Open Graph, `<meta property="og:type" content="website">` kullanabilir.

Structured Data ise genellikle:
```
    <script type="application/ld+json">
    {
        ...
    }
    </script>
```
şeklinde JSON-LD ile karşımıza çıkabilir.

Birbirlerinin yerine kullanılmazlar. Structured Data ayrı bir konu olarak incelenmelidir.

## Open Graph ve Canonical Aynı Şey mi?
Bu kavramlar da birbirinden ayrılmalıdır.
```
    Canonical → Tercih edilen URL hakkında arama motorlarına sinyal
    Open Graph → Paylaşım metadata'sı
    Structured Data → İçeriğin yapısal anlamı
```
Örneğin aynı sayfada:
```
    <link rel="canonical" href="https://example.com/html">
    <meta property="og:url" content="https://example.com/html">
```
birlikte bulunabilir.

## Open Graph Kullanırken Sık Yapılan Hatalar
### Open Graph Etiketlerini Sadece Ana Sayfada Kullanmak
İçerik sayfalarının paylaşım bilgileri farklı olabilir.

Örneğin:
```
    Ana Sayfa → Ana sayfaya ait başlık/görsel
    Blog Yazısı → Yazıya ait başlık/görsel
    Ürün Sayfası → Ürüne ait başlık/görsel
```
Bu nedenle metadata sayfanın gerçek içeriğine uygun oluşturulmalıdır.

### og:image İçin Erişilemeyen Görsel Kullanmak
Paylaşım platformunun görsele ulaşabilmesi gerekir.

Görsel:
- Hatalı URL'ye sahip olmamalı,
- Yetkilendirme arkasında olmamalı,
- Sunucudan erişilebilir olmalıdır.

### Çok Küçük veya Uygun Olmayan Görsel Kullanmak
Görselin hedeflenen platform tarafından düzgün işlenebilecek boyut ve formatta olması gerekir. Platformların gereksinimleri farklılaşabileceği için uygulama sırasında güncel dokümantasyon kontrol edilmelidir.

### `og:title` ile `<title>` Kavramlarını Karıştırmak
```
    <title> ≠ og:title
```
Aynı metni kullanabilirler ancak aynı HTML özelliği değildirler.

### `og:url` ile Canonical'ı Aynı Şey Sanmak
```
    og:url ≠ canonical
```
Ama standart bir sayfada aynı temiz URL'yi göstermeleri çoğu zaman mantıklıdır.

### Değişiklikten Sonra Cache'i Unutmak
Kod güncellenmesine rağmen eski paylaşım önizlemesi görünüyorsa cache ihtimali de kontrol edilmelidir.

## Tam Bir Open Graph Örneği
Bir web sayfasında temel yapı şu şekilde olabilir:
```
    <!DOCTYPE html> 
    <html lang="tr">
    
    <head>
        <meta charset="UTF-8"> 
        <meta name="viewport" content="width=device-width, initial-scale=1.0" > 
        <title> HTML Öğrenme Notları | Frontend </title>
        <meta name="description" content="Frontend öğrenmeye başlayanlar için hazırlanmış HTML çalışma notları."> 
        <link rel="canonical" href="https://example.com/html">

        <!-- Open Graph --> 
        <meta property="og:title" content="HTML Öğrenme Notları"> 
        <meta property="og:description" content="Frontend öğrenmeye başlayanlar için hazırlanmış HTML çalışma notları."> 
        <meta property="og:image" content="https://example.com/images/html-notlari.jpg"> 
        <meta property="og:image:width" content="1200"> 
        <meta property="og:image:height" content="630"> 
        <meta property="og:image:alt" content="HTML çalışma notları kapak görseli"> 
        <meta property="og:url" content="https://example.com/html"> 
        <meta property="og:type" content="website"> 
        <meta property="og:site_name" content="Frontend Notları"> 
        <meta property="og:locale" content="tr_TR">

        <!-- Twitter / X Card --> 
        <meta name="twitter:card" content="summary_large_image"> 
        <meta name="twitter:title" content="HTML Öğrenme Notları"> 
        <meta name="twitter:description" content="Frontend öğrenmeye başlayanlar için hazırlanmış HTML çalışma notları."> 
        <meta name="twitter:image" content="https://example.com/images/html-notlari.jpg">
    </head>

    <body>
        <main>
            <h1>HTML Öğrenme Notları</h1>
        </main>
    </body>
    </html>
```

## Kısa Kontrol Listesi
Open Graph eklerken temel olarak şunlar kontrol edilebilir:
- `og:title` içeriği doğru mu?
- `og:description` sayfayı doğru açıklıyor mu?
- `og:image` doğru ve erişilebilir mi?
- Görsel URL'si açık ve geçerli mi?
- `og:url` doğru sayfayı gösteriyor mu?
- `og:type` içerik türüne uygun mu?
- Gerekliyse `og:site_name` kullanıldı mı?
- Gerekliyse `og:locale` tanımlandı mı?
- Görsel için `og:image:alt` düşünüldü mü?
- Sayfanın Open Graph bilgileri diğer sayfalardan gerektiğinde farklılaşıyor mu?
- Paylaşım önizlemesi hedeflenen platformlarda test edildi mi?
- Değişiklik sonrası eski önizleme görünüyorsa cache kontrol edildi mi?

## Kısa Özet
Open Graph'ın temel mantığı:
```
    Web Sayfası
        │
        ▼
    Open Graph Metadata
        │
        ├── og:title
        ├── og:description
        ├── og:image
        ├── og:url
        └── og:type
        │
        ▼
    Paylaşım Platformu
        │
        ▼
    Bağlantı Önizlemesi
```
En önemli ayrım ise şudur:
```
    HTML Metadata 
    │ 
    ├── title / description 
    │   └── Sayfa hakkında temel metadata 
    │ 
    ├── canonical 
    │   └── Tercih edilen URL 
    │ 
    ├── Open Graph 
    │   └── Paylaşım metadata'sı 
    │ 
    ├── Twitter / X Card 
    │   └── Platforma özel paylaşım metadata'sı 
    │ 
    └── Structured Data 
        └── İçeriğin yapısal anlamı
```

Open Graph öğrenirken amaç bütün özellikleri ezberlemek değil; **Bir web sayfasının başka bir platformda paylaşılırken hangi bilgileri sunacağını kontrollü ve anlamlı biçimde tanımlayabilmeyi öğrenmektir.**













## Neden SEO ile Birlikte Düşünülür?
- Paylaşım kartı düzgün görünürse
- Kullanıcı daha çok tıklar (CTR artar)
- Sayfaya daha fazla trafik gelir
- Bu da Google'a olumlu kullanıcı sinyali gönderir.

Dolaylı Seo etkisi buradan gelir.

**Önemli:** Open Graph, Google sıralamasını (ranking) doğrudan etkileyen bir faktör değildir. Google bu etiketleri "sıralama sinyali" olarak kullanmaz. 
**Etkisi tamamen dolaylıdır**; daha iyi görünen bir kart → daha çok tıklama → daha çok trafik ve paylaşım. Bunu net ayırmak önemli, çünkü bazı kaynaklar OG'yi doğrudan bir SEO faktörüymüş gibi anlatır, bu yanlıştır.

## Open Graph Meta Tag'leri Tek Tek Açıklama
### **Og:title** : Paylaşım başlığı
- Paylaşıldığında kalın büyük başlık olarak görünür
- Kısa - Markalı - Net
- İdeal uzunluk 40-60 karakter
- `<title>` etiketiyle aynı olmak zorunda değildir; sosyal medya için ayrı, daha "tıklanabilir" bir başlık yazılabilir

### **Og:description** : Alt açıklama
- Başlığın altında çıkan gri küçük metin
- Kullanıcıya "Bu link ne anlatıyor?" sorusunun cevabı
- İdeal uzunluk 110 - 160 karakter
- Reklam gibi değil net ve güven veren bir dil kullanılmalı

### **Og:image** : Paylaşım görseli
- Görsel Kuralları:
    - 1200 x 630px ideal
    - Jpg veya png (webp bazı platformlarda sorun çıkarabilir)
    - Https olmalı - Http bazeb yüklenmez
    - Sunucuda herkesin erişebileceği url (login gerektiren bir sayfadaki görsel çalışmaz)
    - Küçük görsel kırpılır veya hiç gösterilmeyebilir (minimum 200x200px, ama 600x315px altı önerilmez)
    - Relative path (örn: /images/og.jpg) çoğu platformda görünmez, mutlaka tam url (https://site.com/images/og.jpg) yazılmalı
    - Dosya boyutu mümkünse 1MB altında tutulmalı, bazı platformlar büyük dosyaları reddeder
    - Ek olarak şu etiketler de eklenebilir:
    ```
        <meta property="og:image:width" content="1200" />
        <meta property="og:image:height" content="630" />
        <meta property="og:image:alt" content="Görselin açıklaması" />
    ```
    - og:image:width/height yazılmazsa, bazı platformlar görseli indirip boyutunu kendi hesaplamak zorunda kalır; bu da kartın bazen geç veya hatalı görünmesine sebep olabilir.

### **Og:url** : Paylaşılan link
- Sosyal medya şunu sorar; "Bu içerik hangi sayfaya ait?"
- Cannonical gibi düşün:
    - Aynı içerik farklı Url'lerde varsa (örn. ?utm_source=... gibi parametrelerle)
    - Asıl (temiz) url'yi belirtir
- Bu sayede paylaşım sayısı (like/share count) tüm varyasyonlar için tek url'de toplanır, dağılmaz

### **Og:type** : İçerik türü
- "Bu sayfa ne tür bir içerik?" sorusunun cevabı

| **Tür**          | **Nerede**          |
|------------------|---------------------|
| website          | Ana sayfa, kategori |
| article          | Blog yazısı         |
| product          | Ürün sayfası        |
| profile          | Kişi profili        |
| video.other      | Video içerikleri    |
| music.song       | Müzik içerikleri    |

- og:type "article" seçilirse, ek olarak şu etiketler de kullanılabilir:

```
    <meta property="article:published_time" content="2026-06-01T10:00:00+03:00" />
    <meta property="article:modified_time" content="2026-06-15T14:30:00+03:00" />
    <meta property="article:author" content="Yazar Adı" />
    <meta property="article:section" content="Teknoloji" />
    <meta property="article:tag" content="seo, open graph" />
```

### **Og:site_name** : Marka adı
- Kartta bazen:
    - `Kaynak:TestSitesi` şeklinde görünür
- Güven hissi verir
- Marka bilinirliği sağlar

### **Og:locale** : Dil / bölge bilgisi (sık unutulan bir etiket)
```
    <meta property="og:locale" content="tr_TR" />
```
- Sayfanın hangi dilde / bölgede olduğunu belirtir.
- Format: dil_ÜLKE (örn: tr_TR, en_US)
- Site birden fazla dilde yayın yapıyorsa og:locale:alternate ile diğer diller de belirtilebilir:
```
    <meta property="og:locale:alternate" content="en_US" />
```

### **og:video / og:audio** — Video ve ses içerikleri (opsiyonel)
- Sayfa bir video veya ses barındırıyorsa, bunu doğrudan oynatılabilir şekilde kart içine gömmek için kullanılır:
```
    <meta property="og:video" content="https://site.com/video.mp4" />
    <meta property="og:video:type" content="video/mp4" />
    <meta property="og:video:width" content="1280" />
    <meta property="og:video:height" content="720" />
```

### **fb:app_id** (Facebook özelinde, opsiyonel)
- Facebook'ta paylaşım analitiklerini (insights) görebilmek için bazen istenir:
```
    <meta property="fb:app_id" content="1234567890" />
```
- Zorunlu değildir, sadece Facebook üzerinden detaylı istatistik takibi isteyenler için önemlidir.

## Instagram - Facebook - Whatsapp Farkı Var Mı? 
- Ayrı ayrı meta yazılmaz, open graph (og) meta tag'larını kullanır.
- Hepsi og okur
    - **Facebook:** Open Graph
    - **Instagram:** Facebook altyapısını, yani og'yi kullanır (Instagram linklerde tıklanabilir kart göstermez ama Story/DM paylaşımlarında ve bio linklerde og bilgisi kullanılır)
    - **WhatsApp / LinkedIn / Messenger:** Facebook OG kullanır
    - **Hepsi için yeterli:** <meta property="og:*" />
- Teknik olarak fark yok, görsel sunum farkı var

| **Konu**          | **Facebook**          | **Instagram**          |
|-------------------|-----------------------|------------------------|
| Meta standardı    | Open Graph            | Open Graph             |
| Görsel önceliği   | Yüksek                | Çok yüksek             |
| Description       | Görünür               | Çoğu zaman kısaltılır  |
| Cache             | Var                   | Var                    |

### Twitter için:
- Twitter og'yi okur
- Ama kendi etiketleriyle daha iyi render eder

```
    <meta name="twitter:card" content="summary_large_image" />
    <meta name="twitter:title" content="Ahlatcı Kuyumculuk | Altın & Pırlanta" />
    <meta name="twitter:description" content="Altın, pırlanta ve özel tasarım takılar." />
    <meta name="twitter:image" content="https://www.ahlatcistore.com.tr/images/og-home.jpg" />
```

## Facebook & Instagram Open Graph Nasıl Çalışır?
Bir url paylaşıldığında:
- Facebook botu (crawler) sayfayı ziyaret eder
- `<head>` içindeki `og:` meta'ları okur
- Sonucu kendi sunucusunda cache'ler (sayfayı her paylaşımda yeniden okumaz)
- Paylaşım kartını oluşturur
- Instagram da aynı sistemi kullanır

## Cache Sorunu (sık karşılaşılan bir problem)
- Open Graph etiketlerini değiştirdiğinizde, Facebook/WhatsApp eski görseli/başlığı göstermeye devam edebilir. Bunun sebebi cache'dir. Çözüm için:
    - Facebook Sharing Debugger (`developers.facebook.com/tools/debug`) üzerinden url girilip "Scrape Again" (yeniden tara) butonuna basılmalı
    - WhatsApp kendi cache'ini tutar, bazen sadece linki farklı şekilde (örn. sonuna `?v=2` ekleyerek) tekrar paylaşmak gerekebilir

## Twitter Card Nedir?
- Twitter (X) için özel meta'lardır.
- Ama çoğu platform OG'si yoksa Twitter Card'a bakar.

### **twitter:card**
- **Örnek :** <meta name="twitter:card" content="summary_large_image" />
- Paylaşım kartının görsel boyutunu belirler.
- **Türler :**

| **Değer**             | **Anlam**                         |
|-----------------------|-----------------------------------|
| summary               | Küçük görsel                      |
| summary_large_image   | Büyük görsel (önerilem)           |
| app                   | Mobil uygulama tanıtım kartı      |
| player                | Video/ses oynatıcı gömülü kart    |

### **twitter:title**
- **Örnek :** <meta name="twitter:title" content="Test Sitesi" />
- Twitter'da görünen başlık
- OG title yoksa burayı kullanır

### **twitter:description**
- **Örnek :** <meta name="twitter:description" content="Test içeriği" />

### **twitter:image**
- **Örnek :** <meta name="twitter:image" content="https://site.com/og.jpg" />

### twitter:site / twitter:creator (opsiyonel ama önerilir)
```
    <meta name="twitter:site" content="@markaadi" />
    <meta name="twitter:creator" content="@yazaradi" />
```
- `twitter:site` : içeriğin ait olduğu markanın Twitter hesabı
- `twitter:creator` : içeriği yazan kişinin twitter hesabı

## Open Graph Protokolü Teknik Detay: prefix Tanımı

Standartlara tam uyum için `<html>` etiketine bir "namespace" (isim alanı) eklenmesi önerilir. Zorunlu değildir, çoğu platform bunsuz da çalışır, ama W3C standardına göre doğrusu budur:
```
    <html prefix="og: https://ogp.me/ns#">
```
## Test ve Doğrulama Araçları (çok önemli, sık atlanan bir adım)

Meta etiketleri yazdıktan sonra mutlaka şu araçlarla kontrol edilmeli:
- Facebook Sharing Debugger — developers.facebook.com/tools/debug (Facebook + Instagram + WhatsApp için)
- Twitter Card Validator — cards-dev.twitter.com/validator
- LinkedIn Post Inspector — linkedin.com/post-inspector

Bu araçlar hem hata varsa gösterir hem de cache'i temizleyip kartı yeniden tarar.

## Sık Yapılan Hatalar
- Görsel url'sini relative (/img/og.jpg) yazmak — mutlaka tam url olmalı
og:image boyutunun çok küçük veya orantısız olması
- Değişiklik yaptıktan sonra debugger ile cache'i yenilememek
og:title ve `<title>` etiketini karıştırıp ikisini de aynı yazmak zorunda hissetmek (aslında farklı amaçlara hizmet edebilirler)
- og:url yazmamak — bu durumda paylaşım sayıları farklı url varyasyonlarına dağılabilir
- Sadece anasayfa için OG yazıp diğer sayfaları (blog, ürün vs.) boş bırakmak — her sayfanın kendine ait, o sayfaya özel OG etiketleri olmalı

## Open Graph - Meta - Schema Farkı
- Birbirinin yerine geçmezler.

| **Yapı**              | **Amaç**                      |
|-----------------------|-------------------------------|
|Meta title/description	| Google arama                  |
|Open Graph             | Sosyal paylaşım               |
|Twitter Card           | Twitter / X                   |
|Schema                 | Arama motoru anlamlandırma    |

- Kısa Özet:
    - Open graph = sosyal vitrin
    - Görsel en önemli parça
    - Canonical ile uyum şart
    - Seo'ya dolaylı katkı sağlar.

## Örnek: Tam Bir Head Bloğu
Tüm konuyu tek bir örnekte toplarsak, gerçek bir sayfada `<head>` içi şöyle görünür:
```
    <html prefix="og: https://ogp.me/ns#">
    <head>
    <title>Ahlatcı Kuyumculuk | Altın & Pırlanta</title>
    <meta name="description" content="Altın, pırlanta ve özel tasarım takılar." />

    <meta property="og:title" content="Ahlatcı Kuyumculuk | Altın & Pırlanta" />
    <meta property="og:description" content="Altın, pırlanta ve özel tasarım takılar." />
    <meta property="og:image" content="https://www.ahlatcistore.com.tr/images/og-home.jpg" />
    <meta property="og:image:width" content="1200" />
    <meta property="og:image:height" content="630" />
    <meta property="og:url" content="https://www.ahlatcistore.com.tr/" />
    <meta property="og:type" content="website" />
    <meta property="og:site_name" content="Ahlatcı Kuyumculuk" />
    <meta property="og:locale" content="tr_TR" />

    <meta name="twitter:card" content="summary_large_image" />
    <meta name="twitter:title" content="Ahlatcı Kuyumculuk | Altın & Pırlanta" />
    <meta name="twitter:description" content="Altın, pırlanta ve özel tasarım takılar." />
    <meta name="twitter:image" content="https://www.ahlatcistore.com.tr/images/og-home.jpg" />
    </head>
```

## Kısa Özet
- Open Graph = sosyal vitrin
- Görsel en önemli parça
- Canonical/og:url ile uyum şart
- SEO'ya doğrudan değil, dolaylı katkı sağlar (tıklama oranı üzerinden)
- Her sayfanın kendine ait OG etiketleri olmalı, tek bir genel etiket seti yetmez
- Değişiklik sonrası mutlaka Facebook Sharing Debugger / Twitter Card Validator ile test edilmeli, aksi halde eski (cache'li) kart görünmeye devam eder