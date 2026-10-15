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
