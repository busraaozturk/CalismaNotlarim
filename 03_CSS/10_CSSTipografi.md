# CSS Tipografi (Typography)
Tipografi, bir web sayfasındaki metinlerin **okunabilir, anlaşılır ve görsel olarak düzenli** sunulmasını sağlayan tasarım ve düzenleme sürecidir.

CSS ile yalnızca yazı tipini veya boyutunu değiştirmeyiz. Metnin kalınlığını, satır yüksekliğini, harf aralıklarını, hizalamasını, dekorasyonunu ve farklı ekranlarda nasıl görüneceğini de kontrol ederiz.

Örneğin aynı içerik, farklı tipografi özellikleriyle çok farklı bir kullanıcı deneyimi oluşturabilir.

```
    .title {
        font-family: Arial, sans-serif;
        font-size: 2rem;
        font-weight: 700;
        line-height: 1.2;
    }

    .description {
        font-size: 1rem;
        line-height: 1.6;
        color: #666;
    }
```

Bu örnekte başlık daha büyük ve kalın, açıklama ise daha rahat okunabilecek satır aralığıyla tanımlanmıştır.

Bu bölümde CSS'in font ve metin özelliklerini, kullanım amaçlarını ve gerçek projelerde dikkat edilmesi gereken noktaları inceleyeceğiz.

## Tipografi Nedir?
Web tasarımında tipografi, metnin hem görünümünü hem de okunabilirliğini etkileyen özelliklerin bütünüdür.

Bir sayfada başlıkların, açıklamaların, bağlantıların ve buton yazılarının birbirinden ayırt edilebilmesi için tutarlı bir tipografi sistemi kullanılır.

CSS'te tipografiyle ilgili özellikleri genel olarak üç gruba ayırabiliriz.

|Grup               |İlgili özellikler                                  |Amacı           |
|-------------------|---------------------------------------------------|----------------|
|Font özellikleri   |font-family, font-size, font-weight, font-style    |Yazı karakterinin görünümünü belirlemek|
|Metin özellikleri  |text-align, text-decoration, text-transform, text-shadow|Metnin sunumunu düzenlemek |
|Metin boşlukları   |line-height, letter-spacing, word-spacing|Okunabilirliği ve metin aralıklarını yönetmek|

Örneğin bir haber sitesinde başlıkların dikkat çekici, uzun paragrafların ise rahat okunabilir olması beklenir.

Bir yönetim panelinde ise gereğinden büyük yazılar, bilgi yoğun ekranlarda kullanılabilirliği azaltabilir.

Bu nedenle iyi bir tipografi sistemi yalnızca estetik değil, aynı zamanda işlevsel olmalıdır.

## font-family - Font Aileleri
font-family, bir HTML elementinin hangi yazı karakteri ailesiyle görüntüleneceğini belirler.

### Temel Kullanım
```
    body {
        font-family: Arial, sans-serif;
    }
```

Bu örnekte tarayıcı önce `Arial` fontunu kullanmayı dener. Arial kullanılamıyorsa `sans-serif` kategorisinden uygun bir font seçer.

### Fallback Zinciri
Birden fazla fontu virgülle ayırarak öncelik sırası oluşturabiliriz.
```
    body {
        font-family: "Segoe UI", Arial, Helvetica, sans-serif;
    }
```

Tarayıcı fontları sırasıyla değerlendirir:
- Segoe UI
- Arial
- Helvetica
- sans-serif

İlk font cihazda veya tanımlanmış web fontları arasında bulunmuyorsa sonraki font değerlendirilir.

Ayrıca seçilen font belirli bir karakteri desteklemiyorsa tarayıcı o karakter için başka bir font kullanabilir.

Bu yapıya **font fallback zinciri** denir.

### Genel Font Kategorileri
CSS'te belirli bir font adı yerine genel font aileleri kullanılabilir.

|Genel aile     |Açıklama                               |Kullanım                        |
|---------------|---------------------------------------|--------------------------------|
|serif          |Karakter uçlarında küçük çıkıntılar bulunabilen fontlar|Editoryal tasarımlar, uzun metinler|
|sans-serif     |Genellikle çıkıntısız ve sade fontlar|Web arayüzleri, dashboard    |
|monospace      |Karakterlerin aynı ilerleme genişliğine sahip olduğu fontlar| Kod blokları, teknik veriler|
|cursive        |El yazısını andıran fontlar        |Dekoratif başlıklar            |
|fantasy        |Dekoratif font kategorisi          |Özel tasarımlar                |

Örnekler: 
```
    .heading {
        font-family: Georgia, serif;
    }

    .description {
        font-family: Arial, sans-serif;
    }

    .code {
        font-family: Consolas, "Courier New", monospace;
    }
```

### Font İsimlerinde Tırnak Kullanımı
Bir font adı birden fazla kelimeden oluşuyorsa tırnak kullanmak iyi bir uygulamadır.
```
    .title {
        font-family: "Segoe UI", "Times New Roman", serif;
    }
```
Tek kelimelik font adlarında tırnak zorunlu değildir.
```
    .title {
        font-family: Arial, sans-serif;
    }
```
Önemli: Fallback zincirinin sonuna sans-serif, serif veya monospace gibi bir genel font ailesi eklemek, tercih edilen fontların bulunmadığı ortamlarda daha öngörülebilir bir sonuç sağlar.

## font-size - Yazı Boyutu
font-size, metnin yazı boyutunu belirler.
```
    p {
        font-size: 16px;
    }
```
Yazı boyutunu farklı CSS birimleriyle tanımlayabiliriz.
```
    .title {
        font-size: 32px;
    }

    .subtitle {
        font-size: 2rem;
    }

    .description {
        font-size: 1em;
    }

    .small-text {
        font-size: 90%;
    }

    .hero-title {
        font-size: 4vw;
    }
```

### Kullanılabilen Birimler
|Birim      |Açıklama                   |
|-----------|---------------------------|
|px         |CSS pikseli                |
|rem        |Kök elementin font boyutuna göre   |
|em         |font-size için üst elementin hesaplanmış font boyutuna göre    |
|%          |Üst elementin font boyutuna göre   |
|vw         |Viewport genişliğine göre  |

### Neden Genellikle rem Tercih Edilir?
rem, kök elementin (html) font boyutunu temel alır.
```
    html {
        font-size: 100%;
    }

    body {
        font-size: 1rem;
    }

    h1 {
        font-size: 2rem;
    }
```

Tarayıcının varsayılan font boyutu 16px ise:
- 1rem yaklaşık 16px,
- 2rem yaklaşık 32px olur

Ancak kullanıcının tarayıcı ayarları farklıysa bu değerler de değişebilir. Bu nedenle rem, kullanıcının tercih ettiği varsayılan yazı boyutuna uyum sağlamayı kolaylaştırır.

**Erişilebilirlik notu:** rem kullanmak tek başına erişilebilir bir tasarım oluşturmaz. Metnin yakınlaştırıldığında taşmaması, okunabilir kontrasta sahip olması ve esnek yerleşimlerle desteklenmesi de önemlidir.

## font-weight - Yazı Kalınlığı
font-weight, yazının kalınlığını belirler.

### Anahtar Kelimeler
```
    .normal {
        font-weight: normal;
    }

    .bold {
        font-weight: bold;
    }

    .light {
        font-weight: lighter;
    }

    .strong {
        font-weight: bolder;
    }
```

|Değer                      |Açıklama                                   |
|---------------------------|-------------------------------------------|
|normal                     |Normal kalınlık; 400 ile eş değer          |
|bold                       |Kalın yazı; 700 ile eş değer               |
|lighter                    |Üst elemente göre daha hafif göreli ağırlık|
|bolder                     |Üst elemente göre daha kalın göreli ağırlık|

lighter ve bolder değerleri doğrudan belirli bir sayıya karşılık gelmez; üst elementin ağırlığına göre değerlendirilir.

### Sayısal Değerler
```
    .title {
        font-weight: 700;
    }

    .description {
        font-weight: 400;
    }

    .caption {
        font-weight: 300;
    }
```

Yaygın ağırlık adları:
|Değer          |Yaygın isim            |
|---------------|-----------------------|
|100            |Thin                   |
|200            |Extra Light            |
|300            |Light                  |
|400            |Regular                |
|500            |Medium                 |
|600            |Semi Bold              |
|700            |Bold                   |
|800            |Extra Bold             |
|900            |Black                  |

Bu isimler yaygın tasarım adlandırmalarıdır; her fontun bütün ağırlıkları sunması gerekmez. Modern CSS, özellikle variable fontlarla, bu aralıktaki ara sayısal değerleri de destekler.

### Her Font Bütün Ağırlıkları Destekler mi?
Hayır. Örneğin kullanılan font yalnızca 400 ve 700 ağırlıklarını içeriyor olabilir.
```
    .title {
        font-weight: 600;
    }
```

Tarayıcı, font eşleştirme kurallarına göre mevcut uygun ağırlıklardan birini seçebilir veya koşullara bağlı olarak sentetik kalınlaştırma uygulayabilir.

Dolayısıyla 600 yazmak, her zaman fontun gerçek Semi Bold tasarımının kullanılacağı anlamına gelmez.

**Öneri:** Web font yüklerken gerçekten kullandığımız ağırlıkları seçmeliyiz.

## font-style - Yazı Stili
font-style, yazının normal veya eğik görüntülenmesini sağlar.

Temel değerler:
```
    .normal {
        font-style: normal;
    }

    .italic {
        font-style: italic;
    }

    .oblique {
        font-style: oblique;
    }
```

### italic ve oblique Arasındaki Fark
**italic**, font ailesinde özel olarak tasarlanmış italik karakterleri tercih eder.

**oblique**, eğik yazı stilini ifade eder; uygun oblique yüzü bulunmadığında tarayıcı normal karakterleri eğerek oluşturabilir.

|Değer          |Temel anlamı                                       |
|---------------|---------------------------------------------------|
|normal         |Normal yazı                                        |
|italic         |İtalik font yüzü tercih edilir                     |
|oblique        |Eğik font yüzü veya sentetik eğim kullanılabilir   |

İlgili font stili bulunmadığında tarayıcı alternatif eşleştirme ya da sentetik stil uygulayabileceğinden, iki değer arasındaki görsel fark her zaman belirgin olmayabilir.

Örnek
```
    .quote {
        font-style: italic;
    }
```
Bu kullanım alıntı metinlerinin görsel olarak ayrıştırılmasına yardımcı olabilir.

Ancak alıntının anlamsal olarak belirtilmesi gerekiyorsa HTML'de uygun elementlerin (blockquote, q gibi) kullanılması gerekir.

## font-variant - Font Varyantları
font variant, fontun belirli tipografik varyantlarını kullanmayı sağlar. Başlangıç seviyesinde en sık karşılaşılan değerlerden biri small-caps değeridir.

```
    .label {
        font-variant: small-caps;
    }
```

### small-caps Nedir?
Small caps, küçük harflerin büyük harf biçiminde ancak genellikle daha küçük boyutlarda gösterilmesidir.

Örneğin bir kategori etiketi veya dekoratif alt başlıkta kullanılabilir.

```
    .section-label {
        font-variant: small-caps;
        letter-spacing: 0.08em;
    }
```

Font gerçek small-caps karakterlerini destekliyorsa tarayıcı bunları kullanabilir; desteklemiyorsa uygun koşullarda benzer görünümü sentetik olarak oluşturabilir.

font-variant ailesi ayrıca ligatürler, sayısal karakter biçimleri ve diğer OpenType özellikleriyle ilgili alt özellikler içerir.

Temel CSS öğrenme aşamasında small-caps kullanımını bilmek yeterlidir.

## font Shorthand
font, birden fazla font özelliğini tek declaration içinde tanımlamamızı sağlayan shorthand özelliğidir.

Örneğin:
```
    .title {
        font-style: italic;
        font-weight: bold;
        font-size: 16px;
        line-height: 1.5;
        font-family: Arial, sans-serif;
    }
```
Bu özellikler daha kısa yazılabilir:
```
    .title {
        font: italic bold 16px/1.5 Arial, sans-serif;
    }
```

### Genel Sözdizimi
```
    font: font-style font-variant font-weight font-size/line-height font-family;
```

Burada sıralamanın bazı bölümleri esnek olsa da önemli kurallar vardır.
- font-size zorunludur.
- font-family zorunludur.
- line-height kullanılıyorsa font-size değerinden hemen sonra / ile yazılır.
- font-size ve font-family öncesindeki isteğe bağlı özellikler kendi geçerli sözdizimlerine uygun kullanılmalıdır.

Örnekler
```
    p {
        font: 16px Arial, sans-serif;
    }

    h2 {
        font: 700 2rem/1.3 "Segoe UI", sans-serif;
    }

    .quote {
        font: italic small-caps 600 1rem/1.6 Georgia, serif;
    }
```

### Shorthand Kullanırken Dikkat
font shorthand yalnızca belirtilen özellikleri değiştirmez; kapsadığı bazı diğer font özelliklerini de başlangıç değerlerine sıfırlayabilir.

Örneğin:
```
    .text {
        font-weight: 700;
        font: 16px Arial, sans-serif;
    }
```
İkinci declaration, önceki font-weight: 700 değerini sıfırlar ve yazı normal ağırlığa döner.

Öneri: Bir bileşenin yalnızca tek bir font özelliğini değiştireceksen ilgili property'yi doğrudan kullanmak daha anlaşılır olabilir.

## line-height - Satır Yüksekliği
line-height, metnin satır kutularının yüksekliğini etkileyerek çok satırlı metinlerin dikey aralığını düzenler.

```
    p {
        font-size: 16px;
        line-height: 1.5;
    }
```

Bu örnekte satır yüksekliği, ilgili elementin font boyutunun 1.5 katı olarak hesaplanır.

16px font boyutunda yaklaşık 24px satır yüksekliği elde edilir.

### Kullanılabilen Değerler
```
    .text-1 {
        line-height: normal;
    }

    .text-2 {
        line-height: 1.5;
    }

    .text-3 {
        line-height: 24px;
    }

    .text-4 {
        line-height: 150%;
    }
```

### Birimsiz line-height Neden Önemli?
Şu örneği inceleyelim:
```
    .parent {
        font-size: 20px;
        line-height: 1.5;
    }

    .child {
        font-size: 12px;
    }
```

Birimsiz 1.5 değeri miras alındığında, çocuk element kendi font boyutuna göre satır yüksekliğini hesaplar.
- Parent: 20px × 1.5 = 30px
- Child: 12px × 1.5 = 18px

Şimdi birimli bir değer kullanalım:

```
    .parent {
        font-size: 20px;
        line-height: 30px;
    }

    .child {
        font-size: 12px;
    }
```

Çocuk element line-height: 30px değerini miras alır.

Bu, küçük yazı boyutuna göre gereğinden fazla satır yüksekliği oluşturabilir.

Benzer şekilde yüzdeyle tanımlanan line-height değerleri de üst elementte hesaplanıp çocuklara hesaplanmış uzunluk olarak aktarılabilir.

### Pratik Kullanım
```
    body {
        line-height: 1.5;
    }

    h1,
    h2,
    h3 {
        line-height: 1.2;
    }

    p {
        line-height: 1.6;
    }
```

Uzun paragraflarda daha rahat bir satır aralığı, büyük başlıklarda ise daha sıkı bir düzen tercih edilebilir.

Bunlar kesin kurallar değildir; font ailesi, yazı boyutu ve tasarımın ihtiyacına göre değerlendirilmelidir.

## text-align - Metin Hizalama
text-align, bir blok içindeki satır içi içeriğin hizalanmasını kontrol eder.

Yaygın değerler:
```
    .left {
        text-align: left;
    }

    .right {
        text-align: right;
    }

    .center {
        text-align: center;
    }

    .justify {
        text-align: justify;
    }
```

### Değerlerin Anlamı
|Değer              |Açıklama                   |
|-------------------|---------------------------|
|left               |Metni sola hizalar         |
|right              |Metni sağa hizalar         |
|center             |Metni ortalar              |
|justify            |Uygun satırlardaki boşlukları dağıtarak iki kenarı hizalamaya çalışır|

Örnek:
```
    <div class="article">
        <h2>CSS Tipografi</h2>
        <p>CSS ile metinlerin görünümünü düzenleyebiliriz.</p>
    </div>

    .article h2 {
        text-align: center;
    }

    .article p {
        text-align: left;
    }
```

### justify Kullanırken Dikkat
```
    p {
        text-align: justify;
    }
```

Bu kullanım bazı satırlarda kelimeler arasındaki boşlukları fazla genişletebilir.

Özellikle dar mobil ekranlarda okunabilirliği olumsuz etkileyebilir.

Bu nedenle uzun metinlerde justify kullanımını gerçek içerik ve farklı ekran genişlikleriyle test etmek gerekir.

### start ve end Değerleri
Modern CSS'te yazı yönüne duyarlı değerler de bulunur.
```
    .description {
        text-align: start;
    }

    .price {
        text-align: end;
    }
```

start ve end, metnin yazı yönüne göre hizalanır.

Çok dilli arayüzlerde fiziksel left ve right değerlerine göre daha esnek olabilir.

**Not:** text-align: center, bir blok elementin kendisini ortalamaz; blok içindeki satır içi içeriğin hizalamasını etkiler. Blokların yerleşimi için Flexbox, Grid veya uygun margin teknikleri kullanılabilir.

## text-decoration - Metin Dekorasyonu
text-decoration, metne alt çizgi, üst çizgi veya üzeri çizili görünüm kazandırır. 

Temel Değerler
```
    .underline {
        text-decoration: underline;
    }

    .overline {
        text-decoration: overline;
    }

    .deleted {
        text-decoration: line-through;
    }

    .none {
        text-decoration: none;
    }
```

|Değer                  |Açıklama                           |
|-----------------------|-----------------------------------|
|underline              |Metnin altını çizer                |
|overline               |Metnin üstünü çizer                |
|line-through           |Metnin üzerini çizer               |
|none                   |Dekorasyon çizgisini kaldırır      |

### Alt Özellikler
Dekorasyon çizgisinin rengini ve stilini de değiştirebiliriz.
```
    .link {
        text-decoration-line: underline;
        text-decoration-color: #7d8570;
        text-decoration-style: solid;
        text-decoration-thickness: 2px;
    }
```

Yaygın çizgi stilleri:
- solid
- double
- dotted
- dashed
- wavy

Örneğin:
```
    .highlight {
        text-decoration: underline wavy #7d8570;
    }
```

### Linklerde Alt Çizgiyi Kaldırmak
Tarayıcılar bağlantıları genellikle altı çizili olarak gösterir.
```
    a {
        text-decoration: none;
    }
```

Bu kullanım bağlantının görsel olarak fark edilmesini zorlaştırabilir.

Özellikle normal paragraf metninin içinde yer alan bağlantılarda yalnızca renge güvenmek yerine alt çizgi gibi ek bir görsel işaret kullanmak daha güvenlidir.

Örnek:
```
    .article a {
        color: #315b8a;
        text-decoration: underline;
        text-underline-offset: 3px;
    }

    .article a:hover {
        text-decoration-thickness: 2px;
    }

    .article a:focus-visible {
        outline: 2px solid currentColor;
        outline-offset: 3px;
    }
```

Burada **text-underline-offset**, alt çizginin metne olan mesafesini düzenler.

**focus-visible** ise klavye kullanıcıları için odak göstergesi sağlar.

Bu konu, önceki bölümlerde ele alınan erişilebilir odak göstergeleriyle doğrudan ilişkilidir.

## text-transform - Büyük / Küçük Harf Dönüşümü
text-transform, metnin görsel olarak büyük veya küçük harfe dönüştürülmesini sağlar.

### Temel Değerler
```
    .uppercase {
        text-transform: uppercase;
    }

    .lowercase {
        text-transform: lowercase;
    }

    .capitalize {
        text-transform: capitalize;
    }

    .normal {
        text-transform: none;
    }
```

|Değer                  |Açıklama                               |
|-----------------------|---------------------------------------|
|uppercase              |Harfleri büyük harf olarak gösterir.   |
|lowercase              |Harfleri küçük harf olarak gösterir.   |
|capitalize             |Kelimelerin başlangıç karakterlerini büyük harfe dönüştürür.   |
|none                   |Dönüşüm uygulamaz                      |

Örnek:
```
    <p class="category">web development</p>

    .category {
        text-transform: uppercase;
    }
```

Görsel Sonuç: `WEB DEVELOPMENT` Ancak HTML içindeki metin hâlâ **web development** olarak kalır.

### capitalize Hakkında
```
    .title {
        text-transform: capitalize;
    }
```
Bu özellik, CSS'in kelime ve karakter dönüştürme kurallarına göre çalışır. Her dil için dilbilgisel açıdan doğru başlık biçimlendirmesi oluşturacağı varsayılmamalıdır.

Özellikle Türkçedeki i, ı, İ ve I dönüşümlerinde doğru dil bilgisinin belirtilmesi önemlidir.
```
    <p lang="tr" class="title">istanbul ve izmir</p>
```

### Erişilebilirlik Notu
text-transform yalnızca görsel sunumu etkiler; kaynak metni değiştirmez.

Bununla birlikte bazı ekran okuyucular, özellikle tamamen büyük harfle görüntülenen veya kısaltma gibi algılanan metinleri farklı seslendirebilir.

Bu nedenle bütün uzun paragrafları büyük harfe dönüştürmekten kaçınmak iyi bir uygulamadır.

## text-shadow - Metin Gölgesi
text-shadow, metnin arkasına gölge eklememizi sağlar.

Sözdizimi : `text-shadow: offset-x offset-y blur-radius color;`

Örnek:
```
    .title {
        text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.25);
    }
```
Burada:
- İlk 2px: gölgenin yatay uzaklığı
- İkinci 2px: gölgenin dikey uzaklığı
- 4px: bulanıklık yarıçapı
- rgba(...): gölgenin rengi

### Birden Fazla Gölge
Virgülle birden fazla gölge tanımlanabilir.
```
    .title {
        text-shadow:
            1px 1px 2px rgba(0, 0, 0, 0.2),
            3px 3px 8px rgba(0, 0, 0, 0.1);
    }
```

### box-shadow ile Farkı
|Özellik                    |Etkilediği alan                            |
|---------------------------|-------------------------------------------|
|text-shadow                |Metin karakterlerinin görsel gölgesi       |
|box-shadow                 |Elementin kutusunun gölgesi                |

**box-shadow** özelliğini **05 — CSS Box Model** bölümünde incelemiştik.

**Öneri:** Özellikle küçük yazılarda yoğun metin gölgeleri okunabilirliği azaltabilir. Gölgeyi dekoratif amaçla ve ölçülü kullanmak daha uygundur.

## Metin Boşlukları - Text Spacing
Metnin okunabilirliğini etkileyen önemli özelliklerden biri boşluk yönetimidir.

Bu bölümde üç temel özelliği birlikte değerlendirebiliriz:
- letter-spacing
- word-spacing
- line-height

### 1. letter-spacing - Harfler Arası Boşluk
```
    .title {
        letter-spacing: 2px;
    }
```
Harflerin arasındaki boşluğu değiştirir. Negatif değerler de kullanılabilir.
```
    .heading {
        letter-spacing: -0.02em;
    }
```
Negatif değerler harfleri birbirine yaklaştırabilir.

Örneğin küçük ve büyük harflerden oluşan uzun metinlerde aşırı sıkıştırma okunabilirliği azaltabilir.

### 2. word-spacing - Kelimeler Arası Boşluk
```
    .description {
        word-spacing: 4px;
    }
```
Kelimeler arasındaki boşlukları düzenler.

Özellikle uzun metinlerde gereğinden fazla kelime aralığı vermek okumayı zorlaştırabilir.

### 3. line-height - Satır Aralığı
```
    .description {
        line-height: 1.6;
    }
```
Çok satırlı metinlerin dikey düzenini etkiler.

### Karşılaştırma
|Property                       |Etkilediği boşluk                              |
|-------------------------------|-----------------------------------------------|
|letter-spacing                 |Karakterler arası                              |
|word-spacing                   |Kelimeler arası                                |
|line-height                    |Satır kutularının yüksekliği                   |

### Gerçek Kullanım Örneği
```
    .card-label {
        font-size: 0.75rem;
        font-weight: 600;
        letter-spacing: 0.08em;
        text-transform: uppercase;
    }

    .card-title {
        font-size: 1.5rem;
        line-height: 1.25;
        letter-spacing: -0.02em;
    }

    .card-description {
        font-size: 1rem;
        line-height: 1.6;
    }
```

Burada küçük etiket, başlık ve açıklama için farklı tipografik düzenler oluşturulmuştur. Bu yaklaşım, bir arayüzde **görsel hiyerarşi** oluşturmanın temel yollarından biridir.

## Google Fonts ile Harici Font Kullanımı
Tarayıcıların ve işletim sistemlerinin sunduğu fontlarla sınırlı değiliz.

Google Fonts gibi servislerden web fontları yükleyebiliriz.

### 1. `<link>` ile Font Yükleme
Örneğin Google Fonts üzerinden Inter fontunu kullanalım. Html dosyasının `<head>` bölümüne aşağıdaki bağlantıları ekleyebiliriz:
```
    <head>
        <meta charset="UTF-8">

        <link rel="preconnect" href="https://fonts.googleapis.com">
        <link
            rel="preconnect"
            href="https://fonts.gstatic.com"
            crossorigin
        >

        <link
            href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap"
            rel="stylesheet"
        >
    </head>
```

Ardından CSS'te kullanabiliriz:
```
    body {
        font-family: "Inter", Arial, sans-serif;
    }
```
Bu örnekte Inter fontunun 400, 500, 600 ve 700 ağırlıkları istenmektedir.

### display = swap Nedir?
Google Fonts bağlantısındaki: `display = swap` parametresi, **font-display: swap** davranışının kullanılmasını sağlar.

Tarayıcı web fontu yüklenirken fallback fontla metni gösterebilir ve web fontu hazır olduğunda yazı karakterini değiştirebilir.

Bu yaklaşım metnin görünür kalmasına yardımcı olur; ancak font değişiminden kaynaklanan yerleşim kaymaları yine de yaşanabilir.

### 2. @import ile Font Yükleme
Alternatif olarak CSS içerisinde @import kullanılabilir.
```
    @import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap");

    body {
        font-family: "Inter", sans-serif;
    }
```
**@import** kuralları, CSS dosyasının başında, izin verilen diğer başlangıç kurallarından sonra ve normal stil kurallarından önce yer almalıdır.

### `<link>` mi, @import mı?

Genellikle HTML `<head>` bölümünde `<link>` kullanmak tercih edilir.

Çünkü tarayıcı HTML'i işlerken font stil dosyasını daha erken keşfedebilir. CSS içindeki @import ise ilgili CSS dosyasının keşfedilip işlenmesine bağlı ek bir yükleme aşaması oluşturabilir.

Bu nedenle `<link>` yaklaşımı çoğu projede daha uygun bir başlangıçtır.

### 3. Performans Açısından Dikkat Edilecekler
Web fontları ek ağ istekleri ve indirme maliyeti oluşturabilir.

Bu nedenle:
- Gerçekten kullanılacak font ailelerini yüklemeliyiz.
- Gereksiz font ağırlıklarını ve stillerini istememeliyiz.
- Mümkün olduğunda modern font formatlarını ve uygun alt kümeleri tercih etmeliyiz.
- Fallback font tanımlamalıyız.
- Font yüklenirken oluşabilecek yerleşim kaymalarını test etmeliyiz.

**Not:** Bir variable fontun tek dosyada çok sayıda ağırlığı desteklemesi mümkün olduğundan, çok ağırlık kullanımı her zaman ayrı ayrı çok sayıda font dosyası indirilmesi anlamına gelmez.

### 4. @font-face ile Kendi Fontunu Kullanmak
Google Fonts dışında projede barındırdığımız font dosyalarını da kullanabiliriz.
```
    @font-face {
        font-family: "MyFont";
        src: url("/fonts/my-font.woff2") format("woff2");
        font-weight: 400;
        font-style: normal;
        font-display: swap;
    }

    body {
        font-family: "MyFont", sans-serif;
    }
```

Burada:
- font-family fonta verdiğimiz aile adıdır
- src font dosyasının yoludur.
- font-weight dosyanın temsil ettiği ağırlığı belirtir.
- font-style font stilini tanımlar.
- font-display font yüklenirken metnin nasıl gösterileceğini etkiler.

Gerçek projelerde font dosyalarının lisans koşullarını da kontrol etmeliyiz.

## Responsive Tipografi
Responsive tasarım yalnızca elementlerin sütun sayısını değiştirmek değildir. Metin boyutları da farklı ekranlarda dengeli ve okunabilir olmalıdır.

Örneğin masaüstünde 64px boyutunda bir başlık etkileyici görünebilir; ancak aynı değer küçük bir mobil ekranda gereğinden fazla yer kaplayabilir.

### 1. Media Query ile Font Boyutu
Geleneksel yaklaşım:
```
    .hero-title {
        font-size: 3rem;
    }

    @media (max-width: 768px) {
        .hero-title {
            font-size: 2rem;
        }
    }
```

Bu yöntem geçerlidir ve gerektiğinde kullanılmalıdır.

Ancak yazı boyutunun ekran genişliğine göre kademesiz değişmesini istiyorsak clamp() daha uygun olabilir.

### 2. clamp() ile Responsive Font Boyutu
```
    .hero-title {
        font-size: clamp(1rem, 2vw, 2rem);
    }
```

clamp() üç değer alır: `clamp(minimum, tercih-edilen, maksimum)`

Bu örnekte:
- Minimun: 1rem
- Tercih edilen: 2vw
- Maksimun: 2rem

Yazı boyutu, uygun koşullarda viewport genişliğiyle birlikte büyür veya küçülür; tanımlanan alt ve üst sınırlar arasında kalır.

### 3. Tipografi Ölçeği Oluşturmak
Gerçek projelerde her element için rastgele font boyutu seçmek yerine tutarlı bir ölçek kullanmak daha uygundur.

Örneğin:
```
    :root {
        --text-xs: 0.75rem;
        --text-sm: 0.875rem;
        --text-base: 1rem;
        --text-lg: 1.125rem;

        --heading-sm: clamp(1.25rem, 1.1rem + 0.5vw, 1.5rem);
        --heading-md: clamp(1.5rem, 1.2rem + 1vw, 2rem);
        --heading-lg: clamp(2rem, 1.5rem + 2vw, 3.5rem);
    }
```

Ardından:
```
    body {
        font-size: var(--text-base);
    }

    .card-title {
        font-size: var(--heading-sm);
    }

    .section-title {
        font-size: var(--heading-md);
    }

    .hero-title {
        font-size: var(--heading-lg);
    }
```

Bu yaklaşımın avantajları:
- Tasarımda tutarlılık sağlar.
- Yazı boyutlarını merkezi olarak yönetmeyi kolaylaştırır.
- Responsive davranışları tekrar tekrar yazma ihtiyacını azaltabilir.
- Bileşenler arasında ortak bir tasarım dili oluşturur.

### 4. Responsive Tipografide Erişilebilirlik
Yalnızca vw kullanmak bazı durumlarda kullanıcı font tercihleriyle yeterince uyumlu olmayabilir.
```
    .title{
        font-size: 4vw;
    }
```

Bu nedenle viewport tabanlı değerleri rem gibi kullanıcı ayarlarına duyarlı birimlerle birlikte kullanmak daha dengeli bir yaklaşımdır.

Ancak clamp() kullanıması da tek başına erişilebilirliği garanti etmez. Özellikle büyük metin yakınlaştırmalarında maksimum sınırın yazının büyümesini kısıtlayıp kısıtlamadığı test edilmelidir.

**Önemli:** Responsive tipografi için media query kullanmak yanlış değildir. clamp() sürekli ölçekleme için kullanışlıdır; belirli bir ekran aralığında tasarımın bilinçli olarak değişmesi gerekiyorsa media query daha uygun olabilir.

## direction - Metin Yönü
Farklı dillerde metinler farklı yönlerde yazılabilir.

Örneğin:
- Türkçe ve İngilizce genellikle soldan sağa (ltr)
- Arapça ve İbranice genellikle sağdan sola (rtl) yazılır.

CSS'te direction özelliği bulunur.
```
    .text-ltr {
        direction: ltr;
    }

    .text-rtl {
        direction: rtl;
    }
```

### HTML dir Attribute'u
Metnin yönünü belirtmek için çoğu durumda HTML'in `dir` global attribute'unu kullanmak daha uygundur.
```
    <p dir="ltr">Merhaba dünya</p>

    <p dir="rtl">مرحبا بالعالم</p>
```

HTML'de ayrıca `<p dir="auto">Metin içeriği</p>` kullanımı da mümkündür.

`dir="auto"`, metnin yönünü içerikteki güçlü yönlü karakterlere göre belirlemeye çalışır.

### Neden HTML `dir` Tercih Edilir?
Çünkü metnin yazı yönü yalnızca görsel bir tercih değildir; içeriğin doğru yorumlanmasıyla da ilgilidir.

HTML'de dir kullanmak, yön bilgisini belgenin anlamsal yapısında belirtmemizi sağlar.

Bu konu, HTML **Global Attributes** bölümündeki dir açıklamasıyla ilişkilidir.

### Mantıksal CSS Özellikleriyle İlişkisi
Çok dilli tasarımlarda şu kullanım:
```
    .card {
        margin-left: 16px;
    }
```
yerine:
```
    .card {
        margin-inline-start: 16px;
    }
```
tercih edilebilir.

**margin-inline-start,** yazı yönüne göre uygun başlangıç tarafına uygulanır.

Bu sayede LTR ve RTL arayüzler için daha esnek stiller oluşturabiliriz.

## Sık Yapılan Hatalar
### 1. Generic Font Family Eklememek
Eksik fallback:
```
    body{
        font-family: "Inter";
    }
```
Daha güvenli kullanım:
```
    body {
        font-family: "Inter", Arial, sans-serif;
    }
```
Font yüklenemediğinde alternatifler kullanılabilir.

### 2. Her Yerde Sabit line-height Kullanmak
```
    .parent {
        line-height: 24px;
    }
```
Bu değer, iç içe elementlerde farklı font boyutlarına uygun olmayabilir.

Çoğu metin düzeninde daha esnek kullanım:
```
    .parent {
        line-height: 1.5;
    }
```
olabilir.

Ancak sabit satır yüksekliği gereken özel arayüzlerde birimli değer kullanmak başlı başına hata değildir.

### 3. Link Alt Çizgisini Alternatifsiz Kaldırmak
```
    a {
        text-decoration: none;
    }
```
Bağlantıların diğer metinlerden ayırt edilmesini zorlaştırabilir.

Özellikle metin içindeki linklerde alt çizgi veya başka belirgin görsel işaretler korunmalıdır.

Klavye kullanıcıları için :focus-visible göstergesi de sağlanmalıdır.

### 4. Gereksiz Font Dosyaları Yüklemek
Bir projede yalnızca 400, 500 ve 700 ağırlıkları kullanılıyorsa gereksiz diğer ağırlıkları yüklemek performans maliyetini artırabilir.

Ancak variable fontların dosya yapısı farklı olabileceğinden, gerçek indirme boyutlarını kontrol etmek gerekir.

### 5. Uzun Paragraflarda Aşırı Harf Aralığı Kullanmak
```
    p {
        letter-spacing: 5px;
    }
```
Bu kullanım metni okumayı zorlaştırabilir.

Harf aralığı özellikle küçük etiketlerde ve kısa başlıklarda daha dikkatli kullanılmalıdır.

### 6. text-transform ile Kaynak Metnin Değiştiğini Sanmak
```
    .title {
        text-transform: uppercase;
    }
```
Bu kullanım HTML içeriğini değiştirmez.

Metnin gerçek karakterlerini değiştirmek gerekiyorsa işlem içerik veya uygulama katmanında yapılmalıdır.

### 7. Her Ekran Boyutu İçin Ayrı Font Kuralı Yazmak
```
    .title {
        font-size: 40px;
    }

    @media (max-width: 1200px) {
        .title {
            font-size: 36px;
        }
    }

    @media (max-width: 992px) {
        .title {
            font-size: 32px;
        }
    }

    @media (max-width: 768px) {
        .title {
            font-size: 28px;
        }
    }
```
Bu yaklaşım çalışır ancak sürekli ölçekleme gereken durumlarda bakım maliyetini artırabilir.

Alternatif:
```
    .title {
        font-size: clamp(1.75rem, 1.25rem + 2vw, 2.5rem);
    }
```
Burada amaç media query kullanımını tamamen kaldırmak değil, uygun durumlarda daha sade ve akıcı bir çözüm oluşturmaktır.

### 8. Görsel Hiyerarşiyi Yalnızca Font Boyutuyla Oluşturmak
Bir başlığı ayırt etmek için yalnızca boyutunu büyütmek zorunda değiliz.
```
    .section-title {
        font-size: 1.75rem;
        font-weight: 700;
        line-height: 1.2;
        letter-spacing: -0.02em;
        color: #26251f;
    }
```
Boyut, ağırlık, satır yüksekliği, renk ve boşluklar birlikte değerlendirildiğinde daha dengeli bir hiyerarşi oluşturulabilir.

## Kısaca Özet
|Property               |Görevi                 |Örnek          |
|-----------------------|-----------------------|---------------|
|font-family    |Font ailesi    |"Inter", sans-serif    |
|font-size      |Yazı boyutu    |1rem   |
|font-weight    |Yazı kalınlığı |600    |
|font-style     |Normal/italik/eğik stil|italic |
|font-variant   |Tipografik varyant |small-caps |
|font           |Font shorthand |600 1rem/1.5 Arial|
|line-height    |Satır yüksekliği|1.5    |
|text-align     |Metin hizalaması   |center     |
|text-decoration|Metin dekorasyonu|underline    |
|text-transform |Harf dönüşümü  |uppercase  |
|text-shadow    |Metin gölgesi  |1px 2px 4px #999|
|letter-spacing |Harf aralığı   |0.05em     |
|word-spacing   |Kelime aralığı |2px        |
|direction      |Yazı yönü      |rtl        |

### font Shorthand Şeması
```
font: italic small-caps 700 16px/1.5 Arial, sans-serif;
      │      │        │    │    │      │
      │      │        │    │    │      └── Font ailesi
      │      │        │    │    └───────── Satır yüksekliği
      │      │        │    └────────────── Yazı boyutu
      │      │        └─────────────────── Yazı kalınlığı
      │      └──────────────────────────── Font varyantı
      └─────────────────────────────────── Yazı stili
```
**Hatırlatma:** font-size ve font-family zorunludur. Diğerleri isteğe bağlıdır.

### Responsive Tipografi Örneği
```
    :root {
        --font-family-base: "Inter", Arial, sans-serif;

        --text-sm: 0.875rem;
        --text-base: 1rem;
        --text-lg: 1.125rem;

        --heading-md: clamp(1.5rem, 1.2rem + 1vw, 2rem);
        --heading-lg: clamp(2rem, 1.5rem + 2vw, 3.5rem);
    }

    body {
        font-family: var(--font-family-base);
        font-size: var(--text-base);
        line-height: 1.6;
        color: #26251f;
    }

    h1 {
        font-size: var(--heading-lg);
        font-weight: 700;
        line-height: 1.15;
        letter-spacing: -0.03em;
    }

    h2 {
        font-size: var(--heading-md);
        font-weight: 600;
        line-height: 1.25;
    }

    p {
        font-size: var(--text-base);
        line-height: 1.7;
    }

    small {
        font-size: var(--text-sm);
    }
```
Bu yapı sayesinde yazı boyutlarını ortak değişkenlerden yönetebilir, başlıkları ekran genişliğine göre ölçekleyebilir ve sayfa genelinde bir tipografi oluşturabiliriz.

### Tipografi Mantığı
```
    CSS TİPOGRAFİ
    │
    ├── FONT ÖZELLİKLERİ
    │   ├── font-family
    │   ├── font-size
    │   ├── font-weight
    │   ├── font-style
    │   ├── font-variant
    │   └── font (shorthand)
    │
    ├── METİN GÖRÜNÜMÜ
    │   ├── text-align
    │   ├── text-decoration
    │   ├── text-transform
    │   └── text-shadow
    │
    ├── METİN BOŞLUKLARI
    │   ├── line-height
    │   ├── letter-spacing
    │   └── word-spacing
    │
    ├── FONT YÜKLEME
    │   ├── Sistem fontları
    │   ├── Google Fonts
    │   └── @font-face
    │
    ├── RESPONSIVE TİPOGRAFİ
    │   ├── rem
    │   ├── vw
    │   ├── clamp()
    │   └── Media queries
    │
    └── ERİŞİLEBİLİRLİK
        ├── Okunabilir font boyutları
        ├── Yeterli satır yüksekliği
        ├── Görsel hiyerarşi
        ├── Ayırt edilebilir bağlantılar
        └── Metin yakınlaştırma
```
Bu Bölümün En Önemli Noktası:

`iyi tipografi yalnızca güzel görünen yazılar oluşturmak değildir. Metnin okunabilir, anlaşılır, erişilebilir ve farklı ekran boyutlarında dengeli görünmesini sağlamaktır.`

Bir web arayüzünde font ailesi, yazı boyutu, ağırlık, satır yüksekliği ve boşluklar birlikte değerlendirildiğinde daha profesyonel ve tutarlı bir tasarım sistemi oluşturulabilir.