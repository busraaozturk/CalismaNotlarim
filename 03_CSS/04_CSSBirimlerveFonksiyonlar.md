# CSS Birimler ve Fonksiyonlar (Units & Functions)
CSS ile bir elementin rengini belirleyebildiğimiz gibi genişliğini, yüksekliğini, yazı boyutunu ve diğer ölçülerini de kontrol edebiliriz:

Örneğin:
```
    .card {
        width: 300px;
        padding: 20px;
        font-size:16px;
    }
```

Ancak bütün ölçüleri sabit değerlerle tanımlamak her ekran ve kullanıcı ihtiyacı için uygun olmayabilir. Bu nedenle CSS farklı ölçü birimleri ve hesaplama fonksiyonları sunar.

Bu bölümde aşağıdaki konuları inceleyeceğiz:
```
    CSS Units & Functions
    │
    ├── 1. CSS Birimleri
    │   ├── Absolute Units
    │   └── Relative Units
    │
    ├── 2. px
    ├── 3. em
    ├── 4. rem
    ├── 5. px / em / rem Karşılaştırması
    ├── 6. Diğer Nispi Birimler
    │   ├── %
    │   ├── vw / vh
    │   └── vmin / vmax
    │
    ├── 7. Responsive Tasarım Stratejisi
    ├── 8. Pratik Birim Kullanımı
    ├── 9. CSS Fonksiyonları
    │   ├── calc()
    │   ├── min()
    │   ├── max()
    │   └── clamp()
    │
    ├── 10. CSS Custom Properties
    ├── 11. Sık Yapılan Hatalar
    └── 12. Kısaca Özet
```

## CSS'te Birim (Unit) Nedir?
CSS'te bazı property'ler sayısal değerler alır.

Örneğin:
```
    .card{
        width:300px;
    }
```

Burada:
```
    width → Property
    300 → Sayısal
    px → Birim
```
300px, genişliğin 300 CSS pikseli olduğunu belirtir.

Ancak şu şekilde geçerli bir width değeri değildir:
```
    .card {
        width: 300;
    }
```

Çünkü **width** gibi uzunluk bekleyen property'lerde sıfır dışındaki sayısal değerlerin uygun bir birimle yazılması gerekir.

Örneğin:
```
    width:300px;
    width: 20rem;
    width: 50%;
```
geçerli kullanımlardır.

İstisna: CSS'te 0 uzunluk değeri genellikle birimsiz yazılabilir.
```
    margin:0;
    padding:0;
```

Ayrıca opacity, z-index, line-height gibi bazı property'ler birimsiz sayılar da kabul edebilir.

### CSS Birimlerinin İki Temek Kategorisi
CSS uzunluk birimleri iki ana gruba ayrılıt.
```
    CSS Length Units
    │
    ├── Absolute Units
    │   └── px
    │
    └── Relative Units
        ├── em
        ├── rem
        ├── vw
        ├── vh
        ├── vmin
        └── vmax
```

½ de sıklıkla nispi ölçülerle birlikte incelenir. Ancak teknik olarak bir uzunluk birimi değil, yüzde değeridir.

**Absolute Units (Mutlak Birimler):** Başka bir elementin ölçüsüne göre hesaplanmayan birimlerdir.

**Relativrr Units (Nispi Birimler):** Değerleri font boyutu, viewport veya ilgili referans ölçüye bağlı olarak hesaplanan birimlerdir.

## Mutlak Birim - px
px, CSS'te en sık kullanılan ölçü birimlerinden biridir.
```
    .card {
        width: 300px;
        padding: 20px;
        border-radius: 8px;
    }
```

Burada:
- width: 300px → geniişlik
- padding: 20px → iç boşluk
- border-radius: 8px → köşe yuvarlaklığı belirlenmektedir.

### px Nasıl Çalışır?
px,  CSS'in mutlak uzunluk birimlerinden biridir.
```
    .box{
        width:300px;
    }
```
Bu değer, parent elementin font boyutuna göre kendiliğinden değişmez.

Örneğin:
```
    .parent {
        font-size: 20px;
    }

    .box {
        width: 300px;
    }
```

Parent'ın **font-size** değeri değişse bile **.box** genişliği 300px olarak tanımlı kalır. Ancak burada önemli bir ayrım vardır: `CSS pikseli, fiziksel yoğunluğu CSS piksellerinin ekranda nasıl görüntüleneceğini etkileyebilir.`

Tarayıcı zoom'u ve cihazın piksel yoğunluğu CSS piksellerinin ekranda nasıl görüntüleneceğini etkileyebilir. Dolayısıyla px değerlerinin tarayıcı zoom'undan hiç etkilenmediğini söylemek doğru değildir.

### px Neden Her Ölçü İçin İdeal Değildir?
Şu örneği düşünelim:
``` 
    .container {
        widtth: 1200px
    }
```
Bu genişlik, dar bir mobil ekrana sığmayabilir. 

Benzer şekilde:
```
    .card {
        width:400px;
        height:500px;
    }
```
gibi sabit ölçüler, ,çer,k veya kullanılabilir alan değiştiğinde sorun oluşturulabilir. Özellikle sabit **height** değerleri, metin büyüdüğünde içeriğin taşmasına yol açabilir. Ancak bunun nedeni px biriminin yanlış olması değil, tasarımın ihtiyaç duyduğu esnekliğin sağlanmamasıdır.

## px Ne Zaman Kullanılır?
px özellikle hassas görsel detaylarda kulllanışlıdır.
```
    .card {
        border: 1px solid #dddddd;
        box-shadow: 0 2px 8px rgb(0 0 0 / 10%);
    }
```
Burada: 
```
    1px → İnce kenarlık
    2px → Gölgenin dikey konumu
    8px → Gölgenin bulanıklığı
```
tanımlanmaktadır.

px, yalnızca border ve shadow için kullanılmak zorunda değildir. Ancak yazı boyutları ve genel boşluklarda kullanıcı tercihleriyle daha kolay ölçeklenen **rem** veya **em** çoğu zaman avantaj sağlar.

## Nispi Birim - em
em, font boyutuna bağlı bir uzunluk birimidir.

Örneğin:
```
    .card{
        font-size: 20px;
    }

    .card-title {
        font-size: 1.5rem;
    }
```

HTML:
```
    <div class="card">
        <h2 class="card-title">
            Ürün Başlığı
        </h2>
    </div>
```

Burada **.card-title** için:
```
    Parent font-size : 20px
    em değeri : 1.5
    20 x 1.5 → 30px
```
hesaplaması yapılır. Sonuç olarak başlığın font boyutu 30px olur.

### em Hangi Font Boyutunu Referans Alır?
Burada önemli bir  ayrım vardır. *em* birimi font-size property'sinde kullanılıyorsa parent elementin hesaplanmış font boyutuna göre değerlendirilir.
```
    .card {
        font-size:20px;
    }

    .card-title {
        font-size: 1.5em;
    }
```

Ancak **padding, margin veya width** gibi diğer property'lerde kullanılan **em, elementin kendi hesaplanmış font boyutunu** referans alır.

Örneğin:
```
    .button {
        font-size: 20px;
        padding: 1em;
    }
```
Bu durumda `padding:1em, 20px`olarak hesaplanır. Bu ayrım, em birimini doğru anlamak için önemlidir.

### Font-Size Miras Zinciri
CSS'te **font-size** normalde miras alınabilen bir property'dir. Bir element için font boyutu tanımlanmadığında parent elementin hesaplanmış font boyuru kullanılabilir.

Örneğin:
```
    <html>
        <body>
            <div class="card">
                <p class="text">
                    Merhaba
                </p>
            </div>
        </body>
    </html>
```
Basitleştirilmiş miras zinciri:
```
    html → font-size: 16px
        ↓
    body → font-size: inherit
        ↓
    .card → font-size: inherit
        ↓
    .text → font-size: inherit
```

Eğer .card üzerinde:
```
    .card {
        font-size: 20px;
    }
```

tanımlanırsa .text elementi de başka bir değer belirtmediği dürece bu font boyutunu miras alır. Buradaki **inherit**, miras alma davranışını açıklamak için gösterilmiştir; her elemente ayrıca yazılması gerekmez.

### İç İçe em Kullanımı
em kullanırken dikkat edilmesi gereken konulardan biri iç içe font boyutu tanımlarıdır.

Örneğin:
```
    .parent {
        font-size: 20px;
    }

    .child {
        font-size: 1.5em;
    }

    .grandchild {
        font-size: 1.5em;
    }
```

HTML:
```
    <div class="parent">
        <div class="child">
            <p class="grandchild">
                Merhaba
            </p>
        </div>
    </div>
```

Hesaplama:
```
    .parent
    20px
    ↓
    .child
    20 × 1.5 = 30px
    ↓
    .grandchild
    30 × 1.5 = 45px
```

Burada em değerleri iç içe kullanıldıkça font boyutları katlanarak büyüyebilir. Bu davranış bazen istenebilir. Ancak farkında olmadan kullanılırsa tasarımı yönetmek zorlaşabilir.

### em Avantajları
em, bileşenin kendi font boyutuyla orantılı ölçüler tanımlamak için kullanışlıdır.

Örneğin:
```
    .button {
        font-size:1rem;
        padding: 0.75em 1.5em;
    }
```
Butonun font boyutu büyütülürse em ile tanımlanan padding değerleri de orantılı olarak büyür. Bu nedenle **em** özellikle:
- Buton iç boşlukları,
- Metinle orantılı ikonlar,
- Badge ve chip gibi küçük bileşenler,
- Font boyutuna göre ölçeklenmesi istenen ölçüler için uygundur.

Temel mantık: em, bileşenin yazı boyutuyla birlikte büyüyen veya küçülen ölçüler oluşturmayı kolaylaştırır.

## Niapi Birim - rem
rem, *root em* ifadesinden gelir. em biriminden farklı olarak referans aldığı font boyutu, kök element olan <html> elementinin font boyutudur.

Örneğin:
```
    html {
        font-size: 16px;
    }

    .card-title {
        font-size: 2rem;
    }
```

Hesaplama:
```
    Root font-size → 16px
    rem değeri → 2
    16 x 2 → 32px
```

Sonuç: `font-size: 32px;` olur.

### rem Parent Elementten Etkilenir mi?
rem, parent elementin font boyutuna bağlı değildir.

Örneğin:
```
    html {
        font-size: 16px;    
    }

    .parent {
        font-size: 24px;
    }

    .child {
        font-size: 2rem;
    }
```

.child için aşağıdaki gibi hesaplanır:
```
    html font-size → 16px
    2rem → 32px
```

Parent elementin 24px olması bu hesaplamayı değiştirmez.
```
    html → 16px
    │
    ├── .parent → 24px
    │       │
    │       └── .child → 2rem = 32px
    │
    └── .another-child → 2rem = 32px
```

Bu nedenle rem, genel ölçüler için daha tahmin edilebilir bir sistem oluştururç

### 1rem Her Zaman 16px midir?
Hayır. Tarayıcıların yaygın varsayılan font boyutu 16px olduğu için çoğu başlangıç örneğinde `1rem = 16px` kabul edilir.

Ancak bu değer kesşn ve değişmez değildir. Kullanıcının tarayıcı veya kök elementte tanımlanan font boyuru farklı olabilir.

Örneğin:
```
    html {
        fonr-size: 20px;
    }
```
olduğunda:
```
    1rem = 20px
    2rem = 40px
```
olur.

Bu yüzden rem birimini sabit olarak 16px şeklinde ezberleyemeyiz.

### rem Neden Tercih Edilir?
rem, genel tasarım ölçülerinin ortak bir referansa bağlı olmasını sağlar.

Örneğin:
```
    .card{
        padding: 1.5rem;
        border-radius: 0.75rem;
    }

    .card-title {
        font-size: 1.5rem;
    }

    .card-description {
        margin-top: 1rem;
    }
```
Burada ölçüler kök font boyutuna bağlıdır. Bu yaklaşım:
- Genel tipografi ölçeği,
- Sayfa ve bileşen boşlukları,
- Gap değerleri,
- Bazı genişlik ve yükseklik sınırları için tutarlı bir sistem kurmayı kolaylaştırır.

Ayrıca kök font boyutu kullanıcı tercihlerine göre değiştiğinde rem tabanlı ölçüler de buna uyum sağlayabilir. Ancak **rem kullanmak tek başına responsive tasarım oluşturmaz.**

Bir elementin genişliği 80rem olarak sabitlenmişse dar ekranlarda yine taşma yaşanabilir. Responsive tasarım için birim seçiminin yanında esnek yerleşim ve uygun boyut sınırları da gereklidir.

## px, em ve rem Karşılaştırması
Bu üç birim CSS'te farklı ihtiyaçlara hizmet eder.

|Özellik        |px          |em             |rem            |
|---------------|------------|---------------|---------------|
|Referans       |CSS pikseli |Font boyutu    |Kök font boyutu|
|Parent font-size'dan etkilenir mi?|Hayır|Kullanıma göre|Hayır|
|Font ayarlarıyla ölçeklenme|Dolaylı / sınırlı|Evet|Evet|
|Responsive tasarımda kullanılabilir mi?|Evet|Evet|Evet|
|Hesaplama kolaylığı |Yüksek |İç içe kullanımda zorlaşabilir|Yüksek|
|Genel tasarım ölçeğine uygunluk|Duruma bağlı|Bileşen odaklı|Yüksek|
|Yaygın kullanım|İnce detaylar, sabit ölçüler|Bileşen içi oranlar|Tipografi, genel boşluklar|

***Akılda Kalıcı Benzetme***
```
    px → Çiviyle sabitlemek / Belirli bir CSS piksel ölçüsü
    em → Lastik gibi esnemek / Elementin font boyutuyla orantılı
    rem → Ortak ayarlanabilir / Kök font boyutuna bağlı
```

Bu benzetme birimlerin temel farkını hatırlamak içindir. px tamamen değişmez, rem ise otomatik olarak her ekrana uyum sağlar anlamına gelmez.

## Diğer Nispi Ölçüler
CSS'te em ve rem dışında farklı referanslara bağlı ölçüler de bulunur.

### 1. % - Yüzde
% ilgili property'nin tanımladığı referans değere göre hesaplanır.

Örneğin:
```
    .parent {
        width: 600px;
    }

    .child {
        width: 50%;
    }
```

Bu örnekte .child genişliği şöylr olur:
```
    600px x 50%
        ↓
    300px
```

Ancak bütün yüzde değerlerinin her zaman parent genişliğine göre hesaplandığını düşünmemeliyiz. Yüzdenin hangi ölçüyü referans aldığı kullanılan property'ye bağlıdır.

Örneğin, yüzdeyle tanımlanan **height** için referans yüksekliğin belirlenmiş olması önemli olabilir.

### 2. vw - Viewport Width
vw, viewport genişliğine bağlıdır.
```
    1vw → Viewport genişliğinin %1'i
```

Örneğin viewport genişliği 1200px ise: `10vw = 120px` olur.

CSS:
```
    .hero-title {
        font-size: 4vw;
    }
```
Bu kullanım viewport genişliği değiştikçe yazı boyutunu da değiştirir. Ancak yalnızca vw kullanmak çok küçük ekranlarda metni aşırı küçültebilir, büyük ekranlarda ise aşırı büyütebilir. Bu nedenle responsive tipopgrafide **clamp()** gibi sınırlandırma yöntemleri kullanışlıdır.

### 3. vh - Viewport Height
vh, viewport yüksekliğine bağlıdır. 
```
    1vh → Viewport yüksekliğinin %1'i
```

Örneğin:
```
    .hero {
        min-height: 100vh;
    }
```

viewport yüksekliğiyle ilişkili bir minimum yükseklik tanımlar. Mobil tarayıcılarda adres çubuğu gibi arayüzlerin görünmesi veya gizlenmesi kullanılabilir yüksekliği etkileyebilir.

Modern CSS'te bu durumlar için svh, lvh ve dvh gibi viewport birimleri de vardır. Başlangıçta bu birimleri tanımak yeterlidir; ayrıntılarını responsive tasarım konusunda inceleyebiliriz.

### 4. vmin ve vmax
**vmin**, viewport'un genişlik ve yüksekliğinden küçük olanına göre hesaplanır.

**vmax** ise büyük olanına göre hesaplanır.

Örneğin:
```
    .circle {
        width: 20vmin;
        height: 20vmin;
    }
```
Bu ölçüler viewport'un kısa kenarıyla orantılıdır.

|Birim      |Referans   |
|-----------|-----------|
|     %     |Property'ye bağlı referans ölçü|
|    vw     |Viewport genişliği|
|    vh     |Viewport yüksekliği|
|    vmin   |Viewport'un kısa kenarı|
|    vmax   |Viewport'un uzun kenarı|

## Responsive Tasarım ve Birim Stratejisi
Responsive tasarım, bir arayüzün farklı ekran boyutlarında ve kullanım koşullarında işlevsel ve okunabilir kalmasıbı sağlamayı amaçlar.

Örneğin bir ürün kartı masaüstünde geniş bir alanda görüntülenirken mobilde daha dar bir alana yerleşebilir. Ancak responsive tasarım yalnızca px yerine rem yazmak değildir.

### Esnek Olmayan Yaklaşım
Örneğin:
```
    .container {
        width: 1200px;
    }

    .product-card {
        width: 400px;
        height: 500px;
    }
```

Burada bütün ölçüler sabitlenmiştir. Dar ekranlarda yatay taşıma oluşabilir. İçerik uzadığında sabit yükseklik de sorun yaratabilir. Bu nedenle özellikle ana yerleşim alanlarında esnek ölçüler kullanmak daha güvenli olabilir.

### Daha Esnek Yaklaşım
Örneğin:
```
    .container {
        width: min(100% - 2rem, 75rem);
        margin-inline: auto;
    }
```
Burada şu mantık vardır:
```
    100% - 2rem → Kullanılabilir genişlikten boşluk bırak
    75rem → Maksimum hedef genişlik
    min() → Küçük olanı kullan
```

Bu sayede container, geniş ekranlarda belirli bir sınırı aşmazken dar ekranlarda küçülebilir. `min()` fonksiyonunu ilerleyen bölümde ayrıntılı olarak inceleyeceğiz.

### Responsive Tasarımda Birlikte Çalışan Yapılar
```
    html font-size
        │
        ├── rem
        │   └── Genel tipografi ve ölçüler
        │
        └── em
            └── Bileşen içi oranlar

    Flexbox / Grid → Esnek yerleşim
    max-width / min-width → Boyut sınırları
    Media Queries → Gerektiğinde yerleşim değişiklikleri
```

Bunlar birbirini sırayla çalıştıran zorunlu aşamalar değildir. Birlikte kullanılabilen farklı CSS araçlarıdır.

### Kök Font Boyutuyla Ölçeklendirme
Örneğin:
```
    html {
        font-size: 16px;
    }

    .card {
        padding: 2rem;
        gap: 1rem;
    }

    .card-title {
        font-size: 1.5rem;
    }
```

Burada: 
```
    2rem = 32px
    1rem = 16px
    1.5rem = 24px
```
olur.

Şimdi bir media query yazalım:
```
    @media (max-width: 768px) {
        html {
            font-size: 14px;
        }
    }
```

Bu durumda media query koşulu sağlandığında aşağıdaki gibi hesaplanır:
```
    2rem = 28px
    1rem = 16px
    1.5rem = 14px 
```

Yani kök font boyutunu değiştirmek, rem tabanlı birçok ölçüyü birlikte etkileyebilir. Ancak önemli bir erişilebilirlik notu: `Mobil ekranlarda bütün yazıları küçültmek için kök font boyutunu düşürmek genel bir en iyi uygulama değildir. Özellikle kullanıcıların tercih ettiği yazı boyutlarını dikkate almak gerekir.`

Bu örnek yalnızca rem biriminin ortak referans üzerinden nasıl hesaplandığını göstermek içindir. Gerçek projelerde çoğu zaman kök font boyutunu tarayıcı varsayılanına bırakmak ve gerekli bileşen ölçülerini ayrı ayrı düzenlemek daha uygundur.

### Responsive Tasarımda Önce Neyi Düşünmeliyiz?
Katı bir öncelik sırası yerine şu yaklaşımı benimseyebiliriz:
- 1. İçeriğin doğal olarak büyüyüp küçülebilmesine izin vermek.
- 2. Flexbox veya Grid ile esnek yerleşim kurmak.
- 3. width, max-width, min-width gibi property'lerle uygun sınırlar belirlemek.
- 4. rem, em, % ve viewport birimlerini ihtiyaca göre kullanmak.
- 5. Yerleşimin gerçekten değişmesi gereken noktalarda media query kullanmak.

Media query son çare değildir; responsive tasarımın temel araçlarından biridir. Ancak her küçük ekran sorununu çok sayıda media query ekleyerek çözmeye çalışmak yerine önce yerleşimin neden esnek olmadığını anlamak daha sağlıklıdır.

## Pratik Kullanım Kuralları - Hangi Birim Nerede
### 1. Layout - Flexbox ve Grid
Layout oluştururken asıl konu yalnızca birim seçimi değildir. Elementlerin nasıl yerleşeceğini de belirlememiz gerekir.

Örneğin:
```
    .product-grid {
        display: grid;
        grid-template-columns: repeat(
            auto-fit,
            minmax(min(100%, 16rem), 1fr)
        );
        gap: 1.5rem;
    }
```

Bu örnekte Grid, kullanılabilir alana göre sütunların sayısını değiştirebilir. Böylece her ekran genişliği için ayrı bir media query yazmak gerekmeyebilir. Grid ve Flexbox özelliklerinin ayrıntılarını ilgili layout konularında işleyeceğiz.

### 2. Genel Ölçüler — rem
Örneğin:
```
    .card {
        padding: 1.5rem;
        border-radius: 0.75rem;
        max-width: 25rem;
        min-height: 18rem;
    }
```
Bu yaklaşım genel ölçülerin ortak bir font boyutuna bağlı olmasını sağlar.

**min-height**, içeriğin gerektiğinde daha fazla alan kullanmasına izin verdiği için sabit **height** değerine göre bazı durumlarda daha esnektir.

### 3. Bileşen İçi Oranlar — em
Örneğin:
```
    .button {
        font-size: 1rem;
        padding: 0.75em 1.5em;
    }
```
Butonun font boyutu değiştiğinde padding de orantılı değişir.

Benzer şekilde:
```
    .button-icon {
        width: 1em;
        height: 1em;
    }
```
ikonun boyutunu kendi font boyutuyla ilişkilendirir. İkonun parent ile aynı font boyutunu miras aldığı durumlarda ikon ve metin birlikte ölçeklenebilir.

### 4. İnce Detaylar — px
```
    .card {
        border: 1px solid #e5e5e5;
        box-shadow: 0 2px 8px rgb(0 0 0 / 8%);
    }
```
Bu tür görsel detaylarda px oldukça kullanışlıdır.

### 5. Tam Bir Buton Örneği
```
    <button class="button">
        Devam Et
    </button>

    .button {
        font-size: 1rem;
        padding: 0.75em 1.5em;
        border: 1px solid #7d8570;
        border-radius: 0.5rem;
        background-color: #7d8570;
        color: white;
    }
```
Burada:
|Property   |Birim  |Neden?|
|-----------|-------|------|
|font-size  |rem    |Genel tipografi ölçeği|
|padding    |em     |Buton yazısıyla orantılı boşluk|
|border     |px     |İnce kenarlık|
|border-radius|rem|Tutarlı köşe ölçüsü|

Bu örnek, farklı birimlerin aynı bileşen içinde bilinçli olarak kullanılabileceğini gösterir.

##  CSS Fonksiyonları Nedir?
CSS'te bazı değerler doğrudan sayı veya anahtar kelime olarak yazılır.

Örneğin:
```
    width: 300px;
    color: red;
```
Ancak bazı durumlarda bir değeri hesaplamak veya birden fazla seçenek arasından belirlemek isteyebiliriz.

Bunun için CSS fonksiyonları kullanılabilir.

Genel yapı: `property: function(arguments);`

Örneğin:
```
    .container {
        width: calc(100% - 40px);
    }
```
Burada *calc()*, CSS'in değer hesaplamak için sunduğu fonksiyonlardan biridir.

Bu bölümde dört temel matematiksel fonksiyonu inceleyeceğiz:
```
    CSS Functions
    │
    ├── calc()
    ├── min()
    ├── max()
    └── clamp()
```

### 1. calc() Fonksiyonu
calc(), CSS içerisinde matematiksel işlemler yapmamızı sağlar.

Örneğin:
```
    .container {
        width: calc(100% - 40px);
    }
```
Burada:
```
    100% → Referans genişlik
    40px → Çıkarılacak ölçü
    calc() → Hesaplama
```
mantığı vardır.

Parent genişliği 800px ise:
```
    800px - 40px → 760px
```
sonucu elde edilir.

### calc() ile Kullanılan Operatörler

calc() içerisinde temel olarak:
```
    + → Toplama
    - → Çıkarma
    * → Çarpma
    / → Bölme
```
işlemleri yapılabilir.

Örneğin:
```
    .box {
        width: calc(50% + 20px);
    }

    .box {
        width: calc(100% / 2);
    }

    .box {
        padding: calc(1rem * 2);
    }
```
Özellikle farklı birimleri bir arada kullanabilmesi önemlidir.

Örneğin:`width: calc(100% - 2rem);` Burada yüzde ve rem birlikte kullanılmaktadır.

### Operatörlerde Boşluk Kullanımı
calc() içerisinde + ve - operatörlerinin iki yanında boşluk bırakılmalıdır.

Yanlış: `width: calc(100%-40px);`

Doğru: `width: calc(100% - 40px);`

`*` ve `/` için aynı boşluk zorunluluğu yoktur; ancak okunabilirlik için operatörlerin etrafında boşluk bırakmak iyi bir alışkanlıktır.

Ayrıca bütün birim kombinasyonları her matematiksel işlemde geçerli değildir. Örneğin uzunlukları birbirleriyle doğrudan çarpmak geçerli bir CSS uzunluk sonucu üretmez.

### 2.  min() ve max() Fonksiyonları
Bu iki fonksiyon, verilen değerler arasından uygun olanı seçmek için kullanılır.

**min() — Küçük Değeri Seçer**

Örneğin:
```
    .container {
        width: min(90%, 600px);
    }
```
Burada iki değer bulunmaktadır:
```
    90%
    600px
```
Tarayıcı, hesaplama sonucunda küçük olanı kullanır.

Örneğin parent genişliği 1000px ise:
```
    90% = 900px
    600px = 600px
    min() → 600px
```
Parent genişliği 500px ise:
```
    90% = 450px
    600px = 600px
    min() → 450px
```
Bu nedenle min() responsive genişlikler için kullanışlıdır.

**max() — Büyük Değeri Seçer**

Örneğin:
```
    .card {
        padding: max(1rem, 2vw);
    }
```
Burada:
```
    1rem
    2vw
```
değerlerinden hesaplama sonucunda büyük olan seçilir.

Bu yaklaşım, bir ölçünün belirli bir alt sınırın altında kalmamasını istediğimiz durumlarda kullanılabilir.
| Fonksiyon     | Davranış                  |Örnek              |
|---------------|---------------------------|-------------------|
|min()          |Küçük değeri seçer         |min(90%, 600px)    |
|max()          |Büyük değeri seçer         |max(1rem, 2vw)     |

### clamp() Fonksiyonu
clamp(), bir değerin alt ve üst sınırlarını belirlememizi sağlar.

Genel syntax: `clamp(minimum, preferred, maximum)`

Burada:
```
    minimum → Alt sınır
    preferred → Tercih edilen değer
    maximum → Üst sınır
```
tanımlanır.

Örneğin:
```
    .hero-title {
        font-size: clamp(1rem, 2vw, 1.5rem);
    }
```
Bu kullanımda font boyutu:
- 1rem değerinin altına düşmez.
- Tercih edilen 2vw değerine göre değişebilir.
- 1.5rem değerinin üstüne çıkmaz.

**clamp() Nasıl Çalışır?**

Kök font boyutunun 16px olduğunu varsayalım. `font-size: clamp(16px, 2vw, 24px);`

Viewport genişliği 600px olduğunda:
```
    2vw = 12px
    Minimum = 16px
    ↓
    Sonuç = 16px
```
Viewport genişliği 1000px olduğunda:
```
    2vw = 20px
    ↓
    Sonuç = 20px
```
Viewport genişliği 1600px olduğunda:
```
    2vw = 32px
    Maximum = 24px
    ↓
    Sonuç = 24px
```
Bu nedenle clamp(), esnek ama sınırlandırılmış ölçüler oluşturmak için kullanışlıdır.

**Responsive Tipografi Örneği**
```
    .hero-title {
        font-size: clamp(
            1.75rem,
            1.25rem + 2vw,
            3rem
        );
    }
```
Bu örnekte yazı boyutu viewport'a göre değişebilir ancak tanımlanan sınırların dışına çıkmaz. Bu yaklaşım bazı responsive tipografi ihtiyaçlarında media query sayısını azaltabilir. Ancak her tasarım için tek başına yeterli değildir.

## CSS Değişkenleri — Custom Properties
CSS' te tekrar kullanılabilir değerler tanımlamak için **Custom Properties** kullanabiliriz. Günlük kullanımda bunlara CSS değişkenleri de denir.

Örneğin:
```
    :root{
        --color-primary: #7d8570;
    }
```

Burada:
```
    --color-primary → Custom Property
    #7d8570 → Tanımlanan değer
```
vardır.

### Custom Property Nasıl Kullanılır?
Tanımlanan değeri kullanmak için **var()** fonksiyonundan yararlanırız.
```
    :root {
        --color-primary: #7d8570;
    }

    .button {
        background-color: var(--color-primary);
    }
```

Burada şu mantık vardır:
```
    --color-primary → Değer tanımlar
    var(--coloprimary) → Değer kullanılır
```

### Neden `:root` Kullanılır?
`:root`, HTML belgesinde kök elementi hedefler. Bu nedenle genel tasarım değerleri sıklıkla burada tanımlanır.

Örneğin:
```
    :root {
        --color-primary : #7d8570;
        --color-text: #26251f;
        --spacing-md: 1rem;
        --radius-md: 0.75rem;
    }
``` 

Bu değerleri farklı elementlerde kullanabiliriz:
```
    .card {
        color: var(--color-text);
        padding: var(--spacing-md);
        border-radius: var(--radius-md);
    }

    .button {
        background-color: var(--color-primary);
    }
```
Böylece aynı değerleri her yerde tekrar yazmak zorunda kalmayız.

### Custom Properties Yalnızca :root İçinde mi Tanımlanır?
Hayır. Bir elementin kendi custom property değerleri olabilir.

Örneğin:
```
    :root {
        --button-color: #7d8570;
    }

    .button {
        background-color: var(--button-color);
    }

    .button-danger {
        --button-color: #c0392b;
    }
```

HTML:
```
    <button class="button">
        Normal Buton
    </button>

    <button class="button button-danger">
        Sil
    </button>
```

- İlk buton genel değeri kullanır.
- İkinci buton ise kendi üzerinde tanımlanan değeri kullanır.

Bu davranış custom properties'in cascade ve inheritance mekanizmalaarıyla birlikte çalışmasından kaynaklanır.

### var() Fallback Değeri

Bir custom property tanımlanmamışsa kullanılacak alternatif değer belirtilebilir.

Örneğin:
```
    .button {
        background-color: var(--button-color, black);
    }
```
Burada şu mantık vardır:
```
    --button-color → Kullanılabilir bir değer var mı?
    Evet → Onu kullan
    Hayır → black
```
mantığı vardır.

Ancak fallback, tanımlanan rengin görsel olarak uygun olup olmadığını kontrol etmez. Örneğin bir custom property tanımlıysa fakat kullanılan property için geçersiz bir değere dönüşüyorsa var() fallback'i her durumda bu sorunu çözmez.

### CSS Değişkenleri ve Sass/Less Değişkenleri
CSS custom properties ile Sass/Less değişkenleri aynı çalışma mekanizmasına sahip değildir.
| Özellik   | CSS Custom Properties | Sass/Less Değişkenleri |
|-----------|-----------------------|------------------------|
|Nerede değerlendirilir?| Tarayıcıda| Derleme aşamasında|
|Cascade'den etkilenir mi?| Evet| Doğrudan hayır|
|Inheritance ile çalışır mı?|Evet, normal custom properties| CSS mirası gibi değil|
|Media query ile değişebilir mi?|Evet | Derleme kuralları farklıdır|
|Javascript ile güncellenebilir mi?|Evet|Derlenmil değişken doğrudan değil|

Örneğin:
```
    :root {
        --spacing: 1rem;
    }

    @media (min-width: 768px) {
        :root {
            --spacing: 1.5rem;
        }
    }

    .card {
        padding: var(--spacing);
    }
```
Burada --spacing değeri media query koşuluna göre değişebilir. Bu nedenle CSS custom properties modern tasarım sistemlerinde oldukça kullanışlıdır.

Not: var() yalnızca custom property değerini kullanmak içindir. 
Örneğin @media (max-width: var(--breakpoint)) biçimi normal CSS'te geçerli bir 
media query sınırı oluşturmaz.

## Sık Yapılan Hatalar
### 1. em Değerinin İç İçe Katlanmasını Unutmak
```
    .parent{
        font-size: 1.5em;
    }

    .child {
        font-size: 1.5em;
    }
```

Burada child font boyutu, parent'ın hesaplanmış font boyutunu referans alır. 
Bu nedenle iç içe em kullanımlarında beklenenden büyük değerler oluşabilir. 
Genel tipografi için rem, bileşen için em kullanmak birçok durumda daha öngörülebilir olabilir.

### 2. Bütün Ölçüleri Sabit px Değerleriyle Tanımlamak
```
    .container{
        width:1200px;
    }
```
Dar ekranlarda taşma oluşturabilir.

Daha esnek bir yaklaşım olabilir:
```
    .container{
        width: 100%;
        max-width: 75rem;
    }
```
Ancak gerçek projede container^ın dış boşlukları ve box model davranışı da dikkate alınmalıdır.

### 3. rem Kullanmanın Tek Başına Responsive Olduğunu Sanmak
```
    .container {
        width:100rem;
    }
```
Bu genişlik de dar ekranlarda sorun oluşturabilir. rem, responsive tasarımın araçlarından biridir; tek başına çözüm değildir.

### 4. calc() Sözdizimini Yanlış Yazmak
Yanlış: `width: calc(100%-40px);`

Doğru: `width: calc(100% - 40px);`

Özellikle + ve - operatörlerinin etrafındaki boşluklara dikkat edilmelidir.

### 5. min() ve max() Fonksiyonlarını Karıştırmak
`width: min(90%, 600px);` küçük olanı seçer.

`width: max(90%, 600px);` büyük olanı seçer.

İsimleri benzer olsa da sonuçları farklıdır.

### 6. Her Responsive Sorun İçin Media Query Yazmak
Bir layout dar ekrana sığmıyorsa doğrudan çok sayıda media query eklemek yerine önce şu noktaları incelemek faydalıdır:
- Sabit genişlik var mı?
- Flexbox veya Grid daha esnek kurulabilir mi?
- max-width kullanılabilir mi?
- İçerik doğal olarak satır değiştirebiliyor mu?

Media query, gerektiğinde bilinçli olarak kullanılmalıdır.

### 7. Custom Property Adının Başındaki -- İşaretini Unutmak
Yanlış:
```
    :root {
        primary-color: red;
    }
```
Doğru:
```
    :root {
        --primary-color: red;
    }
```
Kullanım:
```
    .button {
        color: var(--primary-color);
    }
```

### 8. var() Fonksiyonunu Normal Bir Property Gibi Kullanmak
Yanlış:
```
    .button {
        color: --primary-color;
    }
```
Doğru:
```
    .button {
        color: var(--primary-color);
    }
```
Custom property değerleri var() aracılığıyla kullanılmalıdır.

## Kısaca Özet
CSS'te ölçüler farklı referanslara bağlı olarak tanımlanabilir.

### Birim Karşılaştırması
|Birim      |Referans       |Kullanım       |
|-----------|---------------|---------------|
|px         |CSS pikseli    |İnce detaylar, belirli ölçüler|
|em         |Font boyutu    |Bileşen içi oranlar|
|rem        |Kök font boyutu|Genel tipografi ve boşluklar|
|%          |Property'ye bağlı referans|Oransal genişlikler ve diğer yüzdeli ölçüler|
|vw         |Viewport genişliği|Ekrana bağlı ölçüler|
|vh         |Viewport yüksekliği|Yükseklik odaklı alanlar|
|vmin       |Viewport kısa kenarı|Ekran oranına bağlı ölçüler|
|vmax       |Viewpoet uzun kenarı|Ekran oranına bağlı ölçüler|

Akılda kalıcı yaklaşım:
```
    px → Belirli CSS piksel ölçüsü
    em → Elementin font boyutuyla oran
    rem → Kök font boyutuyla oran
```

### Responsive Tasarımının Temel Mantığı
```
    Esnek içerik
        +
    Uygun ölçü birimleri
        +
    Flexbox / Grid
        +
    Boyut sınırları
        +
    Gerektiğinde media query
        ↓
    Responsive arayüz
```

### CSS Fonksiyonları
|Fonksiyon|Görevi|Örnek|
|---------|------|-----|
|calc()   |Matematiksel hesaplama|calc(100% - 2rem)|
|min()    |Küçük değeri seçer| min(90%, 600px)|
|max()|Büyük değeri seçer|max(1rem, 2vw)|
|clamp()|Değeri alt ve üst sınır arasında tutar|clamp(1rem, 2vw, 2rem)|

### CSS Custom Properties
Tanımlama:
```
    :root {
        --color-primary: #7d8570;
    }
```
Kullanma:
```
    .button {
        background-color: var(--color-primary);
    }
```
Fallback:
```
    .button {
        background-color: var(--color-primary, black);
    }
``` 
Genel akış:
``` 
    Custom Property
    --color-primary
       ↓
    Değer
    #7d8570
       ↓
    var(--color-primary)
       ↓
    CSS Property
    background-color
```
Bu bölümün temel amacı, her yerde tek bir birim kullanmak değil; hangi ölçünün neye bağlı olduğunu anlamak, esnek tasarımlar oluşturmak ve CSS fonksiyonlarıyla ölçüleri kontrollü şekilde yönetebilmektir.