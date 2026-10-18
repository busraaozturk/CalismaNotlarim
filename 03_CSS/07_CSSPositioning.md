# CSS Positioning (Konumlandırma)
Web sayfalarında elementler varsayılan olarak belirli bir düzene göre yerleşir. Ancak bazı tasarımlarda bu düzenin dışına çıkmamız gerekir.

Örneğin:
- Ürün kartının sağ üst köşesine indirim etiketi eklemek,
- Sayfa kaydırılırken bir menüyü üstte tutmak,
- Ekranın sağ alt köşesine yukarı çık butonu yerleştirmek,
- Bir görselin üzerine metin veya ikon eklemek,
- Açılır menüyü ilgili butonun altında konumlandırmak.

Bu tür ihtiyaçlar için **CSS'te Positioning (Konumlandırma)** özelliklerini kullanırız.

Temel property: `position` Bu property, elementin nasıl konumlandırılacağını ve hangi referans noktasına göre hareket edeceğini belirler.

##  Normal Akış (Flow Layout) Nedir?
Önceki Display bölümünde öğrendiğimiz gibi HTML elementleri, varsayılan olarak belge akışı içerisinde yerleşir.

Örneğin:
```
    <div>Birinci Kutu</div>
    <div>İkinci Kutu</div>
    <div>Üçüncü Kutu</div>
```
Bu elementler normal blok akışında alt alta yerleşir.
```
    ┌────────────────────┐
    │    Birinci Kutu    │
    └────────────────────┘

    ┌────────────────────┐
    │    İkinci Kutu     │
    └────────────────────┘

    ┌────────────────────┐
    │    Üçüncü Kutu     │
    └────────────────────┘
```
Bu yerleşime **Normal Flow (Normal Akış)** denir.

Normal akışta elementlerin yerleşimi HTML sırası, display davranışı ve diğer CSS yerleşim kurallarına göre hesaplanır.

**position property**'si, elementin bu akıştaki konumunu değiştirebilir veya elementi normal akışın dışına çıkarabilir. Ancak her position değeri elementi akıştan çıkarmaz. Bu ayrım, Positioning konusunun en önemli noktalarından biridir.

## position Property'sine Genel Bakış
CSS'te beş teöel position değeri bulunur:
```
    position: static;
    position: relative;
    position: absolute;
    position: fixed;
    position: sticky;
```

Her değer iki önemli soruyu farklı şekilde cevaplar:
1. Element normal akışta yer kaplamaya devam eder mi?
2. Element hangi noktaya göre konumlandırılır?

|Değer          |Temel davranışı                    |
|---------------|-----------------------------------|
|static         |Varsayılan yerleşim kurallarını kullanır   |
|relative       |Normal konumunu korur, görsel olarak kaydırılabilir    |
|absolute       |Normal akıştan çıkar, containing block'a göre konumlanır   |
|fixed          |Normal akıştan çıkar, genellikle viewport'a göre sabitlenir|
|sticky         |Normal akışta kalır, kaydırma sırasında belirlenen eşiğe yapışır   |

### Konumlandırma Property'leri
Positioning ile birlikte sık kullanılan dört özellik:
- top
- right
- bottom
- left

Bu özellikler, konumlandırılmış elementin ilgili referans alanına göre yerinin belirlenmesinde kullanılır.

Örneğin:
```
    .box {
        position: relative;
        top: 20px;
        left: 30px;
    }
```

Burada element:
- **top:** 20px ile normal konumundan aşağı,
- **left:** 30px ile normal konumundan sağa kaydırılır.

**Önemli:** top, right, bottom ve left değerlerinin etkisi kullanılan position türüne gçre değişir.

Ayrıca modern CSS'te yazı yönünden bağımsız konumlandırma için **inset, inset-inline ve inset-block** gibi özellikler de bulunur.

## position: static - Varsayılan Konumlandırma
HTML elementlerinin varsayılan position değeri: `position: static;` şeklindedir.

Bu değer kullanıldığında element, normal yerleşim kurallarına göre konumlanır.

Örneğin:
```
    <div class="box">Birinci</div>
    <div class="box">İkinci</div>

    .box {
        position: static;
        padding: 20px;
        margin-bottom: 10px;
        background-color: #f2f0eb;
    }
```
Elementler normal akışta yerleşmeye devam eder.

### top, right, bottom, left Neden Çalışmaz?
Örneğin:
```
    .box {
        position: static;
        top: 50px;
        left: 20px;
    }
```

Burada top ve left değerleri elementin konumunu değiştirmez. Çünkü bu offset özellikleri `position: static` üzerinde etkili değildir. Konumlandırma yapmak için uygun bir **position** değeri seçilmelidir.

**Kısaca:** static, özel konumlandırma uygulanmamış elementlerin temel davranışıdır.

## position: relative - Kendi Konumuna Göre Kaydırma
relative, elementi normal akıştan çıkarmadan görsel konumunu değiştirmemizi sağlar.

Örneğin: 
```
    <div class="box first">Birinci</div>
    <div class="box second">İkinci</div>
    <div class="box third">Üçüncü</div>

    .box {
        padding: 20px;
        margin-bottom: 10px;
        background-color: #f2f0eb;
    }

    .second {
        position: relative;
        top: 20px;
        left: 30px;
    }
```

Burada ikinci kutu normal konumuna göre:
- 20px aşağı
- 30px sağa kaydırılır.

### Relative Element Normal Akıştan Çıkar mı?
Hayır. Elementin normal akışta kapladığı alan korunur. Örneğin normal yerleşim:
```
    ┌──────────────────┐
    │     Birinci      │
    └──────────────────┘

    ┌──────────────────┐
    │     İkinci       │
    └──────────────────┘

    ┌──────────────────┐
    │     Üçüncü       │
    └──────────────────┘
```

İkinci kutuya `top: 20px` uygulandığında:
```
    ┌──────────────────┐
    │     Birinci      │
    └──────────────────┘

    ┌──────────────────┐
    │  İkinci'nin eski │
    │  yerleşim alanı  │
    └──────────────────┘
            │
            │ 20px aşağı
            ▼
        ┌──────────────────┐
        │     İkinci       │
        └──────────────────┘

    ┌──────────────────┐
    │     Üçüncü       │
    └──────────────────┘
```

Üçüncü kutu, ikinci kutunun görsel olarak kaydırılmasını dikkate alarak yeniden yerleşmez.

Bu nedenle relative kaydırma, elementlerin görsel olarak üst üste binmesine neden olabilir.

### top ve left Nasıl Çalışır?
```
    .box {
        position: relative;
        top:10px;
        left:20px;
    }
```
Bu örnekte:
```
    top: 10px → 10 px aşağı kaydırır
    left: 20px → 20px sağa kaydırır
```

Benzer şekilde:
```
    .box {
        position:relative;
        bottom: 10px;
        right: 20px;
    }
```
elementi yukarı ve sola kaydırır.

Aynı eksende hem top hem bottom veya hem left hem tight tanımlandığında CSS'in çakışma çözümleme kuralları devreye girer. Başlangıçta her eksen için tek bir offset kullanmak daha anlaşılırdır.

### Relative Ne Zaman Kullanılır?
**relative**, iki yaygın amaçla kullanılır:
1. Elementi normal konumundan küçük miktarlarda kaydırmak.
2. absolute konumlandırılmış çocuklara referans alanı oluşturmak.

İkinci kullanım modern arayüzlerde oldıkça yaygındır.

## position: absolute - Referans Alanına Göre Konumlandırma
absolute, elementi normal akıştan çıkarak belirli bir referans alanına göre konumlandırmamızı sağlar.

Örneğin:
```
    .badge{
        position: absolute;
        top: 10px;
        right: 10px;
    }
```

Bu kullanımda elementin yerleşimi normal blok veya inline akışındaki sırasına göre yapılmaz.

### Absolute Normal Akıştan Çıkar mı?
Evet. Absolute konumlandırılmış element normal akışta kendisine yer ayrılmasını sağlamaz.

Örneğin:
```
    <div class="first">Birinci</div>
    <div class="second">İkinci</div>
    <div class="third">Üçüncü</div>

    .second {
        position: absolute;
    }
```

Bu durumda ikinci element normal akıştan çıkar. Birinci ve üçüncü elementler , ikinci element normal akışta yer kaplamıyormuş gibi yerleşir.

Ancak ikinci element yine de görüntülenebilir ve diğer elementlerle çakışabilir.

### Absolute Neye Göre Konumlanır?
Burada **Containing Block (Referans Alanı)** kavramını öğrenmemiz gerekir. Bir absolute elementin top, right, bottom ve left değerleri, kendisi için oluşturulan containing block'a göre hesaplanır.

Yaygın durumda bu referans, **position** değeri **static** olmayan en yakın üst elementtir.

Örneğin:
```
    <div class="parent">
        <span class="child">Yeni</span>
    </div>

    .parent {
        position: relative;
    }

    .child {
        position: absolute;
        top: 10px;
        right: 10px;
    }
```

Burada `.child, .parent` elementinin padding kenarına göre konumlandırılır.

### Positioned Parent Nedir?
*position* değeri aşağıdakilerden biri olan elementler positioned olarak kabul edilir.
```
    position: relative;
    position: absolute;
    position: fixed;
    position: sticky;
```

**static** ise positioned değildir.

**Önemli teknik ayrıntı:** *transform, filter, contain* gibi bazı CSS özellikleri de absolute element için containing block oluşturabilir. Dolayısıyla referansın her zaman yalnızca **position** değerine göre belirlendiğini düşünmemeliyiz.

### Positioned Parent Yoksa Ne Olur?

Absolute element için uygun bir üst referans bulunmuyorsa **initial containing block** kullanılır. Normal sürekli sayfa düzeninde bu alan başlangıçta viewport boyutlarıyla ilişkilidir.

Ancak bu durum, absolute elementin viewport'a sabitlendiği anlamına gelmez. Sayfa kaydırıldığında absolute element normalde içerikle birlikte hareket eder. Bu nokta fixed ile arasındaki önemli farklardan biridir.

### Pratik Örnek - Ürün Katında İndirim Etiketi
HTML:
```
    <div class="product-card">
        <span class="discount-badge">%20 İndirim</span>

        <img src="product.jpg" alt="ürün görseli">

        <h3>Ürün Adı</h3>
        <p>1.250TL</p>
    </div>
```

CSS:
```
    .product-card {
        position: relative;
        padding: 16px;
        border: 1px solid #dddddd;
        border-radius: 12px;
    }

    .product-card img {
        display: block;
        width: 100%;
        height: auto;
    }

    .discount-badge {
        position: absolute;
        top: 12px;
        right: 12px;

        padding: 6px 10px;
        background-color: #b42318;
        color: white;
        border-radius: 6px;
    }
```

Beklenen Yerleşim:
```
    ┌─────────────────────────────┐
    │               ┌───────────┐ │
    │               │ %20       │ │
    │               │ İndirim   │ │
    │               └───────────┘ │
    │                             │
    │        ÜRÜN GÖRSELİ         │
    │                             │
    ├─────────────────────────────┤
    │ Ürün Adı                    │
    │ 1.250 TL                    │
    └─────────────────────────────┘
```

Etiket kartın sağ üst köşesine yerleştirilir. Bu **absolute konumlandırmanın gerçek projelerde en sık kullanıldığı örneklerden biridir.

## relative ve absolute Birlikte Kullanımı
Frontend geliştirmede çok sık karşılaşacağımız bir desen:
```
    .parent {
        position: relative;
    }

    .child {
        position:absolute;
        top: 0;
        right: 0;
    }
```
şeklindedir.

### Neden Birlikte Kullanılırlar?
Çünkü :
- Parent normal akışta kalır.
- Parent, child için referans alanı oluşturur.
- Child normal akıştan çıkar.
- Child, parent'ın belirlenen köşesine yerleştirilebilir.

```
    PARENT (position: relative)
    ┌─────────────────────────────────┐
    │                      ┌────────┐ │
    │                      │ CHILD  │ │
    │                      │absolute│ │
    │                      └────────┘ │
    │                                 │
    │          Parent İçeriği         │
    │                                 │
    └─────────────────────────────────┘
```

Bu desen yalnızca rozetlerde değil; görsel üzerindeki ikonlarda, bildirim sayaçlarında ve çeşitli açılır panellerde de kullanılır.

### Örnek - Bildirim Sayacı
HTML:
```
    <button class="notification-button" type="button">
        Bildirimler
        <span class="notification-count">3</span>
    </button>
```

CSS:
```
    .notification-button {
        position: relative;
        padding: 12px 20px;
    }

    .notification-count {
        position: absolute;
        top: -8px;
        right: -8px;

        min-width: 20px;
        height: 20px;
        padding: 0 4px;
        border-radius: 999px;

        display: grid;
        place-items: center;

        background-color: crimson;
        color: white;
        font-size: 12px;
    }
```

Burada bildirim sayacı butonun sağ üst köşesine taşınır.

**Dikkat:** Absolute element normal akışta yer kaplamadığı için parent'ın yüksekliğini otomatik olarak büyütmesini beklememeliyiz. İçeriğin taşması ihtimalini tasarımda dikkate almalıyız.

## position: fixed - Viewport'a Göre Sabitleme
fixed, elementi normal akıştan çıkarır ve çoğu durumda viewport'a göre konumlandırır.

Viewport, web sayfasının tarayıcıda görüntülenen alanıdır.

Örneğin:
```
    .back-to-top {
        position: fixed;
        right: 24px;
        bottom: 24px;
    }
```

Bu element normal koşullarda ekranın sağ alt köşesinde kalır. Kullanıcı sayfayı aşağı kaydırsa bile aynı noktada görüntülenmeye devam eder.

### Fixed Nasıl Davranır?
```
    VIEWPORT
    ┌──────────────────────────────┐
    │                              │
    │         Sayfa İçeriği        │
    │                              │
    │                              │
    │                       ┌────┐ │
    │                       │ ↑  │ │
    │                       └────┘ │
    └──────────────────────────────┘
```
Sayfa kaydırıldığında içerik hareket ederken fixed element görünür alanın aynı noktasında kalır.

### Pratik Örnek - Yukarı Çık Butonu
HTML:
```
    <a href="#top" class="back-to-top" aria-label="Sayfanın başına git">
        ↑
    </a>
```

CSS:
```
    .back-to-top {
        position: fixed;
        right: 20px;
        bottom: 20px;

        display: grid;
        place-items: center;

        width: 48px;
        height: 48px;

        border-radius: 50%;
        background-color: #26251f;
        color: white;
        text-decoration: none;

        z-index: 100;
    }
```

Bu örneğin çalışması için sayfanın üst kısmında `<body id="top">` gibi bir hedef bulunabilir.

### Fixed Kullanım Alanları
- Sabit navigasyon alanları,
- Yukarı çık butonları,
- Cookie bilgilendirme panelleri,
- Ekrana sabitlenmiş yardımcı kontroller.

### Fixed Her Zaman Viewport'a mi Göredir?
Genellikle evet, ancak istisnalar vardır. Örneğin üst elementlerde *transform, filter* veya *bazı containment* özellikleri kullanılması fixed elementin referans alanını değiştirebilir.

```
    .parent {
        transform: translateZ(0);
    }

    .child {
        position: fixed;
    }
```

Bu durumda **.child**, her zaman beklediğimiz şekilde viewport'a göre davranmayabilir. Dolayısıyla fixed elementlerin üst elementlerindeki CSS özelliklerini de kontrol etmek gerekir.

### Mobil Ekranlarda Fixed Kullanımı
Mobil tarayıcılarda:
- Adres çubuğunun açılıp kapanması,
- Ekran klavyesinin görünmesi,
- Görsel viewport'un değişmesi,
- Güvenli ekran alanları

fixed elementlerin konumunu etkileyebilir. Özellikle ekranın altına sabitlenen kontrollerde bu durum önemlidir.

Örneğin:
```
    .bottom-action {
        position: fixed;
        right: 16px;
        bottom: calc(16px + env(safe-area-inset-bottom, 0px));
    }
```
Bu kullanım desteklenen ortamlarda cihazın alt güvenli alanını hesaba katmaya yardımcı olur.

## position: sticky - Kaydırmaya Bağlı Konumlandırma
sticky, normal akışta yer alan bir elementin kaydırma sırasında belirli bir eşikte sabitlenmesini sağlar. Davranılı relative ve fixed konumlandırmanın bazı özelliklerini bir araya getirir.

Ancak teknik olarak sticky element, fixed elemente dönüşmez. 

Normal akıştaki alanını korur ve belirli sınırlar içerisinde kaydırılarak konumlandırılır.

### Temel Kullanım
```
    .section {
        position: sticky;
        top: 0;
    }
```

Bu örnekte element normal konumunda görüntülenir. Sayfa kaydırılıp element viewport'un üst kenarına yaklaşında **top: 0** eşiğine yapışır.

### Stick Davranış Şeması
Başlangıç:
```
    ┌────────────────────────────┐
    │ Sayfa Başlığı              │
    │                            │
    │ Bölüm Başlığı              │
    │ İçerik                     │
    │ İçerik                     │
    └────────────────────────────┘
```

Kaydırma sonrasında
```
    ┌────────────────────────────┐
    │ Bölüm Başlığı  ← STICKY    │
    ├────────────────────────────┤
    │ İçerik                     │
    │ İçerik                     │
    │ İçerik                     │
    └────────────────────────────┘
```

### Sticky İçin Eşik Değeri
Örneğin:
```
    .header {
        position: sticky;
        top: 0;
    }
```

Burada **top: 0** yapışma eşiğini belirler. Eğer üstte sabit bir alan varsa: 
```
    .section-title {
        position: sticky;
        top: 64px;
    }
```
kullanılabilir.

Bu durumda bölüm başlığı, uygun kaydırma koşullarında viewport'un üstünden 64px uzaklıkta tutulur.

**Önemli:** Dikey yönde sticky davranışı istiyorsak genellikle top veya bottom gibi bir eşik tanımlamalıyız. İlgili eksende her iki inset değeri de auto ise o eksende sticky davranışı oluşmaz.

### Sticky Parent Sınırlarını Aşar mı?
Hayır. Sticky element, containing block sınırları içerisinde kalır. Örneğin bir bölüm başlığı yalnızca ilgili bölümün içinde sticky davranışı gösterebilir. Bölüm sona erdiğinde başlık da onunla birlikte kaydırılır.

Bu nedenle sticky, farklı kategorilerin kendi başlıklarını kaydırma sırasında görünür tutmak için kullanışlıdır.

### Pratik Örnek — Sticky Kategori Başlığı
HTML:
```
    <section class="category">
        <h2 class="category-title">Elektronik</h2>

        <p>Ürün içeriği...</p>
        <p>Ürün içeriği...</p>
        <p>Ürün içeriği...</p>
    </section>
```

CSS:
```
    .category-title {
        position: sticky;
        top: 0;

        padding: 12px 16px;
        background-color: white;
        border-bottom: 1px solid #dddddd;

        z-index: 10;
    }
```

Bölüm kaydırıldığında başlık üstte kalabilir. Buradaki background-color, alttan kayan içeriğin başlığın arkasında görünmesini engellemek için önemlidir.

### Sticky Neden Çalışmayabilir?
Yaygın nedenler:
- İlgili eksende **top, bottom, left veya right** eşiğinin tanımlanmaması,
- Parent veya üst elementlerde **overflow: hidden, auto, scroll** gibi değerlerin bulunması,
- Sticky elementin hareket edebileceği yeterli alanın olmaması,
- Parent'ın yüksekliğinin sticky hareketine izin vermemesi,
- Beklenenden farklı bir scroll container'ın kullanılması.

Örneğin:
```
    .parent {
        overflow: hidden;
    }

    .child {
        position: sticky;
        top: 0;
    }
```

Burada .parent yeni bir kaydırma mekanizması oluşturabildiği için sticky davranışı beklenenden farklı olabilir. Bu her durumda sticky'nin tamamen devre dışı kaldığı anlamına gelmez. Sticky'nin hangi kaydırma alanını referans aldığı önemlidir.

## Position Değerlerinin Karşılaştırılması
Şimdi beş temel konumlandırma değerini birlikte inceleyelim.

|Position       |Normal akışta mı?      |Referans noktası       |Offset çalışır mı? |Scroll davranışı|
|---------------|-----------------------|-----------------------|------------|-----------------|
|static |Evet   |Normal yerleşim    |Hayır  |İçerikle kayar     |
|relative   |Evet   |Kendi normal konumu    | Evet  |İçerikle kayar |
|absolute   |Hayır  |Containing block       |Evet   |Genellikle içerikle kayar|
|fixed      |Hayır  |Genellikle viewport    |Evet   |Genellikle sabit kalır|
|sticky     |Evet   |Scrollport ve containing block sınırları|Evet  |Eşiğe kadar kayar, sonra yapışır|

### Hangi Durumda Hangisi Kullanılır?

Normal içerik yerleşimi: `position:static;`

Küçük görsel kaydrımalar veya absolute çocuğa referans: `position: relative`

Kart köşesinde rozet, görsel üzerinde ikon: `position: absolute`

Ekranın köşesinde sabit buton: `position: fixed`

Kaydırma sırasında üstte kalan bölüm başlığı: `position: sticky`

Bu ayrımı anlamak, konumlandırma sorasında yanlış property kullanmamızı önler.

## z-index ve Stacking Context
CSS'te bazı elementler görsel olarak üst üste gelebilir.

Örneğin:
- Açılır menü bir kartın üzerine gelebilir.
- Modal pencere sayfa içeriğini örtebilir.
- Bildirim etiketi ürün görselinin üzerinde bulunabilir.

Bu durumlarda hangi elementin önde görüntüleneceğini kontrol etmek için `z-index`property'sini kullanabiliriz.

### z-index Nedir?
z-indec, uygun yerleşim koşullarında elementlerin yığılma sırasını belirler.

Örneğin:
```
    <div class="box-one">Birinci</div>
    <div class="box-two">İkinci</div>

    .box-one {
        position: relative;
        z-index: 1;
    }

    .box-two {
        position: relative;
        z-index: 2;
    }
```

Bu iki element üst üste geldiğinde ve aynı stacking context içinde karşılaştırılabildiğinde .box-two önde görüntülenir.

```
    ÖN
    |
    |   z-index: 2
    |
    |   z-indec: 1
    |
    ARKA
```

### z-index Hangi Elementlerde Çalışır?
z-index, positioned elementlerde kullanılır:
```
    position:relative;
    position:absolute;
    position:fixed;
    position:sticky;
```

Ancak yalnızca bunlarla sınırlı değildir.

**Önemli istisna:** Flex ve Grid item'ları *position: static* olsalar bile z-index ile yığılma sırasına katılabilir.

Örneğin:
```
    .container {
        display: flex;
    }

    .item {
        z-index: 2;
    }
```

Burada **.item** bir flex item ise z-index etkili olabilir.

Normal blok akışındaki sıradan bir **position: static** elementte ise z-index beklenen şekilde çalışmaz.

### z-index Değerleri

Pozitif değer kullanılabilir:
```
    .element{
        z-index: 10;
    }
```

Sıfır değeri kullanılabilir:
```
    .element{
        z-index: 0;
    }
```

Negatif değer de kullanılabilir:
```
    .element{
        z-index: -1;
    }
```

Ancak negatif z-index elementin her zaman tüm sayfanın arkasına geçeceği anlamına gelmez. Sonuç **stacking context** yapısına bağlıdır.

### Stacking Context Nedir?
**Stacking Context**, elementlerin kendi aralarında belirli bir yığılma düzenine göre sıralandığı bağımsız bir katman grubudur. Bir stacking context içindeki çocukların z-index değerleri, başka bir stacking context'in çocuklarıyla doğrudan karşılaştırılamaz.

Bu kavramı anlamak için örnek inceleyelim.

**Örnek — z-index: 9999 Neden İşe Yaramıyor?**
```
    <div class="parent-one">
        <div class="child">Açılır Menü</div>
    </div>

    <div class="parent-two">
        Diğer Alan
    </div>

    .parent-one {
        position: relative;
        z-index: 1;
    }

    .child {
        position: absolute;
        z-index: 9999;
    }

    .parent-two {
        position: relative;
        z-index: 2;
    }
```
İlk bakışta .child değerinin 9999 olduğu için en üstte olması gerektiğini düşünebiliriz. Ancak:
```
    ANA STACKING CONTEXT
    │
    ├── parent-two
    │   └── z-index: 2
    │
    └── parent-one
        ├── z-index: 1
        │
        └── child
            └── z-index: 9999
```

Burada .parent-one ve .parent-two ayrı stacking context'ler oluşturur. .parent-one ana yığılma sırasında z-index: 1, .parent-two ise z-index: 2 seviyesindedir.

Dolayısıyla .child kendi grubunda 9999 olsa bile .parent-two grubunun önüne geçemez.

**Temel kural:** Yüksek z-index, elementin bütün sayfadaki diğer elementlerin önüne geçeceğini garanti etmez.

### Stacking Context Oluşturan Yygın Durumlar
Bazı örnekler:
```
    .element {
        position: relative;
        z-index: 1;        
    }
    .element {
        opacity: 0.9;
    }

    .element {
        transform: translateX(10px);
    }
```
Bu özellikler belirli koşullarda yeni stacking context oluşturur.

Ayrıca position: fixed, position: sticky, isolation: isolate ve başka CSS özellikleri de stacking context oluşturabilir.

### Gerçek projelerde z-index Yönetimi
Her probleme `z-index: 999999;` yazarak yaklaşmak doğru değildir. Bunun yerine katmanlar için tutarlı değerler tanımlanabilir.
```
    :root {
        --z-dropdown: 100;
        --z-sticky: 200;
        --z-overlay: 300;
        --z-modal: 400;
    }
```
Örneğin:
```
    .dropdown {
        position: absolute;
        z-index: var(--z-dropdown);
    }

    .modal {
        position: fixed;
        z-index: var(--z-modal);
    }
```
Bu yaklaşım değerlerin yönetimini kolaylaştırır.

Ancak stacking context sınırları yine geçerlidir; değişken kullanmak bu sınırları ortadan kaldırmaz.

## float - Kayan Elementler
float, bir elementi sola veya sağa yaslayarak metin gibi satır içi içeriğin çevresinden akmasını sağlayan CSS property'sidir.

Örneğin:
```
    <article class="article">
        <img src="article.jpg" alt="Makale görseli">

        <p>
            Bu paragraf görselin çevresinden akacak şekilde
            yerleştirilebilir. Metin devam ettikçe görselin
            yanında ve altında görüntülenir.
        </p>
    </article>

    .article img {
        float: left;
        width: 160px;
        margin-right: 16px;
        margin-bottom: 12px;
    }
```
Beklenen yerleşim:
```
    ┌───────────────────────────────┐
    │ ┌───────────┐ Metin metin     │
    │ │           │ metin metin     │
    │ │  GÖRSEL   │ metin metin     │
    │ │           │ metin metin     │
    │ └───────────┘ metin metin     │
    │ Metin metin metin metin       │
    └───────────────────────────────┘
```

### Float Normal Akışı Nasıl Etkiler?
Float element normal blok akışından çıkarılır. Ancak absolute elementten farklı olarak çevresindeki satır içi içeriğin yerleşimini etkiler. Metin, float elementin kapladığı alanın çevresinden akar. Bu nedenle float'u absolute positioning ile aynı davranış olarak düşünmemeliyiz.

### float Değerleri
- float: left; → Elementi sola yaslar
- float: right; → Elementi sağa yaslar
- float: none; → Float davranışını kaldırır

### clear Property'si
clear, bir elementin belirli yöndeki float'ların yanına yerleşmesini engellemek için kullanılır.
```
    .footer {
        clear: both;
    }
```
Yaygın değerler:
```
    clear: left;
    clear: right;
    clear: both;
    clear: none;
```
**clear: both**, ilgili elementin hem sol hem sağ float'ların altına geçmesini sağlayabilir.

### Float ve flow-root İlişkisi
```
    .article {
        display: flow-root;
    }
```
Bu kullanım yeni bir BFC oluşturur. Böylece kapsayıcı, içindeki float elementlerin boyutlarını kendi yüksekliği hesaplanırken dikkate alabilir.

Float kaynaklı kapsayıcı yüksekliği sorunlarında kullanışlıdır.

### Modern CSS'te Float Kullanımı
Eskiden float ile çok sütunlu sayfa düzenleri oluşturulurdu. Ancak günümüzde:
- Flexbox,
- CSS Grid

bu tür layout ihtiyaçları için daha uygundur.

Float'un temel kullanım alanı hâlâ metnin bir görsel veya benzeri içerik etrafından akmasını sağlamaktır.

## visibilty Property'si
**visibility**, elementin görünür olup olmayacağını kontrol eder.

Önceki 06 — CSS Display bölümünde display: none, visibility: hidden ve opacity: 0 arasındaki farkları ayrıntılı olarak incelemiştik.

Burada yalnızca temel değerleri hatırlayalım.

### visibility: visible
Elementin normal şekilde görünmesini sağlar.
```
    .box {
        visibility: visible;
    }
```

### visibility: hidden
Elementi görünmez yapar. Ancak normal yerleşimde kapladığı alan korunur.
```
    .box {
        visibility: hidden;
    }
```
Bu yönüyle *display: none* kullanımından farklıdır.

### visibility: collapse
collapse, özellikle tablo satırları ve sütunları için tanımlanmış özel bir görünürlük değeridir.

Örneğin:
```
    tr.is-collapsed {
        visibility: collapse;
    }
```
Bu kullanım desteklenen tablo yerleşimlerinde ilgili satırın kapladığı alanı kaldırabilir.

Ancak davranış tarayıcıya ve element türüne göre farklılık gösterebilir.

Normal elementlerde çoğunlukla hidden benzeri davranır.

**Hatırlatma:** Görünürlük yöntemlerinin yer kaplama, tıklanabilirlik ve erişilebilirlik farkları için 06 — CSS Display bölümündeki karşılaştırma tablosuna başvurabiliriz.

## Sık Yapılan Hatalar
### 1. Absolute Elementin Yanlış Yerde Görünmesi
```
    .badge {
        position: absolute;
        top: 0;
        right: 0;
    }
```
Bu kodun hangi alana göre çalıştığı kontrol edilmezse rozet beklenmedik bir yerde görüntülenebilir.

Yaygın çözüm:
```
    .card {
        position: relative;
    }

    .badge {
        position: absolute;
        top: 0;
        right: 0;
    }
```
Böylece kart referans alanı olur.

### 2. relative Elementin Eski Yerinin Korunduğunu Unutmak
```
    .box {
        position: relative;
        top: 40px;
    }
```
Bu kullanım elementi aşağı kaydırır ancak normal akıştaki alanını kaldırmaz. Sonraki elementler otomatik olarak 40px aşağı itilmez. Bu durum görsel çakışmaya neden olabilir.

### 3. z-index Değerini Static Elemente Vermek
```
    .box {
        position: static;
        z-index: 100;
    }
```
Normal blok akışındaki bir elementte bu kullanım beklenen etkiyi oluşturmaz.

Uygun bir çözüm:
```
    .box {
        position: relative;
        z-index: 100;
    }
```
Ancak Flex ve Grid item'larının position: static iken de z-index kullanabildiğini unutmamalıyız.

### 4. z-index Değerini Sürekli Artırmak
```
    .dropdown {
        z-index: 999999;
    }
```
Bu yaklaşım stacking context sorunlarını çözmeyebilir.

Bunun yerine:
- Üst elementlerin stacking context oluşturup oluşturmadığını,
- transform, opacity ve position değerlerini,
- Elementlerin DOM ve yerleşim ilişkilerini kontrol etmeliyiz.

### 5. Fixed Elementin Mobilde Yanlış Konumlanması
```
    .action-button {
        position: fixed;
        bottom: 0;
    }
```
Bu kullanım bazı mobil ekranlarda butonun sistem alanlarına çok yaklaşmasına veya klavyeyle çakışmasına neden olabilir.

Güvenli alanlar, viewport davranışı ve responsive ölçüler dikkate alınmalıdır.

### 6. Sticky Elementin Çalışmaması
```
    .parent {
        overflow: hidden;
    }

    .child {
        position: sticky;
        top: 0;
    }
```
Bu durumda sticky'nin referans aldığı kaydırma mekanizması değişebilir.

Kontrol edilmesi gerekenler:
- Üst elementlerin overflow değerleri,
- Parent yüksekliği,
- Kaydırılan gerçek element,
- Sticky eşiği,
- Hareket için yeterli alan bulunup bulunmadığı.

### 7. Absolute ile Bütün Sayfa Düzenini Oluşturmaya Çalışmak
```
    .sidebar {
        position: absolute;
        left: 0;
    }

    .content {
        position: absolute;
        left: 300px;
    }
```
Bu yaklaşım responsive ekranlarda ve değişken içerik yüksekliklerinde sorun çıkarabilir. 

Genel sayfa yerleşimleri için Flexbox veya Grid daha uygun olabilir.

Absolute positioning ise belirli elementleri başka elementlerin üzerine veya köşelerine yerleştirmek için kullanılmalıdır.

### 8. Float ile Modern Layout Oluşturmaya Çalışmak
```
    .column {
        float: left;
        width: 50%;
    }
```
Bu yaklaşım geçmişte yaygın olsa da modern arayüzlerde genellikle Flexbox veya Grid tercih edilir.

Float'u özellikle metin sarma ihtiyacı için kullanmak daha anlaşılır bir yaklaşımdır.

## Kısaca Özet
CSS Positioning, elementlerin normal yerleşim içerisindeki konumlarını değiştirmemizi veya belirli referans noktalarına göre konumlandırmamızı sağlar.

### Beş Temel Position Değeri
|Değer      |Normal Akış    |Referans           |Yaygın Kullanım        |
|-----------|---------------|-------------------|-----------------------|
|static     |İçinde         |Normal Yerleşim    |Standart içerik        |
|relative   |İçinde         |Kendi normal konumu|Kaydırma, absolute referansı|
|absolute   |Dışında        |Containing block   |rozet, ikon, overlay   |
|fixed      |Dışında        |Genellikle viewport|Sabit buton, panel     |
|sticky     |İçinde         |Scrollport ve parent sınırları |Yapışkan başlık|

### Position Mantığı
```
    CSS POSITION
    │
    ├── static
    │   └── Normal yerleşim
    │
    ├── relative
    │   ├── Normal akışta kalır
    │   └── Kendi konumuna göre kayar
    │
    ├── absolute
    │   ├── Normal akıştan çıkar
    │   └── Containing block'a göre konumlanır
    │
    ├── fixed
    │   ├── Normal akıştan çıkar
    │   └── Genellikle viewport'a sabitlenir
    │
    └── sticky
        ├── Normal akışta kalır
        └── Kaydırma eşiğine yapışır
```

### relative + absolute Deseni
```
    PARENT
    position: relative

    ┌──────────────────────────────┐
    │                    ┌───────┐ │
    │                    │ CHILD │ │
    │                    └───────┘ │
    │                              │
    │        Normal İçerik         │
    │                              │
    └──────────────────────────────┘

    CHILD
    position: absolute
    top: 0
    right: 0
```
Bu yapı kart rozetlerinde, görsel üzerindeki ikonlarda ve çeşitli açılır alanlarda kullanılır.

### z-index ve Stacking Context
```
    **z-index** → Uygun koşullarda katman sırasını belirler
    **Stacking Context** → Elementleri bağımsız yığılma gruplarında düzenler
    **Yüksek z-index** → Her zaman bütün sayfanın önüne geçmez
```

### Akılda Kalması Gerekenler

**static** → Varsayılan konumlandırmadır.
**relative** → Elementin normal akıştaki yerini koruyarak görsel olarak kaydırılmasını sağlar.
**absolute** → Elementi normal akıştan çıkarır ve referans alanına göre konumlandırır.
**fixed** → Elementi genellikle viewport'a göre sabitler.
**sticky** → Elementi kaydırma sırasında belirli bir eşikte tutar.
**z-index** → Uygun koşullarda üst üste gelen elementlerin sırasını belirler.
**stacking context** → Elementlerin hangi yığılma grubu içerisinde karşılaştırılacağını belirler.
**float** → Özellikle metnin görsel etrafından akmasını sağlar.
**visibility** → Elementin görünürlüğünü kontrol eder; her zaman yerleşim alanını kaldırmaz.

Bu bölümün en önemli noktası: `position kullanırken önce elementin normal akışta kalıp kalmadığını, ardından hangi referans alanına göre konumlandırıldığını belirlemeliyiz.`

Bu iki soruya doğru cevap vermek, CSS konumlandırma sorunlarının büyük bölümünü anlamamızı kolaylaştırır.

