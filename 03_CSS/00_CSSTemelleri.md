# CSS Temelleri 
HTML ile bir web sayfasının **yapısını ve içeriğin anlamını** oluşturabiliriz. Ancak sayfanın renkleri, yazı tipleri, boşlukları, boyutları ve genel görsel düzeni gibi özelliklerini yönetmek için CSS kullanırız.

Bu bölümde CSS'in ne olduğunu, frontend geliştirmedeki görevini, HTML'e nasıl dahil edildiğini ve temel CSS sözdimini inceleyeceğiz.

CSS Temelleri
│
├── 1. CSS Nedir?
├── 2. Frontend Geliştirmede CSS'in Yeri
├── 3. CSS'i HTML'e Dahil Etme
│   ├── External CSS
│   ├── Internal CSS
│   └── Inline CSS
│
├── 4. CSS Sözdizimi
│   ├── Rule
│   ├── Selector
│   ├── Declaration
│   ├── Property
│   └── Value
│
├── 5. CSS Yorum Satırları
├── 6. Sık Yapılan Hatalar
└── 7. Kısaca

## Css Nedir?
Css 'in açılımı **Cascading Style Sheets (Basamaklı Stil Sayfaları)'dır.**  CSS, HTML ile oluşturulan içeriğin **görsel sunumunu ve düzenini** kontrol etek için kullanılan bir stil dilidir.

Örneğin HTML ile aşağıdaki şekilde bir içerik oluşturabiliriz.
```
    <h1>Ürünlerimiz</h1>
    <p>Yeni sezon ürünlerimizi keşfedin</p>
```

Css ile bu içeriğin görünümünü değiştirebiliriz:
```
    h1{
        color:darkgreen;
        font-size:40px;
    }

    p{
        color:gray;
    }
```

Burada HTML `Bu bir başlık, bu da bir paragraf.` bilgisini verir. CSS ise `Başlık şu renkte ve boyutta, paragraf ise şu renkte görünsün` bilgisiini verir.

Temel ayrım:
```
    HTML - İçeriğin yapısı ve anlamı
    CSS - İçeriğin görsel sunumu
```

### CSS ile Neler Yapılabilir?
CSS ile bir web sayfasının birçok görsel özelliğini kontrol edebiliriz. Örneğin:
- Renkler,
- Yazı tipleri,
- Yazı boyutları,
- Genişlik ve yükseklikler,
- Boşluklar,
- Kenarlıklar,
- Arka planlar,
- Elementlerin sayfadaki konumları,
- Sayfa düzenleri,
- Responsive tasarım,
- Geçişler ve animasyonlar

Bunlar CSS ile yönetilebilir maddelerdir.

Örneğin:
```
    button {
        background-color: black;
        color: white;
        padding: 12px 24px;
        border-radius: 8px;
    }
```

HTML'deki butonun yapısı değişmez: `<button>Sepete Ekle</button>` Ancak görsel sunumu CSS tarafından değiştirilir.

### Seperation of Concerns
Web geliştirmeden önemli yaklaşımlardan biri **Seperation of Concerns** yani sorumlulukların ayrılmasıdır. Temel fikir: `Farklı görevleri mümkün olduğunca kendi sorumluluk alanlarında yönetmek.

HTML'in görevi: `Yapı + İçeriğin anlamı`
CSS'in görevi: `Görsel sunum + Düzen`
JavaScript'in temel görevi ise: `Davranış + Etkileşim` olarak düşünülebilir.

Örneğin:
```
    <button class="add-to-cart">
        Sepete Ekle
    </button>
```
HTML butonun ne olduğunu tanımlar.

CSS, butonun görünümünü belirler:
```
    .add-to-cart{
        background-color:black;
        color:white;
    }
```

JavaScript ise gerektiğinde butonla gerçekleşen etkileşimi yönetebilir:
```
    button.addEventListener("click", function(){
        console.log("Ürün sepete eklendi.");
    });
```

Bu ayrım kodun:
- Daha okunabilir,
- Daha düzenli,
- Daha kolay değiştirilebilir,
- Daha kolay bakım yapılabilir olmasına yardımcı olur.

## Frontend Geliştirmede CSS'in Yeri
Html temellerinde ftontend tarafındaki üç temel teknolojiyi görmüştük:
```
    Frontend
    │
    ├── HTML
    │   └── Yapı ve anlam
    │
    ├── CSS
    │   └── Görsel sunum ve düzen
    │
    └── JavaScript
        └── Davranış ve etkileşim
```

Burada aynı konuyu tekrar detaylandırmak yerine CSS açısından düşünelim.

HTML ile ürün kartının yapısını oluşturabiliriz:
```
    <article class="product-card">

        <h2>Kol Saati</h2>

        <p>12.500 TL</p>

        <button>Sepete Ekle</button>

    </article>
```

CSS ile bu yapının görssel sunumunu değiştirebiliriz.
```
    .product-card {
        padding: 24px;
        border: 1px solid #ddd;
        border-radius: 12px;
    }
```

JavaScript ise gerektiğinde kart üzerindeki etkileşimleri yönetebilir. Dolayısıyla CSS'in temel sorusu: `Bu içerik nasıl sunulmalı?` şeklindedir.

## CSS'i HTML'e Dahil Etme Yöntemleri
Tarayıcının yazdığımız CSS kurallarını HTML belgesine uygulayabilmesi için CSS'i belgeyle ilişkilendirmemiz gerekir.

CSS üç temel yöntemle kullanılabilir:
```
    CSS Kullanımı
    │
    ├── External CSS
    ├── Internal CSS
    └── Inline CSS
```

Bu yöntemlerin hepsi geçerlidir ancak kullanım amaçları ve sürdürülebilirlikleri farklıdır.

### 1.External CSS
External CSS, CSS kodlarının HTML dosyasından ayrı bir .css dosyasında tutulmasıdır.

Örneğin proje yapımız şu şekilde olabilir:
```
    project/
    │
    ├── index.html
    └── style.css
```

**style.css**
```
    body {
        background-color: white;
    }

    h1 {
        color: darkgreen;
    }
```

CSS dosyasını HTML belgesine `<link>` elementiyle bağlarız:
```
    <head>
        <link
            rel="stylesheet"
            href="style.css"
        >
    </head>
```

Buradaki `rel="stylesheet"` bağlanan kaynağın bir stil sayfası olduğunu belirtir. `href="style.css"` is CSS dosyasının konumunu belirtir.

### External CSS'in Avantajları
External CSS gerçek projelerde en yaygın kullanılan yaklaşımdır.
- **HTML ve CSS Ayrı Tutulur**
Bu ayrım kodun daha düzenli olmasını sağlar.
```
    index.html → Yapı
    style.css → Görsel stil
```

- **Aynı CSS Birden Fazla Sayfada Kullanılabilir**
Örneğin:
```
    index.html ────┐
                │
    products.html ─┼──→ style.css
                │
    contact.html ──┘
```
birden fazla HTML belgesi aynı stil dosyasını kullanabilir. Böylece aynı CSS kodlarını her sayfada tekrar yazmamız gerekmez.

- **Bakım Kolaylaşır**

Örneğin bütün sayfalardaki ana rengimizi değiştirmek istiyorsak ilgili CSS dosyasında değişiklik yapmak yeterli olabilir. Bu nedenle external CSS:
- Tekrar kullanılabilirlik,
- Kod organizasyonu,
- Bakım kolaylığı açısından avantajlıdır.