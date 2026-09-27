# HTML'de Görseller ve Medya
Web sayfaları yalnızca metinlerden oluşmaz. Ürün görselleri, fotoğraflar, videolar, ses dosyaları ve farklı ekranlara uygun görsel kaynakları da sayfanın önemli parçalarıdır.

HTML, bu içerikleri sayfaya eklemek için çeşitli elementler sunar. Bu bölümde özellikle `<img>`, `<picture>`, `<figure>`, `<audio>` ve `<video>` elementlerinin temel kullanımını inceleyeceğiz.

## `img` Etiketi
HTML'de bir görsel göstermek için `<img>` elementi kullanılır.

En temel kullanımı:
```
    <img src="images/product.jpg" alt="Siyah akıllı saat">
```

Burada iki önemli attribute bulunur:
- `src`: Görsel dosyasının konumunu belirtir.
- `alt`: Görselin alternatif metnini belirtir.

`<img>` bir **void elementtir.** Yeni kapanış etiketi bulunmaz.

```
<!-- Doğru -->
<img src="image.jpg" alt="Dağ manzarası">

<!-- Böyle bir kapanış etiketi kullanılmaz -->
<img src="image.jpg" alt="Dağ manzarası"></img>
```

### `src` Attribute'u
`src` **source (kaynak)** anlamına gelir ve tarayıcıya hangi görselin yüklenmesi gerektiğini söyler.
```
    <img src="images/profile.png" alt="Profil Fotoğrafı">
```

Burada tarayıcı `images` klasörünün içerisindeki `profile.png` dosyasını yükler.

Harici bir kaynaktaki görsel de kullanılabilir:
```
    <img
        src="https://example.com/images/product.jpg"
        alt="Ürün görseli"
    >
```

Ancak gerçek projelerde görselin nereden ve nasıl sunulduğu proje mimarisine göre değişebilir.

### `alt` Attribute'u
`alt`, **alternative text (alternatif metin)** anlamına gelir.

Görselin neyi ifade ettiğini metinsel olarak açıklamak için kullanılır.

```
    <img
        src="watch.jpg"
        alt="Siyah deri kayışlı klasik kol saati"
    >
```

`alt` özellikle erişilebilirlik açısından önemlidir. Görme engelli kullanıcıların kullandığı ekran okuyucular, uygun durumlarda bu metinden yararlanarak görsel hakkında bilgi sağlayabilir.

Ayrıca görsel yüklenemediğinde alternatif metin kullanıcıya görsel hakkında bilgi verebilir.

**İyi Bir `alt` Nasıl Olmalıdır?**

Görselin anlamını mümkün olduğunca kısa ve açıklayıcı şekilde aktarmalıdır.

Örneğin:
```
    <!-- Yetersiz -->
    <img src="shoe.jpg" alt="Görsel">

    <!-- Daha açıklayıcı -->
    <img
        src="shoe.jpg"
        alt="Beyaz tabanlı siyah spor ayakkabı"
    >
```

Ancak `alt`metni yazarken görselde bulunan her ayrıntıyı uzun anlatmak da gerekmez.

Amaç: `Görselin bulunduğu bağlamdaki anlamını aktarmaktadır.`

**Dekoratif Görsellerde `alt`**

Her görsel kullanıcıya anlamlı bilgi sunmayabilir.

Örneğin yalnızca tasarım amacıyla kullanılan dekoratif bir görsel varsa boş `alt` kullanılabilir:
```
    <img src="decorative-shape.svg" alt="">
```
Bu kullanım ekran okuyucuya görselin içerik açısından önemli olmadığını belirtir.

Burada; `alt=""` ile:
```
    <!-- alt tamamen yok -->
    <img src="decorative-shape.svg">
```
aynı şey değildir.

Anlamlı bir görselde uygun alternatif metin sağlanmalıdır; dekoratif görsellerde ise boş `alt` kullanımı tercih edilebilir.

**Görsel Boyutları: `width` ve `height`**
HTML içerisinde görselin doğal görüntüleme boyutları `width` ve `height`attribute'larıyla belirtilebilir.
```
<img
    src="product.jpg"
    alt="Akıllı saat"
    width="600"
    height="400"
>
```

Buradaki değerler CSS'teki gibi 600px şeklinde yazılmaz:
```
    <!-- Doğru -->
    width="600"

    <!-- Yanlış -->
    width="600px"
```

Görseller için width ve height değerlerinin belirtilmesi tarayıcının görsel yüklenmeden önce sayfada ne kadar alan ayrılması gerektiğini hesaplamasına yardımcı olur. Bu da görsel yüklenirken sayfa içeriğinin beklenmedik şekilde kaymasını azaltabilir.

Responsive tasarımda görüntünün ekranda nasıl boyutlandırılacağı ise çoğunlukla CSS ile kontrol edilir:
```
    img {
        max-width: 100%;
        height: auto;
    }
```

Burada HTML görsel hakkında temel bilgiyi sağlarken CSS görselin **ekranda nasıl davranacağını** yönetir.

**Görselleri Açıklamalarıyla Kullanmak: `<figure>` ve `<figcaption>`**

Bir görselin kendisine ait bir açıklaması varsa `<figure>` ve `<figcaption>` kullanılabilir.

```
    <figure>

        <img
            src="cappadocia.jpg"
            alt="Kapadokya üzerinde uçan sıcak hava balonları"
        >

        <figcaption>
            Gün doğumunda Kapadokya'daki sıcak hava balonları.
        </figcaption>

    </figure>
```

Burada:
```
    <figure> → görsel ve ilişkili içeriği gruplar.
    <figcaption> → bu içeriğin açıklamasını belirtir.
```
`figure` yalnızca fotoğraflar için kullanılmak zorunda değildir. Grafik, diyagram, illüstrasyon veya kod örneği gibi kendi başına anlam taşıyan içerikler için de kullanılabilir.

Her `<img>` elementini `<figure>` içerisine almak gerekmez. Figure, görsel veya benzeri içerik bağımsız bir öğe olarak sunuluyor ve açıklamayla ilişkilendiriliyorsa anlamlıdır.

**Responsive Görseller ve `<picture>`**
Modern web uygulamalarında aynı görsel her cihaz veya durumda ideal olmayabilir.

Örneğin masaüstünde geniş bir görsel kullanırken mobil cihazda farklı kırpılmış bir görsel göstermek isteyebiliriz.

HTML bunun için `<picture>` elementini sağlar.

Basit bir örnek:
```
    <picture>

        <source
            media="(max-width: 768px)"
            srcset="hero-mobile.jpg"
        >

        <img
            src="hero-desktop.jpg"
            alt="Dağların arasında bulunan göl"
        >

    </picture>
```

Burada ekran genişliği `768px`veya daha küçük olduğunda `hero-mobile.jpg` kullanılabilir. Diğer durumlarda ise `<img>` içerisindeki `hero-desktop.jpg` görseli kullanılır.

`<img>` burada aynı zamanda **fallback (yedek) kaynak** görevini görür ve `<picture>`içerisinde bulunması gerekir.

**Farklı Görsel Formatları Sunmak**
`<picture>` yalnızca ekran boyutuna göre farklı görsel göstermek için kullanılmaz. Tarayıcıya farklı görsel formatları da sunabiliriz.

Örneğin:
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
            alt="Siyah akıllı saat"
        >

    </picture>
```
Tarayıcı desteklediği uygun kaynağı seçebilir. Mantık kabaca şöyledir:
```
    AVIF destekleniyor mu?
            ↓
        Evet → AVIF

        Hayır
            ↓
    WebP destekleniyor mu?
            ↓
        Evet → WebP

        Hayır
            ↓
        JPG
```

Başlangıç seviyesinde `<picture>` için bu mantığı bilmek yeterlidir. Responsive image optimizasyonunun `srcset`, `sizes` ve farklı çözünürlük seçimleri gibi daha ileri ayrıntıları ayrıca incelenebilir.

### Görsellerde `loading` Attribute'u

Görsellerde karşılaşabileceğimiz bir diğer özellike `loading` attribute'udur.

Örneğin:
```
    <img
        src="product.jpg"
        alt="Siyah akıllı saat"
        loading="lazy"
    >
```

`loading="lazy"`, tarayıcıya görselin yüklenmesini kullanıcı ilgili alana yaklaşana kadar ertelemesinin uygun olduğunu bildirir. Özellikle sayfanın aşağı bölümlerinde bulunan çok sayıda görsel için faydalı olabilir.

Örneğin bir ürün listesinde şu şekilde kullanılabilir:
```
    <img
        src="product-24.jpg"
        alt="Kahverengi deri çanta"
        loading="lazy"
    >
```
Ancak sayfanın ilk açılışında hemen görünmesi gereken önemli görsellerde, örneğin üst bölümdeki ana içerik görselinde, `lazy` kullanımı her zaman uygun olmayabilir.

## HTML'de Video Kullanımı
HTML5 ile birlikte web sayfasına video eklemek için `<video>` elementi kullanılabilir. Basit kullanım:
```
    <video src="intro.mp4" controls>
        Tarayıcınız video elementini desteklemiyor.
    </video>
```

Buradaki `controls` attribute'u kullanıcıya oynatma, durdurma, ses ve ilerleme gibi tarayıcının sağladığı video kontrollerini gösterir.

## `<source>`ile Video Kaynakları
Video içerisinde birden fazla kaynak tanımlamak için `<source>` kullanılabilir.
```
    <video controls>

        <source
            src="intro.webm"
            type="video/webm"
        >

        <source
            src="intro.mp4"
            type="video/mp4"
        >

        Tarayıcınız video elementini desteklemiyor.

    </video>
```
Tarayıcı desteklediği uygun kaynağı kullanabilir. Buradaki `<source>`elementi de kapanış etiketi olmayan bir **void elementtir.**

### Video Attribute'ları
`<video>` elementiyle birlikte bazı temel attribute'lar kullanılabilir.

**`controls`**

Video kontrollerini gösterir.

`<video scr="video.mp4" controls></video>`

**`autoplay`**

Videonun otomatik olarak oynatılmasını ister.

`<video src="video.mp4" autoplay></video>`

Ancak modern tarayıcılar özellikle sesli videoların otomatik oynatılmasını kullanıcı deneyimi nedeniyle kısıtlayabilir.

Bu nedenle otomatik oynatılan videolarda sıkça bu kullanımıyla karşılaşılır:
```
    <video
        src="video.mp4"
        autoplay
        muted
    ></video>
```

**`muted`**

Videonun başlangıçta sessiz olmasını sağlar.

`<video src="video.mp4" muted></video>`

**`loop`**

Video sona ulaştığında tekrar oynatılmasını sağlar.

`<video src="video.mp4" loop></video>``

Bu özellikler birlikte de kullanılabilir:
```
    <video
        src="background.mp4"
        autoplay
        muted
        loop
    >
    </video>
```

Örneğin arka planda sürekli oynayan dekoratif videolarda böyle bir yapıyla karşılaşabiliriz.

**`poster` Attribute'u**

Video başlamadan önce gösterilecek görsel `poster` ile belirtilebilir.
```
    <video
        src="product-video.mp4"
        controls
        poster="product-cover.jpg"
    >
    </video>
```

Video henüz oynatılmıyorken kullanıcı: `product-cover.jpg` görselini görebilir.
Bu görseli bir anlamda videonun **kapak görseli** olarak düşünebiliriz.

## HTML'de Ses Kullanımı
Ses dosyaları için `<audio>`elementi kullanılır.
```
    <audio src="podcast.mp3" controls>
        Tarayıcınız audio elementini desteklemiyor.
    </audio>
```

Video elementinde olduğu gibi birden fazla kaynak da verilebilir:
```
    <audio controls>

        <source
            src="podcast.ogg"
            type="audio/ogg"
        >

        <source
            src="podcast.mp3"
            type="audio/mpeg"
        >

        Tarayıcınız audio elementini desteklemiyor.

    </audio>
```

`audio`elementinde de `controls`, `autoplay`, `muted` ve `loop` gibi özelliklerle karşılaşabiliriz.

## Boolean Attribute Mantığı
Burada küçük ama HTML öğrenirken önemli bir ayrıntı var. Şu ana kadar:
```
    controls
    autoplay
    muted
    loop
```
gibi attribute'lar gördük. Bunlara **boolean attribute** denir.

Örneğin `controls` attribute'unun bulunması özelliğin aktif olduğunu belirtir.
```
    <video controls></video>
```

Benzer şekilde `<video autoplay muted loop></video>` şeklinde kullanılabilir. Bu yüzden HTML'de genellikle `controls="true"` yazmamız gerekmez.

## Görsellerde Erişilebilirlik ve Performans
Görseller kullanılırken yalnızca ekranda güzel görünmelerine odaklanmamak gerekir. 

Temel olarak şu noktalara dikkat etmek iyi bir yaklaşımdır. Anlamlı görsellere uygun `alt` metni ekleyin.
```
    <img
        src="product.jpg"
        alt="Kahverengi deri omuz çantası"
    >
```

Dekoratif görseller için içi boş `alt` kullanın. `<img src="decoration.svg">`

Mümkün olduğunda görsel boyutlarını belirtin.
```
<img
    src="product.jpg"
    alt="Kahverengi deri omuz çantası"
    width="600"
    height="800"
>
```

Sayfanın aşağısındaki uygun görsellerde lazy loading değerlendirin.
```
<img
    src="product.jpg"
    alt="Kahverengi deri omuz çantası"
    loading="lazy"
>
```

Ayrıca web için uygun boyutlandırılmış ve optimize edilmiş görseller kullanmak sayfa performansı açısından önemlidir.

## Kısaca Özet
HTML'de temel görsel ve medya elementleri şu şekilde düşünülebilir:
| Element        | Kullanım amacı                                  |
| -------------- | ----------------------------------------------- |
| `<img>`        | Görsel göstermek                                |
| `<picture>`    | Farklı koşullara uygun görsel kaynakları sunmak |
| `<source>`     | Alternatif medya/görsel kaynakları tanımlamak   |
| `<figure>`     | Bağımsız görsel veya medya içeriğini gruplamak  |
| `<figcaption>` | Figure içeriğine açıklama eklemek               |
| `<video>`      | Video eklemek                                   |
| `<audio>`      | Ses içeriği eklemek                             |

Örneğin basit bir içerik sayfasında bunların birkaçını birlikte görebiliriz:
```
<article>

    <h1>Kapadokya Gezi Rehberi</h1>

    <figure>

        <img
            src="cappadocia.jpg"
            alt="Kapadokya üzerinde uçan sıcak hava balonları"
            width="1200"
            height="800"
        >

        <figcaption>
            Gün doğumunda Kapadokya.
        </figcaption>

    </figure>

    <p>
        Kapadokya, kendine özgü doğal oluşumları ve
        sıcak hava balonlarıyla bilinen önemli bir
        seyahat bölgesidir.
    </p>

    <video controls poster="video-cover.jpg">

        <source
            src="cappadocia.webm"
            type="video/webm"
        >

        <source
            src="cappadocia.mp4"
            type="video/mp4"
        >

        Tarayıcınız video elementini desteklemiyor.

    </video>

</article>
```

Burada önemli olan yalnızca bir görseli veya videoyu **sayfaya ekleyebilmek** değil, doğru HTML elementiyle, erişilebilirliği ve performansı da düşünerek kullanabilmektir.