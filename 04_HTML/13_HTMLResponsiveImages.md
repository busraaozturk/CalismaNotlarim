# HTML Responsive Images — `srcset` ve `sizes`
Responsive tasarımda yalnızca sayfanın düzeninin ekran boyutuna uyum sağlaması yeterli değildir. Kullanılan görsellerin de farklı cihazlara uygun şekilde sunulması önemlidir.

Örneğin masaüstü ekran için hazırlanmış 2000 px genişliğindeki büyük bir görseli, 390 px genişliğindeki bir telefona indirmek çoğu zaman gereksiz veri kullanımına neden olur.

HTML bu problemi çözebilmek için özellikle:
```
    srcset
    sizes
    <picture>
    <source>
```
yapılarını sunar.

Bu konunun ana odağı: `srcset` ve `sizes` kullanarak tarayıcının uygun görsel dosyasını seçmesini sağlamaktır.

## Responsive Image Nedir?
Responsive image, kullanıcının:
- Ekran boyutuna,
- Görselin sayfada kaplayacağı alana,
- Cihazın ekran yoğunluğuna
 
göre uygun görsel kaynağının kullanılabilmesini sağlayan yaklaşımdır.

Örneğin aynı görselin farklı boyutlarını hazırladığımızı düşünelim:
```
    product-480.jpg
    product-800.jpg
    product-1200.jpg
    product-1600.jpg
```
Telefon kullanan bir ziyaretçinin her zaman `product-1600.jpg` dosyasını indirmesi gerekli olmayabilir. Tarayıcının ihtiyaca göre daha uygun bir kaynağı seçebilmesi sağlanabilir.

## Neden Responsive Images Kullanılır?
Temel amaçlardan biri gereksiz büyük görsellerin indirilmesini önlemektir.

Örneğin:
```
    Desktop: 1920 px ekran
            ↓
    Büyük görsel mantıklı olabilir.

    Mobil: 390 px ekran
            ↓
    Aynı dev görsel gereksiz olabilir.
```
Görseller web sayfalarının önemli miktarda veri kullanan kaynaklarından biri olabilir.

Uygun görsel boyutlarının sunulması:
- İndirilen veri miktarını azaltmaya,
- Sayfanın daha hızlı yüklenmesine,
- Mobil kullanıcı deneyimini iyileştirmeye
yardımcı olabilir.

## `src` ile Normal Görsel Kullanımı
Temel bir görsel:
```
    <img
        src="product.jpg"
        alt="Siyah kol saati"
    >
```
şeklinde kullanılabilir. Burada tarayıcıya tek bir temel kaynak veriyoruz: `product.jpg`

Responsive image kullanımında ise tarayıcıya birden fazla aday kaynak sunabiliriz. Bunun için `srcset` kullanılabilir.

## `srcset` Nedir?
`srcset`, tarayıcıya aynı görselin farklı alternatif kaynaklarını bildirmemizi sağlar.

Örneğin:
```
    <img
        src="product-800.jpg"
        srcset="
            product-480.jpg 480w,
            product-800.jpg 800w,
            product-1200.jpg 1200w
        "
        alt="Siyah kol saati"
    >
```
Burada tarayıcıya üç farklı görsel adayı verilmiştir:
```
    product-480.jpg   → 480w
    product-800.jpg   → 800w
    product-1200.jpg  → 1200w
```
Buradaki:
```
    480w
    800w
    1200w
```
değerlerine **width descriptor** denir.

## `w` Ne Anlama Gelir?
Örneğin `product-800.jpg 800w` ifadesindeki `800w` görsel dosyasının **intrinsic (doğal) genişliğinin 800 CSS piksel olduğu anlamına gelmez; aday görsel kaynağının doğal genişliğinin 800 piksel olduğunu tarayıcıya bildirir.**

Örneğin:
```
    srcset="
        image-small.jpg 480w,
        image-medium.jpg 800w,
        image-large.jpg 1200w
    "
```
şöyle okunabilir:
```
    image-small.jpg → Dosyanın doğal genişliği 480 px
    image-medium.jpg → Dosyanın doğal genişliği 800 px
    image-large.jpg → Dosyanın doğal genişliği 1200 px
```
Bu bilgiler tarayıcının hangi kaynağın uygun olduğunu değerlendirmesine yardımcı olur.

## Görseli Tarayıcı Seçer
Responsive images konusunda önemli noktalardan biri budur.

Biz:
```
    srcset="
        image-480.jpg 480w,
        image-800.jpg 800w,
        image-1200.jpg 1200w
    "
```
yazarak "Mobilde kesinlikle 480 px olanı kullan." demiyoruz. Bunun yerine tarayıcıya adaylar sunuyoruz. Tarayıcı seçim yaparken çeşitli bilgileri değerlendirebilir:
```
    Viewport
        +
    Görselin sayfada kaplayacağı alan
        +
    Cihazın piksel yoğunluğu
        +
    Mevcut görsel adayları
        ↓
    Uygun kaynak seçimi
```
Bu nedenle srcset: **Kesin cihaz eşleştirmesi değil, tarayıcıya kaynak seçenekleri sunma mekanizmasıdır.**

## `sizes` Nedir?
`srcset` tarayıcıya **"Hangi görsel dosyaları mevcut?"** bilgisini verir.

`sizes` ise tarayıcıya kabaca **"Bu görsel farklı viewport koşullarında sayfada yaklaşık ne kadar alan kaplayacak?"** bilgisini verir.

Örneğin:
```
    <img
        src="product-800.jpg"
        srcset="
            product-480.jpg 480w,
            product-800.jpg 800w,
            product-1200.jpg 1200w
        "
        sizes="
            (max-width: 600px) 100vw,
            50vw
        "
        alt="Siyah kol saati"
    >
```
Burada sizes:
```
    Viewport 600px veya daha küçükse → Görsel yaklaşık viewport'un %100'ü kadar.
    Diğer durumlarda → Görsel yaklaşık viewport'un %50'si kadar.
```
bilgisini verir.

## sizes Nasıl Okunur?
Şu örneğe bakalım:
```
    sizes="
        (max-width: 600px) 100vw,
        (max-width: 1000px) 50vw,
        33vw
    "
```
Tarayıcı koşulları sırayla değerlendirir.

Mantık:
```
    Viewport ≤ 600px
        ↓
      100vw


    Viewport ≤ 1000px
        ↓
       50vw


    Diğer durumlar
        ↓
       33vw

    Son değer: 33vw
```
önceki koşullar karşılanmadığında kullanılan varsayılan slot boyutudur.

## `vw` Nedir?
sizes içerisinde sıkça `vw` ile karşılaşırız.

**vw: Viewport Width** anlamına gelir.

Örneğin: `100vw` viewport genişliğinin tamamını ifade eder. `50vw` viewport genişliğinin yarısını ifade eder.

Örneğin ekran genişliği 1000px ise yaklaşık olarak:
```
    100vw → 1000px
    50vw  → 500px
    25vw  → 250px
```
şeklinde düşünülebilir.

`vw` bir CSS uzunluk birimidir. CSS tarafında daha detaylı incelenebilir.

## `srcset` ve `sizes` Birlikte Nasıl Çalışır?
İki attribute'un görevlerini ayırmak önemlidir.

### srcset
```
    srcset="
        image-480.jpg 480w,
        image-800.jpg 800w,
        image-1200.jpg 1200w
    "
```
Tarayıcıya `Elimde bu görsel kaynakları var.` der.

### sizes
```
    sizes="
        (max-width: 600px) 100vw,
        50vw
    "
```
ise `Görsel sayfada yaklaşık bu genişlikte gösterilecek.` bilgisini verir.

Sonrasında:
```
    srcset → Mevcut kaynaklar
            +
    sizes → Görselin beklenen görüntülenme alanı
            +
    Cihaz bilgileri → Tarayıcı uygun görseli seçer
```

## Gerçek Bir Ürün Kartı Örneği
Bir e-ticaret ürün kartımız olduğunu düşünelim. Mobilde kart `Ekranın yaklaşık yarısını` masaüstünde ise `Ekranın yaklaşık dörtte birini` kaplıyor olabilir.

Örneğin:
```
    <img
        src="watch-800.jpg"
        srcset="
            watch-320.jpg 320w,
            watch-480.jpg 480w,
            watch-800.jpg 800w
        "
        sizes="
            (max-width: 768px) 50vw,
            25vw
        "
        alt="Siyah kol saati"
    >
```
Mantık:
```
    Mobil ≤ 768px
        ↓
    Görsel yaklaşık 50vw

    Daha geniş ekran
        ↓
    Görsel yaklaşık 25vw
```
Tarayıcı bu bilgiyle uygun aday dosyayı seçebilir. **Buradaki değerler örnektir. Gerçek sizes değeri tasarımın gerçek layout'una göre belirlenmelidir.**

## `sizes` CSS'in Yerine Geçmez
Bu önemli bir ayrımdır. Şöyle yazmak `sizes="50vw"` görseli otomatik olarak, `width: 50vw;` yapmaz.

`sizes` tarayıcıya **kaynak seçimi için bilgi verir.** Görselin gerçek tasarım boyutu yine CSS tarafından belirlenir.

Örneğin:
```
    .product-image {
        width: 100%;
        height: auto;
    }
```
**HTML:**
```
    <img
        class="product-image"
        src="watch-800.jpg"
        srcset="
            watch-400.jpg 400w,
            watch-800.jpg 800w
        "
        sizes="
            (max-width: 768px) 50vw,
            25vw
        "
        alt="Siyah kol saati"
    >
```
Burada:
```
    CSS → Görsel gerçekte nasıl görünecek?
    sizes → Tarayıcı kaynak seçerken hangi görüntülenme genişliğini varsaymalı?
```
şeklinde bir ayrım vardır.

## `srcset` İçerisinde `x` Kullanımı
`srcset` yalnızca `w` descriptor ile kullanılmaz. **Pixel density descriptor** olarak `x` ile de karşılaşabiliriz.

Örneğin:
```
    <img
        src="logo.png"
        srcset="
            logo.png 1x,
            logo@2x.png 2x
        "
        alt="Site logosu"
    >
```
Burada:
```
    1x → Standart yoğunluk için aday
    2x → Daha yüksek piksel yoğunluğu için aday
```
sunulur.

Bu kullanım özellikle aynı görselin farklı ekran yoğunlukları için hazırlanmış sürümlerinde görülebilir.

## `w` ve `x` Arasındaki Fark
İki yaklaşımı karıştırmamak gerekir.

### Width Descriptor
```
    srcset="
        image-480.jpg 480w,
        image-800.jpg 800w,
        image-1200.jpg 1200w
    "
```
Görsellerin doğal genişliklerini belirtir.

### Pixel Density Descriptor
```
    srcset="
        image.png 1x,
        image@2x.png 2x
    "
```
Farklı ekran yoğunlukları için alternatifler belirtir.

Basitçe:
```
    w → Görselin kaynak genişliği
    x → Piksel yoğunluğu adayı
```
Responsive layout içerisinde farklı genişliklerde gösterilen içerik görsellerinde `w` + `sizes` yaklaşımı oldukça kullanışlıdır.

## `src` Hâlâ Gerekli mi?
Responsive image kullanırken genellikle temel bir src de bulunur:
```
    <img
        src="product-800.jpg"
        srcset="
            product-480.jpg 480w,
            product-800.jpg 800w,
            product-1200.jpg 1200w
        "
        sizes="
            (max-width: 600px) 100vw,
            50vw
        "
        alt="Siyah kol saati"
    >
```
`src`, görsel için temel kaynak görevi görür ve yapı içerisinde bulunması doğru bir yaklaşımdır. Tarayıcı responsive kaynak seçimini desteklediğinde `srcset` içerisindeki adayları değerlendirebilir.

## `<picture>` ile `srcset` Arasındaki İlişki
`<picture>` elementini daha önce görseller konusunda gördüğümüz için baştan detaylandırmayacağız. Ancak `srcset` ile arasındaki temel farkı hatırlamak önemlidir. `<img srcset>` genellikle **Aynı görselin uygun boyut/yoğunluk sürümünü seçmek** için kullanılır. `<picture>` ise **farklı kaynak seçimlerini daha açık şekilde kontrol etmek için kullanılabilir.**

Örneğin farklı formatlar:
```
    <picture>

        <source
            srcset="product.avif"
            type="image/avif"
        >

        <source
            srcset="product.webp"
            type="image/webp"
        >

        <img
            src="product.jpg"
            alt="Siyah kol saati"
        >

    </picture>
```
veya tasarıma göre farklı görsel kompozisyonları kullanılabilir.

## Art Direction Nedir?
Bazen mobilde yalnızca daha küçük bir görsel kullanmak yeterli değildir. Görselin kompozisyonunun da değişmesi gerekebilir.

Örneğin masaüstünde şekildeki gibi geniş bir görselimiz olabilir.
┌───────────────────────────────┐
│        Ürün        Model      │
│                               │
└───────────────────────────────┘

Mobilde aynı görsel küçültüldüğünde ürün çok küçük kalabilir. Bu durumda mobil için daha yakın kırpılmış farklı bir görsel kullanılabilir:
┌─────────────┐
│             │
│    Ürün     │
│             │
└─────────────┘

Bu yaklaşıma **art direction** denir.

Örneğin:
```
    <picture>

        <source
            media="(max-width: 600px)"
            srcset="hero-mobile.jpg"
        >

        <img
            src="hero-desktop.jpg"
            alt="Yeni sezon saat koleksiyonu"
        >

    </picture>
```
Burada mesele yalnızca dosya boyutunu küçültmek değildir. **Farklı ekran için farklı görsel kompozisyonu kullanıyoruz.**

## Resolution Switching ve Art Direction Farkı
Responsive images konusunda bu iki kavram önemlidir.

### Resolution Switching
Aynı görselin farklı boyutlarını kullanırız.
```
    image-480.jpg
    image-800.jpg
    image-1200.jpg
```
İçerik aynıdır. Sadece çözünürlük/boyut değişir.

Örneğin:
```
    <img
        src="image-800.jpg"
        srcset="
            image-480.jpg 480w,
            image-800.jpg 800w,
            image-1200.jpg 1200w
        "
        sizes="100vw"
        alt="Şehir manzarası"
    >
```

### Art Direction
Görselin kendisi veya kırpımı değişir.
```
    hero-desktop.jpg → Geniş kompozisyon
    hero-mobile.jpg → Mobil için yakın kompozisyon
```
Genellikle `<picture>` ile uygulanabilir.

Temel ayrım:
```
    Aynı görsel,sadece uygun çözünürlüğü seç
            ↓
    Resolution Switching

    Ekrana göre görselin kompozisyonunu değiştir
            ↓
    Art Direction
```

## Responsive Image ve CSS Background Image
Responsive image özellikleri özellikle içerik olarak anlam taşıyan HTML görsellerinde kullanılır.

Örneğin:
```
    <img
        src="product.jpg"
        alt="Siyah kol saati"
    >
```
ürün içeriğinin bir parçasıdır. Ancak yalnızca dekoratif bir arka plan:
```
    .hero {
        background-image: url("background.jpg");
    }
```
CSS tarafından yönetilebilir. Bu iki kullanım aynı problem değildir.
```
    İçeriğin parçası olan görsel
            ↓
        <img>

    Dekoratif tasarım görseli
            ↓
    CSS background-image
```
Responsive CSS background görselleri CSS konusu içerisinde ayrıca değerlendirilebilir.

## Responsive Image Kullanırken `alt`
Responsive image kullanmak `alt` kullanımını değiştirmez.
Örneğin:
```
    <img
        src="watch-800.jpg"
        srcset="
            watch-400.jpg 400w,
            watch-800.jpg 800w
        "
        sizes="50vw"
        alt="Siyah deri kayışlı kol saati"
    >
```
Burada farklı dosyalar aynı içeriğin alternatif boyutlarını temsil eder. Bu nedenle görselin anlamını açıklayan alt yine `<img>` üzerinde bulunur.

## Responsive Image Kullanırken `loading`
Responsive kaynak seçimi ile lazy loading farklı problemlere çözüm sağlar.

Örneğin:
```
    <img
        src="watch-800.jpg"
        srcset="
            watch-400.jpg 400w,
            watch-800.jpg 800w,
            watch-1200.jpg 1200w
        "
        sizes="
            (max-width: 768px) 50vw,
            25vw
        "
        loading="lazy"
        alt="Siyah kol saati"
    >
```
Burada:
```
    srcset + sizes → Hangi görsel kaynağı daha uygun?
    loading="lazy" → Görsel ne zaman yüklensin?
```
sorularına cevap verir. Aynı şey değildirler.

## Sık Yapılan Hatalar
Responsive images kullanırken şu hatalarla karşılaşabiliriz:

### Tek bir dev görseli bütün cihazlara göndermek
```
    <img
        src="product-3000.jpg"
        alt="Ürün"
    >
```
Görsel küçük gösteriliyor olsa bile büyük dosya indirilmiş olabilir.

### `srcset` Değerlerini Yanlış Tanımlamak
Gerçek dosya genişlikleriyle uyuşmuyorsa tarayıcıya yanlış bilgi vermiş oluruz.
```
    srcset="
        image-480.jpg 800w,
        image-1200.jpg 400w
    "
```

### `sizes` Değerini Gerçek Layout'tan Bağımsız Yazmak
Kart gerçekte ekranın dörtte birini kaplıyorsa: `sizes="100vw"` demek tarayıcıya yanlış bir tahmin verebilir. `sizes`, gerçek tasarımla uyumlu olmalıdır.

### `sizes` ile CSS width'ini Aynı Şey Sanmak

`sizes="50vw"` görselin CSS genişliğini belirlemez.

### `w` ve `x` Descriptor'larını Karıştırmak

`800w` ile `2x` aynı bilgiyi ifade etmez.

### Her Responsive Görsel İçin <picture> Kullanmak
Eğer yalnızca aynı görselin farklı çözünürlüklerini seçmek istiyorsak:
```
    <img srcset="..." sizes="...">
```
yeterli olabilir.

`<picture>` özellikle farklı kaynak/format veya art direction gerektiğinde daha anlamlıdır.

### Mobil ve Desktop İçin Farklı Kompozisyon Gerekirken Sadece Küçültmek

Bazı hero/banner görsellerinde yalnızca çözünürlüğü değiştirmek yeterli olmayabilir.

Bu durumda art direction düşünülmelidir.

### Gerçek Bir Örnek
Bir ürün listeleme sayfasında kartların:
```
    Mobil → 2 sütun
    Tablet → 3 sütun
    Desktop → 4 sütun
```
olduğunu düşünelim.

**HTML:**
```
    <article class="product-card">

        <img
            class="product-card__image"
            src="watch-800.jpg"
            srcset="
                watch-320.jpg 320w,
                watch-480.jpg 480w,
                watch-800.jpg 800w
            "
            sizes="
                (max-width: 600px) 50vw,
                (max-width: 1024px) 33vw,
                25vw
            "
            loading="lazy"
            alt="Siyah deri kayışlı kol saati"
        >

        <h2>
            Siyah Kol Saati
        </h2>

    </article>
```
Mantık:
```
    Mobil 2 sütun → Her kart yaklaşık 50vw
    Tablet 3 sütun → Her kart yaklaşık 33vw
    Desktop 4 sütun → Her kart yaklaşık 25vw
```
Tarayıcı daha sonra:
```
    Görselin beklenen genişliği
        +
    Cihaz yoğunluğu
        +
    srcset adayları
        ↓
    Uygun görsel kaynağı
```
üzerinden seçim yapabilir.

Gerçek projede container genişliği, gap, padding ve maksimum genişlik gibi değerler bulunduğundan `sizes` ifadesi daha hassas hesaplanabilir. Başlangıç seviyesinde önemli olan çalışma mantığını anlamaktır.

### Hangi Yapıyı Ne Zaman Kullanmalıyım?
Basit karar mantığı:
```
    Görsel responsive olacak
            │
            ▼
    Ne değişecek?
    │
    ├── Aynı görselin çözünürlüğü/boyutu
    │       │
    │       └── srcset + sizes
    │
    ├── Ekrana göre görsel kompozisyonu
    │       │
    │       └── <picture> + <source>
    │
    └── Görsel formatı
            │
            └── <picture> + <source>
```
Böylece her durumda aynı çözümü kullanmak yerine ihtiyaca göre seçim yapabiliriz.

## Kısa Kontrol Listesi
Responsive görseller oluştururken:
- Aynı görselin farklı boyutları mevcut mu?
- `srcset` adaylarının genişlik bilgileri doğru mu?
- `sizes` gerçek layout'a uygun mu?
- Görsel mobilde ve masaüstünde yaklaşık ne kadar alan kaplıyor?
- `w` ve `x` descriptor'larının farkı doğru anlaşıldı mı?
- Farklı görsel kompozisyonu gerekiyorsa `<picture>` değerlendirildi mi?
- Yalnızca çözünürlük değişiyorsa gereksiz `<picture>` kullanılıyor mu?
- Görsel içerik mi yoksa yalnızca dekoratif mi?
- `alt` doğru şekilde kullanılıyor mu?
- Lazy loading gerekiyorsa ayrıca değerlendirildi mi?
- Mobil kullanıcıya gereksiz büyük bir görsel indiriliyor mu?

## Kısaca
Responsive image yapısının temel mantığı:
```
    <img>
    │
    ├── src
    │   └── Temel görsel kaynağı
    │
    ├── srcset
    │   └── Alternatif görsel kaynakları
    │
    └── sizes
        └── Görselin layout'ta kaplayacağı tahmini alan
```
Tarayıcı:
```
    srcset
    +
    sizes
    +
    viewport
    +
    ekran yoğunluğu
            ↓
    Uygun görsel kaynağını seçer
```
Temel ayrım ise:
```
    Resolution Switching
        ↓
    Aynı görselin uygun boyutunu seçmek
        ↓
    srcset + sizes

    Art Direction
        ↓
    Ekrana göre görsel kompozisyonunu değiştirmek
        ↓
    picture + source
```
Bu konudaki en önemli nokta:
**Responsive image kullanımında hangi dosyanın indirileceğini tek tek cihazlara göre bizim belirlememiz yerine, tarayıcıya doğru adayları ve doğru boyut bilgisini sunarız; tarayıcı uygun kaynağı seçer.**