# HTML'de Metin Etiketleri
HTML'de metin oluştururken yalnızca içeriğin ekranda nasıl göründüğünü değil, **o içeriğin ne anlama geldiğini** de tanımlarız.

Örneğin bir metni kalın göstermek istediğimiz için doğrudan `<strong>` kullanmak doğru bir yaklaşım değildir. Önce şu soruyu sormamız gerekir:
```
    Bu metin neden vurgulanıyor ve içerikteki anlamı nedir?
```
HTML bize paragraflardan alıntılara, önemli ifadelerden silinmiş içeriklere kadar farklı anlamları ifade eden elementler sunar.

Bu bölümde temel metin elementlerini ve aralarındaki önemli farkları inceleyeceğiz.

## Metin Elementlerinin Görevi
HTML'in temel amacı içeriğin görünümünü değil, yapısını ve anlamını tanımlamaktır.

Örneğin: `<strong>Önemli bilgi</strong>` kullanırken amacımız, `"Bu metin kalın görünsün."` demek değildir.

Asıl ifade ettiğimiz: `"Bu içerik güçlü bir öneme sahip."` bilgisidir.

Metnin nasıl görüneceği CSS ile değiştirilebilir.

Bu nedenle HTML elementi seçerken, `Nasıl görünsün?` yerine, `Bu içerik ne anlama geliyor?` sorusunu sormak daha doğru bir yaklaşımdır.

### Block ve Inline Element Mantığı
Metin elementlerini öğrenirken **block ve inline** kavramlarını temel seviyede bilmek yararlıdır.

Örneğin `<p>` bir paragraf oluşturur:
```
    <p>Birinci paragraf.</p>
    <p>İkinci paragraf.</p>
```
Paragraflar normal akışta ayrı bloklar olarak yer alır. Buna karşılık `<strong>` metnin içerisinde kullanılabilir:
```
    <p>
        Siparişinizi tamamlamak için
        <strong>adres bilgilerinizi kontrol edin.</strong>
    </p>
```
Buradaki **strong**, paragrafın içerisinde kalır.

Basitçe:
```
    Block → Belge akışında ayrı bir blok oluşturur.

    p
    div
    ...

    Inline → Metin akışının içerisinde yer alır.

    strong
    em
    span
    ...
```
Ancak block ve inline ayrımını yalnızca görünüş üzerinden düşünmemek gerekir. CSS ile bir elementin görsel display davranışı değiştirilebilir.

Bu bölümdeki ayrım, elementlerin HTML içerisindeki doğal kullanımını anlamamıza yardımcı olmak içindir.

## Paragraf ve Ayırıcılar
Metin içeriği oluştururken en temel elementlerden üçü:
- p
- br
- hr elementleridir.

Fakat görevleri birbirinden farklıdır.

### 1.`<p>` — Paragraf
`<p>` elementi bir paragrafı temsil eder.

Örneğin:
```
    <p>
        HTML, web sayfalarının yapısını oluşturmak için kullanılan bir işaretleme dilidir.
    </p>
```
Birbirinden ayrı düşünceleri farklı paragraflara ayırabiliriz:
```
    <p>
        HTML sayfanın yapısını ve içeriğin anlamını tanımlar.
    </p>

    <p>
        CSS ise sayfanın görsel sunumunu yönetir.
    </p>
```
Bu kullanım yalnızca görsel olarak iki metin arasında boşluk oluşturmaz. Aynı zamanda `Bunlar iki ayrı paragraftır.` anlamını verir.

**`<p>` İçerisinde Her Element Kullanılabilir mi?**
Hayır. Örneğin bir paragrafın içerisine başka bir paragraf yerleştirilmez.

Yanlış:
```
    <p>
        Birinci paragraf.

        <p>
            İkinci paragraf.
        </p>
    </p>
```
Benzer şekilde:
```
    <p>
        Metin

        <div>
            İçerik
        </div>
    </p>
```
şeklinde bir yapı da doğru değildir.

Paragrafların içerisinde metin akışına uygun içerikler kullanılmalıdır.

Örneğin:
```
    <p>
        HTML öğrenirken
        <strong>semantik kullanıma</strong>
        dikkat etmek önemlidir.
    </p>
```
doğru bir kullanımdır.

### 2.`<br>` — Satır Kırılması
`<br`> elementi metnin içerisinde gerçek bir satır kırılması gerektiğinde kullanılır.

Örneğin bir adres:
```
    <p>
        Atatürk Caddesi No: 10<br>
        Kadıköy / İstanbul<br>
        Türkiye
    </p>
```
veya şiir gibi satırların anlamlı olduğu içeriklerde kullanılabilir. `<br>` bir **void elementtir**, yani kapanış etiketi bulunmaz.
```
    <br>
```

**`<br>` Ne İçin Kullanılmamalıdır?**
Sayfada görsel boşluk oluşturmak için aşağıdaki gibi kullanılmamalıdır:
```
    <p>Başlık</p>

    <br>
    <br>
    <br>

    <p>İçerik</p>
```

Görsel boşluk CSS'in sorumluluğudur.
```
    Gerçek satır kırılması → <br>
    Görsel boşluk → CSS
```

### 3. `<hr>` — Konu Ayrımı
`<hr`> elementi çoğu zaman ekranda yatay bir çizgi şeklinde görünür. Ancak görevi `"Sayfaya çizgi eklemek"` değildir.

`<hr>`, içerikte konu veya bağlam değişimini temsil eden tematik bir ayrım oluşturur.

Örneğin:
```
    <p>
        HTML'in temel yapısını inceledik.
    </p>

    <hr>

    <p>
        Şimdi CSS'in web sayfasındaki görevine geçelim.
    </p>
```
Burada `hr`, iki içerik arasında anlam bakımından bir geçiş bulunduğunu belirtir. Sadece dekoratif bir çizgi istiyorsak bunu CSS ile oluşturmak daha doğru olur.

## Vurgu: `<b> / <strong> ve <i> / <em>`
Bu elementler HTML öğrenirken en sık karıştırılan yapılardandır. Çünkü tarayıcının varsayılan stillerinde:
```
    b      → kalın
    strong → kalın
    i      → italik
    em     → italik
```
gibi görünebilirler. Fakat HTML açısından önemli olan görünüşleri değil anlamlarıdır.

### 1. `<strong>` — Güçlü Önem
`<strong>` içeriğin güçlü bir öneme, ciddiyete veya aciliyete sahip olduğunu belirtir.

Örneğin:
```
    <p>
        <strong>Uyarı:</strong>
        Bu işlem geri alınamaz.
    </p>
```
Buradaki "Uyarı" yalnızca kalın gösterilmek istenmiyor. İçeriğin önemli bir parçası olduğu belirtiliyor.

Başka bir örnek:
```
    <p>
        Formu göndermeden önce
        <strong>bilgilerinizi mutlaka kontrol edin.</strong>
    </p>
```

### 2. `<b>` — Dikkat Çekme
`<b>` elementi metnin bir bölümüne ekstra önem yüklemeden dikkat çekmek için kullanılabilir.

Örneğin:
```
    <p>
        Yeni koleksiyonda
        <b>Meridian Classic</b>
        modeli de yer alıyor.
    </p>
```

Burada ürün adına özel bir önem veya aciliyet anlamı yüklemiyoruz. Yalnızca metin içerisinde dikkat çekmesini sağlıyoruz.

Temel fark:

|Element    |Anlam                              |
|-----------|-----------------------------------|
|<strong>   |Güçlü önem, ciddiyet veya aciliyet |
|<b>        |Ekstra önem yüklemeden dikkat çekme|

Dolayısıyla: `Kalın olsun` diye otomatik olarak `<strong>` seçilmemelidir. Eğer amaç tamamen görsel olarak kalın yazı oluşturmaksa CSS kullanılabilir.

### 3. `<em>` — Vurgu
`<em>` elementi metinde **vurgu (stress emphasis)** belirtir. Bu vurgu bazen cümlenin anlamını da değiştirebilir.

Örneğin:
```
    <p>
        Ben <em>bugün</em> geleceğim.
    </p>
```
Burada vurgu: `Bugün geleceğim, başka bir gün değil.` anlamını güçlendirebilir.

Şöyle yazarsak:
```
    <p>
        <em>Ben</em> bugün geleceğim.
    </p>
```
vurgu artık kişinin üzerindedir: `Ben geleceğim, başka biri değil.`

Bu nedenle em, yalnızca "italik yazı" değildir.

### 4. `<i>` — Farklı Ses veya Terim
`<i>` elementi metnin normal anlatımından farklı bir ses, terim veya kullanım biçimini temsil edebilir.

Örneğin yabancı bir ifade:
```
    <p>
        Tasarımda <i>white space</i> kullanımı oldukça önemlidir.
    </p>
```
veya teknik bir terim:
```
    <p>
        Bu işlem <i>lazy loading</i> olarak adlandırılır.
    </p>
```
gibi bağlamlarda kullanılabilir.

Temel ayrım:

|Element    |Anlam                                  |
|-----------|---------------------------------------|
|<em>       |Vurgulanan ifade                       |
|<i>        |Farklı ses, terim veya anlatım biçimi  |

Yine yalnızca italik görünmesini istediğimiz bir metin için CSS kullanabiliriz.

**Erişilebilirlik Açısından Vurgu**

Semantik HTML kullanmak yardımcı teknolojilere içeriğin yapısı hakkında daha anlamlı bilgi sağlayabilir.

Ancak:
```
    "strong her ekran okuyucuda mutlaka daha güçlü sesle okunur."
```
veya:
```
    "em kesinlikle farklı tonla okunur."
```
gibi bir garanti yoktur.

Ekran okuyucuların bu elementleri seslendirme biçimleri kullandıkları yazılıma ve ayarlara göre değişebilir.

Bu nedenle **strong ve em** elementlerini görsel veya sesli bir etki oluşturmak için değil, **içeriğin gerçek anlamına uygun oldukları için kullanmalıyız.**

## `<pre>` — Önceden Biçimlendirilmiş Metin
HTML'in normalde ardışık boşlukları ve satır sonlarını birleştirdiğini görmüştük.

Örneğin:
```
    <p>
        Merhaba          Dünya
    </p>
```
normal metin akışında boşlukları yazdığımız haliyle korumaz.

`<pre>` ise **preformatted text**, yani önceden biçimlendirilmiş metni temsil eder.

Örneğin:
```
    <pre>
    Ad:       Büşra
    Meslek:   Frontend Developer
    Seviye:   Junior
    </pre>
```
Buradaki:
- Boşluklar,
- Girintiler,
- Satır kırılmaları

korunur.

Bu nedenle `<pre>` özellikle biçimin metnin bir parçası olduğu içeriklerde kullanılabilir.

### `<pre>` ve `<code>` Birlikte Kullanımı
Kod örneklerinde sıklıkla:
```
    <pre><code>const message = "Merhaba Dünya";
    console.log(message);</code></pre>
```
kullanımıyla karşılaşırız.

Burada iki element farklı görevler üstlenir:
```
    <pre> → Boşlukları ve satır kırılmalarını korur.
    <code> → İçeriğin bilgisayar kodu olduğunu belirtir.
```
Yani `<pre>` tek başına `Bu bir kod örneğidir.` anlamına gelmez. Kod içeriğini semantik olarak belirtmek için `<code>` kullanılır.

## `<mark>, <sub> ve <sup>`
Bu elementler metnin belirli bölümlerine özel anlamlar kazandırmak için kullanılır.

### 1. `<mark>` — Bağlama Göre Öne Çıkarma
`<mark>` elementi mevcut bağlam açısından ilgili veya dikkat çekilmesi gereken bir metni işaretler.

Örneğin kullanıcı: `HTML` kelimesini aramış olsun.

Arama sonucunda:
```
    <p>
        Modern web geliştirmede
        <mark>HTML</mark>
        temel teknolojilerden biridir.
    </p>
```
şeklinde eşleşen bölüm işaretlenebilir.

Tarayıcılar mark elementini genellikle sarı arka planla gösterir. Ancak yine önemli olan renk değil, **bağlamsal olarak ilgili içeriğin işaretlenmesidir.**

### 2. `<sub>` — Alt Simge
`<sub>` elementi subscript, yani alt simge içindir.

Örneğin suyun kimyasal formülü:
```
    H<sub>2</sub>O
```
tarayıcıda:
```
    H₂O
```
şeklinde temsil edilir.

Başka bir örnek: `CO<sub>2</sub>`

### 3. `<sup>` — Üst Simge
`<sup>` elementi superscript, yani üst simge içindir.

Örneğin: `x<sup>2</sup>` şu ifadeyi temsil eder: `x²`

Dipnot işaretlerinde de kullanılabilir:
```
    <p>
        HTML ilk olarak 1990'lı yıllarda geliştirildi.<sup>1</sup>
    </p>
```
sub ve sup yalnızca metni küçültüp yukarı veya aşağı taşımak için kullanılmamalıdır.
```
    Anlam alt simge gerektiriyor → sub
    Anlam üst simge gerektiriyor → sup
    Sadece görsel olarak küçük yazı istiyorum → CSS
```

## Grouping Text: `<div>` ve `<span>`
HTML'de içeriği gruplamak için sıklıkla `<div>` ve `<span>` elementleriyle karşılaşırız. Bu iki element kendi başlarına özel bir semantik anlam taşımaz.

### 1. `<div>`
`<div>` genel amaçlı bir block kapsayıcıdır.

Örneğin:
```
    <div class="product-info">

        <h2>Kol Saati</h2>

        <p>12.500 TL</p>

</div>
```
Burada farklı elementleri tek bir yapı altında grupluyoruz.

### 2. `<span>`
`<span>` genel amaçlı inline kapsayıcıdır.

Örneğin:
```
    <p>
        Ürün fiyatı:
        <span class="price">12.500 TL</span>
    </p>
```
**span** metin akışının içerisinde belirli bir bölümü gruplamamızı sağlar.

**`<div>` ve `<span>` Ne Zaman Kullanılır?**
Bu elementler özellikle:
- CSS ile stil uygulamak,
- JavaScript ile belirli bir bölümü hedeflemek,
- İçeriği teknik olarak gruplamak
gerektiğinde kullanılabilir.

Ancak önce şu soru sorulmalıdır: `Bu içeriğin anlamını karşılayan daha uygun bir HTML elementi var mı?`

Örneğin navigasyon için:
```
    <div class="navigation">
```
yerine uygun bağlamda `<nav>` kullanmak daha anlamlı olabilir.

***div ve span:*** Uygun bir semantik element bulunmadığında kullanılan genel amaçlı kapsayıcılardır.

Temel fark:

|<div>      |<span>     |
|-----------|-----------|
|Genel amaçlı kapsayıcı |Genel amaçlı kapsayıcı|
|Doğal olarak block düzeyinde | Doğal olarak inline düzeyinde|
|Daha büyük içerik gruplarında sık kullanılır | Satır içindeki küçük bölümlerde sık kullanılır|
|Kendi başına semantik anlam taşımaz    | Kendi başına semantik anlam taşımaz   |

## Değişiklikleri İşaretleme: `<del>, <ins> ve <s>`
Bir belgedeki değişiklikleri veya artık geçerli olmayan bilgileri ifade etmek için farklı HTML elementleri bulunur.

Bunların anlamları birbirine karıştırılmamalıdır.

### 1. `<del>` — Silinen İçerik
`<del>` belgeden silinmiş veya kaldırılmış içeriği temsil eder.

Örneğin:
```
    <p>
        Kampanya tarihi:
        <del>20 Eylül</del>
        30 Eylül
    </p>
```
Burada 20 Eylül bilgisinin belgeden kaldırılmış/değiştirilmiş olduğu ifade edilir.

### 2. `<ins>` — Eklenen İçerik
`<ins>` belgeye sonradan eklenmiş içeriği temsil eder. **del** ile birlikte kullanılabilir:
```
    <p>
        Kampanya tarihi:
        <del>20 Eylül</del>
        <ins>30 Eylül</ins>
    </p>
```
Böylece:
```
    20 Eylül → Silinen içerik
    30 Eylül → Eklenen içerik
```
ilişkisi kurulabilir.

**cite Attribute'u**

del ve ins elementlerinde değişikliğin nedenini veya açıklamasını sağlayan bir kaynağın URL'sini belirtmek için cite attribute'u kullanılabilir.

Örneğin:
```
    <del cite="https://example.com/change-log">
        Eski içerik
    </del>
```
Buradaki cite kullanıcıya otomatik olarak görünür bir bağlantı oluşturmaz. Değişiklik hakkında kaynak bilgisi sağlayan metadata niteliğindedir.

**datetime Attribute'u**

Değişikliğin zamanını makine tarafından okunabilir biçimde belirtmek için datetime kullanılabilir.
```
    <ins datetime="2026-09-27">
        Yeni içerik
    </ins>
```
veya zaman bilgisiyle:
```
    <del datetime="2026-09-27T14:30:00+03:00">
        Eski içerik
    </del>
```
Bu bilgiler kullanıcıya otomatik olarak gösterilmek zorunda değildir.

### 3. `<s>` — Artık Geçerli Olmayan Bilgi
`<s>` elementi artık doğru, geçerli veya güncel olmayan bilgileri temsil edebilir.

Örneğin eski fiyat:
```
    <p>
        <s>15.000 TL</s>
        12.500 TL
    </p>
```
Burada eski fiyatın belgeden yapılan bir düzenleme sonucu silindiğini anlatmak zorunda değiliz. Sadece `Bu bilgi artık geçerli değil.` anlamı vardır.

**`<del>` ve `<s>` Farkı**
İkisi tarayıcıda üstü çizili görünebilir. Ancak anlamları farklıdır.

|Element    |Anlam          |
|-----------|---------------|
|<del>      |Belgeden silinen/kaldırılan içerik|
|<s>        |Artık doğru veya geçerli olmayan içerik|

Örneğin doküman değişikliğini göstermek için **del** ve **ins** anlamlıdır.
```
    <del>Eski teslimat süresi: 5 gün</del>
    <ins>Yeni teslimat süresi: 3 gün</ins>
```

Eski ürün fiyatını göstermek için ise **s** uygun olabilir.
```
    <s>15.000 TL</s>
    <strong>12.500 TL</strong>
```
## Alıntı, Kaynak ve Tanımlamalar
HTML yalnızca normal paragrafları değil;
- Alıntıları,
- Kaynakları,
- Kısaltmaları,
- Terim tanımlarını,
- İletişim bilgilerini de semantik olarak işaretleyebilir.

Bu bölümde:
```
    blockquote
    q
    cite
    abbr
    dfn
    address
```
elementlerini inceleyeceğiz.

### 1. `<blockquote>` — Blok Alıntı
Başka bir kaynaktan alınan, genellikle daha uzun ve ayrı bir bölüm olarak sunulan alıntılar için `<blockquote>` kullanılabilir.

Örneğin:
```
    <blockquote>
        <p>
            Web'in gücü evrenselliğindedir.
        </p>
    </blockquote>
```
Kaynak URL'si cite attribute'u ile belirtilebilir:
```
    <blockquote cite="https://example.com/source">
        <p>
            Alıntılanan içerik.
        </p>
    </blockquote>
```
Buradaki cite attribute'u kaynağı makine tarafından okunabilir biçimde ilişkilendirebilir; ancak tarayıcı bu URL'yi kullanıcıya otomatik olarak görünür bir kaynak bağlantısı şeklinde sunmak zorunda değildir.

Kullanıcının kaynağı görebilmesi gerekiyorsa bunu görünür içerikte ayrıca sunmak gerekir.

### 2. `<q>` — Satır İçi Alıntı
Kısa ve metin akışının içerisinde bulunan alıntılar için `<q>` kullanılabilir.

Örneğin:
```
    <p>
        Eğitmen,
        <q>Semantik HTML kullanmaya dikkat edin.</q>
        dedi.
    </p>
```
Temel fark:
```
    <blockquote> → Ayrı bir blok oluşturan alıntı
    <q> → Metin içerisindeki kısa alıntı
```
**q** için de kaynak URL'si cite attribute'u ile ilişkilendirilebilir.

### 3. `<cite>` — Eser veya Kaynak Başlığı
`<cite>` elementi yaratıcı bir eserin başlığını/referansını işaretlemek için kullanılabilir.

Örneğin:
```
    <p>
        <cite>Clean Code</cite>
        yazılım geliştirme üzerine bilinen eserlerden biridir.
    </p>
```
Burada önemli bir ayrım vardır `<cite>...</cite>` ile `<blockquote cite="...">` aynı şey değildir.

**`<cite>` Elementi ve cite Attribute'u**

**- <cite> elementi**

Görünür içerikte bir eserin başlığını/referansını işaretler. `<cite>Clean Code</cite>`

**- cite attribute'u**

blockquote, q, del ve ins gibi belirli elementlerde kaynağı/açıklayıcı kaynağı URL olarak belirtmek için kullanılabilir. `<blockquote cite="https://example.com/source">`

Dolayısıyla cite elementi ve cite attribute'u aynı şey değildir.
```
    <cite> → HTML elementi
    cite="" → HTML attribute'u
```

Bu ayrım özellikle önemlidir çünkü isimlerinin aynı olması sıkça karıştırılmalarına neden olur.

### 4. `<abbr>` — Kısaltma
`<abbr>` bir kısaltmayı veya akronimi işaretlemek için kullanılabilir.
Örneğin:
```
    <p>
        <abbr title="HyperText Markup Language">HTML</abbr>
        bir işaretleme dilidir.
    </p>
```
Buradaki `title="HyperText Markup Language"` kısaltmanın açılımı hakkında ek bilgi sağlayabilir.

Ancak önemli bilgileri yalnızca **title tooltip**'ine bırakmak erişilebilirlik açısından yeterli bir yaklaşım değildir.

Gerekli durumlarda açılımı görünür metinde de vermek daha doğru olabilir:
```
    <p>
        HyperText Markup Language (<abbr>HTML</abbr>)
        web sayfalarının yapısını tanımlamak için kullanılır.
    </p>
```
**title** global attribute'u ilgili **Global Attributes** bölümünde ayrıca incelenmektedir.

### 5.`<dfn>` — Tanımlanan Terim
`<dfn>` elementi bir terimin tanımlandığı yeri işaretlemek için kullanılır.

Örneğin:
```
    <p>
        <dfn>Semantic HTML</dfn>,
        HTML elementlerinin içerikteki anlamlarına uygun olarak kullanılmasıdır.
    </p>
```
Burada yalnızca "Semantic HTML" ifadesini italik göstermek istemiyoruz.

Şunu ifade ediyoruz: **Bu noktada "Semantic HTML" terimini tanımlıyoruz.**

Dolayısıyla `<dfn>` özellikle teknik dokümantasyon ve eğitim içeriklerinde kullanışlı olabilir.

### 6. `<address>` — İletişim Bilgisi
`<address>` elementi sık yanlış anlaşılan HTML elementlerinden biridir.

İsminden dolayı `Her fiziksel adres **<address>** içerisinde yazılmalıdır.` şeklinde düşünülebilir. Bu doğru değildir.

**address**, ilgili **article** veya sayfanın/belgenin **iletişim bilgilerini temsil etmek** için kullanılır.

Örneğin:
```
    <address>
        Büşra Öztürk<br>
        E-posta:
        <a href="mailto:example@example.com">
            example@example.com
        </a>
    </address>
```
Bir şirket sayfasında:
```
    <footer>

        <address>
            Example Teknoloji<br>
            <a href="mailto:info@example.com">
                info@example.com
            </a>
        </address>

    </footer>
```
gibi kullanılabilir.

Ancak bir makalede `Etkinlik Atatürk Caddesi No: 20 adresinde yapılacaktır.` şeklinde yalnızca konum belirten bir posta adresi bulunması, tek başına `<address>` kullanmamız gerektiği anlamına gelmez.

Temel soru:
```
    Bu bir iletişim bilgisi mi?
            │
            ├── Evet → address uygun olabilir.
            │
            └── Hayır → address olmak zorunda değil.
```