# CSS Seçiciler — Selectors
**00_CSSTemelleri** bölümünde temel bir CSS kuralının şu yapıya sahip olduğunu görmüştük:
```
    selector {
        property: value;
    }
```

Örneğin:
```
    p {
        color:red;
    }
```

Buradaki `p` **CSS selector, yani seçicidir.**

Selector'ın görevi `CSS kuralının hangi HTML elementlerine uygulanacağını belirlemektir.`

CSS'te elementleri yalnızca etiket adına göre değil;
- Element adına,
- Class değerine,
- ID değerine,
- Attribute'larına,
- Sayfadaki konumlarına,
- Diğer elementlerle ilişkilerine,
- Belirli durumlarıa göre hedefleyebiliriz.

Bu bölümde CSS'in temel seçici yapılarını inceleyeceğiz.
```
    CSS Selectors
    │
    ├── 1. Selector Nedir?
    │
    ├── 2. Simple Selectors
    │   ├── Element Selector
    │   ├── Class Selector
    │   ├── ID Selector
    │   └── Universal Selector
    │
    ├── 3. Class vs ID
    │
    ├── 4. Combinators
    │   ├── Descendant
    │   ├── Child
    │   ├── Next Sibling
    │   └── Subsequent Sibling
    │
    ├── 5. Grouping
    ├── 6. Attribute Selectors
    ├── 7. Pseudo-Classes
    ├── 8. Pseudo-Elements
    ├── 9. Sık Yapılan Hatalar
    └── 10. Kısaca
```

## Selector Nedir?
Selector, CSS kuralının **hangi Html element veya elementlerini hedefleyeceğini belirleyen bölümdür.**

Örneğin: 
```
    p {
        color:gray;
    }
```

Buradaki: `p` selector'dır.

Tarayıcı bu kuralı okuduğunda sayfadaki eşleşen p elementlerini bulur ve ilgili CSS bildirimlerini uygular.

HTML:
```
    <p>Birinci paragraf.</p>
    <p>İkinci paragraf.</p>
```

CSS:
```
    p {
        color: gray;
    }
```
Bu selector iki **p elementiyle de eşleşir.** Bunu temel olarak:
```
    Selector
       ↓
    Hangi elementler?
       ↓
    Eşleşen HTML elementleri
       ↓
    CSS kuralları uygulanır
```
şeklinde düşünebiliriz.

Ancak her zaman bütün **p elementlerini hedeflemek istemeyebiliriz.** Örneğin yalnızca belirli bir paragrafı veya belirli bir ürün kartının içerisindeki butonu hedeflemek isteyebiliriz. Bunun için CSS farklı selector türleri sunar.

## Basit Seçiciler - Simple Selectors
Başlangıçta bilmemiz gereken temel seçiciler aşağıdaki şekildedir:
```
    Element Selector
    Class Selector
    ID Selector
    Universal Selector
```

### 1. Element Selector - Tip Seçici
Element selector, HTML elementlerini **etiket adına göre** hedefler.

Örneğin sayfadaki *p* elementlerini hedefler.
```
    p {
        color: gray;
    }
```

HTML:
```
    <p>Birinci paragraf</p>
    <p>Birinci paragraf</p>
    <p>Birinci paragraf</p>
```
Bu üç element de **selector** ile eşleşir.

Başka bir örnek
```
    button {
        background-color: black;
        color: white;
    }
```
sayfadaki eşleşen button elementlerini hedefler.
```
    <button>Sepete Ekle</button>
    <button>Satın Al</button>
```
Her iki buton da bu CSS kuralından etkilenir.

### Element Selector Ne Zaman Kullanılır?
Bir element türününü genel görünümünü belirlemek istediğimizde kullanılabilir. Örneğin:
```
    body {
        font-family: Arial, sans-serif;
    }

    h1 {
        font-size: 40px;
    }

    p {
        line-height: 1.6;
    }
```

Burada belirli bir component'i değil, ilgili element türlerinin genel stilini tanımlıyoruz.

Temel yapı:
```
    HTML
    <p>...</p>
        ↓
    CSS
    p { }
```
Element selector'ın önünde `. veya #` gibi bir işaret bulunmaz.

### 2. Class Selector
Class selector, HTML elementlerini **class attribute'una** göre hedefler.
HTML:
```
    <button class="primary-button">
        Sepete Ekle
    </button>
```

CSS:
```
    .primary-button {
        background-color: black;
        color:white;
    }
```

Class selector yazarken class adının önüne `.` nokta eklenir.

```
    HTML → class="primary-button"
                ↓
    CSS → .primary-button
```

### Aynı Class Birden Fazla Elementte Kullanılabilir
Class yapısının önemli özelliklerinden biri **tekrar kullanılabilmesidir.**

Örneğin:
```
    <button class="primary-button">
        Sepete Ekle
    </button>

    <a class="primary-button" href="/products">
        Ürünleri Gör
    </a>
```

Her iki element de bu kuralla eşleşebilir.
```
    .primary-button {
        background-color: black;
        color: white;
    }
```

Class yalnızca belirli bir HTML elementine özgü değildir.

### Bir Element Birden Fazla Class Alabilir.
Bir HTML elementi birden fazla class değerine sahip olabilir.

Örneğin:
```
    <button class="button button-large">
        Sepete Ekle
    </button>
```

Burada elementin iki class'ı vardır.
```
    button
    button-large
```

Bunları ayrı ayrı hedefleyebiliriz:
```
    .button {
        border:none;
    }

    .button-large {
        padding: 16px 32px;
    }
```
Aynı element her iki CSS kuralıyla da eşleşir. Bu özellik tekrar kullanılabilir CSS yapıları oluştururken oldukça kullanışlıdır.

### 3. ID Selector
ID Selector, HTML elementini **id attribute**'una göre hedefler.

HTML:
```
    <section id="featured-products">
        <h2>Öne Çıkan Ürünler</h2>
    </section>
```

CSS:
```
    #featured-products {
        padding: 40px;
    }
```

ID Selector yazarken ID adının önüne; `#` işareti eklenir.
```
    HTML: id="featured-products"
            ↓
    CSS: #featured-products
```

### ID Benzersiz olmalıdır
Bir HTML belgesindeki **id** değeri ilgili belge içerisinde benzersiz olmalıdır.

Doğru:
```
    <section id="featured-products">
        ...
    </section>

    <section id="new-products">
        ...
    </section>
```
Aynı ID'yi farklı elementlerde tekrar kullanmak doğru değildir.

Yanlış:
```
    <section id="products">
        ...
    </section>
```

Eğer aynı stil birden fazla elementte kullanılacaksa genellikle class daha uygun olur:
```
    <section class="product-section">
        ...
    </section>

    <section class="product-section">
        ...
    </section>
```
CSS:
```
    .product-section {
        padding: 40px;
    }
```

### 4. Universal Selector
Universal selector `*` şeklinde yazılır. Eşleşebilecek tüm elementleri hedeflemek için kullanılır. 

Örneğin:
```
    * {
        box-sizing:border-box;
    }
```

Bu tarz kurallar bazı başlangıç/reset yaklaşımlarında görülebilir. Ancak `Bütün elementlerin **margin ve padding değerlerini sıfırlamak her projede zorunlu bir kural değildir.` Projenin CSS yaklaşımına göre karar verilmelidir.

### Universal Selector ve Reset
CSS'te tarayıcıların varsayılan stillerini düzenlemek için **CSS Reset** gibi yaklaşımlar bulunur. Universal selector bazı reset kurallarının içerisinde kullanılabilir. Ancak:
```
    Universal Selector ≠ CSS Reset
```
Universal selector yalnızca bir **seçicidir.**

Reset ise tarayıcıların varsayılan stillerini belirli bir başlangıç noktasına getirmeyi amaçlayan daha geniş bir CSS yaklaşımıdır. Normalize yaklaşımı da bununla ilişkili fakat farklı bir konudur.

## Class ve ID - Ne Zaman Hangisi?
CSS öğrenirken en sık karşılaşılan sorulardan biri: `Class mı kullanmalıyım, ID mi?` sorusudur.

Temel fark:
|Class      |ID             |
|-----------|---------------|
|. ile seçilir| # ile seçilir |
|Tekrar kullanılabilir | Belge içinde benzersiz olmalıdır|
|Birden fazla elementte bulunabilir| Aynı Id değeri tekrar edilmemelidir|
|Bir element birden fazla class alabilir| Bir elementin id değeri tek bir kimliktir.|

Örneğin tekrar kullanılacak kartlar:
```
    <article class="product-card">
        ...
    </article>

    <article class="product-card">
        ...
    </article>

    <article class="product-card">
        ...
    </article>
```

CSS:
```
    .product-card {
        border: 1px solid #ddd;
    }
```

Burada class mantıklıdır çünkü aynı yapı tekrar kullanılmaktadır. Benzersiz bir bölüm ID ile tanımlanabilir:
```
    <section id="featured-products">
        ...
    </section>
```

Ancak bir elementin benzrsiz olması `CSS yazarken mutlaka ID selector kullanmalıyız.` anlamına gelmez.

Gerçek projelerde stillendirme için class'lar sıklıkla daha esnek ve tekrar kullanılabilir bir yapı sağlar.

### Specificity Farkı
Class ve ID selector'ların CSS'teki öncelik hesaplamaları aynı değildir.

Örneğin:
```
    .card{
        color:black;
    }

    #featured-card {
        color:red;
    }
```
gibi kurallarda hangi stilin uygulanacağını yalnızca kodun yukarıdan aşağı sırası belirlemez. CSS'te: **specificity** adı verilen bir kavram da bulunur. ID selector, class selector'dan daha yüksek specificity'ye sahiptir. Şimdilik, `Selector türünün CSS öncelik hesaplamasında etkisi olduğunu bilinmesi bu konu için yeterli.`

## Birleştirici Seçiciler - Combinators
Elementleri **birbirleriyle olan ilişkilerine göre** seçmek isteriz. Örneğin; `.product-card içerisindeki bütün p elementlerini seç.` veya `.menu elementinin doğrudan çocukları olan a elementlerini seç.` Bunun için **combinator** kullanılabiliriz. 

Temel combinator'lar şu şekildedir:
```
    Descendant
    Child
    Next Sibling
    Subsequent Sibling
```

### 1. Descendant Combinator - Boşluk
Descendant Combinator **boşluk** ile ifade edilir. 

Örneğin:
```
    .product-card p{
        color:gray;
    }
```
Bu selector, `.product-card içerisinde bulunan p elementlerini seç.` anlamına gelir.

HTML:
```
    <article class="product-card">
        <h2>Kol Saati</h2>
        <div class="product-info">
            <p>12.500 TL</p>
        </div>
    </article>
```

Buradaki **p, .product-card** elementinin doğrudan çocuğu değildir. Arada `<div class="product-info">` bulunmaktadır. Buna rağmen `.product-card p` selector'ı p elementini seçer. Çünkü descendant combinator  yalnızca doğrudan çocukları değil, içerideki eşleşen alt öğeleri hedefleyebilir.

Yapı:
```
    .product-card
    │
    └── .product-info
        │
        └── p  ← seçilir
```

### 2. Child Combinator - >
Child combinator: `>`ile gösterilir. Yalnızca **doğrudan çocuk elementleri** hedefler.

Örneğin:
```
    .product-card > p {
        color:gray;
    }
```

HTML:
```
    <article class="product-card">
        <p>Stokta var.</p>
        <div class="product-info">
            <p>12.500 TL</p>
        </div>
    </article>
```

Yapı:
```
    .product-card
    │
    ├── p                ← seçilir
    │
    └── .product-info
        │
        └── p            ← seçilmez
```

Çünkü ikinci p, .product-card elementinin doğrudan çocuğu değildir.

### Descendant ve Child Farkı
Bu iki combinator sık karıştırılır.

**Descendant:** `.parent p` parent içerisindeki eşleşen alt öğeleri hedefleyebilir.

**Child:** `.parent > p` yalnızca parent'ın **doğrudan çocuklarını hedefler.**

Özet:
```
    .parent
    │
    ├── p
    │
    └── div
        └── p

    .parent p   
```

Sonuç:
```
   ✓ İlk p
    ✓ İkinci p

    .parent > p
```

Sonuç:
```
    ✓ İlk p
    ✗ İkinci p
```

### 3. Next Sibling Combinator - +
+ combinator!ı bir elementin **hemen ardından gelen kardeş elementi** hedeflemek için kullanılır.

Örneğin.
```
    h2 + p {
        color:gray;
    }
```

HTML:
```
    <h2>Ürün Açıklaması</h2>
    <p>Birinci paragraf</p>
```

Burada:
```
    h2
    │
    ├── hemen sonraki p → seçilir
    │
    └── sonraki p       → seçilmez
```

Yalnızca h2 elementinin hemen ardından gelen ve selector'ın sağ tarafıyla eşleşen p seçilir.

### Kardeş Element Ne Demektir?
İki element aynı parent'a sahipse **sibling**, yani kardeş elementlerdir.

Örneğin:
```
    <section>
        <h2>Başlık</h2>
        <p>Paragraf</p>
    </section>
```
Burada:
```
    section
    │
    ├── h2
    └── p
```

**h2** ve **p** aynı parent'a sahip oldukları için kardeştir.

### 4. Subsequent Sibling Combinator - ~
~ combinator'ı bir elementten sonra gelen **eşleşen kardeş elementleri** hedeflemek için kullanılır. 

Örneğin:
```
    h2 ~ p {
        color:gray;
    }
```

HTML:
```
    <section>
        <h2>Ürün Açıklaması</h2>
        <p>Birinci paragraf.</p>
        <div>Ek bilgi</div>
        <p>İkinci paragraf.</p>
    </section>
```

Burada h2 sonrasında gelen ve aynı parent altında bulunan eşleşen p elementleri seçilir.

```
    section
    │
    ├── h2
    ├── p      ← seçilir
    ├── div
    └── p      ← seçilir
```
Arada başka bir element bulunması bunu engellemez.

### Combinator Karşılaştırması
|Combinator     |Yazım          |Ne Seçer?  |
|---------------|---------------|-----------|
|Descendant     |A B            |A içerisindeki eşleşen B'ler|
|Child          |A > B          |A'nın doğrudan çocuğu olan B'ler|
|Next Sibling   |A + B          |A'dan hemen sonraki eşleşen kardeş B|
|Subsequent Sibling| A ~ B      |A'dan sonra gelen eşleşen kardeş B'ler|

Şema olarak:
```
    A B → A'nın içerisindeki B
    A > B → A'nın doğrudan çocuğu B
    A + B → A'nın hemen sonraki kardeşi B
    A ~ B → A'dan sonra eşleşen kardeş B'ler
```

## Gruplama ~ Grouping Selectors
Bazen farklı selector'lara aynı CSS kurallarını uygulamaz isteriz. Örneğin:
```
    h1 {
        font-family: Arial, sans-serif;
    }
    h2 {
        font-family: Arial, sans-serif;
    }
    h3 {
        font-family: Arial, sans-serif;
    }
```

Burada aynı declaration üç kex tekrar edilmiştir. Selector'ları virgüller ayırarak gruplayabiliriz:

```
    h1,
    h2,
    h3 {
        font-family:Arial, sans-serif;
    }
```

Bu selector listesi: `h1, h2, h3` elementlerinin her biriyle eşleşebilir ve aynı **declaration block'u** uygular.

Başka bir örnek:
```
    .button,
    .link-button
    {
        border-radius: 8px;
    }
```
Bu yöntem kod tekrarını azaltabilir.

### Virgül Önemlidir
Şu iki selector aynı değildir: `.card p` ve `.card, p`. Birincisi; `.card içerisindeki p elementlerini seçer.` İkincisi; `.card ile eşleşen elementleri ve p elementlerini seç.` anlamına gelir.

Dolayısıyla: 
```
    boşluk → ilişki
    virgül → selector listesi
```

### Attributes Selectors
Temel yapı: `[attribute]` şeklindedir.

Örneğin:
```
    [disabled] {
        opacity: 0.5;
    }
```
Bu selector disabled attribute'una sahip elementlerle eşleşir.

HTML:
```
    <button disabled>
        Satın Al
    </button>
```
### Belirli Attribute Değerini Seçmek
Şu yapı: `[attribute="value"]` attribute'un belirli bir değere saip olduğu elementleri seçer.

Örneğin:
```
    input[type="text"] {
        border:1px solid gray;
    }
```

HTML:
```
    <input type="text">
    <input type="email">
    <input type="password">
```
Burada yalnızca: `<input type="text">` selector ile eşleşir.

Başka bir örnek HTML:
```
    <a href="https://example.com" target="_blank">
        Siteyi Aç
    </a>

    <a href="/about">
        Hakkımızda
    </a>
```

CSS:
```
    a[target="_blank"] {
        font-weight: bold;
    }
```

Bu selector: `a elementi olan ve target="_blank" attribute değerine sahip elementleri seç.` anlamına gelir.

Burada:
```
    a → Element selector
    [target="_blank"] → Attribute selector
```
birlikte kullanılmıştır.

Attribute selector'ların daha gelişmiş eşleşme operatörleri de bulunur. Ancak temel selector konusundaki ana mantığı anlamak için aşağıdaki yapıları bilmek yeterlidir.
```
    [attribute]
    [attribute="value"]
```

## Pseudo-Classes
Pseudo-class, bir elementi yalnızca adı, class'ı veya attribute'u üzerinden değil, **belirli bir durumuna veya yapısal konumuna göre** hedeflememizi sağlar.

Pseudo-class'lar tek iki nokta ile yazılır: `:`
Örneğin:
```
    button:hover{
        background-color: gray;
    }
```

Buradaki `:hover` bir pseudo-class'tır.

### :hover
Kullanıcının işaretleme aygıtıyla bir elementin üzerine geldiği durumu hedefleyebilir.
```
    button:hover {
        background-color: black;
        color:white;
    }
```

Bu sayede elementin belirli bir etkileşim durumuna farklı stil uygulayabiliriz. Ancak `hover` her cihazdaki temel etkileşim biçimi değildir.Dokunmatik cihazlarda aynu kullanım beklentisine güvenilmemelidir.

### :focus
Bir element focus aldığında kullanılabilir.

Örneğin:
```
    input:focus {
        outline: 2px solid blue;
    }
```
Klavye ve form etkileşimlerinde focus durumu erişilebilirlik açısından özellikle önemlidir.

Focus göstergelerini yalnızca görsel gerekçelerle tamamen kaldırmak:
```
    *:focus {
        outline: none;
    }
```
gibi yaklaşımlarla yapılmamalıdır.

Focus ve klavye erişilebilirliği HTML Accessibility konusunda gördüğümüz prensiplerle birlikte düşünülmelidir.

### :first-child
Bir element kardeşleri arasında ilk çocuk olduğunda eşleşebilir.

Örneğin:
```
    li:first-child {
        font-weight: bold;
    }
```
HTML:
```
    <ul>
        <li>HTML</li>
        <li>CSS</li>
        <li>JavaScript</li>
    </ul>
```

İlk li `HTML` selector ile eşleşir.

### :nth-child()
Belirli sıradaki çocukları seçmek için kullanılabilir.

Örneğin:
```
    li:nth-child(2) {
        font-weight: bold;
    }
```
HTML:
```
    <ul>
        <li>HTML</li>
        <li>CSS</li>
        <li>JavaScript</li>
    </ul>
```
Burada ikinci çocuk olan `CSS` eşleşir. Tek ve çift sıraları seçmek de mümkündür:
```
    li:nth-child(odd) {
        background-color: #f5f5f5;
    }
```
veya:
```
    li:nth-child(even) {
        background-color: #eee;
    }
```
**nth-child()** çok daha gelişmiş formüller destekler. Bunların tamamını başlangıç aşamasında ezberlemek gerekli değildir.

Öncelikle:
```
    2
    odd
    even
```
gibi temel kullanımları anlamak yeterlidir.

### :checked
Checkbox ve radio gibi seçilebilir form kontrollerinin seçili durumunu hedefleyebilir.

HTML:
```
    <input
        type="checkbox"
        id="terms"
    >

    <label for="terms">
        Koşulları kabul ediyorum.
    </label>
```
CSS:
```
    input:checked {
        accent-color: green;
    }
```
Buradaki CSS yalnızca input checked durumundayken uygulanır.

### Pseudo-Class'ların Mantığı
Pseudo-class'ları basitçe:
```
    Element
    ↓
    Belirli bir durumda mı?
    ↓
    Evet
    ↓
    CSS uygula
```
şeklinde düşünebiliriz.

Örneğin:
```
    button
    │
    ├── normal
    │
    ├── :hover
    │
    └── :focus
```
CSS bu farklı durumlara göre farklı stiller uygulayabilir. Bu nedenle bazı etkileşim ve durum stilleri için JavaScript yazmamız gerekmez. Ancak pseudo-class'lar JavaScript'in genel alternatifi değildir. Yalnızca CSS'in desteklediği durumları seçmemizi sağlar.

## Pseudo-Elements
Pseudo-element, bir elementin **belirli bir bölümünü** veya CSS'in seçilebilir bir soyut parçasını hedeflemek için kullanılır.

Modern yazımda genellikle çift iki nokta `::` kullanılır.

Örneğin:
```
    p::first-letter {
        font-size: 32px;
    }
```
Buradaki `::first-letter` bir pseudo-element'tir.

### ::first-letter
Bir metin bloğunun ilk harfini hedeflemek için kullanılabilir.
```
    .article-text::first-letter {
        font-size:40px;
        font-weight:bold;
    }
```

### ::first-line
Bir metin bloğunun ilk biçimlendirilmiş satırını hedefleyebilir.
```
    .article-text::first-line {
        font-weight: bold;
    }
```
İlk satırın nerede bittiği ekran genişliği, font ve diğer layout özelliklerine göre değişebilir.

### ::before
Elementin içeriğinin baş tarafında CSS tarafından oluşturulan bir pseudo-element sağlar.

Örneğin:
```
    .required::before {
        content: "*";
    }
```
HTML:
```
    <label class="required">
        E-posta
    </label>
```

### ::after
Elementin içeriğinin son tarafında CSS tarafından oluşturulan bir pseudo-element sağlar.

Örneğin:
```
    .external-link::after {
        content: " ↗";
    }
```

HTML:
```
    <a
        class="external-link"
        href="https://example.com"
    >
        Example
    </a>
```

### content Property
::before ve ::after ile sık karşılaşacağımız property `content` property'sidir.

Örneğin:
```
    .badge::before {
        content:"Yeni"
    }
```

Ancak önemli içerikleri yalnızca CSS ile oluşturmak iyi bir yaklaşım değildir. Örneğin kullanıcı için gerekli bir form label'ını:
```
    .input::before {
        content: "E-posta";
    }
```
ile oluşturmaya çalışmak yerine gerçek HTML içeriği kullanılmalıdır. HTML içeriğin yapısı ve anlamı için, CSS ise görsel sunum için kullanılmalıdır.

### Pseudo-Class ve Pseudo-Element Farkı
Bu iki kavram sık karıştırılır.

**Pseudo-Class**

Bir elementin durumunu veya belirli yapısal koşulunu seçer.
```
    button:hover
    input:focus
    li:first-child
```

**Pseudo-Element**

Elementin belirli bir bölümünü veya oluşturulan bir parçasını hedefler.
```
    p::first-letter
    p::first-line
    .card::before
    .card::after
```
Temel fark:
```
    Pseudo-Class → : → Element hangi durumda / koşulda?
    Pseudo-Element → :: → Elementin hangi parçası?
```

### : ve :: Kullanımı
Modern CSS'te genel ayrım:
```
    Pseudo-Class
        ↓
    :hover
    :focus
    :first-child

    Pseudo-Element
        ↓
    ::before
    ::after
    ::first-letter
    ::first-line
```
şeklindedir.

Eski CSS sözdizimleriyle geriye dönük uyumluluk nedeniyle `:before` ve `:after` gibi tek `:` kullanılan eski kullanımlarla da karşılaşabiliriz. Modern kod yazarken pseudo-element'lerde:
```
    ::before
    ::after
```
yazımını tercih etmek ayrımı daha açık hale getirir.

## Sık Yapılan Hatalar
### 1. Class ve ID İşaretlerini Karıştırmak
HTML `<div class="card">` ise `.card {}` kullanılır.

HTML `<div id="featured">` ise `#featured` kullanılır.

Özet:
```
    class → .
    id → #
```

### 2. Class Selector'da . İşaretini Unutmak
HTML `<div class="card">` için `card {}` yazarsak `.card` class'ını seçmiş olmayız. Bu kullanım **card** adlı bir element selector'ı anlamına gelir.

Doğru: `.card {}`

### 3. Aynı ID'yi Birden Fazla Elemente Vermek
Yanlış:
```
    <div id="card"></div>
    <div id="card"></div>
```
Tekrar kullanılacak yapılar için:
```
    <div class="card"></div>
    <div class="card"></div>
```
daha uygun olur.

### 4. Descendant ve Child Selector'ı Karıştırmak
`.card p` ile `.card > p` aynı değildir.

```
    .card p → İçerideki eşleşen p'ler
    .card > p → Yalnızca doğrudan çocuk p'ler
```

### 5. + ve ~ Combinator'larını Karıştırmak
```
    h2 + p
```
yalnızca hemen sonraki eşleşen kardeşi seçer.
```
    h2 ~ p
```
ise h2 sonrasında gelen eşleşen kardeş p elementlerini seçebilir.

### 6. Pseudo-Class ve Pseudo-Element'i Karıştırmak
Yanlış düşünce:`:hover → pseudo-element`

Doğrusu: `:hover → pseudo-class`
Doğrusu: `::before → pseudo-element`

Temel ipucu:
```
    : → pseudo-class
    :: → pseudo-element
```
Bu iyi bir başlangıç kuralıdır.

### 7. Çok Uzun ve Aşırı Spesifik Selector'lar Yazmak
Teknik olarak şöyle selector'lar yazabiliriz:
```
    main .products .product-list .product-card .product-info p {
        color: gray;
    }
```
Ancak gereksiz derecede uzun selector zincirleri:
- Okunabilirliği azaltabilir,
- CSS'in HTML yapısına fazla bağımlı olmasına neden olabilir,
- Component değişikliklerinde stillerin kolayca bozulmasına yol açabilir,
- Override işlemlerini zorlaştırabilir.

Bunun yerine uygun durumlarda:
```
    .product-description {
        color: gray;
    }
```
gibi daha açık ve tekrar kullanılabilir selector'lar tercih edilebilir.

### 8. :hover Durumunu Tek Etkileşim Olarak Düşünmek
Örneğin:
```
    button:hover {
        background-color:black;
    }
```
kullanmak normaldir. Ancak kullanıcılar yalnızca mouse kullanmaz.

Klavye kullanıcıları için:
```
    button:focus {
        outline: 2px solid blue;
    }
```
gibi focus durumları da önemlidir.

Ayrıca dokunmatik cihazlarda hover davranışı masaüstündeki mouse kullanımından farklı olabilir. Bu nedenle etkileşim tasarımını yalnızca **:hover** üzerine kurmamak gerekir.

## Kısa Özet
CSS selector'larının temel görevi: `CSS kurallarının hangi elementlerle eşleşeceğini belirlemektir.`

Temel selector türlerini şöyle özetleyebiliriz:

|Selector           |Örnek               |Görevi            
|-------------------|--------------------|-----------
|Element            |p                   |Element adına göre seçer
|Class              |.card               |Class değerine göre seçer
|ID                 |#header             |ID değerine göre seçer
|Universal          |*                   |Eşleşebilecek tüm elementleri seçer
|Descendant         |.card p             |İçerideki eşleşen alt öğeleri seçer
|Child              |.card > p           |Doğrudan çocukları seçer
|Next Sibling       |h2 + p              |Hemen sonraki eşleşen kardeşi seçer
|Subsequent Sibling |h2 ~ p              |Sonraki eşleşen kardeşleri seçer
|Grouping           |h1, h2              |Birden fazla selector'ı aynı kurala bağlar
|Attribute          |[disabled]          |Attribute'a göre seçer
|Attribute + Value  |input[type="text"]  |Attribute değerine göre seçer
|Pseudo-Class       |:hover              |Durum veya yapısal koşula göre seçer
|Pseudo-Element     |::before            |Elementin belirli/oluşturulan parçasını hedefler

Genel şema:
```
    CSS Selectors
    │
    ├── Basit Seçiciler
    │   ├── p
    │   ├── .card
    │   ├── #header
    │   └── *
    │
    ├── İlişkiye Göre Seçiciler
    │   ├── A B
    │   ├── A > B
    │   ├── A + B
    │   └── A ~ B
    │
    ├── Gruplama
    │   └── A, B
    │
    ├── Attribute
    │   ├── [attribute]
    │   └── [attribute="value"]
    │
    ├── Pseudo-Class
    │   ├── :hover
    │   ├── :focus
    │   ├── :first-child
    │   ├── :nth-child()
    │   └── :checked
    │
    └── Pseudo-Element
        ├── ::before
        ├── ::after
        ├── ::first-line
        └── ::first-letter
```
Selector yazarken temel olarak şu soruyu sorarız:
```
    Neyi hedeflemek istiyorum?
            ↓
    Element türünü mü? → p

    Tekrar kullanılabilir bir grubu mu? → .class

    Benzersiz bir kimliği mi? → #id

    Bir attribute'u mu? → [attribute]

    Başka bir elementle ilişkisini mi?
    → A B
    → A > B
    → A + B
    → A ~ B

    Belirli bir durumunu mu?
    → :hover
    → :focus

    Belirli bir parçasını mı?
    → ::before
    → ::first-letter
```
Bu seçicilerin nasıl çalıştığını bilmek CSS'in temelini oluşturur. Ancak bir sonraki önemli soru şudur: `Bir element birden fazla CSS kuralıyla eşleşirse hangi stil uygulanır?` Bu sorunun cevabı bizi CSS'in en önemli temel konularından olan Cascade, Specificity ve Inheritance kavramlarına götürür.