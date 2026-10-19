# CSS Flexbox (Esnek Kutu Yerleşimi)
CSS Flexbox, bir kapsayıcı içerisindeki elementlerin yerleşimini ve hizalanmasını yönetmek için kullanılan **tek boyutlu (one-dimensional) bir layout sistemidir.** 

Tek boyutlu olması, Flexbox'ın elementleri temel olarak bir ana eksen (satır veya sütun) üzerinde düzenlemesi anlamına gelir.

Flexbox sayesinde:
- Elementleri yatay veya dikey hizalayabiliriz.
- Elementler arasındaki boşlukları kontrol edebiliriz.
- İçeriği yatay ve dikey olarak ortalayabiliriz.
- Elementlerin büyüme ve küçülme davranışlarını yönetebiliriz.
- Farklı ekran genişliklerine uyum sağlayan düzenler oluşturabiliriz. 
- Navbar, kart listesi, buton grubu ve form alanları gibi bileşenleri kolayca tasarlayabiliriz.

## Flexbox Nedir ve Neden Kullanılır?
Normal belge akışında blok elementler genellikle alt alta yerleşir.
```
    <div class="container">
        <div class="box">1</div>
        <div class="box">2</div>
        <div class="box">3</div>
    </div>
```

Varsayılan görünüm:
``` 
    ┌─────────────────────────┐
    │            1            │
    ├─────────────────────────┤
    │            2            │
    ├─────────────────────────┤
    │            3            │
    └─────────────────────────┘
```

Flexbox kullanarak bu elementleri yan yana yerleştirebiliriz.
```
    .container {
        display: flex;
    }
```

Sonuç:
```
    ┌────────┬────────┬────────┐
    │   1    │   2    │   3    │
    └────────┴────────┴────────┘
```

Flexbox'ın önemli avantajı, elementlerin yalnızca yan yana yerleşmesini sağlaması değildir.

Aynı zamanda elementlerin kullanılabilir alanı nasıl paylaşacağını ve farklı boyutlara nasıl uyum sağlayacağını da yönetir.

### Flexbox Ne Zaman Kullanılır?
Flexbox özellikle aşağıdaki arayüzlerde kullanışlıdır:
- Navbar ve menüler
- Buton grupları
- Form alanları
- İkon ve metin hizalaması
- Kart içeriği düzenleri
- Header ve footer bileşenleri
- Yatay veya dikey merkezleme
- Responsive bileşen yerleşimleri

**Önemli:** Flexbox genel olarak tek boyutlu düzenler için uygundur. Satır ve sütunların birlikte kontrol edilmesi gereken iki boyutlu düzenlerde CSS Grid daha uygun olabilir.

## Flex Container ve Flex Item
Flexbox sisteminde iki temel kavram bulunur:
1. Flex Container: *display: flex* veya *display: inline-flex* uygulanan kapsayıcıdır.
2. Flex Item: Flex container'ın doğrudan çocuklarıdır.

Örnek:
```
    <div class="container">
        <div class="item">1</div>
        <div class="item">2</div>
        <div class="item">3</div>
    </div>

    .container {
        display: flex;
    }
```
Yapı:
```
    FLEX CONTAINER
    ┌─────────────────────────────────┐
    │                                 │
    │ ┌────────┐ ┌────────┐ ┌────────┐│
    │ │ Item 1 │ │ Item 2 │ │ Item 3 ││
    │ └────────┘ └────────┘ └────────┘│
    │                                 │
    └─────────────────────────────────┘
```

### Flex Container Özellikleri
Kapsayıcı üzerinde kullanılan temel özellikler:
``` 
    .container {
        display: flex;
        flex-direction: row;
        flex-wrap: nowrap;
        justify-content: flex-start;
        align-items: stretch;
        align-content: normal;
        gap: 16px;
    }
```

### Flex Item Özellikleri
Doğrudan çocuk elementlerde kullanılan özellikler:
```
    .item {
        flex-grow: 0;
        flex-shrink: 1;
        flex-basis: auto;

        align-self: auto;
        order: 0;
    }
```

Flex item'lar üzerinde ayrıca flex shorthand property'si kullanılabilir. 

**Dikkat:** Flex container içerisindeki bir elementin torunları otomatik olarak aynı container'ın flex item'ı olmaz.
```
    <div class="container">
        <div class="item">
            <span>Metin</span>
        </div>
    </div>
```
Burada .item bir flex item'dır. Ancak span, .container açısından doğrudan flex item değildir.

## Main Axis ve Cross Axis
Flexbox'ı doğru kullanabilmek için iki ekseni anlamamız gerekir.
1. Main Axis (Ana Eksen) : flex item'larının temel yerleşim yönünü belirler.
2. Cross Axis (Çapraz Eksen) : main axis'e dik olan eksendir.

### flex-direction: row
Varsayılan yön **row** değeridir.

```
    .container {
        display: flex;
        flex-direction: row;
    }
```

```
                MAIN AXIS →
    ┌─────────────────────────────┐
    │ ┌─────┐ ┌─────┐ ┌─────┐     │
    │ │  1  │ │  2  │ │  3  │     │
    │ └─────┘ └─────┘ └─────┘     │
    │                             │
    └─────────────────────────────┘
                ↓
            CROSS AXIS
```

Bu durumda:
- Main Axis yataydır.
- Cross Axis dikeydir.

### flex-direction: column
```
    .container {
        display: flex;
        flex-direction: column;
    }
```

```
    ┌───────────────────────┐
    │ ┌───────────────┐     │
    │ │       1       │     │
    │ └───────────────┘     │
    │          ↓            │
    │ ┌───────────────┐     │
    │ │       2       │     │
    │ └───────────────┘     │
    │          ↓            │
    │ ┌───────────────┐     │
    │ │       3       │     │
    │ └───────────────┘     │
    └───────────────────────┘

    MAIN AXIS ↓
    CROSS AXIS →
```
Bu durumda:
- Main axis dikeydir.
- Cross axis yataydır.

### Neden Önemlidir?
Çünkü **justify-content** ve **align-items** gibi özellikler doğrudan yatay veya dikey eksene bağlı değildir.

Bu özellikler main axis ve cross axis üzerinden çalışır.

|Property               |Kontrol ettiği eksen           |
|-----------------------|-------------------------------|
|justify-content        |Main axis                      |
|align-items            |Cross axis                     |
|align-self             |Cross axis                     |
|align-content          |Birden fazla flex satırının cross axis üzerindeki dağılımı|

**Temel kural:** flex-direction değiştiğinde eksenlerin yönü de değişir.

## display: flex ve display: inline-flex
Flexbox oluşturmanın iki temel yolu vardır.
```
    .container {
        display: flex;
    }
```
veya:
```
    .container {
        display: inline-flex;
    }
```

### display: flex
Element, dış yerleşimde blok seviyesinde bir flex container oluşturur.
```
    .container {
        display: flex;
    }
```

Genellikle kullanılabilir yatay alanı dolduran kapsayıcılarda tercih edilir.

### display: inline-flex
Element, dış yerleşimde inline seviyesinde bir flex container oluşturur.
```
    .container {
        display: inline-flex;
    }
```

Örneğin ikon ve metinden oluşan küçük bir etiket için kullanılabilir.
```
    <span class="tag">
        <span>✓</span>
        <span>Onaylandı</span>
    </span>

    .tag {
        display: inline-flex;
        align-items: center;
        gap: 6px;
    }
```

|Özellik                |flex                   |inline-flex            |
|-----------------------|-----------------------|-----------------------|
|İçeride Flexbox kullanır mı?|Evet  |Evet   |
|Dış yerleşim davranışı |Block-level    |Inline-level   |
|Yaygın kullanım    |Header, kart listesi, layout   |Etiket, küçük bileşen, ikonlu metin    |

Her iki kullanımda da doğrudan çocuklar *flex-item* olur.

## flex-direction - Yerleşim Yönü
flex-direction, flex item'ların main axis üzerinde hangi yönde sıralanacağını belirler. Dört temel değeri vardır:
- flex-direction: row;
- flex-direction: row-reverse;
- flex-direction: column;
- flex-direction: column-reverse;

### row
Varsayılan değerdir.
```
    .container {
        display: flex;
        flex-direction: row;
    }

    [ 1 ] [ 2 ] [ 3 ]
```

Öğeler inline başlangıç yönünden inline bitiş yönüne doğru sıralanır. Soldan sağa yazılan Türkçe içeriklerde bu genellikle soldan sağadır.

### row-reverse
```
    .container {
        display: flex;
        flex-direction: row-reverse;
    }
```

Soldan sağa yazılan bir sayfada görsel sıra: `[ 3 ] [ 2 ] [ 1 ]`

### column
```
    .container {
        display: flex;
        flex-direction: column;
    }

    [ 1 ]
    [ 2 ]
    [ 3 ]
```

### column-reverse
```
    .container {
        display: flex;
        flex-direction: column-reverse;
    }

    [ 3 ]
    [ 2 ]
    [ 1 ]
```

**Erişilebilirlik notu:** row-reverse ve column-reverse görsel sıralamayı değiştirir. DOM sırasını veya klavye odak sırasını değiştirmez. Bu nedenle anlamlı içerik sıralamasını yalnızca CSS ile tersine çevirmemeliyiz.

## justify-content - Ana Eksen Üzerinde Hizalama
justify-content, flex item'ların main axis üzerindeki boş alanı nasıl paylaşacağını belirler. En sık kullanılan değerler:
- justify-content: flex-start;
- justify-content: flex-end;
- justify-content: center;
- justify-content: space-between;
- justify-content: space-around;
- justify-content: space-evenly;

Aşağıdaki örneklerde flex-direction: row kullanıldığını varsayalım.
```
    .container {
        display: flex;
        justify-content: flex-start;
    }

    ┌──────────────────────────────┐
    │ [1] [2] [3]                  │
    └──────────────────────────────┘
```
Elementleri main axis başlangıcında toplar.

### flex-end
```
    .container {
        display: flex;
        justify-content: flex-end;
    }

    ┌──────────────────────────────┐
    │                  [1] [2] [3] │
    └──────────────────────────────┘
```
Elementleri main axis sonunda toplar.

### center
```
    .container {
        display: flex;
        justify-content: center;
    }

    ┌──────────────────────────────┐
    │         [1] [2] [3]          │
    └──────────────────────────────┘
```
Elementleri ana eksende ortalar.

### space-between
```
    .container {
        display: flex;
        justify-content: space-between;
    }

    ┌──────────────────────────────┐
    │ [1]          [2]         [3] │
    └──────────────────────────────┘
```
İlk item başlangıca, son item sona yerleşir. Aradaki boşluk eşit dağılır.

### space-around
```
    .container {
        display: flex;
        justify-content: space-around;
    }

    ┌──────────────────────────────┐
    │   [1]      [2]      [3]      │
    └──────────────────────────────┘
```
Her item'ın iki yanına eşit paylı boşluk dağıtılır. Bu nedenle dış kenarlardaki boşluk, item'lar arasındaki toplam boşluğun yarısı olur.

### space-evenly
```
    .container {
        display: flex;
        justify-content: space-evenly;
    }

    ┌──────────────────────────────┐
    │    [1]    [2]    [3]         │
    └──────────────────────────────┘
```
Item'lar arasındaki ve kapsayıcının dış kenarlarındaki boşluklar eşit dağıtılır.

### justify-content Ne Zaman Etkisiz Görünür?
Örneğin:
```
    .container {
        display: flex;
        justify-content: space-between;
    }

    .item {
        flex: 1;
    }
```

Item'lar kullanılabilir alanı tamamen dolduruyorsa justify-content tarafından dağıtılacak pozitif boş alan kalmayabilir.

Bu durumda space-between beklenen görünür etkiyi oluşturmaz.

## align-items - Çapraz Eksen Üzerinde Hizalama
align-items, flex item'ların cross axis üzerindeki hizalanmasını belirler.

Yaygın değerleri:
- align-items: stretch;
- align-items: flex-start;
- align-items: flex-end;
- align-items: center;
- align-items: baseline;

Örnek kapsayıcı:
```
    .container {
        display: flex;
        height: 180px;
        border: 1px solid #dddddd;
    }
```

### stretch
Varsayılan değerdir.
```
    .container {
        align-items: stretch;
    }
```

Uygun boyutlandırma koşullarında item'lar çapraz eksende kullanılabilir alanı dolduracak şekilde uzar.

**Not:** Item'a cross axis üzerinde belirli bir boyut verilmişse stretch davranışı beklenen şekilde gerçekleşmeyebilir.

### flex-start
```
    .container {
        align-items: flex-start;
    }
```
Item'ları cross axis başlangıcında hizalar.

### flex-end
```
    .container {
        align-items: flex-end;
    }
```
Item'ları cross axis sonunda hizalar.

### center
```
    .container {
        align-items: center;
    }
```
Item'ları cross axis üzerinde ortalar.

### baseline
```
    .container {
        align-items: baseline;
    }
```
Item'ların metin taban çizgilerini hizalamaya çalışır.

Özellikle farklı yazı boyutları içeren elementlerde kullanışlıdır.
```
    <div class="price">
        <span class="amount">1.250</span>
        <span class="currency">TL</span>
    </div>

    .price {
        display: flex;
        align-items: baseline;
        gap: 4px;
    }

    .amount {
        font-size: 32px;
    }

    .currency {
        font-size: 14px;
    }
```

### justify-content ve align-items Farkı
|Property       |Eksen          |Temel görevi           |
|---------------|---------------|-----------------------|
|justify-content|Main axis      |Boş alanı dağıtmak ve item grubunu hizalamak|
|align-items    |Cross axis     |Item'ları çapraz eksende hizalamak|

Bu iki özellik Flexbox'ın temelini oluşturur.

## Yatay ve Dikey Ortalama
Flexbox'ın en sık kullanılan özelliklerinden biri, bir elementi hem yatay hem dikey ortalayabilmesidir.

Örneğin:
```
    <div class="container">
        <div class="box">Merhaba</div>
    </div>

    .container {
        display: flex;
        justify-content: center;
        align-items: center;

        min-height: 300px;
    }
```

Sonuç:
```
    ┌───────────────────────────────┐
    │                               │
    │                               │
    │         ┌───────────┐         │
    │         │  Merhaba  │         │
    │         └───────────┘         │
    │                               │
    │                               │
    └───────────────────────────────┘
```

Burada:
- justify-content: center main axis üzerinde ortalar
- align-items: center cross axis üzerinde ortalar

İki eksende ortalama birlikte sağlanır.

### margin: auto Alternatifi
Tek bir flex item için:
```
    .container {
        display: flex;
        min-height: 300px;
    }

    .box {
        margin: auto;
    }
```
Bu da uygun koşullarda elementi iki eksende ortalayabilir.

## gap - Elementler Arasındaki Boşluk
gap, flex item'lar arasında boşluk oluşturur.
```
    .container {
        display: flex;
        gap: 16px;
    }
```

Bu kullanımda komşu item'lar arasında 16px boşluk bulunur.

### gap ve margin Farkı
```
    .item {
        margin-right: 16px;
    }
```
Bu kullanım her item'ın sağında boşluk oluşturabilir. Ancak son item'ın sağında da gereksiz boşluk kalabilir.

Flexbox'ta:
```
    .container {
        display: flex;
        gap: 16px;
    }
```
kullanımı çoğu durumda daha anlaşılırdır. Çünkü boşluk doğrudan item'lar arasında oluşturulur.

### row-gap ve column-gap
```
    .container {
        display: flex;
        row-gap: 20px;
        column-gap: 12px;
    }
```
row-gap, flex satırları arasındaki boşluğu; column-gap ise sütun yönündeki boşluğu kontrol eder.

Kısaltılmış kullanım:
```
    .container {
        gap: 20px 12px;
    }
```

İlk değer row-gap, ikinci değer column-gap içindir.

**Önemli:** gap item'lar arasındaki sabit boşluğu yönetir. justify-content ise kullanılabilir fazla alanın dağıtımını yönetir.

## flex-wrap - Alt Satıra Geçme
Flexbox varsayılan olarak item'ları tek satırda tutmaya çalışır.
```
    .container {
        display: flex;
        flex-wrap: nowrap;
    }
```

Ancak item'ların toplam genişliği kapsayıcıyı aştığında küçülme veya taşma gibi davranışlar görülebilir. Bunu yönetmek için flex-wrap kullanılır.

### nowrap
```
    .container {
        flex-wrap: nowrap;
    }
```
Varsayılan değerdir. Item'lar tek satırda tutulur.

### wrap
```
    .container {
        flex-wrap: wrap;
    }
```
Gerekli olduğunda item'ların yeni flex satırlarına geçmesine izin verir.
```
    ┌────────────────────────────┐
    │ [1]   [2]   [3]            │
    │                            │
    │ [4]   [5]                  │
    └────────────────────────────┘
```

### wrap-reverse
```
    .container {
        flex-wrap: wrap-reverse;
    }
```
Flex satırlarının cross axis üzerindeki dizilme yönünü tersine çevirir.

## Pratik Örnek - Responsive Kart Listesi
HTML:
```
    <div class="cards">
        <article class="card">Kart 1</article>
        <article class="card">Kart 2</article>
        <article class="card">Kart 3</article>
        <article class="card">Kart 4</article>
    </div>
```

CSS:
```
    .cards {
        display: flex;
        flex-wrap: wrap;
        gap: 16px;
    }

    .card {
        flex: 1 1 220px;
        min-width: 0;
        padding: 20px;
        border: 1px solid #dddddd;
    }
```

Burada kartlar kullanılabilir alana göre büyüyebilir, küçülebilir ve yeni satıra geçebilir. Ancak *flex-wrap* tek başına bütün responsive ihtiyaçları çözmez. Bazı tasarımlarda media query veya Grid daha uygun olabilir.

## align-content - Flex Satırlarını Hizalama
align-content, birden fazla flex satırı oluştuğunda bu satırların cross axis üzerindeki dağılımını kontrol eder.

Örneğin:
```
    .container {
        display: flex;
        flex-wrap: wrap;

        height: 400px;
        align-content: space-between;
    }
```

Bu durumda birden fazla flex satırı varsa satırlar arasında kullanılabilir çapraz eksen boşluğu dağıtılır.

Yaygın değerler:
```
    align-content: flex-start;
    align-content: flex-end;
    align-content: center;
    align-content: space-between;
    align-content: space-around;
    align-content: space-evenly;
    align-content: stretch;
```

### align-items ve align-content Farkı
|Property               |Etkisi                                     |
|-----------------------|-------------------------------------------|
|align-items            |Flex item'ların kendi satırları içerisindeki çapraz eksen hizalaması |
|align-content          |Flex satırlarının kapsayıcı içerisindeki çapraz eksen dağılımı          |

**Önemli:** Tek satırlı bir flex container'da align-content genellikle görünür bir etki oluşturmaz. Bu özelliğin anlamlı olması için birden fazla flex satırı ve dağıtılabilecek alan bulunmalıdır.

## flex-grow - Kullanılabilir Alanı Büyüyerek Paylaşma
**flex-grow,** flex item'ın main axis üzerindeki pozitif boş alanı diğer item'larla hangi oranda paylaşacağını belirler.

Varsayılan değer:
```
    .item {
        flex-grow: 0;
    }
```

Bu durumda item yalnızca flex-grow nedeniyle büyümez.

Örnek:
```
    <div class="container">
        <div class="item first">1</div>
        <div class="item second">2</div>
        <div class="item third">3</div>
    </div>
```

```
    .container {
        display: flex;
        width: 600px;
    }

    .item {
        flex-basis: 100px;
        flex-grow: 1;
    }
```

Üç item da aynı büyüme oranına sahiptir. Her biri başlangıç boyutundan sonra kalan pozitif boş alanı eşit oranda paylaşır.

### Farklı Grow Değerleri
```
    .first {
        flex-grow: 1;
    }

    .second {
        flex-grow: 2;
    }

    .third {
        flex-grow: 1;
    }
```

Bu durumda uygun koşullarda kalan pozitif boş alan:
- Birinci item'a 1 pay,
- İkinci item'a 2 pay,
- Üçüncü item'a 1 pay olarak dağıtılır.

**Önemli:** flex-grow: 2; elementin toplam genişliğinin diğer elementin kesinlikle iki katı olacağı anlamına gelmez. Paylaştırılan şey, başlangıç boyutları hesaba katıldıktan sonra kalan pozitif alandır.

## flex-shrink - Alan Daraldığında Küçülme
flex-shrink, kapsayıcıda yeterli alan olmadığında flex item'ların ne ölçüde küçülebileceğini belirler.

Varsayılan değer:
```
    .item {
        flex-shrink: 1;
    }
```
Bu nedenle flex item'lar, kapsayıcı daraldığında çoğu durumda küçülmeye çalışır.

### Küçülmeyi Engelleme
```
    .logo {
        flex-shrink: 0;
    }
```
Bu kullanım, logo gibi küçülmesini istemediğimiz elementlerde yararlı olabilir.

Örneğin:
```
    <header class="header">
        <div class="logo">LOGO</div>
        <nav class="navigation">Menü bağlantıları</nav>
    </header>
```

```
    .header {
        display: flex;
        align-items: center;
        gap: 20px;
    }

    .logo {
        flex-shrink: 0;
    }
```
Logo küçülmeye zorlanmaz.

Ancak yeterli alan yoksa diğer elementler taşabilir. Bu nedenle responsive davranışı ayrıca planlamak gerekir.

### Shrink Oranları Nasıl Hesaplanır?
flex-shrink değerleri doğrudan toplam genişlik oranı değildir. Küçülme hesaplamasında item'ların flex base size değerleri de dikkate alınır. Ayrıca *min-width* ve *max-width* gibi sınırlar sonucu etkileyebilir.

## flex-basis - Başlangıç Boyutu
flex-basis, flex item'ın main axis üzerindeki başlangıç boyutunu belirler.

Örneğin:
```
    .item {
        flex-basis: 200px;
    }
```

### flex-basis ve width Farkı
```
    .item {
        width: 200px;
    }
```
Bu kullanım elementin genişliğini belirler.
```
    .item {
        flex-basis: 200px;
    }
```
Bu kullanım ise Flexbox'ın ana eksen üzerindeki başlangıç boyutunu belirler.

**flex-direction: row** kullanıldığında ana eksen çoğunlukla yataydır. Dolayısıyla flex-basis genişlikle ilişkilidir.

**flex-direction: column** kullanıldığında ana eksen dikeydir. Dolayısıyla flex-basis yükseklikle ilişkilidir.

### auto Değeri
```
    .item {
        flex-basis: auto;
    }
```
Bu durumda ilgili ana eksen boyutu için width veya height gibi özellikler dikkate alınabilir. Bunlar da otomatikse içerik boyutlandırması devreye girer.

### 0 Değeri
```
    .item {
        flex-basis: 0;
    }
```

Bu değer başlangıç boyutu hesabını sıfırdan başlatabilir. Ancak minimum boyut kısıtları ve içerik yine sonucu etkileyebilir.

## flex Shorthand Property
flex, üç özelliği tek satırda yazmamızı sağlar: `flex: grow shrink basis;`

Örneğin:
```
    .item {
        flex: 1 1 200px;
    }
```

Açılımı:
```
    .item {
        flex-grow: 1;
        flex-shrink: 1;
        flex-basis: 200px;
    }
```

### Sık Kullanılan Değerler
|Kullanım                   |Anlamı                     |
|---------------------------|---------------------------|
|flex: initial              |0 1 auto                   |
|flex: auto                 |1 1 auto                   |
|flex: none                 |0 0 auto                   |
|flex: 1                    |Genellikle eşit alan paylaşımı için kullanılır       |
|flex: 0 0 200px            |200px başlangıç boyutu, büyüme ve küçülme yok              |
|flex: 1 1 250px            |250px temel boyut, büyüyebilir ve küçülebilir      |

### flex: 1 Ne Yapar?
```
    .item {
        flex: 1;
    }
```
Pratikte bu kullanım **flex: 1 1 0%** olarak genişletilir.

Item'lar kullanılabilir alanı eşit büyüme paylarıyla paylaşmaya çalışır. Ancak içeriklerin minimum boyutları veya diğer CSS kısıtları nedeniyle toplam genişlikler her zaman tam eşit olmayabilir.

### flex: 1 ve flex: auto Farkı
```
    .item {
        flex: 1;
    }
```
Başlangıç boyutu hesabında sıfır temel boyut kullanmaya yönelir.
```
    .item {
        flex: auto;
    }
```
İçerik veya tanımlanmış boyutları başlangıç hesabına dahil eder. Bu nedenle farklı uzunlukta içeriklere sahip item'ların alan paylaşımı farklı olabilir.

## min-width: 0 — Flexbox'ta Önemli Bir Ayrıntı
Flexbox ile çalışırken karşılaşabileceğimiz sorunlardan biri, uzun metinlerin veya geniş içeriklerin kapsayıcıdan taşmasıdır.

Örneğin:
```
    <div class="row">
        <div class="icon">📄</div>

        <div class="content">
            <p class="filename">
                cok-uzun-ve-bosluk-icermeyen-dosya-adi-ornek.pdf
            </p>
        </div>
    </div>
```

```
    .row {
        display: flex;
        width: 300px;
    }

    .icon {
        flex-shrink: 0;
    }

    .content {
        flex: 1;
    }

    .filename {
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
    }
```
Bazı durumlarda **.content** beklediğimiz kadar küçülmez. Bunun nedeni flex item'ların varsayılan otomatik minimum boyut davranışı olabilir.

Çözüm:
```
    .content {
        flex: 1;
        min-width: 0;
    }
```
Bu sayede item, içerik kaynaklı otomatik minimum genişlik sınırının altına inebilir.

Benzer şekilde dikey Flexbox düzenlerinde gerektiğinde:
```
    .content {
        min-height: 0;
    }
```
kullanılabilir.

**Not:** min-width: 0 her Flexbox problemine uygulanması gereken zorunlu bir kural değildir. Özellikle daralmayan flex item ve metin taşması problemlerinde kullanışlıdır.

## align-self — Tek Bir Item'ı Hizalama
align-self, belirli bir flex item'ın cross axis üzerindeki hizalamasını değiştirmemizi sağlar.

Örneğin:
```
    .container {
        display: flex;
        align-items: center;
    }

    .special {
        align-self: flex-start;
    }
```
Burada bütün item'lar genel olarak ortalanırken **.special** kendi satırının cross axis başlangıcına hizalanır.

Yaygın değerler:
```
    align-self: auto;
    align-self: flex-start;
    align-self: flex-end;
    align-self: center;
    align-self: stretch;
    align-self: baseline;
```

### Ne Zaman Kullanılır?
Örneğin bir kart grubunda yalnızca bir elementin farklı hizalanması gerektiğinde kullanılabilir.

Ancak bütün item'ların hizalamasını değiştirmek istiyorsak *align-items* daha uygundur.

## order — Görsel Sıralamayı Değiştirme
order, flex item'ların görsel sıralamasını kontrol eder.

Varsayılan değer:
```
    .item {
        order: 0;
    }
```
Örneğin:
```
<div class="container">
    <div class="first">1</div>
    <div class="second">2</div>
    <div class="third">3</div>
</div>
```

```
.container {
    display: flex;
}

.first {
    order: 2;
}

.second {
    order: 0;
}

.third {
    order: 1;
}
```
Görsel sıra: `[ 2 ] [ 3 ] [ 1 ]`

Daha küçük order değeri önce gelir. Eşit değerlerde kaynak sırası korunur.

### Erişilebilirlik Açısından Önemli
order yalnızca görsel sıralamayı değiştirir.

HTML kaynak sırası, ekran okuyucu okuma düzeni ve klavye gezinme sırası otomatik olarak değişmez.

Bu nedenle anlamlı içerik sırasını order ile değiştirmek yerine HTML içerisinde doğru sırayı oluşturmalıyız.

## flex-flow Shorthand
flex-flow, iki property'yi birleştirir:
- flex-direction
- flex-wrap

Örneğin:
```
    .container {
        flex-flow: row wrap;
    }
```
Açılımı:
```
    .container {
        flex-direction: row;
        flex-wrap: wrap;
    }
```
Başka bir örnek:
```
    .container {
        flex-flow: column nowrap;
    }
```
Bu kullanım özellikle kısa ve anlaşılır Flexbox tanımlarında tercih edilebilir.

## Flexbox ve Auto Margin
Flexbox içerisinde **margin: auto** farklı hizalama ihtiyaçlarını çözmek için kullanılabilir.

Örneğin bir navbar'da giriş butonunu sağ tarafa yerleştirmek isteyelim.
```
    <nav class="navbar">
        <a href="/">Logo</a>
        <a href="/products">Ürünler</a>
        <a href="/about">Hakkımızda</a>
        <a class="login" href="/login">Giriş Yap</a>
    </nav>
```

```
    .navbar {
        display: flex;
        align-items: center;
        gap: 20px;
    }

    .login {
        margin-left: auto;
    }
```
Soldan sağa bir düzende .login elementi kullanılabilir boş alanı sol margin üzerinden alarak sağ tarafa itilir.

### Neden space-between Kullanmadık?
Çünkü space-between, bütün item'lar arasındaki boş alanı dağıtır. Burada yalnızca son item'ı sağ tarafa itmek istiyoruz. Bu nedenle margin-left: auto daha kontrollü bir çözümdür.

Modern yazı yönü duyarlı kullanımda:
```
    .login {
        margin-inline-start: auto;
    }
```
tercih edilebilir.

## Gerçek Proje Örneği - Responsive Header
Şimdi öğrendiğimiz özellikleri gerçek bir arayüzde kullanalım.

HTML:
```
    <header class="site-header">
        <div class="header-inner">
            <a href="/" class="logo">Brand.</a>

            <nav class="nav" aria-label="Ana menü">
                <a href="/">Anasayfa</a>
                <a href="/products">Ürünler</a>
                <a href="/about">Hakkımızda</a>
            </nav>

            <a href="/contact" class="contact-button">
                İletişim
            </a>
        </div>
    </header>
```

CSS:
```
    * {
        box-sizing: border-box;
    }

    .site-header {
        padding: 20px;
        border-bottom: 1px solid #e5e2da;
    }

    .header-inner {
        display: flex;
        align-items: center;
        gap: 24px;

        max-width: 1200px;
        margin-inline: auto;
    }

    .logo {
        flex-shrink: 0;

        font-size: 24px;
        font-weight: 700;
        text-decoration: none;
        color: #26251f;
    }

    .nav {
        display: flex;
        align-items: center;
        gap: 24px;

        margin-inline: auto;
    }

    .nav a {
        color: #66645d;
        text-decoration: none;
    }

    .contact-button {
        flex-shrink: 0;

        padding: 12px 20px;
        border-radius: 8px;

        background-color: #7d8570;
        color: white;
        text-decoration: none;
    }
```

Bu örnekte:
- Header içerisindeki üç ana bölüm Flexbox ile yan yana yerleştirilir.
- **align-items: center** ile dikey hizalama sağlanır.
- gap ile bölümler arasında boşluk oluşturulur.
- Navbar bağlantıları kendi içerisinde Flexbox kullanır.
- Logo ve iletişim butonunun küçülmesi engellenir.

Responsive Düzen:
```
    @media (max-width: 768px) {
        .header-inner {
            flex-wrap: wrap;
            justify-content: space-between;
        }

        .nav {
            order: 3;
            flex-basis: 100%;

            justify-content: center;
            flex-wrap: wrap;

            margin-inline: 0;
        }
    }
```

Bu örnekte küçük ekranlarda navbar ikinci satıra geçer.

Ancak bu, gerçek bir mobil açılır menü değildir. Mobil hamburger menü, açma-kapama davranışı ve erişilebilir etkileşimler için ayrıca HTML, CSS ve gerektiğinde JavaScript gerekir.

## Gerçek Proje Örneği — Responsive Kart Düzeni

Flexbox ile kartların yan yana yerleşmesini ve ekran daraldığında yeni satıra geçmesini sağlayabiliriz.

HTML:
```
    <section class="card-list">
        <article class="card">
            <h3>HTML</h3>
            <p>Web sayfalarının yapısını oluşturur.</p>
            <a href="#">Detaylar</a>
        </article>

        <article class="card">
            <h3>CSS</h3>
            <p>Web sayfalarının görsel tasarımını yönetir.</p>
            <a href="#">Detaylar</a>
        </article>

        <article class="card">
            <h3>JavaScript</h3>
            <p>Web sayfalarına etkileşim kazandırır.</p>
            <a href="#">Detaylar</a>
        </article>
    </section>
```
CSS:
```
    .card-list {
        display: flex;
        flex-wrap: wrap;
        gap: 20px;
    }

    .card {
        display: flex;
        flex-direction: column;

        flex: 1 1 260px;
        min-width: 0;

        padding: 24px;
        border: 1px solid #e5e2da;
        border-radius: 12px;
    }

    .card p {
        flex-grow: 1;
    }

    .card a {
        align-self: flex-start;
        margin-top: 20px;
    }
```
### Burada Ne Yaptık?
**card-list** üzerinde:
```
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
```
kullanarak kartları yan yana ve gerektiğinde alt satıra geçebilir hale getirdik.

Kartlarda `flex: 1 1 260px;` kullanarak yaklaşık 260px başlangıç boyutu belirledik ve kartların büyüyüp küçülebilmesini sağladık.

Kartın kendi içerisinde:
```
    display: flex;
    flex-direction: column;
```
kullanarak içeriği dikey yönde düzenledik.

Paragrafta `flex-grow: 1;` kullanarak uygun boş alanın paragraf bölgesine ayrılmasını sağladık.

Böylece aynı satırdaki eşit yüksekliğe uzayan kartlarda bağlantıların alt kısımda hizalanması kolaylaşır.

## Flexbox ve CSS Grid Arasındaki Fark
Flexbox ve Grid birbirinin alternatifi olmak zorunda değildir. İkisi farklı yerleşim ihtiyaçlarını çözmek için tasarlanmıştır.
|Özellik        |Flexbox            |CSS Grid               |
|---------------|-------------------|-----------------------|
|Yerleşim modeli|Tek boyutlu        |İki boyutlu            |
|Temel kontrol  |Satır veya sütun   |Satır ve sütun birlikte|
|İçerik hizalama|Çok uygun          |Çok uygun              |
|Navbar         |Genellikle uygun   |Kullanılabilir         |
|Kart içeriği   |Genellikle uygun   |Kullanılabilir         |
|Düzenli kart ızgarası|Kullanılabilir|Genellikle daha uygun |
|Karmaşık sayfa yerleşimi|Sınırlı olabilir|Genellikle daha uygun|

### Flexbox Örneği
```
    .navbar {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
```
### Grid Örneği
```
    .products {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 20px;
    }
```
**Temel yaklaşım:** İçeriğin tek bir ana yönde akmasını istiyorsak Flexbox; satır ve sütunların birlikte tanımlandığı bir düzen istiyorsak Grid daha uygun olabilir.

## Sık Yapılan Hatalar
### 1. justify-content ile align-items Özelliklerini Karıştırmak

Yanlış varsayım: `justify-content her zaman yatay hizalama yapar.`

Doğrusu: `justify-content, main axis üzerinde çalışır`

```
    .container {
        display: flex;
        flex-direction: column;
        justify-content: center;
    }
```

Burada main axis dikey olduğu için justify-content dikey hizalamayı etkiler.

### 2. align-items: center Kullanıp Sonuç Alamamak
```
    .container {
        display: flex;
        align-items: center;
    }
```
Kapsayıcıda görünür bir çapraz eksen boşluğu bulunmuyorsa hizalama fark edilmeyebilir. Bu durumda kapsayıcının boyutlarını ve içerik ölçülerini kontrol etmeliyiz.

### 3. flex-wrap Kullanmayı Unutmak
```
    .container {
        display: flex;
    }
```
Varsayılan flex-wrap: nowrap olduğu için item'lar yeni satıra geçmez.

Gerekirse:
```
    .container {
        display: flex;
        flex-wrap: wrap;
    }
```
kullanılmalıdır.

### 4. flex-grow: 1 ile Bütün Item'ların Kesinlikle Eşit Genişlikte Olacağını Düşünmek
```
    .item {
        flex-grow: 1;
    }
```
Bu kullanım yalnızca büyüme payını eşitler. Başlangıç boyutları farklıysa sonuç genişlikleri de farklı olabilir.

Eşit başlangıç temeli için uygun koşullarda:
```
    .item {
        flex: 1;
        min-width: 0;
    }
```
kullanılabilir.

### 5. Uzun İçeriğin Taşmasını Anlayamamak
Flex item'ın otomatik minimum boyutu daralmayı engelliyor olabilir.
```
    .content {
        min-width: 0;
    }
```
bazı yatay Flexbox taşma problemlerini çözebilir.

### 6. order ile Anlamlı İçerik Sırasını Değiştirmek
```
    .first {
        order: 3;
    }
```
Bu işlem yalnızca görsel sıralamayı değiştirir. Erişilebilirlik için mantıksal sıralama HTML içerisinde korunmalıdır.

### 7. Her Yerleşim Problemini Flexbox ile Çözmeye Çalışmak
Flexbox güçlüdür ancak her durumda en uygun seçenek değildir. Özellikle satır ve sütunların birlikte kontrol edilmesi gereken düzenlerde Grid tercih edilebilir.

### 8. gap ve justify-content Farkını Karıştırmak
```
    .container {
        display: flex;
        gap: 20px;
        justify-content: space-between;
    }
```

Burada `gap`, item'lar arasında en az belirlenen boşluğu oluşturur. `justify-content` ise kalan pozitif alanı dağıtabilir. İki özellik birbirini tamamlayabilir.

## Kısaca Özet
Flexbox, elementleri tek bir ana eksen üzerinde düzenlemek ve kullanılabilir alanı yönetmek için kullanılan modern CSS yerleşim sistemidir.

### Flex Container Property'leri
|Property       |Görevi         |
|---------------|---------------|
|display: flex  |Flex container oluşturur   |
|flex-direction |Ana eksenin yönünü belirler|
|flex-wrap      |Item'ların yeni satıra geçmesini yönetir|
|flex-flow      |Direction ve wrap kısaltmasıdır    |
|justify-content|Main axis üzerindeki boş alanı dağıtır |
|align-items    |Item'ları cross axis üzerinde hizalar  |
|align-content  |Flex satırlarını cross axis üzerinde dağıtır|
|gap            |Item'lar arasındaki boşluğu belirler   |

### Flex Item Property'leri
|Property               |Görevi                 |
|-----------------------|-----------------------|
|flex-grow              |Pozitif boş alanın paylaşım oranı  |
|flex-shrink            |Daralma sırasında küçülme davranışı|
|flex-basis             |Ana eksendeki başlangıç boyutu     |
|flex                   |Grow, shrink ve basis kısaltması   |
|align-self             |Tek item'ın cross axis hizalaması  |
|order                  |Görsel sıralama                    |
|margin: auto           |Uygun boş alanı margin üzerinden kullanma  |

### En Sık Kullanılan Flexbox Desenleri
Yatay hizalama:
```
    .container {
        display: flex;
        align-items: center;
        gap: 16px;
    }
```
Yatay ve dikey ortalama:
```
    .container {
        display: flex;
        justify-content: center;
        align-items: center;
    }
```
Responsive item yerleşimi:
```
    .container {
        display: flex;
        flex-wrap: wrap;
        gap: 20px;
    }
```
Eşit alan paylaşımı:
```
    .item {
        flex: 1;
        min-width: 0;
    }
```
Dikey kart içeriği:
```
    .card {
        display: flex;
        flex-direction: column;
    }
```
Sağa itilen son item:
```
    .last-item {
        margin-inline-start: auto;
    }
```

### Flexbox Mantığı
```
    FLEXBOX
    │
    ├── FLEX CONTAINER
    │   │
    │   ├── flex-direction
    │   │   └── Ana eksen yönü
    │   │
    │   ├── justify-content
    │   │   └── Ana eksende dağılım
    │   │
    │   ├── align-items
    │   │   └── Çapraz eksende hizalama
    │   │
    │   ├── flex-wrap
    │   │   └── Yeni satıra geçme
    │   │
    │   └── gap
    │       └── Elementler arası boşluk
    │
    └── FLEX ITEM
        │
        ├── flex-grow
        │   └── Büyüme
        │
        ├── flex-shrink
        │   └── Küçülme
        │
        ├── flex-basis
        │   └── Başlangıç boyutu
        │
        ├── align-self
        │   └── Bireysel hizalama
        │
        └── order
            └── Görsel sıralama
```

Bu bölümün en önemli noktası:
`Flexbox kullanırken önce ana eksenin yönünü belirlemeli, ardından elementlerin bu eksen üzerindeki hizalama, büyüme, küçülme ve boşluk paylaşımı davranışlarını yönetmeliyiz.`

Flexbox'ın çalışma mantığını anladığımızda navbar, header, kart, form ve responsive bileşenlerin büyük bir bölümünü daha az CSS koduyla oluşturabiliriz.