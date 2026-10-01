# CSS Temelleri 
HTML ile bir web sayfasının **yapısını ve içeriğin anlamını** oluşturabiliriz. Ancak sayfanın renkleri, yazı tipleri, boşlukları, boyutları ve genel görsel düzeni gibi özelliklerini yönetmek için CSS kullanırız.

Bu bölümde CSS'in ne olduğunu, frontend geliştirmedeki görevini, HTML'e nasıl dahil edildiğini ve temel CSS sözdimini inceleyeceğiz.

CSS Temelleri
│
├── 1. CSS Nedir?
├── 2. Frontend Geliştirmede CSS'in Yeri
├── 3. CSS'i HTML'e Dahil Etme
│   ├── External CSS
│   ├── Internal CSS
│   └── Inline CSS
│
├── 4. CSS Sözdizimi
│   ├── Rule
│   ├── Selector
│   ├── Declaration
│   ├── Property
│   └── Value
│
├── 5. CSS Yorum Satırları
├── 6. Sık Yapılan Hatalar
└── 7. Kısaca

## Css Nedir?
Css 'in açılımı **Cascading Style Sheets (Basamaklı Stil Sayfaları)'dır.**  CSS, HTML ile oluşturulan içeriğin **görsel sunumunu ve düzenini** kontrol etmek için kullanılan bir stil dilidir.

Örneğin HTML ile aşağıdaki şekilde bir içerik oluşturabiliriz.
```
    <h1>Ürünlerimiz</h1>
    <p>Yeni sezon ürünlerimizi keşfedin</p>
```

Css ile bu içeriğin görünümünü değiştirebiliriz:
```
    h1{
        color:darkgreen;
        font-size:40px;
    }

    p{
        color:gray;
    }
```

Burada HTML `Bu bir başlık, bu da bir paragraf.` bilgisini verir. CSS ise `Başlık şu renkte ve boyutta, paragraf ise şu renkte görünsün` bilgisiini verir.

Temel ayrım:
```
    HTML → İçeriğin yapısı ve anlamı
    CSS → İçeriğin görsel sunumu
```

### CSS ile Neler Yapılabilir?
CSS ile bir web sayfasının birçok görsel özelliğini kontrol edebiliriz. Örneğin:
- Renkler,
- Yazı tipleri,
- Yazı boyutları,
- Genişlik ve yükseklikler,
- Boşluklar,
- Kenarlıklar,
- Arka planlar,
- Elementlerin sayfadaki konumları,
- Sayfa düzenleri,
- Responsive tasarım,
- Geçişler ve animasyonlar

Bunlar CSS ile yönetilebilir maddelerdir.

Örneğin:
```
    button {
        background-color: black;
        color: white;
        padding: 12px 24px;
        border-radius: 8px;
    }
```

HTML'deki butonun yapısı değişmez: `<button>Sepete Ekle</button>` Ancak görsel sunumu CSS tarafından değiştirilir.

### Seperation of Concerns
Web geliştirmeden önemli yaklaşımlardan biri **Seperation of Concerns** yani sorumlulukların ayrılmasıdır. Temel fikir: `Farklı görevleri mümkün olduğunca kendi sorumluluk alanlarında yönetmek.

HTML'in görevi: `Yapı + İçeriğin anlamı`
CSS'in görevi: `Görsel sunum + Düzen`
JavaScript'in temel görevi ise: `Davranış + Etkileşim` olarak düşünülebilir.

Örneğin:
```
    <button class="add-to-cart">
        Sepete Ekle
    </button>
```
HTML butonun ne olduğunu tanımlar.

CSS, butonun görünümünü belirler:
```
    .add-to-cart{
        background-color:black;
        color:white;
    }
```

JavaScript ise gerektiğinde butonla gerçekleşen etkileşimi yönetebilir:
```
    button.addEventListener("click", function(){
        console.log("Ürün sepete eklendi.");
    });
```

Bu ayrım kodun:
- Daha okunabilir,
- Daha düzenli,
- Daha kolay değiştirilebilir,
- Daha kolay bakım yapılabilir olmasına yardımcı olur.

## Frontend Geliştirmede CSS'in Yeri
HTML temellerinde ftontend tarafındaki üç temel teknolojiyi görmüştük:
```
    Frontend
    │
    ├── HTML
    │   └── Yapı ve anlam
    │
    ├── CSS
    │   └── Görsel sunum ve düzen
    │
    └── JavaScript
        └── Davranış ve etkileşim
```

Burada aynı konuyu tekrar detaylandırmak yerine CSS açısından düşünelim.

HTML ile ürün kartının yapısını oluşturabiliriz:
```
    <article class="product-card">

        <h2>Kol Saati</h2>

        <p>12.500 TL</p>

        <button>Sepete Ekle</button>

    </article>
```

CSS ile bu yapının görssel sunumunu değiştirebiliriz.
```
    .product-card {
        padding: 24px;
        border: 1px solid #ddd;
        border-radius: 12px;
    }
```

JavaScript ise gerektiğinde kart üzerindeki etkileşimleri yönetebilir. Dolayısıyla CSS'in temel sorusu: `Bu içerik nasıl sunulmalı?` şeklindedir.

## CSS'i HTML'e Dahil Etme Yöntemleri
Tarayıcının yazdığımız CSS kurallarını HTML belgesine uygulayabilmesi için CSS'i belgeyle ilişkilendirmemiz gerekir.

CSS üç temel yöntemle kullanılabilir:
```
    CSS Kullanımı
    │
    ├── External CSS
    ├── Internal CSS
    └── Inline CSS
```

Bu yöntemlerin hepsi geçerlidir ancak kullanım amaçları ve sürdürülebilirlikleri farklıdır.

### 1.External CSS
External CSS, CSS kodlarının HTML dosyasından ayrı bir .css dosyasında tutulmasıdır.

Örneğin proje yapımız şu şekilde olabilir:
```
    project/
    │
    ├── index.html
    └── style.css
```

**style.css**
```
    body {
        background-color: white;
    }

    h1 {
        color: darkgreen;
    }
```

CSS dosyasını HTML belgesine `<link>` elementiyle bağlarız:
```
    <head>
        <link
            rel="stylesheet"
            href="style.css"
        >
    </head>
```

Buradaki `rel="stylesheet"` bağlanan kaynağın bir stil sayfası olduğunu belirtir. `href="style.css"` ise CSS dosyasının konumunu belirtir.

### External CSS'in Avantajları
External CSS gerçek projelerde en yaygın kullanılan yaklaşımdır.
- **HTML ve CSS Ayrı Tutulur**
Bu ayrım kodun daha düzenli olmasını sağlar.
```
    index.html → Yapı
    style.css → Görsel stil
```

- **Aynı CSS Birden Fazla Sayfada Kullanılabilir**
Örneğin:
```
    index.html ────┐
                │
    products.html ─┼──→ style.css
                │
    contact.html ──┘
```
birden fazla HTML belgesi aynı stil dosyasını kullanabilir. Böylece aynı CSS kodlarını her sayfada tekrar yazmamız gerekmez.

- **Bakım Kolaylaşır**

Örneğin bütün sayfalardaki ana rengimizi değiştirmek istiyorsak ilgili CSS dosyasında değişiklik yapmak yeterli olabilir. Bu nedenle external CSS:
- Tekrar kullanılabilirlik,
- Kod organizasyonu,
- Bakım kolaylığı açısından avantajlıdır.

### 2. Internal CSS
CSS Kodları HTML belgesinin `<head>` bölümündeki `<style>` elementi içerisinde de yazılabilir.

Örneğin:
```
    <!DOCTYPE html>
    <html lang="tr">
    <head>
        <meta charset="UTF-8">
        <title>CSS Örneği</title>
        <style>
            h1 {
                color: darkgreen;
            }
            p {
                color: gray;
            }
        </style>
    </head>

    <body>
        <h1>CSS Öğreniyorum</h1>
        <p>İlk CSS kurallarımı yazıyorum.</p>
    </body>

    </html>
```

Bu yönteme **Internal CSS** denir. CSS ayrı bir dosyada değildir. HTML belgesinin içerisinde bulunur.
```
    HTML Dosyası
    │
    ├── head
    │   └── style
    │       └── CSS
    │
    └── body
        └── HTML içeriği
```

### Internal CSS Ne Zaman Kullanılabilir?
Internal CSS:
- Küçük örneklerde,
- Eğitim çalışmalarında,
- Tek bir sayfaya özgü basit stillerde kullanılabilir.

Ancak proje büyüdükçe bütün CSS'i HTML dosyasının içerisinde tutmak kod organizasyonunu zorlaştırabilir. Bu nedenle daha büyük ve çok sayfalı projelerde genellikle external CSS tercih edilir.

### 3. Inline CSS
CSS doğrudan HTML elementinin **style attribute'u** içerisinde de yazılabilir.

Örneğin:
```
    <h1 style="color:darkgreen;">
        CSS Öğreniyorum
    </h1>
```
Bu yönteme **Inline CSS** denir.

Başka bir örnek:
```
    <button style="background-color: black; color: white;">
        Sepete Ekle
    </button>
```

Buradaki CSS yalnızca ilgili element üzerinde doğrudan tanımlanmıştır.

### Inline CSS Neden Genellikle Tercih Edilmez?
Şöyle bir yapı düşünelim:
```
    <h2 style="color: darkgreen;">Ürünler</h2>

    <h2 style="color: darkgreen;">Kategoriler</h2>

    <h2 style="color: darkgreen;">Kampanyalar</h2>
```

Aynı stil tekrar tekrar yazılmıştır. Rengi değiştirmek istediğimizde her elementi ayrı ayrı düzenlememiz gerekebilir. External CSS kullanırsak:
```
    .section-title {
        color: darkgreen;
    }
```
ve:
```
    <h2 class="section-title">Ürünler</h2>

    <h2 class="section-title">Kategoriler</h2>

    <h2 class="section-title">Kampanyalar</h2>
```
şeklinde daha tekrar kullanılabilir bir yapı oluşturabiliriz.

Bu nedenle inline CSS:
- Tekrarı artırabilir,
- HTML ile görsel stil sorumluluğunu karıştırabilir,
- Bakımı zorlaştırabilir.

Inline CSS geçersiz veya yasak değildir; fakat genel proje stillerini yönetmek için çoğunlukla iyi bir tercih değildir.

### External, Internal ve Inline CSS Karşılaştırması
|Yöntem     |Nerede Yazılır?                        |Genel Kullanım
|-----------|---------------------------------------|-----------
|External   |Ayrı .css dosyasında                   |Gerçek projelerde temel    |
|Internal   |HTML içindeki `<style>` elementinde    |Küçük veya sayfaya özgü örnekler   |
|Inline     |Elementin style attribute'unda         |Sınırlı ve özel durumlar   |

Genel proje yapısında: `External Css → En sürdürülebilir temel yaklaşım` olarak düşünülebilir.

## CSS Sözdizimi - Syntax
Temel bir CSS kuralı şu şekilde yazılır:
```
    p{
        color:red;
    }
```

Bu küçük örneğin içerisinde CSS'in temel kavramlarının neredeyse tamamı bulunur.
```
    p {
        color: red;
    }
    │     │     │
    │     │     └── Value
    │     │
    │     └── Property
    │
    └── Selector
```
Bütün yapı ise `CSS Rule` oluşturur.

### 1. Rule — CSS Kuralı
Bir CSS kuralı genel olarak:
```
    selector {
        property: value;
    }
```
şeklindedir.

Örneğin:
```
    p {
        color: blue;
    }
```
Burada:
```
    CSS Rule
    │
    ├── Selector
    │   └── p
    │
    └── Declaration Block
        │
        └── Declaration
            ├── Property → color
            └── Value    → blue
```
şeklinde bir yapı bulunur.

### 2. Selector — Seçici
Selector, CSS kuralının **hangi element veya elementlere uygulanacağını** belirler.

Örneğin:
```
    p {
        color: blue;
    }
```
buradaki `p` selector'dır. Tarayıcıya `p elementlerini hedefle.`
der.

Başka bir örnek:
```
button {
    background-color: black;
}
```
burada hedef `<button>` elementleridir.

CSS'te:
- Element selector,
- Class selector,
- ID selector,
- Attribute selector,
- Combinator'lar,
- Pseudo-class'lar,
- Pseudo-element'ler

gibi çok daha gelişmiş seçici yapıları bulunur.

Burada bilmemiz gereken: `Selector, CSS kuralının hangi HTML öğelerini hedeflediğini belirler.`

### 3. Declaration Block
Selector'dan sonra süslü parantezler içerisinde CSS bildirimleri bulunur:
```
    p {

        color: blue;

        font-size: 18px;

    }
```
Şu bölüm:
```
    {
        color: blue;
        font-size: 18px;
    }
```
***declaration block** olarak adlandırılır.

Bir declaration block içerisinde bir veya birden fazla declaration bulunabilir.

### 4. Declaration — Bildirim
Her `property: value;` ifadesi bir **declaration**, yani bildirimdir.

Örneğin: `color: blue;` bir declaration'dır.

Birden fazla declaration:
```
    p {
        color: blue;
        font-size: 18px;
        line-height: 1.5;
    }
```
şeklinde yazılabilir.

Her declaration genellikle:
```
    Property
    ↓
    :
    ↓
    Value
    ↓
    ;
```
yapısına sahiptir.

### 5. Property - Özellik
Property, elementin **hangi özelliğinin değiştirileceğini** belirtir.
Örneğin: `color:red;` buradaki `color` **property**'dir. Tarayıcıya `Metin rengini değiştirmek istiyorum.` der.

Başka property örnekleri:
```
    font-size: 20px;
    background-color: black;
    width: 300px;
    padding: 16px;
```
Önemli olan property'nin görevidir: `Neyi değiştireceğiz?`

### 6.Value - Değer
Value, property'nin **hangi değeri alacağını** belirtir.
Örneğin; `color:red` buradaki **value**'dır.

Başka bir örnek de ise; `font-size:20px;`
Burada şu şekilde düşünebiliriz:
```
    font-size → Property → Neyi değiştireceğiz?
    20px → Value → Nasıl / hangi değerle değiştireceğiz?
```

### Bir CSS Kuralını Parçalayalım
Örneğin:
```
    button {
        background-color: black;
        color: white;
        padding: 12px;
    }
```
yapısını inceleyelim.

```
    button → Selector

    {
        background-color: black;
        color: white;
        padding: 12px;
    }
    ↓
    Declaration Block
```

Declaration'lar:
```
    background-color: black;
    │                 │
    Property          Value


    color: white;
    │      │
    Property Value


    padding: 12px;
    │        │
    Property Value
```

Bütün yapı aşağıdaki şekildedir:
```
    CSS Rule
    │
    ├── Selector
    │
    └── Declaration Block
        │
        ├── Declaration
        │   ├── Property
        │   └── Value
        │
        ├── Declaration
        │   ├── Property
        │   └── Value
        │
        └── Declaration
            ├── Property
            └── Value
```
Bu yapı CSS'in temelini oluşturur.

## CSS Yorum Satırları - Comments
Css kodunun içerisinde açıklama bırakmak için yorum satırları kullanılabilir. CSS yorum sözdizimi `/*Bu bir CSS yorumudur.*/` şeklindedir.

Örneğin:
```
    /* Header stilleri */

    header {
        padding: 20px;
    }
```

Birden fazla satır da yorum içerisinde bulunabilir:
```
    /*
        Ürün kartı
        temel görünüm ayarları
    */

    .product-card {
        padding: 20px;
    }
```

### HTML ve CSS Yorumları Aynı Değildir
HTML'de `<!-- HTML yorumu -->` kullanmıştık.

CSS'te ise: `/* CSS yorumu */` kullanılır.

Yani bu şekilde farklı sözdizimleri vardır.
```
    HTML → <!-- -->
    CSS  → /* */
```

### CSS Yorumları Ne İçin Kullanılır?
Yorumlar:
- Kod hakkında açıklama bırakmak,
- Stil dosyasındaki bölümleri ayırmak,
- Başka geliştiricilere kısa bilgi vermek için kullanılabilir.

Örneğin:
```
    /* Navigation */
    nav {
        padding: 16px;
    }


    /* Product Cards */
    .product-card {
        border: 1px solid #ddd;
    }
```

### Kodu Geçici Olarak Devre Dışı Bırakmak
Geliştirme sırasında bir declaration'ı geçici olarak test dışı bırakmak için de yorum kullanılabilir:
```
    button {
        background-color: black;

        /* color: white; */

        padding: 12px;
    }
```
Ancak uzun süre kullanılmayacak eski kodları yorum olarak projede biriktirmek yerine sürüm kontrol sistemlerinden yararlanmak genellikle daha temiz bir yaklaşımdır.

## Sık Yapılan Hatalar
CSS öğrenirken bazı sözdizimi ve kullanım hataları sık görülür.
### 1. : İşaretini Unutmak
Yanlış:
```
    p {
        color red;
    }
```

Doğru:
```
    p {
        color: red;
    }
```

Property ile value arasına : yazılır.

### 2. Declaration Sonundaki ; İşaretini Unutmak
Örneğin:
```
    p {
        color: red
        font-size: 18px;
    }
```
burada ilk declaration doğru şekilde sonlandırılmadığı için sonraki bölümün yorumlanması bozulabilir.

Doğru:
```
    p {
        color: red;
        font-size: 18px;
    }
```
Son declaration'da noktalı virgül bazı durumlarda teknik olarak zorunlu olmasa da:
```
    p {
        color: red;
    }
```
şeklinde her declaration sonunda ; kullanmak daha tutarlı ve hata riskini azaltan bir alışkanlıktır.

### 3. Süslü Parantezleri Unutmak
Yanlış:
```
    p
        color: red;
```
Doğru:
```
    p {
        color: red;
    }
```
Declaration block { } içerisinde bulunmalıdır.

### 4. Property ve Value'yu Karıştırmak
Yanlış mantık:
```
    red → property
    color → value
```
Doğrusu: `color: red;` yani:
```
    color → Property
    red → Value
```

## CSS Dosyasını HTML'e Yanlış Bağlamak
Örneğin dosya yapısı:
```
    project/
    │
    ├── index.html
    └── css/
        └── style.css
```
ise `<link rel="stylesheet" href="style.css">` yanlış yolu gösterebilir.

Doğru yol `<link rel="stylesheet" href="css/style.css">` olmalıdır.

CSS dosyası yüklenmiyorsa ilk kontrol edilmesi gereken yerlerden biri dosya yoludur.

## Inline CSS'i Her Yerde Kullanmak
Şu yapı küçük bir örnekte çalışabilir:
```
    <p style="color: red;">
        Merhaba
    </p>
```
Ancak bütün projeyi:
```
    <h1 style="...">...</h1>
    <p style="...">...</p>
    <button style="...">...</button>
```
şeklinde oluşturmak bakım ve tekrar kullanılabilirlik açısından sorun oluşturabilir.

Genel stiller için external CSS daha uygun bir temel yaklaşımdır.

## Selector ile `{` Arasında Boşluk Olmamasını Hata Sanmak
Şu kullanım:
```
    p{
        color: red;
    }
```
geçerli CSS'tir. Ancak:
```
    p {
        color: red;
    }
```
şeklindeki yazım daha okunaklıdır ve yaygın kodlama stilidir.

Dolayısıyla `p{` bir CSS syntax hatası değil, daha çok kod biçimlendirme ve okunabilirlik konusudur.

## Kısaca Özet
**CSS (Cascading Style Sheets)** anlamına gelir. Web sayfasındaki temel görev dağılımını:
```
    HTML → Yapı ve anlam
    CSS → Görsel sunum ve düzen
    JavaScript → Davranış ve etkileşim
```
şeklinde düşünebiliriz.

CSS'i HTML'e üç temel yöntemle dahil edebiliriz:

|Yöntem         |Konum          |Genel Yaklaşım     |
|---------------|---------------|-------------------|
|External CSS   |Ayrı .css dosyası |Projelerde temel tercih|
|Internal CSS   |`<style>` içerisinde|Küçük/sayfaya özgü kullanım|
|Inline CSS     |style="" içerisinde |Sınırlı özel durumlar 

Temel bir CSS kuralı:
```
    p {
        color: red;
    }
```
şeklindedir.

Yapısını ise:
```
    CSS Rule
    │
    ├── Selector
    │   └── p
    │
    └── Declaration Block
        │
        └── Declaration
            │
            ├── Property
            │   └── color
            │
            └── Value
                └── red
```
şeklinde düşünebiliriz.

En temel sözdizimi:
```
    selector {
        property: value;
    }
```
şeklindedir.

CSS öğrenirken bu yapıyı iyi anlamak önemlidir. Çünkü ilerleyen konularda öğreneceğimiz:
- Selectors,
- Cascade,
- Specificity,
- Inheritance,
- Box Model,
- Typography,
- Layout,
-Flexbox,
- Grid,
- Responsive Design gibi konuların tamamı bu temel CSS yapısının üzerine kurulacaktır.