# HTML Global Attributes (Global Nitelikler)
## Attrbute Nedir?
HTML'de **attribute (nitelik)**, bir HTML elementi hakkında ek bilgi vermek veya elementin davranışını/özelliklerini belirlemek için kullanılır.

Genel kullanım: `<element attribute="value">`

Örneğin: `<a href="/products">Ürünler</a>`

Burada:
```
    <a>       → HTML elementi
    href      → Attribute
    /products → Attribute değeri
```

Başka bit örnek: `<img src="watch.jpg" alt="Siyah kol saati">`

Burada `src` ve `alt`, `<img>` elementinin attribute'larıdır.

## Global Attribute Nedir?
Bazı attribute'lar yalnızca belirli HTML elementlerinde kullanılır.

Örneğin: `<img src="image.jpg" alt="Ürün görseli">` Buradaki `src`, `<img>` elementiyle ilişkili bir attribute'dur.

Benzer şekilde: `<a href="products">Ürünler</a>` içerisindeki `href`, bağlantının hedefini belirtir.

Ancak bazı attribute'lar HTML'deki elementlerin çok büyük bölümünde kullanılabilir. Bunlara **Global Attributes** denir.

Örneğin:
```
    <p id="description">...</p>
    <div id="container">...</div>
    <section id="products">...</section>
```
- `id`, global bir attribute'dur.

Aynı şekilde:
```
    <p class="text">...</p>
    <div class="container">...</div>
    <section class="products">...</section>
```
- `class` da global attribute'dur.

Kısaca: `Global Attribute, belirli tek bir HTML elementine ait olmayan ve HTML elementlerinde genel olarak kullanılabilen attribute'dur.`

## `id`
`id`, bir HTML elementine **benzersiz bir kimlik** vermek için kullanılır.
```
    <section id="products">
        ...
    </section>
```
Burada elementin kimliği, `products` olmuştur.

Bir sayfa içerisinde aynı id değerinin birden fazla element için kullanılmaması gerekir.

Doğru:
```
    <section id="products">
        ...
    </section>

    <section id="campaigns">
        ...
    </section>
```

Yanlış:
```
    <section id="products">
        ...
    </section>

    <section id="products">
        ...
    </section>
```

### `id` Ne İçin Kullanılır?
id farklı amaçlarla kullanılabilir.

**CSS**
```
    <h1 id="page-title">Ürünler</h1>

    #page-title {
        font-size: 32px;
    }
```
**JavaScript**
```
    <button id="add-to-cart">
        Sepete Ekle
    </button>

    const button = document.getElementById("add-to-cart");
```

**Sayfa İçi Bağlantı**

Gördüğümüz `<a href="#contact">İletişime Git</a>` şu elementi hedefleyebilir: `<section id="contact"> ... </section>`

Yani:
```
    href="#contact"
        │
        ▼
    id="contact"
```

## `class`
class, HTML elementlerini **gruplandırmak veya sınıflandırmak** için kullanılır.
```
    <div class="product-card">
        ...
    </div>
```

`id`den farklı olarak aynı class birden fazla elementte kullanılabilir.
```
    <div class="product-card">
        Ürün 1
    </div>

    <div class="product-card">
        Ürün 2
    </div>

    <div class="product-card">
        Ürün 3
    </div>
```

Burada üç element de aynı gruba aittir.

Örneğin CSS'te:
```
    .product-card {
        border: 1px solid #ddd;
    }
```
yazıldığında aynı class'a sahip bütün kartlar hedeflenebilir.

### Bir Elemente Birden Fazla Class Verilebilir
Bir element yalnızca tek bir class'a sahip olmak zorunda değildir.
```
    <button class="btn btn-primary large">
        Kaydet
    </button>
```
Burada elementin üç class'ı vardır:
```
    btn
    btn-primary
    large
```
- Class isimleri boşlukla ayrılır.
- Bu yapı özellikle Bootstrap gibi CSS kütüphanelerinde çok sık görülür.

Örneğin:
```
    <div class="d-flex align-items-center justify-content-between">
        ...
    </div>
```

## `id` ve `class` farkı
Bu iki attribute başlangıçta sık karıştırılır.

|id     |class          |
|-------|---------------|
|Element için benzersiz kimlik sağlar   |Elementleri gruplandırır|
|Aynı değer sayfada benzersiz olmalıdır |Aynı class birçok elementte kullanılabilir|
|#name ile CSS'te seçilebilir   |.name ile CSS'te seçilebilir|
|JS tarafından element bulmak için kullanılabilir   |JS tarafından element gruplarını bulmak için kullanılabilir|
|Sayfa içi bağlantılarda hedef olabilir |Fragment hedefi olarak kullanılmaz|

Temel mantık:
```
    id → Bu element hangisi?
    class → Bu element hangi gruba/gruplara ait?
```

## `title`
`title`, element hakkında ek bilgi sağlayabilir.
```
    <abbr title="HyperText Markup Language">HTML</abbr>
```
veya:
```
    <button title="Ürünü favorilere ekle">
        ♡
    </button>
```

Bazı masaüstü tarayıcılarda kullanıcı fareyi elementin üzerinde tuttuğunda title içeriği tooltip benzeri şekilde gösterilebilir. Ancak önemli bir nokta vardır:
```
    title, önemli bilgileri kullanıcıya aktarmanın veya erişilebilir bir isim sağlamanın ana yöntemi olarak kullanılmamalıdır.
```

Örneğin bir form alanında, `<input type="email" title="E-posta adresiniz">` yazıp `<label>` kullanmamak doğru bir yaklaşım değildir. Bunun yerine:
```
    <label for="email">
        E-posta Adresi
    </label>

    <input
        id="email"
        name="email"
        type="email"
    >
```
tercih edilmelidir.

## `lang`
`lang`, bir HTML belgesinin veya belirli bir elementin içeriğinin dilini belirtmek için kullanılan global bir attribute'dur.

Örneğin:
```
    <html lang="tr">
```
`Bu belgenin temel dili Türkçedir.` anlamına gelir.

Sayfa içerisinde farklı dilde bir içerik varsa ilgili element üzerinde de kullanılabilir:
```
    <p>
        HTML öğrenirken
        <span lang="en">accessibility</span>
        kavramıyla karşılaşırız.
    </p>
```

Bu durumda:
```
    Sayfanın dili → Türkçe
    Belirli ifadenin dili → İngilizce
```
olarak belirtilebilir.

`lang` bilgisi tarayıcılar, ekran okuyucular ve arama motorları gibi sistemlerin içeriğin dilini anlamasına yardımcı olur.

**lang kullanımı HTML Accessibility (A11y) ve HTML Metadata ve Temel SEO konularında ayrıca ele alınmıştır.**

## `hidden`
`hidden`, bir elementin şu anda kullanıcıya sunulmaması gerektiğini belirtmek için kullanılan global bir attribute'dur.
```
    <div hidden>
        Bu alan şu anda gizlidir.
    </div>
```

`hidden` bir **boolean attribute** örneğidir. Bu nedenle kullanılması için ayrıca bir değer verilmesi gerekmez. 

JavaScript ile elementin hidden durumu değiştirilebilir:
```
    const message = document.getElementById("message");
    message.hidden = false;
```
**hidden ile erişilebilirlik ilişkisi ve aria-hidden arasındaki fark HTML Accessibility (A11y) konusunda detaylı olarak incelenmiştir.**

## `tabindex`
`tabindex`, bir elementin klavye ile gezinme ve focus davranışını kontrol etmek için kullanılan global bir attribute'dur.

Temel olarak:
- `tabindex="0"` → Elementi doğal klavye sırasına dahil edebilir.
- `tabindex="-1"` → Element Tab sırasına girmez ancak programatik olarak focus alabilir.
- Pozitif değerlerin kullanılması genellikle önerilmez.

> `tabindex`, klavye kullanımı ve focus yönetimiyle doğrudan ilişkili olduğu için detayları **HTML Accessibility (A11y)** konusunda incelenmiştir.

## `contenteditable`
`contenteditable`, kullanıcının bir HTML elementinin içeriğini tarayıcı üzerinden düzenleyebilmesini sağlar.
```
    <p contenteditable="true">
        Bu yazıyı düzenleyebilirsiniz.
    </p>
```
Kullanıcı metnin üzerine tıklayıp içeriği değiştirebilir. Örneğin basit metin editörlerinde kullanılabilir.
```
    <div contenteditable="true">
        İçeriğinizi buraya yazın...
    </div>
```
Ancak önemli bir ayrım vardır:
    
**Kullanıcının tarayıcıda metni değiştirebilmesi, bu değişikliğin otomatik olarak veritabanına kaydedildiği anlamına gelmez.**

Kalıcı hale getirmek için JavaScript ve çoğu gerçek uygulamada backend tarafında ek işlemler gerekir.

## `data-*` Attributes

Frontend geliştirme açısından özellikle önemli global attribute yapılarından biridir. `data-*`, HTML elementleri üzerinde uygulamaya özel veri saklamamıza olanak sağlar.

Örneğin bir ürün kartımız olsun:
```
    <article
        class="product-card"
        data-product-id="42"
        data-category="watch"
    >
        Kol Saati
    </article>
```
Burada:
```
    data-product-id="42"
    data-category="watch"
```
elementle ilgili özel verilerdir.

HTML'nin standart bir, `product-id` attribute'u olmadığı için kendi verimizi `data-*` yapısıyla tanımlayabiliriz.

### JavaScript ile `data-*` Kullanımı
**HTML**
```
    <button
        class="add-to-cart"
        data-product-id="42"
        data-product-name="Kol Saati"
    >
        Sepete Ekle
    </button>
```

**JavaScript**
```
    const button = document.querySelector(".add-to-cart");

    console.log(button.dataset.productId);
    console.log(button.dataset.productName);
```

Burada şu dönüşüm gerçekleşir:
```
    data-product-id → dataset.productId
    data-product-name → dataset.productName
```

Bu nedenle `data-*`, HTML ve JavaScript birliktr çalışırken oldukça sık karşımıza çıkar.

### `data-*` Ne İçin Kullanılmamalıdır?
Sayfanın kullanıcıya gösterilmesi gereken önemli içeriğini yalnızca data-* içerisinde saklamak doğru değildir.

Örneğin:
```
    <div data-product-name="Kol Saati"></div>
```
yerine kullanıcı ürünü görmeliyse:
```
    <div
        class="product"
        data-product-id="42"
    >
        Kol Saati
    </div>
```
daha anlamlıdır.

### `style`
`style`, doğrudan HTML elementi üzerinde CSS yazılmasını sağlar.
```
    <p style="color: red;">
        Merhaba
    </p>
```
Buna inline CSS denir. Birden fazla özellik de yazılabilir:
```
    <p style="font-size: 18px; font-weight: bold;">
        Merhaba
    </p>
```
Teknik olarak geçerli olsa da büyük projelerde tasarım kurallarını HTML içerisinde sürekli `style` ile yazmak kodun bakımını zorlaştırabilir.

Örneğin:
```
    <p class="warning">
        Dikkat!
    </p>
    .warning {
        color: red;
        font-weight: bold;
    }
```
şeklinde HTML ile stil sorumluluğunu ayırmak çoğu durumda daha yönetilebilirdir.

## `dir`
`dir`, metnin yazım yönünü belirtir. Temel değerleri aşağıdaki şekildedir.
```
    ltr
    rtl
    auto
```

### `ltr` - Left to Right
Soldan sağa yazılan içerikler için kullanılır.
```
    <p dir="ltr">
        Hello World
    </p>
```

### `rtl` - Right to Left
Arapça ve İbranice gibi sağdan sola yazılan dillerde kullanılabilir.
```
    <p dir="rtl">
        ...
    </p>
```

### auto
Tarayıcının metin yönünü içeriğe göre belirlemesine olanak sağlar. Özellikle kullanıcı tarafından oluşturulan ve dilinin önceden bilinmediği içeriklerde faydalı olabilir.
```
    <p dir="auto">
        ...
    </p>
```

## Global Attribute'lar Birlikte Kullanılabilir
Bir element birden fazla global attribute'a sahip olabilir. Örneğin:
```
    <article
        id="product-42"
        class="product-card featured"
        lang="tr"
        data-product-id="42"
        title="Ürün detayları"
    >
        <h2>Kol Saati</h2>
    </article>
```

Burada bulunmaktadır:
```
    article
    │
    ├── id
    │   └── product-42
    │
    ├── class
    │   ├── product-card
    │   └── featured
    │
    ├── lang
    │   └── tr
    │
    ├── data-product-id
    │   └── 42
    │
    └── title
        └── Ürün detayları
```

## Sık Yapılan Hatalar
Global Attribute'ları kullanırken özellikle şu hatalara dikkat edilmelidir.
- Aynı `id` değerini bir sayfada tekrar tekrar kullanmak.
- Her elemente gereksiz `id` vermek.
- `id` ve `class` kullanım amaçlarını karıştırmak.
- `title` attribute'unu `<label>` yerine kullanmak.
- `tabindex="1", "2", "3"` ile yapay klavye sırası oluşturmak.
- Bir `<div>` elementine yalnızca `tabindex` ekleyerek onu buton gibi kullanmaya çalışmak.
- Kullanıcıya gösterilmesi gereken içeriği sadece `data-*` içerisinde tutmak.
- Her CSS kuralını `style` attribute'u içerisinde yazmak.
- Sayfanın `lang` bilgisini belirtmemek.

## Tam Örnek
Öğrendiklerimizin birkaçını birlikte kullamalım:
```
    <!DOCTYPE html>

    <html lang="tr">

    <head>
        <meta charset="UTF-8">

        <meta
            name="viewport"
            content="width=device-width, initial-scale=1.0"
        >

        <title>Ürünler</title>
    </head>

    <body>

        <main id="main-content">

            <section
                id="products"
                class="product-list"
            >

                <h1>Ürünler</h1>

                <article
                    id="product-42"
                    class="product-card"
                    data-product-id="42"
                    data-category="watch"
                >

                    <h2>Kol Saati</h2>

                    <p>
                        Paslanmaz çelik kol saati.
                    </p>

                    <button
                        type="button"
                        class="add-to-cart"
                        data-product-id="42"
                        title="Kol saatini sepete ekle"
                    >
                        Sepete Ekle
                    </button>

                </article>

            </section>

            <div
                id="success-message"
                hidden
            >
                Ürün sepete eklendi.
            </div>

        </main>

    </body>

    </html>
```

Burada HTML elementleri yalnızca görsel yapı oluşturmuyor. Attribute'lar sayesinde elementlere ek anlam ve özellikler kazandırıyoruz.
```
    Kimlik → id
    Grup → class
    Uygulamaya özel veri → data-*
    Ek bilgi → title
    Durum → hidden
```

## Kısaca Özet
Global attribute'ların mantığını şöyle düşünebiliriz:
```
    HTML Elementi
    │
    ├── id
    │   └── Kimlik
    │
    ├── class
    │   └── Gruplandırma
    │
    ├── title
    │   └── Ek bilgi
    │
    ├── lang
    │   └── Dil
    │
    ├── hidden
    │   └── Gizli durum
    │
    ├── tabindex
    │   └── Focus / klavye sırası
    │
    ├── contenteditable
    │   └── Düzenlenebilir içerik
    │
    ├── data-*
    │   └── Uygulamaya özel veri
    │
    ├── style
    │   └── Inline CSS
    │
    └── dir
        └── Metin yönü
```
Buradaki en önemli nokta, global attribute'ları ezberlemekten çok **hangi probleme hangi attribute'un çözüm olduğunu anlamak.**

Global attribute kullanırken şu soruları sorabiliriz:
- Element gerçekten bir `id` değerine ihtiyaç duyuyor mu?
- Aynı `id` başka bir elementte kullanılıyor mu?
- Tekrarlanabilir yapılar için `class` kullanılıyor mu?
- Sayfanın doğru `lang` değeri var mı?
- `title` önemli içeriğin yerine kullanılmaya mı çalışılıyor?
- `tabindex` doğal klavye sırasını bozuyor mu?
- Element aslında `<button>` veya `<a>` olması gerekirken `<div>` ile mi oluşturulmuş?
- `data-*` gerçekten uygulamaya özel veri için mi kullanılıyor?
- Gereksiz inline `style` kullanılıyor mu?
- Gizlenen içerikte `hidden` doğru amaçla mı kullanılıyor?