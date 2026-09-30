# HTML Temelleri
HTML öğrenmeye başlarken yalnızca etiketleri ezberlemek yeterli değildir. Öncelikle HTML'in **ne olduğunu, ne işe yaradığını, bir web sayfasındaki rolünü ve tarayıcının HTML belgesini nasıl yorumladığını** anlamak gerekir.

Bu bölümde HTML'in en temel yapı taşlarını ele alacağız:
```
    HTML Temelleri
    │
    ├── 1. Introduction
    │   ├── Markup dili nedir?
    │   └── Frontend geliştirmede HTML'in yeri
    │
    ├── HTML'e CSS ve JavaScript Eklemek
    │
    ├── HTML'in Sınırlılıkları
    │
    ├── Web Nasıl Çalışır?
    │
    ├── Tarayıcı HTML'i Nasıl Okur?
    │
    ├── 2. Your First HTML File
    │   ├── Element, etiket ve attribute
    │   ├── Case Insensitivity
    │   ├── HTML Entities
    │   ├── Comments
    │   └── Whitespaces
    │
    ├── 3. Basic Tags
    │   ├── <!DOCTYPE html>
    │   ├── <html>
    │   ├── <head>
    │   ├── <meta>
    │   └── <body>
    │
    └── 4. İlk HTML Dosyamız
```

## Markup Dili Nedir?
HTML'in açılımı `HyperText Markup Language` yani `Hiper Metin İşaretleme Dili`'dir. Buradaki iki kavram özellikle önemlidir:
```
    HyperText + Markup
```

### HyperText

HyperText, belgelerin bağlantılar aracılığıyla birbirleriyle ilişkilendirilebilmesini ifade eder.

Örneğin, `<a href="about.html">Hakkımızda</a>` ile bir HTML belgesinden başka bir belgeye geçilebilir.

Web'in birbirine bağlı sayfalardan oluşmasının temelinde bu yaklaşım bulunur.

### Markup
Markup ise içeriğin ne olduğunu işaretlemek anlamına gelir.

Örneğin, `<h1>HTML Öğreniyorum</h1>` yazdığımızda yalnızca `HTML Öğreniyorum` metnini yazmış olmayız.

Tarayıcıya bu metnin, `Sayfanın bir başlığıdır.` bilgisini de vermiş oluruz.

Benzer şekilde:

`<p>HTML öğrenmeye başladım.</p>` bu içeriğin bir paragraf olduğunu belirtir.

**HTML'in temel görevi budur: İçeriğin yapısını ve anlamını tanımlamak.**

### HTML Bir Programlama Dili midir?
HTML bir programlama dili değildir. Çünkü HTML kendi başına:
- Koşul çalıştırmaz,
- Döngü oluşturmaz,
- Fonksiyon tanımlamaz,
- Algoritma çalıştırmaz,
- Programlama mantığı yürütmez.

Örneğin JavaScript'te:
```
    if (age >= 18) {
        console.log("Giriş yapabilirsiniz.");
    }
```
gibi bir koşul oluşturabiliriz.

HTML'de ise:
```
    <h1>Ürünler</h1>
    <p>Ürünlerimizi inceleyebilirsiniz.</p>
```
şeklinde içeriğin yapısını tanımlarız.

Temel ayrım:
```
    HTML
    ↓
    İçerik nedir?
    Yapısı nedir?

    Programlama Dili
    ↓
    Ne yapılmalı?
    Hangi işlem gerçekleştirilmeli?
```

### Başka Markup Dilleri Var mı?
HTML tek markup dili değildir. Örneğin:
```
    HTML
    XML
    Markdown
```
işaretleme dillerine örnek olarak verilebilir.

Hatta şu anda hazırladığımız dokümantasyon dosyalarında kullandığımız Markdown da buna güzel bir örnektir.

Markdown'da:
```
    # HTML
    ## HTML Temelleri
```
yazdığımızda # işaretleri metnin başlık olduğunu belirtir.

HTML'de ise:
```
    <h1>HTML</h1>
    <h2>HTML Temelleri</h2>
```
kullanırız.

Her iki durumda da içeriğin yapısı işaretlenmektedir.

## Frontend Geliştirmede HTML'in Yeri
Bir web sayfasının frontend tarafını temel seviyede üç katman üzerinden düşünebiliriz:
```
    Frontend
    │
    ├── HTML
    │   └── Yapı ve içerik
    │
    ├── CSS
    │   └── Görünüm ve tasarım
    │
    └── JavaScript
        └── Davranış ve etkileşim
```
### HTML → Yapı
HTML sayfada **ne olduğunu** belirtir.
```
    <button>Sepete Ekle</button>
```
Burada bir buton oluşturduk.

### CSS → Görünüm
CSS bu butonun nasıl görüneceğini belirleyebilir.
```
    button {
        background: black;
        color: white;
        padding: 12px 24px;
    }
```

### JavaScript → Davranış
JavaScript ise kullanıcı butona bastığında ne olacağını belirleyebilir.
```
    button.addEventListener("click", function () {
        console.log("Ürün sepete eklendi.");
    });
```
Dolayısıyla aynı buton üzerinde aşağıdaki ayrım bulunur:
```
    HTML → Bu bir buton.
    CSS → Buton böyle görünsün.
    JavaScript → Butona basıldığında bunu yap.
```

Bunu basit bir benzetmeyle de düşünebiliriz:
```
    HTML → İskelet
    CSS → Görünüm / kıyafet
    JavaScript → Hareket / davranış
```
Bu benzetme kavramları ayırmak için kullanışlıdır ancak HTML yalnızca "iskelet" değildir. **HTML aynı zamanda içeriğin anlamını da tanımlar.**

Örneğin, `<nav>` bu alanın navigasyon olduğunu, `<main>` sayfanın ana içeriği olduğunu, `<article>` bağımsız bir içerik olduğunu ifade edebilir.

Bu konu ilerleyen bölümlerde Semantic HTML başlığı altında daha ayrıntılı incelenecektir.

## HTML'e CSS ve JavaScript Eklemek
CSS ve JavaScript'in görevlerini bildiğimize göre bunların bir HTML belgesine nasıl dahil edildiğine de kısaca bakalım.

### CSS Eklemenin Üç Yolu
**1. External CSS — Harici Dosya**

CSS kuralları ayrı bir `.css` dosyasında tutulur ve `<head>` içerisinde `<link>` ile bağlanır.
```
    <head>
        <link rel="stylesheet" href="style.css">
    </head>
```
Bu yöntem büyük projelerde en çok tercih edilen yaklaşımdır. Çünkü stil kodu HTML'den ayrı tutulur ve birden fazla sayfa aynı CSS dosyasını paylaşabilir.

**2. Internal CSS — Belge İçi Stil**

CSS kuralları `<head>` içerisinde `<style>` etiketiyle doğrudan belgeye yazılabilir.
```
    <head>
        <style>
            body {
                font-family: sans-serif;
            }

            h1 {
                color: darkblue;
            }
        </style>
    </head>
```
Genellikle tek bir sayfaya özel, küçük çaplı stiller için kullanılabilir.

**3. Inline CSS — Element Üzerinde Stil**

CSS, doğrudan elementin `style` attribute'u içerisine yazılabilir.
```
    <p style="color: red; font-weight: bold;">
        Bu metin kırmızı ve kalın görünür.
    </p>
```
Bu yöntem hızlı görünse de genellikle tercih edilmez. Çünkü stil ile içerik birbirine karışır ve stilin tekrar kullanılması veya sonradan yönetilmesi zorlaşır.

Temel öncelik sırası:
```
    External CSS  → Genel ve tekrar kullanılabilir yaklaşım
    Internal CSS  → Sayfaya özel küçük stiller
    Inline CSS    → Mümkünse kaçınılması gereken yöntem
```

### JavaScript Eklemenin Yolları
JavaScript de HTML belgesine benzer şekilde iki temel yöntemle eklenebilir.

**1. Harici Dosya — `<script src="...">`**
```
    <body>
        ...

        <script src="app.js"></script>
    </body>
```
JavaScript kodu ayrı bir `.js` dosyasında tutulur ve `<script>` etiketinin `src` attribute'uyla bağlanır.

**2. Belge İçi Script**
```
    <script>
        console.log("Sayfa yüklendi.");
    </script>
```
Kod doğrudan `<script>` etiketinin içerisine yazılabilir.

**`<script>` Nereye Yazılmalı?**

`<script>` etiketi genellikle `</body>` kapanış etiketinden hemen önce yazılır.
```
    <body>

        <h1>Ürünler</h1>
        <p>Yeni sezon ürünleri</p>

        <script src="app.js"></script>

    </body>
```
Böylece tarayıcı önce sayfanın HTML içeriğini oluşturur, JavaScript ise sayfa içeriği hazır olduktan sonra çalışır. `<head>` içerisine yazılan bir script bu davranışı `defer` veya `async` gibi attribute'lar olmadan bozabilir; bu attribute'lar ayrı bir JavaScript konusunda ele alınacaktır.

## HTML'in Sınırlılıkları
HTML güçlü bir yapılandırma dilidir ancak tek başına her ihtiyacı karşılamaz. Örneğin HTML ile:
```
    Bir butona basıldığında ne olacağı belirlenemez.
    Sayfanın görsel düzeni ayrıntılı olarak tasarlanamaz.
    Kullanıcı girdisine göre veri işlenemez.
    Sunucudan veri çekilemez.
```
Bu sınırlılıklar HTML'in eksikliği değil, **görev dağılımının bir sonucudur.**
```
    HTML  → Yapı ve anlam
    CSS   → Görsel sunum
    JS    → Davranış ve mantık
```
Bu nedenle gerçek bir web sayfası genellikle üçünün birlikte kullanılmasıyla ortaya çıkar. HTML'i tek başına yeterli görüp CSS veya JavaScript'in yapması gereken işi HTML'e yüklemeye çalışmak (örneğin boşluk için `<br>` tekrarlamak, tıklama için `<div onclick>` kullanmak) daha önce gördüğümüz sık yapılan hatalara da zemin hazırlar.

## Web Nasıl Çalışır?
HTML öğrenirken:
- Tarayıcı,
- HTTP,
- Domain,
- DNS,
- Hosting,
- SEO gibi kavramlarla da karşılaşırız.

Ancak bunlar HTML sözdiziminin kendisinden daha geniş web kavramlarıdır. Bu nedenle burada tekrar edilmeyecek, ilgili notlarda incelenecektir:
```
    Tarayıcı → 01_TemelKonular/TarayıcıKavramları.md
    HTTP     → 01_TemelKonular/HttpNedir.md
    Domain   → 01_TemelKonular/DomainName.md
    Hosting  → 01_TemelKonular/HostingNedir.md
    DNS      → Domain ve Hosting notlarının içerisinde
    SEO      → 04_HTML/15_HTMLMetadataTemelSEO.md
```

## Tarayıcı HTML'i Nasıl Okur?
Tarayıcı bir HTML dosyasını açtığında kodu olduğu gibi ekrana yazmaz. Önce HTML kodunu okur (**parse eder**) ve bu koddan bellekte bir ağaç yapısı oluşturur. Bu yapıya **DOM (Document Object Model)** denir.

Örneğin:
```
    <html>
        <body>
            <h1>Ürünler</h1>
            <p>Yeni sezon ürünleri</p>
        </body>
    </html>
```
tarayıcı tarafından şu şekilde bir ağaç olarak düşünülür:
```
    html
    │
    └── body
        │
        ├── h1
        │   └── "Ürünler"
        │
        └── p
            └── "Yeni sezon ürünleri"
```
Kullanıcının ekranda gördüğü sayfa bu ağacın üzerine CSS kurallarının uygulanmasıyla oluşturulur. JavaScript de sayfayı değiştirirken doğrudan bu DOM ağacı üzerinde çalışır.

Temel akış:
```
    HTML kodu
    ↓
    Tarayıcı kodu okur (parse)
    ↓
    DOM ağacı oluşur
    ↓
    CSS uygulanır
    ↓
    Sayfa ekrana çizilir
```

**- Tarayıcı Hataları Tolere Eder**

Tarayıcılar HTML'deki birçok hatada sayfayı tamamen bozmak yerine hatayı kendi kurallarına göre düzeltmeye çalışır. Örneğin kapanış etiketi unutulmuş bir paragrafı yine de paragraf olarak gösterebilir.

Ancak bu, hatalı HTML yazılabileceği anlamına gelmez. Tarayıcının yaptığı düzeltme bizim beklediğimiz yapıyla aynı olmayabilir. Bu da beklenmeyen görünüm, erişilebilirlik ve JavaScript sorunlarına yol açabilir.

**Bu nedenle HTML'i tarayıcının düzeltmesine bırakmak yerine baştan doğru yazmak gerekir.**

## Your First HTML File
HTML'in ne işe yaradığını bildiğimize göre artık HTML kodunun nasıl oluşturulduğunu inceleyebiliriz. Öncelikle üç kavramı birbirinden ayırmamız gerekir:
- Element
- Tag
- Attribute

Bunlar birbirleriyle ilişkili olsa da aynı şey değildir.

### Etiket — Tag
HTML'de `<p>` bir açılış etiketidir. `</p>` ise kapanış etiketidir.

Etiketler `<` ve `>` karakterleri arasında yazılır.

### Element
Şu yapının tamamı `<p>HTML öğreniyorum.</p>` bir HTML elementidir.

Yapıyı parçalarsak:
```
    <p> HTML öğreniyorum. </p>
    ↑          ↑           ↑
    Açılış     İçerik     Kapanış
    etiketi               etiketi
```
Dolayısıyla *tag* ve *element* aynı şey değildir.
```
    Tag → <p>
    Tag, elementin sözdizimindeki bir parçadır.

    Element → <p>HTML öğreniyorum.</p>
    Element ise bütün yapıyı ifade eder.
```
### Attribute Nedir?
Attribute'lar elementler hakkında ek bilgi veya yapılandırma sağlar.

Örneğin: `<a href="https://example.com">Siteye Git</a>`

Burada:
```
    a → Element türü
    href → Attribute
    https://example.com → Attribute değeri
```

Attribute'lar genellikle açılış etiketi içerisinde, `attribute="değer"` şeklinde yazılır.

**- Tırnak Kullanımı**

Attribute değerleri çift veya tek tırnak içerisinde yazılabilir:
```
    <a href="about.html">Hakkımızda</a>
    <a href='about.html'>Hakkımızda</a>
```
Her iki kullanım da geçerlidir. Ancak çift tırnak daha yaygın bir standarttır.

Bazı durumlarda tırnaksız yazım da çalışabilir:
```
    <input type=text>
```
Fakat değer boşluk veya bazı özel karakterler içerdiğinde tırnaksız yazım hataya yol açar:
```
    Yanlış:
    <img src=photo.jpg alt=Siyah kol saati>

    Burada alt değeri yalnızca "Siyah" olarak algılanır.
    "kol" ve "saati" ayrı attribute'lar gibi okunur.

    Doğru:
    <img src="photo.jpg" alt="Siyah kol saati">
```
Bu nedenle **attribute değerlerini her zaman tırnak içerisinde yazmak** en güvenli alışkanlıktır.

Başka bir örnek:
```
    <img
        src="product.jpg"
        alt="Siyah kol saati"
    >
```
Burada:
```
    src → Görsel kaynağı
    alt → Görsel için alternatif metin
```

Attribute'ların kullanımını ilerleyen bölümde **Global Attributes** başlığı altında daha ayrıntılı inceleyeceğiz.

### Boolean Attribute
Bazı attribute'lar bir değerden çok özelliğin **var olup olmadığını** ifade eder.

Örneğin, `<input type="text" disabled>`

Buradaki ***disabled*** bir boolean attribute örneğidir.

**- Dikkat: `disabled="false"` Alanı Aktif Yapmaz**

Boolean attribute'larda önemli olan attribute'un **değeri değil, elementte bulunup bulunmadığıdır.**
```
    <input disabled>             → Devre dışı
    <input disabled="disabled">  → Devre dışı
    <input disabled="">          → Devre dışı
    <input disabled="false">     → Yine devre dışı!
    <input>                      → Aktif
```
Yani bir alanı aktif hale getirmek için `disabled="false"` yazmak işe yaramaz. **Attribute'un elementten tamamen kaldırılması gerekir.**

### Void Element Nedir?
Her HTML elementinin kapanış etiketi bulunmaz.

Örneğin:
```
    <img src="photo.jpg" alt="Manzara">
    <br>
    <input type="text">
    <meta charset="UTF-8">
```
gibi bazı elementler void element olarak tanımlanır.

Bunların, `</img>` veya `</input>` şeklinde kapanış etiketleri bulunmaz. Dolayısıyla `<img src="photo.jpg" alt="Manzara">` doğru kullanımdır.

HTML'deki void elementleri; **İçerisinde child/content barındırmayan ve kapanış etiketi bulunmayan elementler** olarak düşünebiliriz.

**- `<br>` mi `<br />` mi?**

Kod örneklerinde bazen void elementlerin sonunda `/` karakteri görürüz:
```
    <br>
    <br />

    <img src="photo.jpg" alt="Manzara">
    <img src="photo.jpg" alt="Manzara" />
```
HTML'de her iki yazım da geçerlidir. Sondaki `/` karakterinin HTML açısından **hiçbir anlamı yoktur**; tarayıcı onu yok sayar. Bu yazım eski **XHTML** döneminden kalan bir alışkanlıktır.

Ancak **JSX** (React / Next.js) tarafında durum farklıdır. JSX'te void elementlerin `/` ile kapatılması **zorunludur:**
```
    HTML  → <br> veya <br />   (ikisi de geçerli)
    JSX   → <br />             (zorunlu)
```
Dolayısıyla `<br />` yazımını görmek o elementin farklı bir element olduğu anlamına gelmez; yalnızca farklı bir yazım alışkanlığıdır.

**Not:** Void olmayan elementlerde `/` ile kapatma HTML'de işe yaramaz. Örneğin `<div />` yazmak div'i kapatmaz; tarayıcı bunu yalnızca açılış etiketi `<div>` olarak algılar.

### İç İçe Elementler — Nesting
HTML elementleri başka elementlerin içerisinde bulunabilir.

Örneğin:
```
    <p>
        HTML öğrenirken
        <strong>bol bol pratik</strong>
        yapmak önemlidir.
    </p>
```
Burada:
```
    p
    │
    └── strong
```
ilişkisi vardır.

**strong**, **p** elementinin içerisinde bulunmaktadır. Buna **nesting** denir.

### Kapanış Sırası
İç içe elementlerde elementlerin doğru sırayla kapatılması gerekir.

Doğru:
```
    <p>
        HTML <strong>çok önemlidir.</strong>
    </p>
```
Mantık:
```
    <p>
        <strong>
        </strong>
    </p>
```

**Son açılan iç element önce kapatılır.**

Yanlış:
```
    <p>
        HTML <strong>çok önemlidir.
    </p>
    </strong>
```
Bunu kutular gibi düşünebiliriz:
```
    Aç
    │
    ├── Aç
    │   └── Kapat
    │
    └── Kapat
```
İç içe yapıların doğru kurulması HTML belgesinin anlaşılır ve geçerli bir yapıya sahip olması açısından önemlidir.

### Büyük/Küçük Harf Duyarsızlığı
HTML element ve attribute adları **ASCII büyük/küçük harf** açısından duyarsızdır.

Örneğin, `<P>Merhaba</P>` ile `<p>Merhaba</p>` HTML sözdizimi açısından aynı p elementini ifade eder. Ancak modern HTML yazımında standart yaklaşım `<p>` gibi küçük harf kullanmaktır.

Bu nedenle:
```
    <HEADER>
        <H1>Ürünler</H1>
    </HEADER>
```
yerine:
```
    <header>
        <h1>Ürünler</h1>
    </header>
```
yazmak tercih edilir.

Bu:
- Kod okunabilirliğini,
- Tutarlılığı,
- Takım içerisindeki kod standardını iyileştirir.

**Önemli**

HTML element ve attribute adlarının case-insensitive olması, **her attribute değerinin büyük/küçük** harfe duyarsız olduğu anlamına gelmez.

Örneğin `id` ve `class` değerlerinde büyük/küçük harf farkı, bu değerler CSS seçicileri veya JavaScript tarafından kullanıldığında önem taşıyabilir.

Bu nedenle en doğru alışkanlık: **HTML kodunda tutarlı bir isimlendirme standardı kullanmaktır.**

**- DOCTYPE da Büyük/Küçük Harf Duyarsızdır**

Belgenin başındaki DOCTYPE bildirimi için de aynı kural geçerlidir:
```
    <!DOCTYPE html>
    <!doctype html>
```
Her ikisi de geçerlidir. `<!DOCTYPE html>` yazımı daha yaygın olsa da bazı projelerde ve araçlarda küçük harfli yazımla da karşılaşabiliriz.

### HTML Entities
HTML'de bazı karakterlerin özel anlamları vardır.

Örneğin:
```
    <
    >
    &
```
HTML sözdiziminin parçalarıdır. Bazen `<h1>` ifadesini gerçek bir başlık oluşturmak için değil, kullanıcıya metin olarak göstermek isteriz.

Bu durumda `&lt;h1&gt;` yazabiliriz. Tarayıcı bunu `<h1>` olarak gösterir.

Örneğin:
```
    <p>
        Başlık oluşturmak için &lt;h1&gt; kullanılabilir.
    </p>
```
Burada:
```
&lt; → <
&gt; → >
```
karakter referansları kullanılmıştır.

HTML Entities / Character References konusu ayrı bölümde ayrıntılı olarak inceleneceği için burada temel mantığını bilmemiz yeterlidir.

### HTML Yorum Satırları — Comments
Kod içerisinde tarayıcıda görüntülenmesini istemediğimiz açıklamalar yazabiliriz.

HTML yorum sözdizimi aşağıdaki şekildedir:
```
    <!-- Bu bir HTML yorumudur. -->
```

Örneğin:
```
    <!-- Header başlangıcı -->

    <header>
        <h1>Frontend Notları</h1>
    </header>

    <!-- Header bitişi -->
```

Yorumlar:
- Kod hakkında açıklama bırakmak,
- Belirli bölümleri işaretlemek,
- Geliştiricilere kısa notlar bırakmak için kullanılabilir.

**- Yorumlar Kullanıcıya Görünür mü?**

Normal sayfa görünümünde gösterilmezler. Ancak bu `Yorumlar gizlidir.` anlamına gelmez. HTML kaynak kodunu inceleyen biri yorumları görebilir.

Bu nedenle yorumların içerisine:
- Şifre
- API key
- Token
- Gizli kullanıcı bilgileri
- Özel sistem bilgileri

gibi hassas bilgiler yazılmamalıdır.

Örneğin: `<!-- admin-password: 123456 -->`kesinlikle güvenli bir yaklaşım değildir.

**- İç İçe HTML Yorumu**

HTML yorumları iç içe kullanılmamalıdır.

Örneğin:
```
    <!--
        Ana yorum

        <!-- İç yorum -->

    -->
```
geçerli bir iç içe yorum yapısı değildir.

**Neden?** Tarayıcı `<!--` ile yorumu başlatır ve karşılaştığı **ilk** `-->` ifadesinde yorumu bitirir. İçerideki `<!--` ifadesini yeni bir yorum başlangıcı olarak saymaz.
```
    <!--                        → Yorum başlar
        Ana yorum
        <!-- İç yorum -->       → İlk "-->" burada, yorum burada biter
    -->                         → Artık yorumun dışında!
```
Sonuç olarak en alttaki `-->` ifadesi yorumun dışında kalır ve sayfada **düz metin olarak görünebilir.**

Bu nedenle yorum bloklarını ayrı ayrı kullanmak gerekir.

### HTML'de Boşluklar — Whitespaces
HTML içerisinde birden fazla boşluk bırakmak, normal metin akışında tarayıcıda aynı sayıda boşluk gösterileceği anlamına gelmez.

Örneğin:
```
    <p>Merhaba          Dünya</p>
```
tarayıcıda normal akışta:
```
    Merhaba Dünya
```
şeklinde görünür.

Benzer şekilde kaynak kodunda:
```
    <p>
        Merhaba
        Dünya
    </p>
```
yazmak, yalnızca Enter'a bastığımız için kullanıcıya zorunlu olarak:
```
    Merhaba
    Dünya
```
şeklinde iki satır gösterileceği anlamına gelmez.

Normal HTML metin akışında ardışık whitespace karakterleri genellikle tek boşluk gibi işlenir.

**- Satır Atlamak İstiyorsak?**

Metnin yapısına göre farklı HTML elementleri kullanırız. Paragraflar farklıysa:
```
    <p>Birinci paragraf.</p>
    <p>İkinci paragraf.</p>
```
kullanılabilir.

Metnin içerisinde gerçekten bir satır kırılması gerekiyorsa:
```
    <p>
        İstanbul<br>
        Türkiye
    </p>
```
gibi `<br>` kullanılabilir. Ancak `<br>` elementi tasarımda boşluk oluşturmak amacıyla kullanılmamalıdır. **Görsel boşluklar CSS ile yönetilir.**

**- `<pre>`**

HTML'de whitespace davranışının farklı olduğu elementlerden biri: `<pre>` elementidir. `<pre>` içerisindeki boşluklar ve satır kırılmaları korunabilir.

Bu element metin elementleri konusunda daha ayrıntılı incelenecektir.

**- `&nbsp;`**

Character reference yapılarından `&nbsp;` **non-breaking space** oluşturur.

Ancak: `&nbsp;&nbsp;&nbsp;&nbsp;` şeklinde tasarım boşluğu oluşturmak amacıyla kullanılmamalıdır.

`&nbsp;` konusu **HTML Entities ve Özel Karakterler** bölümünde ayrıntılı olarak incelenmektedir.

## Basic Tags — HTML Sayfa İskeleti
HTML'in temel sözdizimini öğrendiğimize göre artık gerçek bir HTML belgesinin nasıl oluşturulduğuna bakabiliriz.

Temel bir HTML belgesi:
```
    <!DOCTYPE html>

    <html lang="tr">

    <head>

        <meta charset="UTF-8">

        <meta
            name="viewport"
            content="width=device-width, initial-scale=1.0"
        >

        <title>İlk HTML Sayfam</title>

    </head>

    <body>

        <h1>Merhaba Dünya!</h1>

        <p>
            İlk HTML sayfamı oluşturdum.
        </p>

    </body>

    </html>
```
Şimdi bu yapının parçalarını inceleyelim.

### `<!DOCTYPE html>`
HTML belgesinin en üstünde genellikle `<!DOCTYPE html>` bulunur. DOCTYPE bir HTML elementi veya etiketi değildir. Bir **document type declaration**, yani **belge türü bildirimidir**.

Modern HTML belgelerinde:
```
    <!DOCTYPE html>
```
kullanımı tarayıcının belgeyi modern standartlara uygun **standards mode** ile işlemesine yardımcı olur.

**- DOCTYPE Olmazsa Ne Olur?**
Tarayıcı bazı durumlarda belgeyi geçmişteki eski web siteleriyle uyumluluğu korumak amacıyla **quirks mode** adı verilen farklı bir uyumluluk modunda işleyebilir. Bu durumda bazı HTML/CSS davranışları modern standartlardan farklı olabilir.

Bu nedenle yeni bir HTML belgesi oluştururken: `<!DOCTYPE html>` kullanmak temel belge yapısının standart bir parçasıdır.

### `<html>`
`<html>`, HTML belgesinin kök (root) elementidir.
```
    <html>
        ...
    </html>
```
Belgenin HTML içeriği bu element içerisinde yer alır.

Temel yapı aşağıdaki şekildedir:
```
    html
    │
    ├── head
    │
    └── body
```

**- lang Attribute'u**
`html` elementinde genellikle belgenin dilini belirten lang attribute'u kullanılır.
```
    Türkçe bir sayfa: <html lang="tr">
    İngilizce bir sayfa: <html lang="en">
```
şeklinde tanımlanabilir.

**lang** özellikle erişilebilirlik ve belgenin dilinin makineler tarafından anlaşılması açısından önemlidir.

Bu konu **Global Attributes ve Accessibility** bölümlerinde daha ayrıntılı ele alınacaktır.

### `<head>`
`<head>` belgenin kendisi hakkında bilgiler içeren bölümdür.

Örneğin:
```
    <head>
        <meta charset="UTF-8">
        <title>Ürünler</title>
    </head>
```
Buradaki bilgiler genellikle sayfanın ana görünür içeriğinin bir parçası değildir.

**head** içerisinde örneğin:
- title
- meta
- link
- style
- script

gibi elementlerle karşılaşabiliriz.

Örneğin:
```
    <head>

        <meta charset="UTF-8">

        <title>Frontend Notları</title>

        <link
            rel="stylesheet"
            href="style.css"
        >

    </head>
```
`<head>` bölümünü basitçe; **Belgenin kendisi hakkında tarayıcıya, arama motorlarına ve diğer sistemlere gerekli bilgilerin verildiği alan** olarak düşünebiliriz.

**Metadata ve SEO** konusu ilerleyen bölümlerde ayrıca ele alınacaktır.

### `<meta>`
`<meta>` elementi HTML belgesi hakkında metadata sağlamak için kullanılabilir. Temel HTML seviyesinde özellikle iki kullanımını bilmek yeterlidir.

Karakter Kodlaması `<meta charset="UTF-8">`belgenin karakter kodlamasını belirtir.

UTF-8 sayesinde:
```
    ç
    ğ
    ı
    İ
    ö
    ş
    ü
```
gibi Türkçe karakterler de doğru şekilde temsil edilebilir.

**- charset Nereye Yazılmalı?**

HTML standardına göre `<meta charset="UTF-8">` bildirimi **belgenin ilk 1024 baytı içerisinde** bulunmalıdır. Tarayıcı karakter kodlamasını belirlemek için belgenin başına bakar; bildirim çok aşağıda kalırsa tarayıcı o noktaya kadar yanlış kodlamayla okumaya başlamış olabilir.

Bu nedenle pratikte `<meta charset="UTF-8">` satırı **`<head>` içerisindeki ilk element** olarak yazılır:
```
    <head>
        <meta charset="UTF-8">   → İlk sırada
        <title>Ürünler</title>
        ...
    </head>
```

**Dosyanın kendisi de UTF-8 olmalıdır.** `<meta charset="UTF-8">` tarayıcıya "bu dosya UTF-8" bilgisini verir; ancak dosya editörde farklı bir kodlamayla kaydedilmişse Türkçe karakterler yine bozuk görünebilir. VS Code gibi modern editörler dosyaları varsayılan olarak UTF-8 kaydeder; editörün alt durum çubuğundan bu kontrol edilebilir.

**- Viewport**

Responsive web sayfalarında sık karşılaşacağımız diğer temel meta tanımı:
```
    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0"
    >
```
Bu tanım mobil cihazlarda viewport'un sayfa genişliğini cihaz genişliğiyle uyumlu şekilde ele almasına yardımcı olur.

Buradaki: `width=device-width` viewport genişliğini cihazın genişliğiyle ilişkilendirir. `initial-scale=1.0` ise başlangıç zoom ölçeğini belirtir.

**description**, **robots** ve **diğer metadata yapıları** burada detaylandırılmayacaktır.

Bunları **HTML Metadata ve SEO** bölümünde ayrıca inceleyeceğiz.

### `<body>`
`<body>` sayfanın kullanıcıya sunulan ana belge içeriğini barındırır.

Örneğin:
```
    <body>

        <h1>Ürünler</h1>

        <p>
            Yeni sezon ürünlerimizi inceleyebilirsiniz.
        </p>

        <button>
            Ürünleri Gör
        </button>

    </body>
```
Sayfada gördüğümüz:
- Başlıklar,
- Paragraflar,
- Görseller,
- Listeler,
- Formlar,
- Tablolar,
- Navigasyon,
- Butonlar,
- Ana içerik bölümleri

gibi yapılar body içerisinde bulunur.

Temel ayrım:
```
    HTML Document
    │
    ├── head
    │   │
    │   └── Belge hakkındaki bilgiler
    │
    └── body
        │
        └── Sayfanın belge içeriği
```

##  İlk HTML Dosyamızı Oluşturalım
Şimdi öğrendiğimiz yapıları bir araya getirelim. Yeni bir dosya oluşturalım: `index.html`

Dosyanın içerisine:
```
    <!DOCTYPE html>

    <html lang="tr">

    <head>

        <meta charset="UTF-8">

        <meta
            name="viewport"
            content="width=device-width, initial-scale=1.0"
        >

        <title>İlk HTML Sayfam</title>

    </head>

    <body>

        <h1>Merhaba Dünya!</h1>

        <p>
            HTML öğrenmeye başladım.
        </p>

    </body>

    </html>
```
yazalım.

### Satır Satır İnceleyelim

**`<!DOCTYPE html>`**
Belgenin modern HTML olarak işlenmesi için kullanılan belge türü bildirimidir.

**`<html lang="tr">`**
HTML belgesinin kök elementidir. Ayrıca belgenin temel dilinin Türkçe olduğunu belirtir.

**`<head>`**
Belge hakkında bilgiler içeren bölüm başlar.

**`<meta charset="UTF-8">`**
Belgenin karakter kodlamasını UTF-8 olarak belirtir.

**`<meta name="viewport" content="width=device-width, initial-scale=1.0">`**
Sayfanın özellikle mobil cihazlardaki viewport davranışı için temel yapılandırmayı sağlar.

**`<title>İlk HTML Sayfam</title>`**
Belgenin başlığını belirler. Bu başlık örneğin tarayıcı sekmesinde kullanılabilir.

**`<body>`**
Kullanıcıya sunulacak belge içeriğinin bulunduğu bölüm başlar.

**`<h1>Merhaba Dünya!</h1>`**
Sayfaya bir başlık ekler. Başlık hiyerarşisini ilerleyen bölümlerde ayrıca inceleyeceğiz.

**`<p>HTML öğrenmeye başladım.</p>`**
Bir paragraf oluşturur.

**`</body></html>`**
Önce body, ardından kök html elementi kapatılır.

## HTML Dosyası Nasıl Kaydedilir?
HTML belgelerinin dosya uzantısı: `.html` şeklindedir.

Örneğin:
```
    index.html
    about.html
    contact.html
    products.html
```
Dosyayı: `index.html` adıyla kaydettikten sonra bir web tarayıcısıyla açabiliriz. Tarayıcı HTML kodunu okuyup oluşturduğu belgeyi kullanıcıya görsel olarak sunar.

Örneğin kaynak kod:
```
    <h1>Merhaba Dünya!</h1>
    <p>HTML öğreniyorum.</p>
```
iken tarayıcıda kullanıcı HTML etiketlerini değil, bunların oluşturduğu belgeyi görür:
```
    Merhaba Dünya!
    HTML öğreniyorum.
```

## Sık Yapılan Hatalar
HTML öğrenirken bazı hatalar oldukça sık görülür.

**1. Elementleri Yanlış Sırada Kapatmak**
Yanlış:
```
    <p>
        HTML <strong>öğreniyorum.
    </p>
    </strong>
```
Doğru:
```
    <p>
        HTML <strong>öğreniyorum.</strong>
    </p>
```
**2. Kapanış Etiketini Unutmak**
Yanlış:
```
    <p>Birinci paragraf
    <p>İkinci paragraf
```
Tarayıcı bazı hataları tolere edebilse de buna güvenerek hatalı HTML yazılmamalıdır. Açık ve doğru sözdizimi tercih edilmelidir.

**3. Void Elementlere Kapanış Etiketi Eklemek**
Yanlış:
```
    <img src="photo.jpg"></img>
```
Doğru:
```
    <img
        src="photo.jpg"
        alt="Manzara"
    >
```
**4. DOCTYPE Bildirimini Unutmak**
Yeni HTML belgelerinde dosyanın başında:
```
    <!DOCTYPE html>
```
bulundurulmalıdır.

**5. Metadata'yı body İçerisine Yazmak**
Örneğin temel charset bildirimi: `<meta charset="UTF-8">` head içerisinde bulunmalıdır.

Doğru yapı:
```
    <head>
        <meta charset="UTF-8">
    </head>
```

**6. HTML'i Tasarım İçin Kullanmaya Çalışmak**
Örneğin boşluk oluşturmak için:
```
    <br>
    <br>
    <br>
    <br>
```
kullanmak doğru bir tasarım yaklaşımı değildir.

HTML: `Yapı + Anlam`
CSS ise: `Sunum + Görsel Düzen`
için kullanılmalıdır.

**7. Her Şeyi `<div>` ile Oluşturmak**
HTML yalnızca `<div>` elementinden oluşmaz.

İçeriğin anlamına göre:
```
    header
    nav
    main
    section
    article
    aside
    footer
```
gibi semantik elementler kullanılabilir.

Bunları **Semantic HTML** konusunda ayrıntılı olarak inceleyeceğiz.

### HTML Kodumuzu Nasıl Kontrol Ederiz?
Tarayıcı hataları tolere ettiği için bazı HTML hatalarını sayfaya bakarak fark edemeyebiliriz. Bu durumda **W3C Markup Validation Service** kullanılabilir:
```
    https://validator.w3.org
```
Bu araçta:
- Bir sayfanın URL'sini girerek,
- HTML dosyası yükleyerek,
- Veya kodu doğrudan yapıştırarak

HTML'in standartlara uygun olup olmadığını kontrol edebiliriz. Araç kapatılmamış etiketleri, yanlış iç içe yapıları, eksik zorunlu attribute'ları ve benzeri hataları satır numarasıyla birlikte gösterir.

## Kısaca Özet
- HTML'in açılımı: `HyperText Markup Language`
- HTML bir programlama dili değil, **işaretleme dilidir.**

Frontend tarafındaki temel görev dağılımını şu şekilde düşünebiliriz:
```
    HTML → Yapı ve anlam
    CSS → Görsel sunum
    JavaScript → Davranış ve etkileşim
```

HTML'in temel yapı taşları şu şekildedir:
```
    Element
    │
    ├── Açılış etiketi
    ├── İçerik
    └── Kapanış etiketi

    Attribute → Element hakkında ek bilgi / yapılandırma
```

Temel HTML belgesi ise:
```
    <!DOCTYPE html>

    <html lang="tr">

    <head>

        <meta charset="UTF-8">

        <meta
            name="viewport"
            content="width=device-width, initial-scale=1.0"
        >

        <title>Sayfa Başlığı</title>

    </head>

    <body>

        <h1>Sayfa Başlığı</h1>

        <p>Sayfa içeriği.</p>

    </body>

    </html>
```
yapısına sahiptir.

Bunu hiyerarşik olarak şu şekilde düşünebiliriz:
```
HTML Belgesi
│
├── <!DOCTYPE html>
│
└── html
    │
    ├── head
    │   ├── meta charset
    │   ├── meta viewport
    │   └── title
    │
    └── body
        └── Sayfanın içeriği
```

Bu bölümden sonra artık bir HTML dosyasına baktığımızda:
- HTML'in neden kullanıldığını,
- Tarayıcının HTML'den DOM ağacını nasıl oluşturduğunu,
- Element ile tag arasındaki farkı,
- Attribute'un ne olduğunu,
- Elementlerin nasıl iç içe geçtiğini,
- Void elementlerin farkını,
- HTML'in whitespace davranışını,
- Yorumların nasıl yazıldığını,
- `DOCTYPE`, `html`, `head`, `meta` ve `body` yapılarını,
- Temel bir HTML dosyasının nasıl oluşturulduğunu

anlayabilecek temel altyapıya sahibiz.

Bundan sonraki HTML konularında bu temel yapının üzerine yeni elementler ve kavramlar ekleyeceğiz.
