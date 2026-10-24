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

cover, görselin en-boy oranını koruyarak arka plan alanunu tamamen kaplayacak şekilde özçeklenmesini sağlar.

Görselin bazı bölümleri görünür alanın dışında kalabilir.

Örnek:
- Element: 600 x 300px
- Görsel: 800 x 800px

Kare görsel, geniş bir alanu tamamen kaplayabilmek için büyütülür veya uygun ölçekte yerleştirilir. Üst ve alt bölümlerinin bir kısmı görünmez hale gelebilir.

### 2. contain
```
    .hero {
        background-image: url("hero.jpg");
        background-size: contain;
    }
```

contain, görselin en-boy oranını koruyarak tamamının arka plan alanına sığmasını sağlar. Bu nedenle alanın bazı bölümleri boş kalabilir.

Ayurıca *background-srepeat* varsayılan olarak repeat olduğu için contain kullanırken tekrar davranışını da kontrol etmek gerekir.

```
    .hero {
        background-size: contain;
        background-repeat: no-repeat;
    }
```

### cover ve contain Karşılaştırması
|Özellik                     |cover                      |contain                    |
|----------------------------|---------------------------|---------------------------|
|Görselin oranı korunur      |Evet                       |Evet                       |
|Alan tamamen kaplanır       |Evet                       |Her zaman değil            |
|Görselin tamamı görünür     |Her zaman değil            |Evet                       |
|Boş alan kalabilir          |Hayır                      |Evet                       |
|Tipik kullanım              |Hero, banner, tam alan görselleri |Logo dekoratif görseller|

### 3. Sabit Boyut Kullanımı
```
    .box {
        background-size: 200px 100px;
    }
```

İlk değer genişliği, ikinci değer yüksekliği belirler.
```
    .box {
        background-size: 200px auto;
    }
```

Bu kullanımda görselin genişliği 200px olurken yükseklik oran korunacak şekilde hesaplanabilir. İki boyutu birbirinden bağımsız vermek görseli esneterek bozabilir.

### 4. Yüzdesel Değerler
```
    .box{
        background-size: 50% auto;
    }
```

Yüzdesel değerler, arka plan boyutlandırma alanına göre hesaplanır. 

**Not:** background-size: cover kullanmamak tek başına hata değildir. Kullanılacak değer, görselin dekoratif mi yoksa tamamının görünmesi gereken bir öğe mi olduğuna göre seçilmelidir.

## background-position - Arka Plan Konumu
*background-position*, arka plan görselinin element içinde hangi konumda görüntüleneceğini belirler.

### Anahtar Kelimeler
```
    .hero {
        background-position: center;
    }
```
Yaygın değerler:
- top
- bottom
- left
- right
- center

Örnek:
```
    .hero {
        background-position: center top;
    }
```
Burada görsel yatayda ortalanır, dikeyde üst tarafa hizalanır.

### İki Değer Kullanımı
```
    .hero {
        background-position: right bottom;
    }
```

Genel iki değerli sayısal kullanımda:
``` 
    .hero {
        background-position: 20px 10px;
    }
```
- 20px: yatay konum
- 10px: dikey konum

değerini ifade eder.

### Yüzdesel Konumlandırma
``` 
    .hero {
        background-position: 50% 50%;
    }
```
Bu değer görseli ortalar.
```
    .hero {
        background-position: 70% 30%;
    }
```
Bu kullanım özellikle cover nedeniyle kırpılan görsellerde önemlidir.

Örneğin görseldeki ana nesne sağ taraftaysa:
```
    .hero {
        background-size: cover;
        background-position: 70% center;
    }
```

ile görünür alanı daha uygun hale getirebiliriz.

**Teknik not:** Yüzdesel konumlandıröa, yalnızca element genişliğinin yüzdesi kadar kaydırma anlamına gelmez. Arka plan konumlandırma alanı ile ölçeklenmiş görsel arasındaki boyut farkı üzerinden hesaplanır.

### Kenardan Belirli Uzaklık Vermek
```
    .icon-background {
        background-position: right 20px bottom 10px;
    }
```
Bu örnekte görsel sağ kenardan 20px, alt kenardan 10px uzaklıkta konumlandırılır.

## background-attachment - Arka Planın Kaydırma Davranışı
background-attachment, arka planın kaydırma sırasında nasıl davranacağını belirler.

Üç temel değer vardır:
|Değer              |Davranış               |
|-------------------|-----------------------|
|scroll             |Elementin kutusuna bağlıdır; elementin içeriği kaydırılırsa arka plan içeriği takip etmez.|
|fixed              |Arka planı viewport'a göre sabitler.   |
|local              |Arka plan elementin kend, kaydırılabilir içeriğiyle birlikte hareket eder. |

### 1. scroll
Varsayılan değerdir.
```
    .section {
        background-attachment: scroll;
    }
```

Element sayfayla birlikte hareket ederkeb arka planı da elemetle birlikte hareket eder. Ancak elementin kendi içeriği ayrıca kaydırılıyorsa arka plan bu iç kaydırmaya bağlı değildir.

### 2. fixed
```
    .hero {
        background-image: url("landscape.jpg");
        background-size: cover;
        background-position: center;
        background-attachment: fixed;
    }
```

Arka plan viewport'a göre sabitlenir.

Sayfa kaydırıldığında element hareket ederken görselin sabit görünmesi, derinlik hissi oluşturan bir etki sağlayabilir.

Bu teknik bazen basit parallax benzeri efektşlerde kullanılır. Ancak gerçek parallax uygulamaları farklı hızlarda hareket etmesini de içerebilir.

### 3. local
```
    .scroll-box {
        height: 200px;
        overflow: auto;

        background-image: url("pattern.png");
        background-attachment: local;
    }
```

Bu kullanımda arka plan, elementin kendi kaydırılabilir içeriğiyle birlikte hareket eder.

### Mobil Tarayıcı Uyarısı
background-attachment: fixed, bazı mobil tarayıcılarda destek veya görüntüleme farklılıkları gösterebilir.

Ayrıca büyük görseller ve sabit arka plan efektleri kaydırma perforöamsını etkileyebilir. Bunedenle özellikle mobil cihazlarda test edilmelidir.

## background Shorthand
background, birden fazla arka plan özelliğini tek satırda tanımlamamızı sağlar.

**Uzun Kullanım**
```
    .hero {
        background-color: #f5f5f5;
        background-image: url("hero.jpg");
        background-repeat: no-repeat;
        background-position: center;
        background-size: cover;
    }
```

**Kısa Kullanım**
```
    .hero {
        background: #f5f5f5 url("hero.jpg") no-repeat center / cover;
    }
```

Her iki örnek de aynı temel arka plan ayarlarını tanımlar.

**Genel Sözdizimi**
```
    background: color image position / size repeat attachment arigin clip;
```

Bu, kavramsal bir şemadır; bütün parçaların her zaman bu sırada yazılması zorunlu değildir.

Ancak önemli bir kural vardır:
`background-size, shorthand içinde background-position değerinden sonra / ile belirtilir.`

```
    .hero {
        background: url("hero.jpg") center / cover no-repeat;
    }
```

Farklı Örnekler:
```
    .card {
        background: #ffffff;
    }

    .banner {
        background: url("banner.jpg") center / cover no-repeat;
    }

    .section {
        background: #26251f url("texture.png") repeat;
    }
```

### Shorthand Kullanırken Dikkat
background shorthand, belirilmeyen ilgili alt özellikleri başlangıç değerlerine sıfırlar.
```
    .hero {
        background-size: cover;
        background: url("hero.jpg");
    }
```

Burada ikinci declaration, önceki background-size: cover ayarını sıfırlar.

Sonuç olarak background-size tekrar auto auto değerine döner.

Doğru yaklaşım:
```
    .hero {
        background: url("hero.jpg") center / cover no-repeat;
    }
```
veya:
```
    .hero {
        background: url("hero.jpg");
        background-size: cover;
    }
```
şeklinde olabilir.

## CSS Gradient - Degradeler
Gradient, iki veya daha fazla renk arasında geçiş oluşturmak için kullanılır.

CSS'te gradient'ler ayrı bir background-gradient property'si değildir. Gradient fonksiyonları birer CSS image değeri üretir ve background-image üzerinden uygulanır.
```
    .box {
        background-image: linear-gradient(red, blue);
    }
```

Ayrı gradient background shorthand ike de kullanılabilir.
```
    .box{
        background: linear-gradient(red, blue);
    }
```

### 1. Linear Gradient
*linear-gradient()* renklerin düz bir eksen boyunca geçiş yapmasını sağlar.
```
    .banner {
        background-image: linear-gradient(to right, #000000, #ffffff);
    }
```

Bu örnekte geçiş soldan sağa doğrudur.

**Yön Belirtmek**
```
    .box-1 {
        background: linear-gradient(to right, red, blue);
    }

    .box-2 {
        background: linear-gradient(to bottom, red, blue);
    }

    .box-3 {
        background: linear-gradient(45deg, red, blue);
    }
```
|Yön                    |Açıklama                       |
|-----------------------|-------------------------------|
|to right               |Soldan sağa                    |
|to left                |Sağdan sola                    |
|to bottom              |Yukarıdan aşağıya              |
|to top                 |Aşağıdan yukarıya              |
|45deg                  |Açısal yön tanımlar            |

Yön belirtilmezse varsayılan geçiş *to bottom* yönündedir.

**Birden Fazla Renk**
```
    .banner {
        background: linear-gradient(red, yellow, green);
    }
```

Renk geçişi üç farklı renk durağı üzerinden oluşturulur.

**Color Stop Kullanımı**
```
    .banner {
        background: linear-gradient(
            to right,
            #26251f 0%,
            #7d8570 50%,
            #faf9f6 100%
        );
    }
```
Burada renklerin geçişte hangi konumlarda yer alacağı açıkça tanımlanmıştır.

### 2. Radial Gradient
*radial-gradient()*, renklerin bir merkez veya belirlenen başlangıç noktası etrafından dışarıya doğru yayılmasını sağlar.
```
    .box{
        background: radial-gradient(circle, #ffffff, #26251f);
    }
```

Bu örnekte dairsel bir renk geçişi oluşturulur.

**Merkez Konumunu Değiştirmek**
```
    .box {
        background: radial-gradient(
            circle at top left,
            #ffffff,
            #7d8570
        );
    }
```
Gradient sol üst bölgeden başlayarak yayılır.

### 3. Conic Gradient
conic-gradient(), renklerin bir merkez etrafında açısal olarak değişmesini sağlar.
```
    .box[
        background: conic-gradient(red, yellow, green);
    ]
```

Bu özellik renk çarkları veya dekoratif açısal geçişler oluşturmak için kullanılabilir.

Örneğin:
```
    .color-wheel {
        width: 200px;
        aspect-ratio: 1;
        border-radius: 50%;

        background: conic-gradient(
            red,
            yellow,
            lime,
            cyan,
            blue,
            magenta,
            red
        );
    }
```

### Gradient Türlerinin Karşılaştırılması
|Gradient               |Geçiş Biçimi                   |Kullanım                |
|-----------------------|-------------------------------|------------------------|
|linear-gradient        |Düz eksen boyunca              |Banner, buton, sayfa arka planı |
|radial-gradient        |Merkezden dışarıya             |Işık ve vurgu efektleri |
|conic-gradient         |Merkez etrafında açısal        |Renk çarkı, dekoratif gösterimler |

### Gradient ile Arka Plan Rengi Birlikte Kullanılabilir mi?
Evet.

```
    .hero{
        background-color: #26251f;
        background-image: linear-gradient(
            to right,
            rgba(0, 0, 0, 0.7),
            rgba(0, 0, 0, 0.1)
        );
    }
```

Gradient saydam bçlgeler içerdiği için alttaki arka plan rengi görünebilir.

## Birden Fazla Arka Plan Katmanı
CSS'te bir elemente birden fazla arka plan görseli tanımlayabiliriz. Bunun için değerleri virgülle ayırırız.
```
    .hero {
        background-image:
            url("pattern.png"),
            url("landscape.jpg");
    }
```

**Öenmli:** İlk yazılan arka plan görseli en üst katmandadır.

```
    ÜST KATNMAN
        pattern.png
            ↓
        landscape.jpg
            ↓
        background-color
    ALT KATMAN
```

### 1. Gradient Overlay Oluşturmak
Gerçek projelerde sık kullanılan bir yöntem, görselin üzerine yan saydam koyu bir gradient yerleştirmektir.

```
    .hero {
        background-image:
            linear-gradient(
                rgba(0, 0, 0, 0.65),
                rgba(0, 0, 0, 0.25)
            ),
            url("hero.jpg");

        background-position: center;
        background-size: cover;
        background-repeat: no-repeat;
    }
```

Bu örnekte:
- 1. hero.jpg en altta görüntülenir
- 2. Gradient görselin üzerine uygulanır.
- 3. Gradient'in saydam renkleri sayesinde görsel görünmeye devam eder.
- 4. Koyu katman, beyaz metnin okunabiirliğini artırmaya yardımcı olabilir.

**HTML ve CSS ÖRNEĞİ**
HTML:
```
    <section class="hero">
        <div class="hero-content">
            <h1>Yeni Yerler Keşfet</h1>
            <p>Bir sonraki yolculuğuna ilham verecek rotalar.</p>
            <a href="#">Rotaları İncele</a>
        </div>
    </section>
```
CSS:
```
    .hero {
        min-height: 450px;
        padding: 48px 24px;

        display: flex;
        align-items: center;
        justify-content: center;

        background:
            linear-gradient(
                rgba(0, 0, 0, 0.65),
                rgba(0, 0, 0, 0.25)
            ),
            url("travel.jpg") center / cover no-repeat;
    }

    .hero-content {
        max-width: 600px;
        color: #ffffff;
        text-align: center;
    }

    .hero-content h1 {
        font-size: clamp(2rem, 4vw, 3.5rem);
        line-height: 1.2;
    }
```
Bu örnek, arka plan özelliklerinin tipografi ve responsive tasarımla birlikte kullanımını gösterir.

Not: Gradient overlay kullanmak metin kontrastını her durumda garanti etmez. Görselin açık ve koyu bölgelerinde metnin okunabilirliği ayrıca kontrol edilmelidir.

### 2. Her Katmana Farklı Ayar Vermek
```
    .hero {
        background-image:
            url("pattern.png"),
            url("hero.jpg");

        background-size:
            120px 120px,
            cover;

        background-repeat:
            repeat,
            no-repeat;

        background-position:
            top left,
            center;
    }
```

Virgülle ayrılan değerler arka plan katmanlarıyla sırasıyla eşleşir.
- İlk background-size, ilk görsele uygulanır.
- İkinci background-size, ikinci görsele uygulanır.

Bu yöntem farklı dekoratif katmanları tek elementte birleştirmemizi sağlar.

## CSS Filtreleri - filter
CSS filter özelliği, bir elementin görüntülenen sonuca görsel efektler uygulamamızı sağlar.

Örneğin, bir görseli bulanıklaştırabilir, parlaklığını azaltabilir veya siyah-beyaz hale getirebiliriz.
```
    img{
        filter: grayscale(100%);
    }
```

### Yaygın Filtre Fonksiyonları
|Fonksiyon                  |Görevi                    |Örnek                   |
|---------------------------|--------------------------|------------------------|
|blur()                     |Bulanıklık oluşturur      |blur(4px)               |
|brightness()               |Parlaklığı değiştirir     |brightness(80%)         | 
|contrast()                 |Kontrastı değiştirir      |contrast(120%)          |
|grayscale()                |Gri tonlama uygular       |grayscale(100%)         |
|saturate()                 |Renk doygunluğunu değiştirir|saturate(150%)        |
|sepia[]                    |Sepya efekti uygular      |sepia(100%)             |
|hue-rotate()               |Renk doygunluğunu değiştirir|saturate(150%)        |
|invert()                   |Renkleri tersine çevirir   |invert(100%)           |
|drop-shadow()              |Görünür şekle gölge uygular |drop-shadow(2px 4px 6px #0005)|

### 1. blur()
```
    .image {
        filter: blur(4px);
    }
```
Görseli bulanıklaştırır. Değer büyüdükçe bulanıklık etkisi artar.

### 2. brightness()
```
    .image{ 
        filter: blur(70%);
    }
```

Görselin parlaklığını azaltır.

Genel olarak:
- 0%: siyah sonuç
- 100%: orijinal parlaklık
- 150%: artırılmış parlaklık