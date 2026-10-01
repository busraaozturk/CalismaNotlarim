# CSS Seçiciler — Selectors
**00_CSSTemelleri** bölümünde temel bir CSS kuralının şu yapıya sahip olduğunu görmüştük:
```
    selector {
        property: value;
    }
```

Örneğin:
```
    p {
        color:red;
    }
```

Buradaki `p` **CSS selector, yani seçicidir.**

Selector'ın görevi `CSS kuralının hangi HTML elementlerinecuygulanacağını belirlemektir.`

CSS'te elementleri yalnızca etiket adına göre değil;
- Element adına,
- Class değerine,
- ID değerine,
- Attribute'larına,
- Sayfadaki konumlarına,
- Diğer elementlerle ilişkilerine,
- Belirli durumlarıa göre hedefleyebiliriz.

Bu bölümde CSS'in temel seçici yapılarını inceleyeceğiz.
```
    CSS Selectors
    │
    ├── 1. Selector Nedir?
    │
    ├── 2. Simple Selectors
    │   ├── Element Selector
    │   ├── Class Selector
    │   ├── ID Selector
    │   └── Universal Selector
    │
    ├── 3. Class vs ID
    │
    ├── 4. Combinators
    │   ├── Descendant
    │   ├── Child
    │   ├── Next Sibling
    │   └── Subsequent Sibling
    │
    ├── 5. Grouping
    ├── 6. Attribute Selectors
    ├── 7. Pseudo-Classes
    ├── 8. Pseudo-Elements
    ├── 9. Sık Yapılan Hatalar
    └── 10. Kısaca
```

## Selector Nedir?
Selector, CSS kuralının **hangi Html element veya elementlerini hedefleyeceğini belirleyen bölümdür.**

Örneğin: 
```
    p {
        color:gray;
    }
```

Buradaki: `p` selector'dır.

Tarayıcı bu kuralı okuduğunda sayfadaki eşleşen p elementlerini bulur ve ilgili CSS bildirimlerini uygular.

HTML:
```
    <p>Birinci paragraf.</p>
    <p>İkinci paragraf.</p>
```

CSS:
```
    p {
        color: gray;
    }
```
Bu selector iki **p elementiyle de eşleşir.** Bunu temel olarak:
```
    Selector
       ↓
    Hangi elementler?
       ↓
    Eşleşen HTML elementleri
       ↓
    CSS kuralları uygulanır
```
şeklinde düşünebiliriz.

Ancak her zaman bütün **p elementlerini hedeflemek istemeyebiliriz.** Örneğin yalnızca belirli bir paragrafı veya belirli bir ürün kartının içerisindeki butonu hedeflemek isteyebiliriz. Bunun için CSS farklı selector türleri sunar.

## Basit Seçiciler - Simple Selectors
Başlangıçta bilmemiz gereken temel seçiciler aşağıdaki şekildedir:
```
    Element Selector
    Class Selector
    ID Selector
    Universal Selector
```

### 1. Element Selector - Tip Seçici
Element selector, HTML elementlerini **etiket adına göre** hedefler.

Örneğin sayfadaki *p* elementlerini hedefler.
```
    p {
        color: gray;
    }
```

HTML:
```
    <p>Birinci paragraf</p>
    <p>Birinci paragraf</p>
    <p>Birinci paragraf</p>
```
Bu üç element de **selector** ile eşleşir.

Başka bir örnek
```
    button {
        background-color: black;
        color: white;
    }
```
sayfadaki eşleşen button elementlerini hedefler.
```
    <button>Sepete Ekle</button>
    <button>Satın Al</button>
```
Her iki buton da bu CSS kuralından etkilenir.

### Element Selector Ne Zaman Kullanılır?
Bir element türününü genel görünümünü belirlemek istediğimizde kullanılabilir. Örneğin:
```
    body {
        font-family: Arial, sans-serif;
    }

    h1 {
        font-size: 40px;
    }

    p {
        line-height: 1.6;
    }
```

Burada belirli bir component'i değil, ilgili element türlerinin genel stilini tanımlıyoruz.

Temel yapı:
```
    HTML
    <p>...</p>
        ↓
    CSS
    p { }
```
Element selector'ın önünde `. veya #` gibi bir işaret bulunmaz.

### 2. Class Selector
Class selector, HTML elementlerini **class attribute'una** göre hedefler.
HTML:
```
    <button class="primary-button">
        Sepete Ekle
    </button>
```

CSS:
```
    .primary-button {
        background-color: black;
        color:white;
    }
```

Class selector yazarken class adının önüne `.` nokta eklenir.

```
    HTML → class="primary-button"
                ↓
    CSS → .primary-button
```

### Aynı Class Birden Fazla Elementte Kullanılabilir
Class yapısının önemli özelliklerinden biri **tekrar kullanılabilmesidir.**

Örneğin:
```
    <button class="primary-button">
        Sepete Ekle
    </button>

    <a class="primary-button" href="/products">
        Ürünleri Gör
    </a>
```

Her iki element de bu kuralla eşleşebilir.
```
    .primary-button {
        background-color: black;
        color: white;
    }
```

Class yalnızca belirli bir HTML elementine özgü değildir.

### Bir Element Birden Fazla Class Alabilir.
Bir HTML elementi birden fazla class değerine sahip olabilir.

Örneğin:
```
    <button class="button button-large">
        Sepete Ekle
    </button>
```

Burada elementin iki class'ı vardır.
```
    button
    button-large
```

Bunları ayrı ayrı hedefleyebiliriz:
```
    .button {
        border:none;
    }

    .button-large {
        padding: 16px 32px;
    }
```
Aynı element her iki CSS kuralıyla da eşleşir. Bu özellik tekrar kullanılabilir CSS yapıları oluştururken oldukça kullanışlıdır.

### 3. ID Selector
ID Selector, HTML elementini **id attrubute**'una göre hedefler.

HTML:
```
    <section id="featured-products">
        <h2>Öne Çıkan Ürünler</h2>
    </section>
```

CSS:
```
    #featured-products {
        padding: 40px;
    }
```

ID Selector yazarken ID adının önüne; `#` işareti eklenir.
```
    HTML: id="featured-products"
            ↓
    CSS: #featured-products
```

### ID Benzersiz olmalıdır
Bir HTML belgesindeki **id** değeri ilgili belge içerisinde benzersiz olmalıdır.

Doğru:
```
    <section id="featured-products>
        ...
    </section>

    <section id="new-products">
        ...
    </section>
```
Aynı ID'yi farklı elementlerde tekrar kullanmak doğru değildir.

Yanlış:
```
    <section id="products">
        ...
    </section>
```

Eğer aynı stil birden fazla elementte kullanılacaksa genellikle class daha uygun olur:
```
    <section class="product-section">
        ...
    </section>

    <section class="product-section">
        ...
    </section>
```
CSS:
```
    .product-section {
        padding: 40px;
    }
```

### 4. Universal Selector
Universal selector `*` şeklinde yazılır. Eşleşebilecek tüm elementleri hedeflemek için kullanılır. 

Örneğin:
```
    * {
        box-sizing:border-box;
    }
```

Bu tarz kurallar bazı başlangıç/reset yaklaşımlarında görülebilir. Ancak `Bütün elementlerin **margin ve padding değerlerini sıfırlamak her projede zorunlu bir kural değildir.` Projenin CSS yaklaşımına göre karar verilmelidir.

### Universal Selector ve Reset
CSS'te tarayıcıların varsayılan stillerini düzenlemek için **CSS Reset** gibi yaklaşımlar bulunur. Universal selector bazı reset kurallarının içerisinde kullanılabilir. Ancak:
```
    Universal Selector ≠ CSS Reset
```
Universal selector yalnızca bir **seçicidir.**

Reset ise tarayıcıların varsayılan stillerini belirli bir başlangıç noktasına getirmeyi amaçlayan daha geniş bir CSS yaklaşımıdır. Normalize yaklaşımı da bununla ilişkili fakat farklı bir konudur.

## Class ve ID - Ne Zaman Hangisi?
CSS öğrenirken en sık karşılaşılan sorulardan biri: `Class mı kullanmalıyım, ID mi?` sorusudur.

Temel fark:
|Class      |ID             |
|-----------|---------------|
|. ile seçilir| # ile seçilir |
|Tekrar kullanılabilir | Belge içinde benzersiz olmalıdır|
|Birden fazla elementte bulunabilir| Aynı Id değeri tekrar edilmemelidir|
|Bir element birden fazla class alabilir| Bir elementin id değeri tek bir kimliktir.|

Örneğin tekrar kullanılacak kartlar:
```
    <article class="product-card">
        ...
    </article>

    <article class="product-card">
        ...
    </article>

    <article class="product-card">
        ...
    </article>
```

CSS:
```
    .product-card {
        border: 1px solid #ddd;
    }
```