# CSS Display (Görüntüleme ve Yerleşim)
HTML ile oluşturduğumuz her element, tarayıcı tarafından belirli yerleşim kurallarına göre görüntülenir.

Örneğin:
```
    <div>Birinci Kutu</div>
    <div>İkinci Kutu</div>
```

Bu iki div elementi varsayılan olarak alt alta yerleşir. Ancak:
```
    <span>Birinci metin</span>
    <span>İkinci metin</span>
```
elementleri, yeterli alan bulunduğunda aynı satırda görüntülenir.

Bunun temel nedeni elementlerin **varsayılan display davranışlarının farklı olmasıdır.** CSS'te bu davranışı kontrol etmek için `display` property'sini kullanırız.

## display Nedir?
**display**, bir elementin oluşturduğu kutuların nasıl davrandığını ve içindeki elementlerin nasıl yerleşeceğini belirleyen *CSS property*'sidir.

Temel olarak iki soruya cevap verir:
1. **Outer display (dış yerleşim):** Elementin kendisi, çevresindeki diğer elementlere göre sayfa akışında nasıl yerleşecek? → `block` veya `inline`
2. **Inner display (iç yerleşim):** Elementin çocukları hangi yerleşim düzenine göre konumlanacak? → `flow` (normal akış), `flex` veya `grid`

```
    DISPLAY
    │
    ├── Outer Display → block / inline
    │
    └── Inner Display → flow / flex / grid
```

Örneğin `display: block;` demek, dışarıdan `block` davranışı + içeride normal akış (`flow`) kullanmak anlamına gelir. `display: inline-flex;` ise dışarıdan `inline`, içeride `flex` davranışı demektir:
```
    .container {
        display: inline-flex;
    }

    Dış yerleşim → inline
    İç yerleşim  → flex
```

Modern CSS, bu iki özelliği `display: block flex;` gibi iki kelimeyle ayrı ayrı da yazdırabilir; bu, yaygın tek kelimelik `display: flex;` ile aynı anlama gelir.

## display:block
Block elementler normal belge akışında **blok seviyeli kutular oluşturur.** En temel özellikleri, genellikle kendi satırlarını kaplamaları ve kendilerinden sonraki bloklaro alt satıra yerleştirmeleridir.

Örneğin:
```
    <div>Birinci</div>
    <div>İkinci</div>
    <div>Üçüncü</div>
```

Tarayıcıda normal akışta şu şekilde yerleşir:
```
    ┌─────────────────────────────┐
    │ Birinci                     │
    └─────────────────────────────┘

    ┌─────────────────────────────┐
    │ İkinci                      │
    └─────────────────────────────┘

    ┌─────────────────────────────┐
    │ Üçüncü                      │
    └─────────────────────────────┘
```

### Block Elementlerin Özellikleri
- Normal blok akışında yeni bir satır oluştururlar.
- Varsayılan **width: auto** ile kullanılabilir yatay alanı genellikle doldururlar.
- width ve height değerleri uygulanabilir.
- padding, border ve margin dört yönde kutu ölçülerini ve yerleşimi etkileyebilir.
- Normal blok akışında bazı dikey margin değerleri birleşebilir.

### width: auto Davranışı
```
    <div class="card">
        Ürün Kartı
    </div>
```

```
    .card {
        display:block;
        background-color: #f2f0eb;
        padding: 16px;
    }
```

Burada genişlik belirtilmediği için normal blok yerleşiminde kutu kullanılabilir genişliği doldurur.

Ancak:
```
    .card {
        display:block;
        width:300px;
    }
```
yazıldığında genişlik belirli bir değere ayarlanır.

***Önemli:*** display:block kullanmak elementin her zaman ekranın tamamını kaplayacağı anlamına gelmez. Genişlik, içinde bulunduğu alan ve diğer CSS kurallarına göre hesaplanır.

### Varsayılan Block Elementler
Tarayıcıların varsayılan stillerinde yaygın olarak blok davranışı gösteren HTML elementleri:

|Element                |Kullanımı                      |
|-----------------------|-------------------------------|
|<div>                  |Genel amaçlı kapsayıcı         |
|<p>                    |Paragraf                       |
|<h1> - <h6>            |Başlıklar                      |
|<section>              |İçerik bölümü                  |
|<article>              |Bağımsız içerik                |
|<header>               |Başlık alanı                   |
|<footer>               |Alt bilgi alanı                |
|<ul>                   |Sırasız liste                  |
|<form>                 |Form kapsayıcısı               |

Bu davranışlar CSS ile değiştirilebilir.

### Block ve Margin Collapse
Box Model bölümünde gördüğümüz margin collapse davranışı normal blok akışında ortaya çıkabilir.
```
    .first {
        margin-bottom: 30px;
    }

    .second {
        margin-top: 20px;
    }
```

Uygun koşullarda iki element arasındaki dikey boşluk: `30px + 20px = 50px` yerine `30px` olabilir.

Bu davranış, Flexbox ve Grid yerleşimindeki item'lar için aynı şekilde gerçekleşmez.

## display: inline
Inline elementler normal satır içi akışa katılır. Block elementlerin aksine kendi başlarına yeni bir satır oluşturmazlar.

Örneğin:
```
    <p>
        Bu bir <strong>önemli</strong>
        ve <a href="#">bağlantılı</a> cümle.
    </p>
```

Burada:
- `<p>` → varsayılan olarak block,
- `<strong>` → varsayılan olarak inline,
- `<a>` → varsayılan olarak inline davranışı gösterir.

Tarayıcı, **strong** ve **a** elementlerini metnin akışı içerisinde görüntüler.

### Inline Elementlerin Özellikleri
Normal, değiştirilmemiş inline kutular için:
- Yeni bir satır oluşturmazlar.
- Satırdaki kullanılabilir alana göre akarlar.
- İçerikleri gerektiğinde birden fazla satıra bölünebilir.
- width ve height değerleri normal inline kutuların boyutunu belirlemez.
- Yatay padding, border ve margin uygulanabilir.
- Dikey margin satır yüksekliğini ve yerleşimini etkilemez.
- Dikey padding ve border görsel olarak çizilebilir ancak normal satır yüksekliğini artırmaz.

### Inline Elementte width Neden Çalışmaz?
Örneğin:
```
    <span class="label">Yeni Ürün</span>

    .label{
        display:inline;
        width:200px;
        height: 60px;
    }
```

Bu değerler normal inline kutunun genişliğini ve yüksekliğini beklediğimiz şekilde değiştirmez. Çünkü inline yerleşimde kutu, metin akışına göre oluşturulur. Eğer bu elemente belirli bir genişlik vermek istiyorsak:
```
    .label {
        display: inline-block;
        width: 200px;
        height: 60px;
    }
```
gibi farklı bir display davranışı kullanabiliriz.

### Inline Elementlerde Padding ve Margin
Örneğin:
```
    .highlight {
        display: inline;
        padding: 10px 20px;
        margin: 10px 20px;
        background-color: #cfc6ae;
    }
```

Burada yatay boşluklar satır içindeki yerleşimi etkiler. Ancak dikey margin değerleri satırları birbirinden uzaklaştırmaz. Dikey padding ise çizilir fakat normal satır yüksekliğini artırmaz; çevredeki satırlarla görsel olarak çakışabilir. Bu nedenle inline elementleri bir kart veya büyük bir kutu gibi ölçülendirmeye çalışmak doğru yaklaşım olmayabilir.

### Varsayılan Inline Elementler
|Element                |Kullanımı                          |
|-----------------------|-----------------------------------|
|`<span>`                 |Genel amaçlı satır içi kapsayıcı   |
|`<a>`                    |Bağlantı                           |
|`<strong>`               |Güçlü önem                         |
|`<em>`                   |Vurgu                              |
|`<code>`                 |Kod parçası                        |
|`<label>`                |Form alanı etiketi                 |

**Not:** Bu kurallar normal, değiştirilmemiş inline kutular için geçerlidir. Örneğin `<img>` gibi *replaced* elementlerin boyutlandırma davranışı farklıdır.

## display: inline-block
inline-block, inline ve block davranışlarının belirli özelliklerini birleştirir.
Bu element:
- Dışarıdan satır içi yerleşime katılır.
- İçeride normal blok akışı kullanır.
- Genişlik ve yükseklik değerlerini kabul eder.
- Padding, border ve margin değerleriyle ölçülendirilebilir.

Örneğin:
```
    <span class="badge">Yeni</span>
    <span class="badge">İndirimli</span>

    .badge {
        display: inline-block;
        padding: 6px 12px;
        border-radius: 8px;
        background-color: #f2f0eb;
    }
```
Bu iki rozet yeterli alan varsa yan yana görüntülenir.

### Inline ve Inline-Block Karşılaştırması
```
    .label {
        display:inline;
        width:100px;
    }
```

Normal inline kutuda width uygulanmaz.
```
    .label {
        display: inline-block;
        width: 100px;
    }
```

Inline-block kutuda ise width uygulanır.

### Nerelerde Kullanılır?
inline-block özellikle:
- Rozetlerde (badge),
- Etiketlerde (chip),
- Satır içinde ölçülendirilmesi gereken öğelerde,
- Küçük durum göstergelerinde kullanışlıdır.

Ancak birden fazla öğeyi kontrollü biçimde hizalamak ve aralarında boşluk oluşturmak istediğimizde Flexbox çoğu zaman daha uygun bir çözümdür.

### Inline-Block Arasındaki Boşluk Sorunu
Örneğin:
```
    <span class="badge">HTML</span>
    <span class="badge">CSS</span>
    <span class="badge">JavaScript</span>
```
Bu elementler arasında HTML kaynak kodundan gelen boşluk karakterleri bulunur. Inline-block elementler satır içi akışta yer aldığı için bu boşluklar ekranda görünür.

```
    [ HTML ]  [ CSS ]  [ JavaScript ]
        ↑        ↑
        Boşluklar
```
Bu boşluğun miktarı font ve yazı özelliklerine göre değişebilir. Boşluğu negatif margin ile düzeltmek yerine kontrollü bir yerleşim sistemi tercih edebiliriz.

Örneğin:
```
    .badge-list {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
    }
```
Burada boşluk gap ile açıkça tanımlanır.

### vertical-align: baseline Davranışı
Inline-block kutular varsayılan olarak satır içindeki baseline hizalamasına katılır. Bu nedenle farklı içeriklere veya yüksekliklere sahip inline-block elementler beklenmedik biçimde hizalanabilir.

Örneğin:
```
    .badge {
        display: inline-block;
        vertical-align: middle;
    }
```
kullanımı, satır içindeki dikey hizalamayı değiştirebilir.

**Not:** vertical-align, genel amaçlı bir dikey ortalama yöntemi değildir. Özellikle inline, inline-block ve tablo hücresi gibi belirli yerleşim bağlamlarında kullanılır.

## display: none ve Diğer Gizleme Yöntemleri
CSS'te bir elementi gizlemek için farklı yöntemler bulunur.

En yaygın olanları şu şekildedir:
```
    display: none;
    visibility: hidden;
    opacity: 0;
```
Ancak bu üç kullanım aynı davranışı oluşturmaz.

### 1. display: none
```
    .menu {
        display: none;
    }
```
Bu kullanım elementin normal kutularını oluşturmaz. Sonuç olarak:
- Element yerleşimde alan kaplamaz.
- Görüntülenmez.
- Normal şekilde tıklanamaz.
- Normal erişilebilirlik ağacından çıkarılır.
- Klavye odağına alınamaz.

Örneğin:
```
    <div class="box-one">Birinci</div>
    <div class="box-two">İkinci</div>

    .box-one {
        display: none;
    }
```
Bu durumda ikinci kutu, birinci kutu yerleşimde yokmuş gibi konumlanır.

**Önemli:** *display: none*, HTML elementini DOM'dan silmez. Element DOM'da kalır; yalnızca görüntüleme ve yerleşim davranışı değişir.

### 2. visibility: hidden
```
    .card {
        visibility: hidden;
    }
```
Bu kullanımda element görünmez olur ancak yerleşimde kapladığı alan korunur.
```
    ┌──────────────────┐
    │   Görünmez alan  │
    └──────────────────┘

    ┌──────────────────┐
    │  Sonraki element │
    └──────────────────┘
```
Element normalde tıklanamaz ve erişilebilirlik ağacından gizlenir. **visibility** kalıtılabilir bir özellik olduğundan çocuklarda görünürlüğün ayrıca ayarlanabildiği özel durumlar bulunur.

### 3. opacity: 0
```
    .card {
        opacity: 0;
    }
```
Bu kullanım elementin oluşturduğu görünümü tamamen saydamlaştırır. Ancak element:
- Yerleşimde alan kaplamaya devam eder.
- Normal koşullarda tıklanabilir.
- Klavyeyle odaklanabilir.
- Erişilebilirlik ağacında kalabilir.

Yani görünmez olması, etkileşiminin ortadan kalktığı anlamına gelmez. Bu durum yanlış kullanıldığında kullanıcı deneyimi ve erişilebilirlik sorunlarına neden olabilir.

### Gizleme Yöntemleri Karşılaştırması

|Özellik                |display: none          |visibility: hidden          |opacity:0              |
|-----------------------|-----------------------|---------------------------|-----------------------|
|Görünür mü?|Hayır|Hayır|Hayır|
|Yer kaplar mı?|Hayır|Evet|Evet|
|Normalde tıklanabilir mi?|Hayır|Hayır|Evet|
|Erişilebilirlik ağacında mı?|Hayır|Genellikle hayır|Genellikle evet|
|Görünürlük geçişi|Özel teknikler gerekir|Kesikli geçiş|Sayısal geçiş yapılabilir|

### Geçiş Animasyonu Farkı
opacity, sayısal bir değer olduğu için kolayca animasyon uygulanabilir.
```
    .card {
        opacity: 0;
        transition: opacity 300ms ease;
    }

    .card:hover {
        opacity: 1;
    }
```

**display** ise geleneksel olarak opacity gibi ara değerler arasında animasyon oluşturmaz. Modern CSS'te display için ayrık geçişler ve @starting-style gibi teknikler bulunmaktadır. Ancak bunların davranışı ve tarayıcı desteği dikkate alınmalıdır.

### HTML hidden Attribute
Html'de de gizleme amacıyla şöyle kullanabiliriz:
```
    <div hidden>
        Gizli İçerik
    </div>
```

Normal hidden durumunda tarayıcı, elementi varsayılan olarak görüntülemez. Ancak CSS ile görüntüleme davranışının değiştirilmesi ve `hidden="until-found"` gibi özel durumlar mümkündür. Bu nedenle HTML hidden attribute'unu yalnızca CSS'teki `display: none` ile tamamen aynı kavram olarak düşünmemeliyiz.

## flex, inline-flex, grid ve inline-grid
CSS'te display, yalnızca block veya inline davranışını kontrol etmez. Aynı zamanda elementin çocuklarının nasıl yerleştirileceğini de belirler.

Bu amaçla en yaygın kullanılan sistemler:
```
    Flexbox
    Grid
```
yerleşimleridir.

Bu bölümde yalnızca temel farklarını inceleyeceğiz.

### 1. display: flex
```
    <nav class="menu">
        <a href="#">Ana Sayfa</a>
        <a href="#">Ürünler</a>
        <a href="#">İletişim</a>
    </nav>

    .menu {
        display: flex;
        gap: 16px;
    }
```

Bu kullanımda çocuklar varsayılan olarak yatay ana eksen boyunca dizilir.
```
    ┌───────────────────────────────────────┐
    │ Ana Sayfa    Ürünler    İletişim      │
    └───────────────────────────────────────┘
```
flex container dışarıdan blok seviyeli davranış gösterir.

### 2. display: inline-flex
```
    .menu {
        display: inline-flex;
        gap: 16px;
    }
```

Burada çocuklar yine Flexbox kurallarına göre yerleşir. Ancak container'ın dış yerleşimi inline seviyelidir.

Yani temel fark aşağıdaki gibidir:
```
    flex
    ↓
    Dış: block
    İç: flex


    inline-flex
    ↓
    Dış: inline
    İç: flex
```

### 3. display: grid
```
    <div class="gallery">
        <div>1</div>
        <div>2</div>
        <div>3</div>
        <div>4</div>
    </div>

    .gallery {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: 16px;
    }
```
Bu kullanım iki sütunlu bir yerleşim oluşturur.
```
    ┌────────────┬────────────┐
    │     1      │     2      │
    ├────────────┼────────────┤
    │     3      │     4      │
    └────────────┴────────────┘
```

### 4. display: inline-grid
```
    .gallery {
        display: inline-grid;
    }
```
Grid iç yerleşimi korunurken container dışarıdan inline seviyeli davranır.
|Display            |Dış davranış           |İç yerleşim            |
|-------------------|-----------------------|-----------------------|
|flex               |Block                  |Flexbox                |
|inline-flex        |Inline                 |Flexbox                |
|grid               |Block                  |Grid                   |
|inline-grid        |Inline                 |Grid                   |

## Daha Az Bilinen Display Değerleri
Günlük kullanımda çoğunlukla block, inline, flex ve grid ile karşılaşırız. Ancak CSS'te başka display değerleri de bulunur.

### 1. display: list-item
Liste öğelerinin varsayılan davranışlarından biridir.

Örneğin:
```
    <ul>
        <li>HTML</li>
        <li>CSS</li>
        <li>JavaScript</li>
    </ul>
```
Normal görüntü:
```
    • HTML
    • CSS
    • JavaScript
```
list-item, bir liste öğesi için marker kutusu oluşturulmasını sağlar.

Bu marker genellikle madde imi veya numara olabilir. Marker'ın görünümü list-style gibi özelliklerden de etkilenir.
```
    li {
        display: list-item;
    }
```

### 2. display: flow-root
flow-root, yeni bir **Block Formatting Context (BFC)** oluşturur. BFC, blok kutuların belirli yerleşim kurallarına göre düzenlendiği bağımsız bir biçimlendirme bağlamıdır.

Başlangıçta bunu, bazı yerleşim davranışlarını kendi sınırları içinde tutan bir kapsayıcı olarak düşünebiliriz.

Örneğin:
```
    .container {
        display: flow-root;
    }
```

### Margin Collapse ile İlişkisi
"Block ve Margin Collapse" bölümünde gördüğümüz dikey margin birleşmesi, parent-child ilişkisinde de ortaya çıkabilir. `flow-root`, parent'a yeni bir BFC kazandırarak bu birleşmeyi engeller:
```
    .container {
        display: flow-root;
    }

    .container p {
        margin-top: 24px;
    }
```
`flow-root` olmadan `.container`'ın üst margin'i, içindeki `<p>`'nin `margin-top` değeriyle birleşebilirdi.

### Float ile İlişkisi
flow-root, içindeki float elementlerin kapsayıcı yüksekliğinin hesaplanmasında da kullanışlıdır.

.container {
    display: flow-root;
}

.image {
    float: left;
}

Bu kullanım float kaynaklı bazı yerleşim sorunlarını önlemeye yardımcı olur.

### 3. display: contents
contents, elementin kendi temel kutusunu kaldırır. Ancak çocuk elementlerin kutuları oluşturulmaya devam eder.

Örneğin:
```
    <div class="container">
        <div class="wrapper">
            <span>Birinci</span>
            <span>İkinci</span>
        </div>
    </div>

    .wrapper {
        display: contents;
    }
```

Bu durumda `.wrapper` kendi normal kutusunu oluşturmaz. Çocuklar, kutu yerleşimi açısından üst kapsayıcının doğrudan çocuklarıymış gibi davranabilir. Ancak HTML DOM yapısı değişmez.
```
    DOM
    container
    └── wrapper
        ├── span
        └── span


    Kutu Yerleşimi
    container
    ├── span
    └── span
```

### Dikkat Edilmesi Gerekenler
`display: contents:`
- Elementin kendi kutusunu ortadan kaldırır.
- Elementin background, border ve padding gibi kutusuna bağlı görsel özelliklerini beklenmedik hâle getirebilir.
- Bazı elementlerde ve tarayıcı/yardımcı teknoloji kombinasyonlarında erişilebilirlik sorunlarına neden olabilir.
- Özellikle semantik anlamı veya etkileşim davranışı önemli olan elementlerde dikkatli kullanılmalıdır.

### 4. Tablo Display Değerleri
CSS, tablo yerleşimine ilişkin display değerlerini de destekler.

Örneğin:
```
    .table {
        display: table;
    }

    .row {
        display: table-row;
    }

    .cell {
        display: table-cell;
    }
```
Bu değerler tablo benzeri yerleşim davranışları oluşturur. Ancak veri tabloları için doğru HTML elementleri olan:
```
    <table>
        <tr>
            <td>Veri</td>
        </tr>
    </table>
```
kullanılmalıdır.

Modern sayfa ve arayüz yerleşimlerinde Flexbox ve Grid çoğunlukla daha uygun seçeneklerdir.

**Önemli:** Grid, HTML tablolarının anlamsal karşılığı değildir. Gerçek tablo verileri için semantik `<table>` yapısı önemini korur.

## Varsayılan Display Değerleri ve Resimler
HTML elementlerinin varsayılan görüntüleme davranışları büyük ölçüde tarayıcının kendi stil dosyasından, yani **User Agent Stylesheet** üzerinden gelir.

Örneğin:
```
    <div>Block</div>
    <span>Inline</span>
```
elementleri için ayrıca display tanımlamasak bile tarayıcı bunları farklı şekilde yerleştirir.

Bu davranışlar gerektiğinde CSS ile değiştirilebilir.

### `<img>` Neden Varsayılan Olarak Inline'dır?
`<img>` elementi varsayılan olarak inline seviyeli, replaced bir elementtir. Bu nedenle metin satırının baseline hizalamasına katılır.

Örneğin:
```
    <div class="image-container">
        <img src="product.jpg" alt="Ürün görseli">
    </div>
```

Bazı durumlarda resmin altında küçük bir boşluk görünür.
```
    ┌───────────────────────┐
    │                       │
    │        RESİM          │
    │                       │
    ├───────────────────────┤
    │  Küçük alt boşluk     │
    └───────────────────────┘
```

Bu boşluk çoğunlukla margin'den kaynaklanmaz. Sebebi, satır kutusunun baseline altında harflerin aşağı uzanan bölümleri için de alan ayırabilmesidir. Örneğin g, p, y gibi harflerin alt kısımları bu bölgeye uzanabilir.

### Çözüm 1 - display: block
```
    img {
        display: block;
    }
```
Resim artık normal inline satır akışında yer almaz. Bu kullanım birçok görsel yerleşiminde alttaki baseline boşluğunu ortadan kaldırır.

### Çözüm 2 — vertical-align
```
    img {
        vertical-align: middle;
    }
```
Resmin satır içindeki hizalaması değiştirilir. Bu da baseline kaynaklı boşluk davranışını değiştirebilir. Ancak her durumda kalan bütün satır kutusu boşluğunu sıfırlayacağı garanti değildir.

### Responsive Görsel Örneği
```
    img {
        display: block;
        max-width: 100%;
        height: auto;
    }
```

Burada:
- `display: block` → resmi blok seviyeli yerleşime geçirir.
- `max-width: 100%` → resmin kendi doğal genişliği daha büyükse kapsayıcı genişliğini aşmasını önlemeye yardımcı olur.
- `height: auto` → görselin doğal en-boy oranını korur.

Bu üç özellik modern arayüzlerde sık kullanılan bir başlangıç yaklaşımıdır.

## Display Görünümü Değiştirir, HTML Anlamını Değil
CSS'in en önemli ilkelerinden biri, **görünüm ile anlamsal yapının birbirinden farklı olmasıdır.**

Örneğin: `<a href="/urunler">Ürünleri Gör</a>` → Bu element bir bağlantıdır.

CSS ile:
```
    a {
        display: block;
    }
```
yazarsak bağlantı blok seviyeli kutu gibi yerleşir.

Ancak hâlâ:
- Bir bağlantıdır.
- href üzerinden gezinme işlevini korur.
- Normal koşullarda klavyeyle odaklanabilir.
- Ekran okuyucular tarafından bağlantı olarak tanımlanır.

Yani:
```
    HTML → Anlam ve işlev
    CSS Display → Görünüm ve yerleşim
```
ilişkisi vardır.

Başka bir örnek: `<button type="button">Kaydet</button>`

Bu elementin görünümünü değiştirmek için şu şekilde kullanabiliriz:
```
    button {
        display: inline-flex;
        align-items: center;
        justify-content: center;
    }
```

Buton, CSS ile farklı yerleşim davranışları kazansa bile HTML'deki buton işlevini korur.

**Temel kural:** Görünüm için yanlış HTML elementi seçmek yerine, doğru semantik elementi kullanıp görünümü CSS ile düzenlemeliyiz.

## Hepsini Bir Arada Görelim: Navigasyon Menüsü
Aynı basit örnek üzerinden — bir menüyü yan yana dizmek — şimdiye kadar gördüğümüz display değerlerini karşılaştıralım.

HTML hep aynı kalacak:
```
    <ul class="menu">
        <li><a href="#">Ana Sayfa</a></li>
        <li><a href="#">Ürünler</a></li>
        <li><a href="#">İletişim</a></li>
    </ul>
```
`<li>` varsayılan olarak **block** olduğu için CSS yazmadan her biri alt alta, madde imli şekilde görünür. Şimdi `<li>`'lere sırayla farklı display değerleri verelim.

**`display: inline` verirsek:**
```
    .menu li {
        display: inline;
    }
```
Öğeler yan yana gelir ama madde imleri bozulur ve aradaki boşluğu kontrol edemeyiz.

**`display: inline-block` verirsek:**
```
    .menu li {
        display: inline-block;
        margin-right: 16px;
    }
```
Yan yana gelirler ve artık `width`/`padding` gibi değerler de verebiliriz. Ama boşluğu `margin` ile elle ayarlamak gerekir.

**`display: flex` verirsek (bu sefer `<li>`'lere değil, `<ul>`'ye):**
```
    .menu {
        display: flex;
        gap: 16px;
        list-style: none;
    }
```
Çocuklar otomatik olarak yan yana dizilir, boşluğu tek satırlık `gap` ile ayarlarız, `list-style: none` ile de madde imini kaldırırız. En az kod, en az sorun.

**Özetle:**
```
    inline        → yan yana gelir ama kontrolsüz
    inline-block   → yan yana gelir, elle boşluk ayarlanır
    flex           → yan yana gelir, gap ile temiz boşluk
```
Bu yüzden bugün menü, kart grubu gibi yan yana dizilmesi gereken yapılarda genellikle Flexbox tercih edilir. Ayrıntılarını ileride Flexbox konusunda göreceğiz.

## Sık Yapılan Hatalar
### 1. Inline Elemente width ve height Vermek
```
    span {
        width: 200px;
        height: 50px;
    }
```
Normal inline kutuda bu değerler beklenen boyutlandırmayı sağlamaz. Ölçülendirilebilir bir satır içi kutu için:
```
    span {
        display: inline-block;
        width: 200px;
        height: 50px;
    }
```
kullanılabilir.

### 2. Resim Altındaki Boşluğu Margin Sanmak
`<img src="image.jpg" alt="Örnek görsel">`

Resmin altında görülen küçük boşluk baseline davranışından kaynaklanabilir.
```
    img {
        display: block;
    }
```
çoğu durumda uygun çözümdür.

### 3. display: none ile Normal Opacity Animasyonu Beklemek
```
    .menu {
        display: none;
        transition: opacity 300ms;
    }
```
Bu kod tek başına açılıp kapanan bir görünürlük animasyonu oluşturmaz. Çünkü **display: none** durumunda elementin kutusu oluşturulmaz.

Animasyon ihtiyacına göre **opacity, visibility,** modern ayrık geçiş teknikleri ve etkileşim yönetimi birlikte değerlendirilmelidir.

### 4. Inline-Block Boşluklarını Negatif Margin ile Düzeltmek
```
    .badge {
        display: inline-block;
        margin-right: -4px;
    }
```
Bu tür sabit düzeltmeler font ve yerleşim değişikliklerinde sorun çıkarabilir.

Bir grup öğeyi düzenlemek için:
```
    .badge-list {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
    }
```
daha öngörülebilir olabilir.

### 5. Ekran Okuyucunun Okuması Gereken Metni `display: none` ile Gizlemek
Bazı içerikleri görsel olarak gizlemek, ancak yardımcı teknolojilere sunmaya devam etmek isteyebiliriz. Örneğin yalnızca ikon gösterilen bir buton:
```
    <button type="button">
        <span class="visually-hidden">Menüyü aç</span>
        <span aria-hidden="true">☰</span>
    </button>
```
Eğer:
```
    .visually-hidden {
        display: none;
    }
```
kullanırsak metin erişilebilirlik ağacından da çıkar.

Bunun yerine görsel olarak gizleyen bir yardımcı sınıf kullanılabilir:
```
    .visually-hidden {
        position: absolute;
        width: 1px;
        height: 1px;
        padding: 0;
        margin: -1px;
        overflow: hidden;
        clip: rect(0, 0, 0, 0);
        white-space: nowrap;
        border: 0;
    }
```
Bu teknik metni görsel olarak gizlerken erişilebilirlik ağacında tutmayı amaçlar. Buradaki örnekte butonun erişilebilir adı **Menüyü aç** olur.

### 6. `display: contents` Kullanırken Erişilebilirliği Göz Ardı Etmek
```
    button {
        display: contents;
    }
```
gibi bir kullanım, elementin kutusunu kaldırdığı için beklenmedik davranışlara ve erişilebilirlik sorunlarına neden olabilir.

Özellikle etkileşimli ve semantik elementlerde `display: contents` kullanmadan önce gerçekten gerekli olup olmadığını değerlendirmeliyiz.

### 7. `display: block` ile Her Şeyin Alt Alta Geleceğini Varsaymak
`display: block`, normal blok akışındaki temel davranışı belirler.

Ancak bir element:
- Flex item,
- Grid item,
- Mutlak konumlandırılmış element olduğunda çevresindeki yerleşim kuralları değişebilir.

Bu nedenle display davranışını her zaman elementin bulunduğu yerleşim bağlamıyla birlikte düşünmeliyiz.

## Kısaca Özet
CSS display, bir elementin nasıl bir kutu oluşturduğunu ve çocuklarının hangi yerleşim sistemiyle düzenleneceğini belirler.

### Temel Display Değerleri
|Değer          |Normal akışta kendi satırı |width/height       |Dikey margin       |Kullanım           |
|---------------|---------------------------|-------------------|-------------------|-------------------|
|block|Evet|Uygulanır|Etkilidir, birleşebilir|Bölümler, kartlar|
|inline|Hayır|Normal inline kutuda uygulanmaz|Yerleşimi etkilemez|Metin içi vurgular|
|inline-block|Hayır|Uygulanır|Etkilidir, birleşmez|Rozetler, etiketler|
|none|Kutu oluşturmaz|-     |-      |Gizleme|
|flex|Blok seviyeli|Uygulanır|Flex item'larda birleşmez|Esnek yerleşim|
|grid|Blok seviyeli|Uygulanır|Grid item'larda birleşmez|Izgara yerleşimi|

### Display Mantığı
```
    CSS DISPLAY
    │
    ├── block
    │   └── Normal blok akışı
    │
    ├── inline
    │   └── Metin içi akış
    │
    ├── inline-block
    │   └── Satır içi, ölçülendirilebilir kutu
    │
    ├── none
    │   └── Kutu oluşturmaz
    │
    ├── flex / inline-flex
    │   └── Flexbox yerleşimi
    │
    ├── grid / inline-grid
    │   └── Grid yerleşimi
    │
    ├── flow-root
    │   └── Yeni BFC oluşturur
    │
    └── contents
        └── Elementin kendi kutusunu kaldırır
```

### Gizleme Yöntemleri
```
    display: none
    ↓
    Görünmez
    Yer kaplamaz
    Normal erişilebilirlik ağacından çıkar


    visibility: hidden
    ↓
    Görünmez
    Yer kaplar
    Normalde etkileşime kapalıdır


    opacity: 0
    ↓
    Tamamen saydam
    Yer kaplar
    Etkileşim devam edebilir
```

### Akılda Kalması Gerekenler
- `block` → Normal blok akışında kendi satırını oluşturur.
- `inline` → Metnin akışı içinde yer alır.
- `inline-block` → Satır içinde kalırken kutu boyutlarıyla çalışmayı sağlar.
- `none` → Elementin kutularını oluşturmaz.
- `flex` → Çocukları esnek bir yerleşim sisteminde düzenler.
- `grid` → Çocukları satır ve sütun temelli bir yerleşim sisteminde düzenler.
- `flow-root` → Yeni bir blok biçimlendirme bağlamı oluşturur.
- `contents` → Elementin kendi kutusunu kaldırır, çocuk kutularının yerleşimini etkiler.

Bu bölümde öğrenmemiz gereken en önemli nokta:
`Box Model, kutunun ölçülerini ve boşluklarını; Display ise kutunun yerleşim davranışını ve çocuklarının nasıl düzenleneceğini anlamamızı sağlar.`

Bu iki konu birlikte CSS yerleşim sisteminin temelini oluşturur.