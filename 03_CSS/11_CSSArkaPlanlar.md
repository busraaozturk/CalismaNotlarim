# CSS Arka Planlar (Backgrounds)
CSS'te arka plan özellikleri, HTML elementlerinin arka plan rengini, konumunu, boyutunu ve görüntülenme biçimini kontrol etmemizi sağlar.

Arka planlar yalnızca dekoratif amaçlarla kullanılmaz. Bir web sayfasında bölümleri birbirinden ayırmak, içerikleri vurgulamak, görsel hiyerarşi oluşturmak ve metinlerin okunabilirliğini artırmak için de kullanılır.

Örneğin bir web sitesinin hero alanında büyük bir arka plan görseli, kart bileşenlerinde sade bir arka plan rengi veya bir başlık bölümünde gradient kullanılabilir.

```
    .hero {
        background-color: #26251f;
        background-image: url("hero.jpg");
        background-repeat: no-repeat;
        background-position: center;
        background-size: cover;
    }
```

Bu örnekte arka plan görseli tekrar etmeden, ortalanarak ve elementin alanını kaplayacak şekilde görüntülenir.

## Arka Plan Nedir?
CSS'te arka plan, bir elementin kutusunun arkasında görüntülenen renk veya görsel katmanlarıdır.

Arka plan özellikleri **background-*** ailesialtında toplanır.

|Özellik                        |Görevi                                       |
|-------------------------------|---------------------------------------------|
|background-color               |Arka plan rengini belirler                   |
|background-image               |Arka plan görseli veya gradient tanımlar     |
|backgroun-repeat               |Görselin tekrarlanma biçimini belirler       |
|background-size                |Görselin boyutunu kontrol eder               |
|background-position            |Görselin konumunu belirler                   |
|background-attachment          |Kaydırma sırasında arka planın davranışını belirler|
|background-origin              |Görselin konumlandırılacağı referans alanını belirler|
|background-clip                |Arka planın boyanacağı alanı sınırlar         |
|background                     |Birden fazla arka plan özelliğini tek satırda tanımlar|
Bu özelliklerin çoğu ayrı ayrı veya background shorthand üzerinden kullanılabilir.

### Temel Örnek
HTML:
```
    <section class="banner">
        <h1>Yeni Koleksiyon</h1>
        <p>Yeni sezon ürünlerini keşfedin.</p>
    </section>
```

CSS:
```
    .banner {
        padding: 80px 24px;
        color: white;
        background-color: #26251f;
        background-image: url("banner.jpg");
        background-position: center;
        background-size: cover;
        background-repeat: no-repeat;
    }
```

Burada background-* özellikleri elementin arka planını kontrol ederken, padding içerikle kutunun kenarları arasında boşluk oluşturur.

## Background-color - Arka Plan Rengi
background-color, bir elementin arka plan rengini belirler.

Temel kullanım:
```
    .card{
        background-color: #f5f5f5;
    }
```

CSS'te renkler farklı biçmlerde tanımlanabilir.
```
    .box-1 {
        background-color: red;
    }

    .box-2 {
        background-color: #7d8570;
    }

    .box-3 {
        background-color: rgb(125, 133, 112);
    }

    .box-4 {
        background-color: rgba(125, 133, 112, 0.5);
    }

    .box-5 {
        background-color: hsl(88, 9%, 48%);
    }
```

### Arka Plan Rengi Hangi Alanı Kaplar?
Bir elementin kutu modeli şu bölümlerden oluşur.
```
    ┌───────────────────────────────┐
    │            MARGIN             │
    │   ┌───────────────────────┐   │
    │   │        BORDER         │   │
    │   │   ┌───────────────┐   │   │
    │   │   │    PADDING    │   │   │
    │   │   │  ┌─────────┐  │   │   │
    │   │   │  │ CONTENT │  │   │   │
    │   │   │  └─────────┘  │   │   │
    │   │   └───────────────┘   │   │
    │   └───────────────────────┘   │
    └───────────────────────────────┘
```
Önemli bir ayrıntı vardır:
**Varsayılan olarak arka plan, içerik ve padding alanlarının yanı sıra border alanının arkasına da boyanır. Margin alanına uygulanmaz.**

Ancak border opaksa arkasındaki arka plan rengi görünmez.
```
    .card{
        padding: 20px;
        border: 5px solid #333;
        background-color: #f2f0eb;
    }
```
Bu örnekte arka plan rengi border'ın arkasına kadar uzanır; fakat opak border kendi rengini gösterir.

### background-clip ile Boyama Alanını Değiştirmek
```
    .card {
        background-color: #f2f0eb;
        background-clip: padding-box;
    }
```
background-clip, arka planın hangi kutu alanına kadar boyanacağını kontrol eder.

|Değer                  |Davranış                                                 |
|-----------------------|---------------------------------------------------------|
|border-box             |Border alanının arkasına kadar boyar (varsayılan)        |
|padding-box            |İçerik ve padding alanını boyar                          |
|content-box            |Yalnızca içerik kutusunu boyar                           |

Bu özellik özellikle saydam border kullanılan tasarımlarda yararlıdır.

## background-image - Arka Plan Görseli
background-image, bir elementin arka planında görsel veya CSS gradient görüntülememizi sağlar.

### url() ile Görsel Ekleme
```
    .hero {
        background-image: url("images/hero.jpg");
    }
```

url() fonksiyonu, kullanılacak görselin adresini belirtir. Yerel bir görsel, projedekş bir dosya yolu veya uygun bir uzak URL kullanılabilir.
```
    .banner {
        background-image: url("/assets/banner.webp");
    }
```

**Önemli:** CSS dosyasındaki göreli görsel yolları genellikle CSS dosyasının bulunduğu konuma göre çözülür.

### background-color ile Birlikte Kullanım
```
    .hero {
        background-color: #26251f;
        background-image: url("hero.jpg");
    }
```
Burada iki özellik birlikte çalışır.
- Görsel başarılı şekilde yüklenirse arka plan görseli görüntülenir.
- Görsel yüklenemezse arka plan rengi görünür.
- Görselin saydam bölgelerinde alttaki arka plan rengi görülebilir.

Bu nedenle özellikle üzerinde metin bulunan görsel alanlarında uygun bir fallback rengi kullanmak faydalıdır.

### background-image ile `<img>` arasındaki fark
|background-image           |`<img>`                        |
|---------------------------|-------------------------------|
|Genellikle dekoratif görseller için kullanılır |İçeriğin anlamlı parçası olan görseller için kullanılır|
|CSS üzerinden kontrol edilir|HTML belgesinin bir parçasıdır|
|background-size ile boyutlandırılır|object-fit ile görüntüleme düzenlenebilir|
|Doğrudan alt metni yoktur|alt attribute'u kullanılabilir|

**Erişilebilirlik:** Görsel içerik için anlam taşıyorsa, yalnızca CSS arka planı olarak sunmak yerine uygun alt metniyle `<img>` kullanmak genellikle daha doğrudur.

## background-repeat - Arka Plan Tekrarı
Bir arka plan görseli, varsayılan olarak hem yatay hem de dikey eksende tekrarlanır.
```
    .pattern {
        background-image: url("pattern.png");
    }
```
Görsel elementten küçükse tekrar ederek kalan alanı doldurabilir.

### Tekrar Değerleri
|Değer                  |Açıklama                   |
|-----------------------|---------------------------|
|repeat                 |Her iki eksende tekrar eder|
|no-repeat              |Tekrar etmez               |
|repeat-x               |Yalnızca yatay eksende tekrar eder |
|repeat-y               |Yalnızca dikey eksende tekrar eder |
|space                  |Tam tekrarları aralarına boşlul dağotarak yerleştirir  |
|round                  |Görselleri alana sığacak biçimde ölçekleyerek tekrarlar    |

### Örnekler
```
    .box-1 {
        background-repeat: repeat;
    }

    .box-2 {
        background-repeat: no-repeat;
    }

    .box-3 {
        background-repeat: repeat-x;
    }

    .box-4 {
        background-repeat: repeat-y;
    }
```

### Gerçek Kullanım
Küçük bir doku görselini tekrar ederek arka plan oluşturabiliriz.
```
    .page {
        background-image: url("texture.png");
        background-repeat: repeat;
    }
```

Ancak büyük bir hero görselinde genellikle tekrar istemeyiz.
```
    .hero {
        background-image: url("hero.jpg");
        background-repeat: no-repeat;
    }
```

## background-size - Arka Plan Boyutu
background-size, arka plan görselinin hangi boyutta görüntüleneceğini belirler.

En sık kullanılan değerler **cover ve contain** değerleridir.

### 1. cover
```
    .hero {
        background-image: url("hero.jpg");
        background-size: cover;
    }
```

cover, görselin en-boy oranını koruyarak arka 