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