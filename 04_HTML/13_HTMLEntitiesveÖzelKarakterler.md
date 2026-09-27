# HTML Entities ve Özel Karakterler
HTML içerisinde yazdığımız bazı karakterlerin HTML açısından özel anlamları vardır.

Örneğin; `<,>,&` karakterleri HTML sözdiziminin bir parçasıdır. Bazen bu karakterleri HTML kodunun bir parçası olarak değil, sayfada normal metin olarak göstermek isteriz. Bu gibi durumlarda **HTML Character References** olarak adlandırılan yapılardan yararlanabiliriz. Günlük kullanımda bunlardan sıklıkla **HTML Entity** olarak bahsedildiğini görürüz.

## HTML Entity Nedir?
HTML entity'leri, özel karakterleri HTML içerisinde güvenli ve anlamlı biçimde ifade etmek için kullanılan karakter referanslarıdır.

Örneğin sayfada, `<h1>` metnini göstermek istediğimizi düşünelim. Bunu HTML içerisinde, `&lt;h1&gt;` şeklinde yazabiliriz.

Tarayıcı kullanıcıya: `<h1>` gösterir.

Burada:
```
    &lt;   →   <
    &gt;   →   >
```
karakter referansları kullanılmıştır.

## Entity Kullanımına Neden İhtiyaç Duyarız?
HTML bazı karakterleri kendi sözdiziminin bir parçası olarak kullanır.

Örneğin, `<h1>Başlık</h1>` yapısında: `< >` karakterleri HTML etiketlerinin sınırlarını belirtir. Ancak bir eğitim sayfasında kullanıcıya, `<h1>` etiketini metin olarak göstermek isteyebiliriz. Bu durumda HTML'in bunu markup olarak yorumlamaması gerekir.

Şöyle yazabiliriz:
```
    <p>
        Başlık oluşturmak için
        &lt;h1&gt; elementi kullanılabilir.
    </p>
```
Tarayıcıda, `Başlık oluşturmak için <h1> elementi kullanılabilir.` şeklinde görünür.

Temel mantık:
```
    HTML içerisinde yazılan özel karakter
            ↓
    Character Reference
            ↓
    Tarayıcı
            ↓
    Kullanıcıya gerçek karakter gösterilir
```

## Entity Yazım Yöntemleri
HTML'de karakterleri ifade etmek için farklı karakter referansı biçimleri bulunur.

Başlangıç seviyesinde iki temel yöntemle karşılaşmamız yeterlidir:
```
    Character Reference
    │
    ├── Named Character Reference
    │
    └── Numeric Character Reference
```

### Named Character Reference
Karakterin tanımlanmış ismi kullanılır. Örneğin, `&lt;` çıktısı `<` olur.

Benzer şekilde: `&gt;` çıktısı `>` olur.

Named character reference yapısı genel olarak, `&isim;` şeklindedir.

Örneğin:
```
    &lt;
    &amp;
    &copy;
```

Burada:
```
    & → Referansın başlangıcı
    lt / amp / copy → Karakterin tanımlanmış adı
    ; → Referansın sonu
```
şeklinde düşünebiliriz.

### Numeric Character Reference
Karakterler sayısal Unicode kod noktaları üzerinden de ifade edilebilir.

Örneğin, `&#60;` tarayıcıda `<` olarak görüntülenir.

Hexadecimal gösterim de kullanılabilir, `&#x3C;` Bu da, `<` karakterini ifade eder.

Yani aynı karakter farklı yöntemlerle yazılabilir:
```
    &lt;
    &#60;
    &#x3C;
       ↓
       <
```
Günlük HTML yazarken sık kullanılan karakterlerde isimlendirilmiş referanslar genellikle daha okunaklıdır. Numeric character reference sistemini bilmek faydalıdır ancak Unicode değerlerini ezberlemek gerekli değildir.

## HTML'de Özel Anlamı Olan Karakterler
HTML öğrenirken özellikle şu karakter referanslarıyla sık karşılaşabiliriz:

|Yazım  | Görünen Karakter|
|-------|-----------------|
|&lt;	|       <         |
|&gt;	|       >         |
|&amp;	|       &         |

Bunların kullanım amaçlarını ayrı ayrı inceleyelim.

### `&lt;` — Küçüktür İşareti <
lt, less than ifadesinden gelir. `&lt;` tarayıcıda `<` olarak görünür. HTML etiketlerini kullanıcıya metin olarak gösterirken özellikle önemlidir.

Örneğin:
```
    <p>
        &lt;header&gt; elementi sayfanın
        üst bölümünü temsil edebilir.
    </p>
```
Tarayıcı: **`<header>` elementi sayfanın üst bölümünü temsil edebilir.** şeklinde gösterir.

### `&gt;` — Büyüktür İşareti >
gt, greater than ifadesinden gelir. `&gt;` tarayıcıda `>` olarak görünür.

Örneğin: `&lt;button&gt;` tarayıcıda `<button>` şeklinde görünür.

### `&amp;` — Ampersand &
Ampersand karakteri: `&`

HTML karakter referanslarının başlangıcında kullanıldığı için özel bir karakterdir. Karakterin kendisini açık biçimde ifade etmek gerektiğinde: `&amp;` kullanılabilir.

Örneğin:
```
    <p>
        HTML &amp; CSS
    </p>
```
çıktısı: `HTML & CSS` olur.

Özellikle HTML içerisinde başka character reference yapıları bulunduğunda `&` karakterinin anlamını bilmek önemlidir.

## Sık Kullanılan Diğer Özel Karakterler
HTML'de başka isimlendirilmiş karakter referansları da bulunmaktadır. Bunların tamamını ezberlemek gerekli değildir.

Sık karşılaşabileceğimiz birkaç örnek:

|Entity |Karakter |Anlam                |
|-------|---------|---------------------|
|&copy;	|   ©     |Copyright            |
|&reg;	|   ®     |Registered           |
|&trade;|	™	  |Trademark            |
|&nbsp;	|Boşluk   |Non-breaking space   |

Örneğin:
```
    <footer>
        &copy; 2026 Frontend Notları
    </footer>
```
tarayıcıda: `© 2026 Frontend Notları` şeklinde görüntülenir.

## `&nbsp;` Nedir?
`nbsp;`, **non-breaking space** anlamına gelir. Normal boşluk ile tamamen aynı amaçta değildir.

Normal bir metinde:
```
    <p>
        Merhaba Dünya
    </p>
```
tarayıcı gerektiğinde iki kelimenin arasından satırı bölebilir.

`&nbsp;` ise iki bölüm arasında satırın kırılmaması gereken bir boşluk oluşturur.

Örneğin:
```
    <p>
        10&nbsp;km
    </p>
```
buradaki değer ve birimin satır sonunda birbirinden ayrılmasını engellemeye yardımcı olabilir.

Temel mantık:
```
    Normal boşluk → Satır gerektiğinde kırılabilir.
    Non-breaking space → Bu noktada satır kırılması engellenir.
```

### `&nbsp;` Tasarım İçin Kullanılmalı mı?
Hayır. Başlangıçta yapılan yaygın hatalardan biri:
```
    <p>
        Merhaba&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Dünya
    </p>
```
şeklinde çok sayıda `&nbsp;` kullanarak elementler arasında görsel boşluk oluşturmaktır. Bu doğru bir tasarım yaklaşımı değildir. Görsel boşluklar CSS ile yönetilmelidir.

Örneğin:
```
    .element {
        margin-right: 24px;
    }
```
veya ihtiyaca göre:
```
    .container {
        display: flex;
        gap: 24px;
    }
```
kullanılabilir.

Yani:
```
    Metnin bölünmesini engellemek → &nbsp;
    Tasarımda boşluk oluşturmak → CSS
```
şeklinde ayırabiliriz.

## Türkçe Karakterler İçin Entity Kullanmak Gerekir mi?
Modern HTML belgelerinde UTF-8 kullanıyorsak Türkçe karakterleri entity olarak yazmamız gerekmez. `<meta charset="UTF-8">` sayfanın UTF-8 karakter kodlamasını kullandığını belirtir.

Dolayısıyla doğrudan:
```
    <p>
        Çalışma, öğrenme, gelişim, şifre, ürün
    </p>
```
yazabiliriz.

Türkçe karakterleri farklı kodlarla yazmaya çalışmak gerekli değildir. Modern HTML'de, `<p>Ürün Açıklaması</p>` çok daha okunaklıdır.

Temel yaklaşım: `Normal şekilde yazabildiğimiz Unicode karakterleri gereksiz yere entity'ye dönüştürmeyiz.`

## Kod Örneklerinde `<` ve `>` Nasıl Gösterilir?
Bu kullanım özellikle dokümantasyon, blog veya eğitim sayfalarında önemlidir. Kullanıcıya HTML kodu göstermek istediğimizi düşünelim.

Örneğin: `<h1>Merhaba</h1>`

Kod parçasını HTML içerisinde göstermek için `<code>` kullanabiliriz:
```
    <code>
        &lt;h1&gt;Merhaba&lt;/h1&gt;
    </code>
```
Tarayıcıda: `<h1>Merhaba</h1>` görünür.

Birden fazla satırlık kodlarda `<pre>` ve `<code>` birlikte kullanılabilir:
```
<pre><code>&lt;section&gt;
    &lt;h2&gt;Ürünler&lt;/h2&gt;
&lt;/section&gt;</code></pre>
```
Burada:
```
    <pre> → Biçimlendirilmiş metni ve boşlukları korur.
    <code> → İçeriğin kod olduğunu belirtir.
    &lt; ve &gt; → HTML karakterlerinin metin olarak görüntülenmesini sağlar.
```
Bu yapı özellikle teknik dokümantasyon hazırlarken oldukça kullanışlıdır.

## Entity ile HTML Elementini Karıştırmamak
Entity bir HTML elementi değildir.

Örneğin:
```
    &lt; → bir element oluşturmaz.
    Tarayıcıya: < karakterini göster.
```
bilgisini verir.

Dolayısıyla:
```
    <h1> → HTML elementi
    &lt; → Karakter referansı
```
birbirinden farklı kavramlardır.

## Entity ile Encoding Aynı Şey mi?
Hayır.

Örneğin:
```
    **<meta charset="UTF-8">** belgenin karakter kodlamasını belirtir.
    **&lt;** ise belirli bir karakteri HTML içerisinde temsil eden character reference'tır.
```
Yani:
```
    UTF-8 → Belgenin karakter kodlaması
    &lt; → Belirli bir karakterin HTML içerisindeki gösterimi
```
aynı şey değildir.

Bu nedenle UTF-8 kullanıyor olmamız, HTML sözdiziminde özel anlam taşıyan karakter referanslarına hiçbir zaman ihtiyaç duymayacağımız anlamına gelmez.

## Entity'leri Ezberlemek Gerekir mi?
Hayır. HTML'de çok sayıda isimlendirilmiş karakter referansı bulunur. Frontend geliştirirken bunların tamamını ezberlemek pratik değildir ve gerekli de değildir. Başlangıçta özellikle şunları tanımak yeterlidir:
```
    &lt;     → <
    &gt;     → >
    &amp;    → &
    &nbsp;   → bölünmeyen boşluk
    &copy;   → ©
    &reg;    → ®
    &trade;  → ™
```
İhtiyaç duyulan diğer karakterler gerektiğinde referanslardan bulunabilir. Burada önemli olan listeyi ezberlemek değil, **character reference sisteminin neden var olduğunu anlamaktır.**

## Sık Yapılan Hatalar
HTML entities konusunda sık karşılaşılan hatalar şunlardır:

### Her özel karakteri entity olarak yazmaya çalışmak
Modern UTF-8 belgelerde `<p>Türkçe öğreniyorum.</p>` şeklinde normal Unicode karakterler kullanılabilir.

### `&nbsp;` ile tasarım yapmak
Yanlış yaklaşım:
```
    <span>Ürün</span>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
    <span>Fiyat</span>
```
Görsel aralık CSS ile oluşturulmalıdır.

### HTML kodunu doğrudan metin olarak yazmak
Kullanıcıya `<div>` göstermek istiyorsak HTML kaynak kodunda gerektiğinde:
```
    &lt;div&gt;
```
kullanmalıyız.

### `&` Karakterinin Özel Anlamını Unutmak
`&`, character reference başlangıcında kullanılan özel karakterlerden biridir. Bu nedenle HTML içerisinde karakter referanslarının nasıl başladığını bilmek önemlidir.

### Entity ile Encoding'i Karıştırmak
`<meta charset="UTF-8">` ile `&amp;` aynı problemi çözmez.

Birincisi belge kodlamasını, ikincisi belirli bir karakter referansını ifade eder.

## Küçük Bir Örnek
Öğrendiklerimizi tek bir örnekte görelim:
```
    <!DOCTYPE html>

    <html lang="tr">

    <head>

        <meta charset="UTF-8">

        <meta
            name="viewport"
            content="width=device-width, initial-scale=1.0"
        >

        <title>HTML Entities</title>

    </head>

    <body>

        <main>

            <h1>HTML Entities</h1>

            <p>
                HTML &amp; CSS frontend geliştirmede
                birlikte kullanılır.
            </p>

            <p>
                Başlık oluşturmak için
                &lt;h1&gt; elementi kullanılabilir.
            </p>

            <pre><code>&lt;h1&gt;Merhaba Dünya&lt;/h1&gt;</code></pre>

            <p>
                &copy; 2026 Frontend Notları
            </p>

        </main>

    </body>

    </html>
```
Tarayıcıda içerik kabaca:
```
    HTML Entities
    HTML & CSS frontend geliştirmede birlikte kullanılır.
    Başlık oluşturmak için <h1> elementi kullanılabilir.
    <h1>Merhaba Dünya</h1>
    © 2026 Frontend Notları
```
şeklinde görünür.

## Kısa Kontrol Listesi
HTML içerisinde özel karakter kullanırken:
- Karakter HTML sözdiziminde özel bir anlam taşıyor mu?
- Karakteri metin olarak mı göstermek istiyorum?
- HTML kodunu kullanıcıya göstereceksem `<` ve `>` karakterlerini doğru ifade ediyor muyum?
- `&nbsp;` gerçekten satır kırılmasını engellemek için mi kullanılıyor?
- Görsel boşluk oluşturmak için gereksiz `&nbsp;` kullanıyor muyum?
- Belgem UTF-8 kullanıyor mu?
- Türkçe karakterleri gereksiz yere entity'ye dönüştürüyor muyum?
- Entity ile karakter kodlamasını birbirine karıştırıyor muyum?

## Kısaca Özet
HTML Character References'ın temel mantığı:
```
    HTML'de göstermek istediğimiz karakter
                    │
                    ▼
        Character Reference
                    │
                    ▼
                Tarayıcı
                    │
                    ▼
        Kullanıcıya gösterilen karakter
```
Sık karşılaşacağımız örnekler:
```
    &lt;      → <
    &gt;      → >
    &amp;     → &
    &nbsp;    → Bölünmeyen boşluk
    &copy;    → ©
    &reg;     → ®
    &trade;   → ™
```
Bu konudaki en önemli nokta: **HTML entity'lerini ezberlemek değil, HTML'in özel anlam verdiği karakterleri gerektiğinde metin olarak nasıl ifade edeceğimizi bilmektir.**

Modern HTML'de UTF-8 sayesinde Türkçe karakterler ve çoğu Unicode karakter doğrudan yazılabilir. Character reference'ları ise özellikle HTML sözdizimiyle çakışabilecek karakterlerde ve belirli özel kullanım durumlarında tercih ederiz.