# Cascade ve Specificity
Bir önceki bölümde CSS selector'larının HTML etikerlerini nasıl hedeflediğini öğrendik.

Örneğin:
```
    .card { 
        color:black;
    }
``` 
ve
```
    #featured-card {
        color:red;
    }
```
gibi farklı selector'lar oluşturabiliriz. Ancak aynı HTML elementi birden fazla CSS kuralıyla eşleşebilir.

Örneğin:
```
    <div
        id="featured-card"
        class="card"
    >
        Öne Çıkan Ürün
    </div>
```
CSS:
```
    .card {
        color: black;
    }

    #featured-card {
        color: red;
    }
```

Burada aynı element için iki farklı **color** değeri tanımlanmıştır:
```
    .card → color: black;
    #featured-card → color: red;
```

Peki tarayıcı hangisini uygular? 

İşte bu sorunun cevabı CSS'in en önemli temel kavramlarından biri olan **Cascade** mekanizmasında bulunur.

Bu bölümde aşağıdaki konuları inceleyeceğiz:
```
    Cascade ve Specificity
    │
    ├── 1. Cascade Nedir?
    │
    ├── 2. Cascade'i Belirleyen Faktörler
    │   ├── Importance
    │   ├── Specificity
    │   └── Source Order
    │
    ├── 3. Specificity Nasıl Hesaplanır?
    ├── 4. Specificity Örnekleri
    ├── 5. Source Order
    ├── 6. !important
    ├── 7. Inline Style
    ├── 8. Sık Yapılan Hatalar
    └── 9. Kısaca
```

## Cascade - Basamaklanma Nedir?
CSS'in açılımını `Cascading Style Sheets` olarak öğrenmiştik. Buradaki **Cascading** kelimesi CSS'in temel çalışma mekanizmalarından birini ifade eder. Bir HTML elementi aynı anda birden fazla CSS kuralıyla eşleşebilir.

Örneğin:
```
    <p class="description">
        Ürün açıklaması
    </p>
```

CSS:
```
    p {
        color: gray;
    }

    .description {
        color: black;
    }
```

Burada aynı element `p` selector'ıyla da `description` selector'ıyla da eşleşmektedir. Her iki kural da aynı property'yi değiştirmeye çalışmaktadır: `color` Tarayıcının bu çakışmayı çözmesi gerekir.

İşte **cascade**, bir element için birden fazla CSS declaration'ı geçerl, olduğunda hangi declaration'ın kullanılacağını belirleyen mekanizmadır.

Basitçe şu şekilde düşünebiliriz:
```
    Bir element
        ↓
    Birden fazla CSS kuralıyla eşleşiyor
        ↓
    Aynı property için farklı değerler var
        ↓
    Cascade
        ↓
    Hangi declaration kullanılacak?
```

### Her Kural Birbiriyle Çakışmaz
Önemli bir ayrım yapalım. 

Şu CSS:
```
    .card{
        color:black;
    }

    .card {
        padding:20px;
    }
```

bir problem oluşturmaz. Çünkü kurallar farklı property'leri tanımlamaktadır.

Sonuçta element:
```
    color: black;
    padding: 20px;
```
değerlerinin ikisini de kullanabilir. Asıl karşılaştırma aynı property için birden fazla uygun declaration olduğunda önem kazanır.

Örneğin:
```
    .card {
        color: black;
    }

    .card {
        color: red;
    }
```
Burada iki farklı color değeri vardır. Tarayıcının bunlardan hangisinin kullanılacağını belirlemesi gerekir.

## Cascade'i Belirleyen Temel Faktörler
Başlangıç seviyesinde cascade mantığını anlamak için üç temel kavrama odaklanabiliriz:
```
    Cascade
    │
    ├── Importance
    │
    ├── Specificity
    │
    └── Source Order
```
Basitleştirilmiş düşünce şu şekildedir:
```
    Öncelik / Importance
            ↓
    Specificity
            ↓
    Source Order
```
Ancak bu `Tarayıcı her durumda yalnızca bu üç satıra bakar.` anlamına gelmez. 

Modern CSS cascade mekanizmasında:
- Stil kaynağı (origin),
- Cascade layer,
- Importance,
- Specificity,
- Scope gibi başka ayrıntılar da bulunabilir.

Bunların tamamını başlangıç seviyesinde öğrenmek gerekli değildir. Şimdilik kendi yazdığımız normal CSS kuralları arasındaki çakışmaları anlamaya odaklanacağız.

### 1. Importance — Önem
Normal bir CSS declaration şu şekilde yazılır:
```
    .card {
        color: black;
    }
```

CSS'te bir declaration `!important` ile önemli olarak işaretlenebilir.

Örneğin:
```
    .card {
        color: black !important;
    }
```
Bu declaration normal declaration'lardan farklı bir cascade önceliğine sahip olur.

Örneğin:
```
    .card {
        color: black !important;
    }

    #featured-card {
        color: red;
    }
```

Burada yalnızca `ID selector daha güçlüdür.` diyerek karar veremeyiz. Çünkü ilk declaration `!important` olarak işaretlenmiştir.

Dolayısıyla cascade değerlendirmesinde normal declaration ile important declaration aynı seviyede değerlendirilmez.

### 2. Specificity — Özgüllük
Birden fazla uygun CSS kuralı aynı cascade önceliğinde yarışıyorsa selector'ların specificity değerleri karşılaştırılır. Specificity'yi basitçe `Bir selector'ın hedefini ne kadar özgül tanımladığını gösteren karşılaştırma sistemi` olarak düşünebiliriz.

Örneğin:
```
    p {
        color: gray;
    }
```
bütün p elementlerini hedefler.

Ancak:
```
    .description {
        color: black;
    }
```
belirli bir class'a sahip elementleri hedefler.

Bu nedenle `.description` selector'ı `p` selector'ından daha yüksek specificity'ye sahiptir.

### 3. Source Order — Kaynak Sırası
Eğer iki kuralın cascade bağlamı ve specificity değeri eşitse, kaynak sırası devreye girebilir.

Örneğin:
```
    .card {
        color: black;
    }

    .card {
        color: red;
    }
```
Her iki selector da aynıdır `.card` Dolayısıyla specificity değerleri eşittir. Bu durumda daha sonra gelen declaration kazanır:
```
    .card {
        color: red;
    }
```
Sonuç `color: red;` olur. Bu nedenle CSS'te `Son yazılan her zaman kazanır.` demek doğru değildir.

Doğrusu: `Cascade'in önceki aşamalarında eşitlik varsa kaynak sırası belirleyici olabilir.`

## Specificity Nasıl Hesaplanır?
Specificity hesaplamasını anlamak için selector'ları temel olarak kategorilere ayırabiliriz. Başlangıç seviyesinde şu dört seviyei düşünebiliriz:
- Inline Style
- ID
- Class / Attribute / Pseudo-Class
- Element / Pseudo-Element

Örneğin:
```
    style=""
    #header
    .card
    [type="text"]
    :hover
    p
    ::before
```
aynı specificity seviyesinde değildir.

### Specificity Şeması
Specificity genellikle şu yapıyla gösterilebilir: `A - B - C`

Burada:
```
    A
    ↓
    ID selector sayısı

    B
    ↓
    Class
    Attribute
    Pseudo-Class sayısı

    C
    ↓
    Element
    Pseudo-Element sayısı
```

Inline style ise normal selector specificity'sinin dışında, element üzerinde doğrudan tanımlanan stil olarak daha yüksek öncelikli bir konumda düşünülebilir.

Öğrenirken bunu pratik olarak dört sütunlu şekilde de gösterebiliriz. `Inline | ID | Class/Attribute/Pseudo-Class | Element/Pseudo-Element`

Örneğin: 

Bir element selector'ını : `0 | 0 | 0 | 1`
Bir class selector'ını : `0 | 0 | 1 | 0`
Bir ID selector'ını temsil eder: `0 | 1 | 0 | 0`

### Element Selector
Örneğin:
```
    p{
        color:gray;
    }
```

Burada: `p → 1 element selector` Specificity: `0 | 0 | 0 | 1` olarak düşünülebilir.

### Class Selector
```
    .text{
        color:black;
    }
```

Burada: `.text → 1 class selextor`

Specificity: `0 | 0 | 1 | 0 ` şeklindedir.

Class seviyesi element seviyesinden daha yüksektir. Dolayısıyla `.text > p` olarak düşünebiliriz.

### ID Selector
```
    #title{
        color:red;
    }
```

Burada:  `#title → 1 ID Selector`

Specificity: ` 0 | 1 | 0 | 0 ` şeklindedir.

ID selector class ve element selector'larından daha yüksek specificity'ye sahiptir.

### Inline Style
HTML:
```
    <p style="color:purple;">
        Merhaba
    </p>
```

Buradaki: `style="color: purple;"` **inline style**'dır.

Öğrenme amacıyla bunu: ` 1 | 0 | 0 | 0 `şeklinde düşünebiliriz.

Bu nedenle normal author CSS kuralları arasında inline style oldukça yüksek önceliğe sahiptir.

### Basit Karşılaştırma
Şu yapıyı düşünelim:
```
    <p
        id="intro"
        class="text"
        style="color: purple;"
    >
        Merhaba
    </p>
```

CSS:
```
    p {
        color: gray;
    }

    .text {
        color: black;
    }

    #intro {
        color: red;
    }
```

Aynı element için dört farklı color declaration'ı bulunmaktadır.

Basitleştirilmiş karşılaştırma:
```
    p
    0 | 0 | 0 | 1


    .text
    0 | 0 | 1 | 0


    #intro
    0 | 1 | 0 | 0


    style=""
    1 | 0 | 0 | 0
```

Normal declaration'lar arasında sonuç: `style="" → purple` olur. Bu örnekte **!important** bulunmadığına dikkat edilmelidir.

### Specificity Toplama İşlemi Gibi Düşünülmemelidir
Specificity değerlerini:
```
    ID = 100
    Class = 10
    Element = 1
```
şeklinde anlatan eski öğretim örnekleriyle karşılaşabiliriz.

Bu yöntem başlangıçta karşılaştırmayı kolaylaştırıyor gibi görünse de specificity gerçek anlamda tek bir toplam puan değildir.

Örneğin çok sayıda class selector kullanmak bir ID selector seviyesine "toplanarak" dönüşmez.

Bu nedenle `0 | 1 | 0 | 0` ve `0 | 0 | 10 | 0` gibi değerleri sütunlar halinde karşılaştırmak daha doğru bir zihinsel modeldir.

Önce daha yüksek seviyedeki sütun karşılaştırılır.

## Specificity Hesaplama Örnekleri
Şimdi farklı selector'ları birlikte inceleyelim.

**Örnek1 - Element Selector**
```
    p {
        color:gray;
    }
```

Selector: `p` içerisinde 
```
    ID → 0
    Class → 0
    Element → 1
```
bulunur.

Specificity: ` 0 | 0 | 0 | 1 `

**Örnek2 - Class Selector**
```
    .description {
        color:black;
    }
```

İçerisinde:
```
    ID → 0
    Class → 1
    Element → 0 
```
bulunur.

**Örnek3 - .product-card p**
```
    .product-card p {
        color: gray;
    }
```

Burada iki selector bileşen, vardır:
```
    .product-card → 1 class
    p → 1 element
```

Specificity: ` 0 | 0 | 1 | 1 ` olur.

Buradaki boşluk `Descendant Combinator` specificity'ye kendi başına bir değer eklemez.

Yani:
```
    .product-card p

    .product-card → katkı sağlar
    p             → katkı sağlar
    boşluk        → katkı sağlamaz
```

### Combinator'lar Specificity Ekler mi?
Hayır.

Örneğin: `.card > p` içerisinde:
```
    .card → Class
    > → Combinator
    p → Element
```
bulunur.

Specificity ` 0 | 0 | 1 | 1 ` olur.

`>` işaretinin kendisi **specificity eklemez.**

Aynı şekilde:
```
    boşluk 
    > 
    + 
    ~
```
combinator'ları kendi başlarına specificity değerini artırmaz.

**Örnek4 - ID + Class**
```
    #featured-products .title{
        color:red;
    }
```

Burada:
```
    #featured-products → 1 ID
    .title → 1 Class
```
bulunur.

Specificity: `0 | 1 | 1 | 0` şeklinde düşünülebilir.

**Örnek5 — Class + Attribute**
```
    .form-field input[type="text"] {
        border-color: gray;
    }
```
Parçalayalım:
```
    .form-field → 1 Class
    input → 1 Element
    [type="text"] → 1 Attribute Selector
```
Attribute selector, specificity açısından class seviyesinde değerlendirilir.

Sonuç: `0 | 0 | 2 | 1 ` olur.

**Örnek6 — Pseudo-Class**
```
    .button:hover {
        background-color: black;
    }
```
Burada:
```
    .button → 1 Class
    :hover → 1 Pseudo-Class
```
bulunur.

Her ikisi de aynı specificity kategorisine katkı sağlar.

Sonuç: ` 0 | 0 | 2 | 0 ` olur.

**Örnek7 — Pseudo-Element**
```
    .article::first-letter {
        font-size: 32px;
    }
```
Burada:
```
    .article → 1 Class
    ::first-letter → 1 Pseudo-Element
```
bulunur.

Pseudo-element'ler element seviyesinde specificity katkısı sağlar.

Sonuç:` 0 | 0 | 1 | 1 ` olur.

### .card ve #featured-card Örneğini Çözelim
Selectors konusunda gördüğümüz örneğe geri dönelim.

HTML:
```
    <div
        id="featured-card"
        class="card"
    >
        Öne Çıkan Ürün
    </div>
```
CSS:
```
    .card {
        color: black;
    }

    #featured-card {
        color: red;
    }
```
Specificity değerleri:
```
    .card → 0 | 0 | 1 | 0
    #featured-card → 0 | 1 | 0 | 0
```
ID sütunu daha yüksek olduğu için `#featured-card` daha yüksek specificity'ye sahiptir.

Sonuç: `color: red;` olur.

Burada: `.card` kuralını CSS dosyasında daha sonra yazmak tek başına sonucu değiştirmez.

Örneğin:
```
    #featured-card {
        color: red;
    }

    .card {
        color: black;
    }
```
olsa bile sonuç yine: `red` olur.

Çünkü source order'a geçmeden önce specificity farkı vardır.

## Source Order Ne Zaman Devreye Girer?
Soure order, yani kaynak sırası özellikle ve specificity seviyesindeki declaration'lar arasında önemlidir.

Örneğin:
```
    .card {
        color:black;
    }

    .card {
        color:red;
    }
```

İlk selector ` 0 | 0 | 1 | 0 `

İkinci selector ` 0 | 0 | 1 | 0 `

Specificity değerleri eşittir. Bu nedenle kaynak sırası devreye girer. Daha sonra gelen:
```
    .card {
        color:red;
    }
```
kazanır.

Sonuç: `color:red;` olur.

### Farklı Selector'lar da Aynı Specificity'ye Sahip Olabilir.

Örneğin:
```
    .card {
        color:black;
    }

    .product {
        color:red;
    }
```

HTML:
```
    <div class="card product">
        Ürün
    </div>
```
İki selector da bir class içerir:
```
    .card → 0 | 0 | 1 | 0
    .product → 0 | 0 | 1 | 0
```

Specificity eşittir.

Css'te .product daha sonra vulunduğu için `color:red;` uygulanır.

### Source Order Hakkında Yanlış Bir Düşünce
Şu cümle tek başına doğru değildir: `CSS'te aşağıda yazılan her zaman kazanır.`

Örneğin:
```
    #title{
        color:red;
    }

    .title {
        color:red;
    }
```

HTML:
```
    <h1
        id="title"
        class="title"
    >
        Ürünler
    </h1>
```
.title daha sonra yazılmıştır.

Ancak
```
    #title → 0 | 1 | 0 | 0
    .title → 0 | 0 | 1 | 0
```
olduğu için ID selector daha yüksek specificity'ye sahiptir.

Sonuç: `red` olur. Bu nedenle source order `Önceki cascade aşamalarında eşitlik olduğunda` belirleyici hale gelir.

## `!important` Nedir?
Css'te bir declaration'ın sonuna : `!important` eklenebilir.

Örneğin: 
```
    .card {
        color:red !important;
    }
```
Bu declaration normal declaration'lardan farklı bir önem seviyesinde değerlendirilir.

Örneğin:
```
    #featured-card{
        color:black;
    }

    .card{
        color:red !important`;
    }
```

Normal şartlarda: `#featured-card` selector'ının specificity değeri daha yüksektir. Ancak `color: red !important;` important declaration olduğu için normal `color:black;` declaration'ından farklı bir cascade önceliğinde değerlendirilir. BBu örnekte sonuç `red` olur.

### `!important` Specificity midir?
Hayır. Bu ayrım önemlidir.
```
    !important ≠ Specificity
```

!important, declaration'ın cascade içindeki **importance seviyesini** etkiler.

Specificity ise uygun declaration'lar arasındaki selector karşılaştırmasının bir parçasıdır.

Bu nedenle `!important çok yüksek specificity verir.` demek teknik olarak doğru değildir.

Daha doğru ifade: `!important, declaration'ı normal declaration'lardan farklı bir importance seviyesine taşır.`

### İki !important Çakışırsa Ne Olur?
Örneğin:
```
    .card{
        color:black !important;
    }

    #featured-card {
        color:red !important;
    }
```

Her iki declaration da : `!important` olduğu için bu kez aralarındaki specificity karşılaştırması önem kazanır.
```
    .card → 0 | 0 | 1 |0
    #featured-card → 0 | 1 | 0 | 0
```
ID selector daha yüksek specificity'ye sahip olduğu için: `red` kazanır.

Yani !important kullanılması cascade'in geri kalanının temamen ortadan kalktığı anlamına gelmez.

### !important Neden Genellikle Kaçınılır?
Şöyle bir CSS düşünelim:
```
    .button {
        background-color: black !important;
    }
```

Daha sonra özel bir buton oluşturmak istiyoruz:
```
    .checkout-button {
        background-color: gree;
    }
```

HTML:
```
    <button class="button checkout-button">
        Ödeme Yap
    </button>
```
Ancak ilk declaration !important olduğu için normal override yaklaşımımız çalışmayabilir.

Bu kez geliştirici:
```
    .checkout-button {
        background-color: green !important;
    }
```
yazmaya başlayabilir.

Daha sonra başka bir yerde:
```
    .payment-page .checkout-button {
        background-color: blue !important;
    }
```
gibi kurallar oluşabilir.

Bu durum zamanla:
```
    !important
        ↓
    Override zorlaşıyor
        ↓
    Daha fazla !important
        ↓
    CSS yönetimi zorlaşıyor
```
döngüsüne dönüşebilir.

Bu nedenle **!important** günlük CSS override yöntemi olarak kullanılmamalıdır.

### !important Hiç Kullanılmaz mı?
!important CSS'in geçerli bir parçasıdır. Belirli kontrollü durumlarda kullanılabilir.

Örneğin:
- Kontrol etmediğimiz bazı üçüncü parti stillerle çalışırken,
- Belirli yardımcı/utility kurallarında bilinçli olarak,
- Cascade yapısının özellikle bu davranışı gerektirdiği sınırlı durumlarda kullanılabilir.

Ancak `Stil çalışmadı → !important ekle` alışkanlığı doğru değildir.

Önce: 
```
    Selector doğru mu?
        ↓
    Specificity ne?
        ↓
    Cascade nasıl çalışıyor?
        ↓
    Source order nasıl?
```
kontrol edilmelidir.

## Inline Style ve Specificity
CSS Temelleri bölümünde inline CSS kullanımını görmüştük.

Örneğin:
```
    <p style="color:red;>
        Ürün açıklaması
    </p>
```

Şimdi inline CSS'in başka bir dezavantajını daha anlayabiliriz: `Normal author CSS kurallarına karşı yüksek önceliğe sahip olması.`

Örneğin:
```
    <p 
        id="description"
        style="color:red"
    >
        Ürün açıklaması
    </p>
```

CSS:
```
    #description {
        color:black;
    }
```

Burada normal ID selector yüksek specificity'ye sahip olsa da inline style'daki normal declaration `color:red` normal stylesheet declaration'ına göre daha önceliklidir. Sonuç : `red` olur.

### Inline Style Nasıl Override Edilebilir?
Örneğin:
```
    <p
        id="description"
        style="color:red;">
        Ürün Açıklaması
    </p>
```
ve 
```
    #description{
        color: blaack !important;
    }
```
durumunda author stylesheet içerisindeki important declaration, normal inline declaration'ın önüne geçebilir.

Ancak bu `Inline CSS kullanıp sonra her şeyi !important ile düzeltelim.` anlamına gelmez.

Tam tersine bu örnek inline CSS'in neden büyük projelerde genel stil yönetimi için tercih edilmediğini gösterir.

## Sık Yapılan Hatalar
### 1. "Son Yazılan Her Zaman Kazanır" Sanmak
Yanlış düşünce:
```
    #title {
        color: red;
    }

    .title {
        color: black;
    }
```
*.title aşağıda olduğu için black kazanır.* Bu doğru değildir.

Specificity değerleri:
```
    #title
    0 | 1 | 0 | 0

    .title
    0 | 0 | 1 | 0
```
olduğu için *#title* daha yüksek specificity'ye sahiptir.

Source order yalnızca gerekli eşitlik durumlarında belirleyicidir.

### 2. Her sorunu !important ile çözmeye çalışmak
Örneğin:
```
    .card {
        color:red !important;
    }
```
çalışıyor diye her stil probleminde !important kullanmak uzun vadede CSS'in yönetimini zorlaştırabilir.

Bir stil beklediğimiz gibi uygulanmıyorsa önce aşağıdaki gibi kontrol edilmelidir:
```
    Selector
        ↓
    Cascade
        ↓
    Specificity
        ↓
    Source Order
```

### 3. ID Selector'larını gereksiz yere stil için kullanmak
Örneğin:
```
    #product-card {
        padding: 20px;
    }
```
daha sonra:
```
    .card {
        padding: 30px;
    }
```
ile override edilmeye çalışıldığında specificity farkı sorun oluşturabilir.

Tekrar kullanılabilir component stillerinde:
```
    .product-card {
        padding: 20px;
    }
```
gibi class tabanlı yapılar çoğu zaman daha esnektir.

ID selector kullanmak yanlış değildir. Ancak yüksek specificity nedeniyle genel stil mimarisinde gereksiz kullanımından kaçınmak faydalıdır.

### 4. Specificity'yi Artırmak İçin Gereksiz Uzun Selector Yazmak
Örneğin:
```
    main .products .product-list .product-card .product-info .title {
        color: black;
    }
```
Bu selector çalışabilir. Ancak daha sonra stil değiştirmek için:
```
    .product-card .title {
        color: red;
    }
```
yazıldığında ilk selector'ın specificity'si daha yüksek olduğu için beklenen override gerçekleşmeyebilir.

Bu da geliştiriciyi daha uzun selector yazmaya yönlendirebilir:
```
    main .products .product-list .product-card.special .product-info .title {
        color: red;
    }
```
Böylece CSS giderek zor yönetilen bir hale gelir.

Uygun olduğunda daha basit selector:
```
    .product-title {
        color: black;
    }
```
kullanmak daha sürdürülebilir olabilir.

### 5. Specificity'yi Tek Bir Sayısal Puan Sanmak
Şöyle düşünmek:
```
    ID = 100
    Class = 10
    Element = 1
```
bazı basit örneklerde sonucu tahmin etmeyi sağlayabilir. Ancak specificity'nin gerçek mantığını doğru temsil etmez.

Daha doğru yaklaşım: `ID | Class/Attribute/Pseudo-Class | Element/Pseudo-Element` sütunlarını ayrı ayrı karşılaştırmaktır.

Örneğin: `1 ID` çok sayıda class ekleyerek "geçilecek bir 100 puan" değildir.

### 6. !important ile Specificity'yi Aynı Şey Sanmak
Yanlış: `!important → En yüksek specificity`
Doğru ayrım: 
```
    !important → Importance / Cascade önceliği`

    #id
    .class
    element
        ↓
    Specificity
```
Bunlar cascade'in farklı kavramlarıdır.

## Kısaca Özet
Bir element aynı property için birden fazla CSS declaration'ıyla eşleşebilir.

Örneğin:
```
    p {
        color: gray;
    }

    .text {
        color: black;
    }

    #intro {
        color: red;
    }
```
Tarayıcı hangi declaration'ın kullanılacağını cascade mekanizmasıyla belirler.

Başlangıç seviyesinde temel düşünce:
```
    Birden fazla declaration eşleşiyor
                ↓
        Cascade değerlendirmesi
                ↓
    ┌───────────────────────────┐
    │ 1. Importance / Öncelik  │
    └─────────────┬─────────────┘
                ↓
    ┌───────────────────────────┐
    │ 2. Specificity           │
    └─────────────┬─────────────┘
                ↓
    ┌───────────────────────────┐
    │ 3. Source Order          │
    └─────────────┬─────────────┘
                ↓
        Kullanılacak değer
```

Specificity seviyelerini ise şöyle özetleyebiliriz:
```
    | Yapı | Örnek | Specificity |
    | --- | --- | --- |
    | Element | `p` | `0-0-0-1` |
    | Pseudo-element | `::before` | `0-0-0-1` |
    | Class | `.card` | `0-0-1-0` |
    | Attribute | `[disabled]` | `0-0-1-0` |
    | Pseudo-class | `:hover` | `0-0-1-0` |
    | ID | `#header` | `0-1-0-0` |
    | Inline style | `style=""` | `1-0-0-0` |
```

Temel karşılaştırma:
```
    Normal author CSS bağlamında:

    Inline Style
        ↓
    ID
        ↓
    Class / Attribute / Pseudo-Class
        ↓
    Element / Pseudo-Element
```

Ancak !important bu tablonun bir specificity seviyesi değildir.
```
    !important
    ↓
    Importance

    #id
    .class
    p
    ↓
    Specificity
```

Source order ise:
```
    Önceki cascade koşulları eşit
    +
    Specificity eşit
            ↓
    Daha sonra gelen uygun declaration
```
mantığında devreye girer.

Bu konudan sonra artık şu örneğin neden böyle sonuçlandığını anlayabiliriz:
```
    .card {
        color: black;
    }

    #featured-card {
        color: red;
    }
```

```
    .card
    0 | 0 | 1 | 0

    #featured-card
    0 | 1 | 0 | 0
```
Sonuç:
```
    #featured-card
        ↓
    color: red;
```
Çünkü ID selector daha yüksek specificity'ye sahiptir.

Cascade ve specificity'yi anlamak CSS öğrenirken çok önemlidir. Çünkü ileride:
- Component stilleri,
- Responsive tasarım,
- Framework CSS'leri,
- Utility class'lar,
- Büyük stil dosyaları,
- Override işlemleri

ile çalışırken: `"CSS'i yazdım ama neden uygulanmıyor?"` sorusunun cevabı çoğu zaman cascade mekanizmasını doğru okumaktan geçecektir.