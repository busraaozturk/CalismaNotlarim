# CSS Box Model (Kutu Modeli)
Web sayfalarında gördüğümüz başlıklar, paragraflar, görseller, butonlar ve kartlar belirli bir alan kaplar. CSS, bu alanların boyutlarını ve birbirleriyle olan mesafelerini yönetmek için **Box Model (Kutu Modeli)** adı verilen bir yapı kullanır.

Örneğin bir ürün kartını düşünelim:
```
    <div class="product-card">
        <h2>Ürün Başlığı</h2>
        <p>Ürün açıklaması</p>
    </div>

    .product-card {
        width: 300px;
        padding: 20px;
        border: 1px solid #dddddd;
        margin: 24px;
    }
```
Burada:
- **width** → içerik alanının genişliğini,
- **padding** → içerik ile kenarlık arasındaki boşluğu,
- **border** → kutunun kenarlığını,
- **margin** → kutunun dışındaki boşluğu belirler.

Bu özelliklerin birlikte nasıl çalıştığını anlamak, CSS ile doğru ve öngörülebilir yerleşimler oluşturmanın temelidir.

## Box Model Nedir?
CSS'te her element, yerleşim hesaplamalarında bir veya birden fazla dikdörtgen kutuyla temsil edilir. Standart bir kutunun dört temel katmanı bulunur.
```
    Box Model
    │
    ├── Content
    ├── Padding
    ├── Border
    └── Margin
```

İçten dışa doğru sıralama:
```
    Content
        ↓
    Padding
       ↓
    Border
       ↓
    Margin
```

Box Model Katmanları
```
    ┌───────────────────────────────────────┐
    │                MARGIN                 │
    │                                       │
    │   ┌───────────────────────────────┐   │
    │   │            BORDER             │   │
    │   │                               │   │
    │   │   ┌───────────────────────┐   │   │
    │   │   │        PADDING        │   │   │
    │   │   │                       │   │   │
    │   │   │   ┌───────────────┐   │   │   │
    │   │   │   │    CONTENT    │   │   │   │
    │   │   │   └───────────────┘   │   │   │
    │   │   │                       │   │   │
    │   │   └───────────────────────┘   │   │
    │   │                               │   │
    │   └───────────────────────────────┘   │
    │                                       │
    └───────────────────────────────────────┘
```

Her katmanın farklı bir görevi vardır:
|Katman         |Görevi             |
|---------------|-------------------|
|Content        |Elementin içeriğinin bulunduğu alan|
|Padding        |İçerik ile border arasındaki boşluk|
|Border         |Padding ve içeriği çevreleyen kenarlık|
|Margin         |Border'ın dışındaki boşluk|

Box Model'i bir kutunun katmanları gibi düşünebiliriz.

**Content** kutunun içindeki ürün, **padding** ürün ile kutunun kenarı arasındaki koruyucu boşluk, **border** kutunun sınırı, **margin** ise kutunun çevresindeki diğer nesnelerle arasındaki mesafedir.

- **Önemli:** **margin**, elementin arka planıyla boyanan bir alan değildir. Dışarıda yerleşim boşluğu oluşturur.

## width ve height
CSS'te bir elementin genişliğini ve yüksekliğini kontrol etmek için: `width` ve `height` property'leri kullanılır.

Örneğin:
```
    .card{
        width: 300px;
        height: 200px;
    }
```

Varsayılan **box-sizing: content-box** davranışında bu değerler elementin **content alanının** boyutlarını belirler.

### width ve height Hangi Değerleri Alabilir?
```
    .card{
        width: 300px;
    }
```
Belirli bir CSS piksel genişliği tanımlar.
```
    .card {
        width:50%;
    }
```
Genişliği ilgili referans alanının yüzde ellisi olarak belirler.
```
    .card {
        width:20rem;
    }
```
Genişliği kök font boyutuna göre hesaplar.
```
    .card {
        width: auto;
    }
```
Genişliğin CSS yerleşim kurallarına göre otomatik hesaplanmasını sağlar. Aynı şekilde height da farklı uzunluk ve yüzde değerleri alabilir.

### auto Nasıl Çalışır?
Normal akıştaki blok seviyeli bir element için:
```
    .container {
        width:auto;
    }
```
kullanıldığında element genellikle bulunduğu alanın kullanılabilir genişliğini doldurur. Ancak bu, her durumda doğrudan **width:100%** ile aynı davranış demek değildir.

Örneğin:
```
    .box {
        width: auto;
        margin: 20px;
    }
```
normal blok yerleşiminde genişlik hesaplanırken margin ve diğer kutu ölçüleri de dikkate alınır.

**height: auto** ise normal akıştaki birçok elementte yüksekliğin içeriğe göre belirlenmesini sağlar.
```
    .card {
        height: auto;
    }
```
Bu nedenle özellikle metin içeren alanlarda gereksiz sabit yükseklikler vermemek önemlidir.

### min-width, max-width, min-height, max-height
Boyutları daha kontrollü yönetmek için minimum ve maksimum sınırlar tanımlayabiliriz.
```
    .card{
        width: 100%;
        max-width: 400px;
    }
```

Burada kart, kullanılabilir alana göre küçülebilir ancak genişliği 400px sınırını aşmaz.

Başka bir örnek:
```
    .card {
        min-height: 200px;
    }
```

Kartın en az 200px yüksekliğinde olmasını sağlar. İçerik daha fazla yer gerektiriyorsa kutu büyüyebilir. Bu özellikler responsive tasarımda oldukça kullanışlıdır.

## padding - İç Boşluk
padding, elementin content alanı ile border'ı arasındaki boşluktur.

Örneğin:
```
    .card{
        padding:20px;
    }
```

Bu kullanım içerikle kenarlık arasında dört yönde 20px boşluk oluşturur.
```
    ┌────────────────────────────┐
    │           BORDER           │
    │                            │
    │    ← 20px PADDING →        │
    │                            │
    │       Ürün Başlığı         │
    │                            │
    └────────────────────────────┘
```

### Padding Neden Kullanılır?
Örneğin bir buton düşünelim:
```
    <button class="button">
        Kaydet
    </button>
```

```
    .button {
        padding:12px 24px;
    }
```

Padding sayesinde metin, butonun kenarlarına yapışmaz.

Bu özellik özellikle:
- Butonlarda,
- Ürün kartlarında,
- Form alanlarında,
- Bilgi kutularında,
- Navigasyon öğelerinde sıkça kullanılır.

### Dört Yönlü Padding
Padding ayrı ayrı tanımlanabilir:
```
    .card{
        padding-top: 10px;
        padding-right: 20px;
        padding-bottom: 15px;
        padding-left: 5px;
    }
```

Burada:
```
             TOP 10px
               │
LEFT 5px ─── CONTENT ─── RIGHT 20px
               │
             15px BOTTOM
```

### Padding Shorthand Kullanımı
CSS'te aynı property'nin birden fazla yönünü tek satırda tanımlamaya **shorthand** denir.

**Tek Değer**

```
    .card {
        padding:16px;
    }
```
Dört yönünün tamamına 16px uygulanır.

**İki Değer**
```
    .card {
        padding: 10px 20px;
    }
```

10px → Üst ve alt
20px → Sağ ve sol

**Üç Değer**
```
    .card {
        padding: 10px 20px 15px;
    }
```

10px → Üst
20px → Sağ ve sol
15px → Alt

**Dört Değer**
```
    .card {
        padding: 10px 20px 15px 5px;
    }
```

Sıralama saat yönündedir: `TOP → RIGHT → BOTTOM → LEFT`

### Padding Özellikleri
Padding hakkında bilmemiz gereken iki önemli nokta vardır:
- Padding, kutunun iç alanına aittir. Elementin arka planı normalde padding alanında da görüntülenir.
- Padding negatif değer alamaz.

Örneğin:
```
    .card {
        padding: -10px;
    }
```
geçersizdir.

## border - Kenarlık
border, elementin content ve padding alanını çevreleyen kenarlıktır.

Bir border'ın üç temel özelliği bulunur.
```
    Border
    │
    ├── Width
    ├── Style
    └── Color
```

### border-width
Kenarlığın kalınlığını belirler.
```
    .card {
        border-width: 2px;
        border-style: solid;
    }
```

### border-style
Kenarlığın görünüm biçimini belirler.

Yaygın Değerler:
|Değer          |Açıklama               |
|---------------|-----------------------|
|solid          |Düz çizgi              |
|dashed         |Kesikli çizgi          |
|dotted         |Noktalı çizgi          |
|double         |Çift çizgi             |
|none           |Kenarlık yok           |

Örneğin:
```
    .card {
        border: 2px dashed #777777;
    }
```

### border-color
Kenarlığın rengini belirler.
```
    .card {
        border:1px solid #7d8570;
    }
```

### Border Shorthand 
Border özelliklerini tek satırda tanımlayabiliriz:
```
    .card{
        border: 1px solid black;
    }
```

Bu ifade:
```
    .card{
        border-width: 1px;
        border-style: solid;
        border-color: black;
    }
```
ile aynı temel kenarlık özelliklerini tanımlar.

### Tek Yönlü Border
Bazı tasarımlarda dört tarafı çevrelemek yerine yalnızca belirli bir kenara çizgi eklemek isteyebiliriz.

Örneğin:
```
    .section {
        border-bottom: 1px solid #dddddd;
    }
```

Diğer yönler şu şekildedir:
```
    border-top
    border-right
    border-bottom
    border-left
```

### border-radius — Köşe Yuvarlama
border-radius, kutunun köşelerini yuvarlamak için kullanılır.
```
    .card {
        border: 1px solid #dddddd;
        border-radius: 12px;
    }
```
Örnekler:
```
    .card {
        border-radius: 8px;
    }

    .button {
        border-radius: 999px;
    }

    .avatar {
        width: 80px;
        height: 80px;
        border-radius: 50%;
    }
```
Son örnekte eşit genişlik ve yüksekliğe sahip bir kutu dairesel görünüm kazanır. **border-radius**, border çizilmese bile elementin arka planının köşelerini etkileyebilir.

## margin - Dış Boşluk
margin, elementin border alanının dışında bulunan yerleşim boşluğudur.

Örneğin:
```
    .card{
        margin:20px;
    }
```
Bu değer kutunun çevresinde dış boşluk tanımlar.

### Padding ve Margin Arasındaki Fark
- Padding  → İçerik ile kenarlık arasındaki boşluk
- Margin  →  Kenarlığın dışındaki boşluk

Örneğin:
```
    .card {
        padding: 20px;
        margin: 30px;
    }
```

Burada:
- padding: 20px;  → kartın içindeki içeriğe nefes alma alanı sağlar.
- margin: 30px;  → kartın dışındaki yerleşim boşluğunu belirler.

### Margin Shorthand
Margin, padding ile aynı shorthand sıralamasını kullanır.
```
    .card{
        margin:20px;
    }
```
Dört yön.

```
    .card {
        margin: 10px 20px;
    }
```
Üst - alt ve sağ - sol

```
    .card{
        margin: 10px 20px 15px;
    }
```
Üst, sağ - sol, alt

```
    .card {
        margin: 10px 20px 15px 5px;
    }
```
Üst, sağ, alt, sol

### margin - auto
Özellikle yatay hizalamada auto değeriyle sıkça karşılaşırız.
```
    .container {
        width: 600px;
        margin-inline: auto;
    }
```

Normal block yerleşiminde uygun koşullarda sağ ve sol margin değerleri kalan alanı paylaşır. Böylece container yatayda ortalanabilir.

Responsive bir örnek:
```
    .container {
        width: min(100% - 2rem, 75rem);
        margin-inline: auto;
    }
```

Bu kullanım dar ekranlarda küçülebilen ve geniş ekranlarda ortalanan bir container oluşturur.

### Negatif Margin
Padding'in aksine margin negatif değer alabilir.
```
    .badge {
        margin-top: -10px;
    }
```
Bu kullanım elementin normal yerleşim konumunu veya çevresindeki boşluk ilişkilerini etkileyebilir. Negatif margin bazı tasarımsal hizalama ihtiyaçlarında kullanılabilir.

Ancak dikkatli kullanılmalıdır; çünkü beklenmeyen çakışmalara veya taşmalara neden olabilir.

### Yüzdeli padding ve margin
padding ve margin yüzdeyle tanımlandığında, **dikey yönler dahil** yüzde, içeren bloğun (genellikle parent'ın) **genişliğine** göre hesaplanır.
```
    .parent {
        width: 400px;
    }

    .child {
        padding-top: 10%;
    }
```
Burada `padding-top` değeri parent'ın yüksekliğine göre değil, genişliğine göre hesaplanır: `400px × 10% → 40px`

### Inline Elementlerde Box Model
`<span>`, `<a>`, `<strong>` gibi inline elementlerde box model farklı davranır:
- `width` ve `height` uygulanmaz; boyut içeriğe göre belirlenir.
- Yatay padding, border ve margin çevredeki elementleri iter.
- Dikey padding ve border görsel olarak çizilir ancak satırların yerleşimini (satır yüksekliğini) değiştirmez; dikey margin ise etkisizdir.

Bu elementlerin kutu ölçülerini tam olarak kullanmak için `display: inline-block` veya `display: block` gibi değerler kullanılabilir. Ayrıntılarını Display konusunda inceleyeceğiz.

### Margin Collapse - Dış Boşluk Birleşmesi
Margin konusunda en çok karıştırılan davranışlardan biri **margin collapse** özelliğidir. Normal block yerleşimindeki bazı elementlerin dikey margin değerleri birleşebilir.

Örneğin:
```
    <div class="box-one">
        Birinci kutu
    </div>

    <div class="box-two">
        İkinci kutu
    </div>
```

```
    .box-one {
        margin-bottom: 30px;
    }

    .box-two {
        margin-top: 20px;
    }
```

İlk bakışta iki kutu arasında: `30px + 20px = 50px` boşluk oluşacağını düşünebiliriz.

Ancak bu örnekte margin collapse gerçekleşirse sonuç şu şekilde olur:
```
    max(30px, 20px)
        ↓
    30px
```

Yani iki dikey margin toplanmak yerine birleşir.

### Margin Collapse Şeması
```
    ┌────────────────────┐
    │    Birinci Kutu    │
    └────────────────────┘
            │
            │ 30px margin-bottom
            │
            │ 20px margin-top
            │
            ↓
        Birleşen boşluk
            30px
            │
    ┌────────────────────┐
    │    İkinci Kutu     │
    └────────────────────┘
```

### Margin Collapse Her Zaman Olur mu?
Hayır. Margin collapse belirli koşullarda gerçekleşir.

Örneğin:
- Normal blok akışında birbirini takip eden blok elementlerin dikey margin'leri birleşebilir.
- Parent ve ilk/son child arasındaki dikey margin'ler de belirli koşullarda birleşebilir.
- Yatay margin'ler birleşmez.
- Flex ve Grid item'larının margin'leri bu şekilde collapse olmaz.
- Mutlak konumlandırılmış elementlerin margin'leri collapse olmaz.

Ayrıca negatif margin değerlerinin bulunduğu durumlarda hesaplama yalnızca büyük değeri seçmekten daha farklıdır. Başlangıçta öğrenilmesi gereken en önemli nokta şudur: `Normal blok akışında iki dikey margin her zaman toplanmaz.`

## box-sizing - content-box ve border-box
Box Model'in en önemli konularından biri **box-sizing** property'sidir. Bu property, width ve height değerlerinin kutunun hangi bölümünü kapsayacağını belirler.

İki temel değer: `box-sizing: content-box;` ve `box-sizing: border-box` şeklindedir.

### 1. content-box
Çoğu element için varsayılan değer **content-box**'tır.

Örneğin:
```
    .card {
        box-sizing: content-box;
        width: 300px;
        padding: 20px;
        border: 2px solid black;
    }
```

Burada width:300px, yalnızca içerik alanının genişliğini belirler.

Toplam border-box genişliği: 
```
    Content Width    = 300px

    Left Padding     = 20px
    Right Padding    = 20px

    Left Border      = 2px
    Right Border     = 2px

    ------------------------

    Total Width      = 344px
```

Formül: `Toplam Genişlik = Content Width + Padding Left + Padding Right + Border Left + Border Right`

Yani: `300 + 20 + 20 + 2 + 2 → 344px` olur.

Margin bu toplamın içinde değildir.

### 2. border-box
Şimdi aynı kutuyu border-box ile tanımlayalım:
```
    .card {
        box-sizing: border-box;
        width: 300px;
        padding: 20px;
        border: 2px solid black;
    }
```

Bu durumda width:300px, content + padding + border alanlarının toplam genişliğini ifade eder.
```
    Toplam Border - Box Genişliği : 300px
    ├── Border Left  2px
    ├── Padding Left 20px
    ├── Content      256px
    ├── Padding Right 20px
    └── Border Right 2px
```

Hesaplama: `300 - 20 - 20 - 2 - 2 → 256px`

Content alanı 256px olur. Ancak kutunun border-box genişliği 300px olarak kalır.

### content-box ve border-box Karşılaştırması
|Özellik        |content-box            |border-box         |
|---------------|-----------------------|-------------------|
|width neyi kapsar?|Content             |Content + Padding + Border|
|Padding genişliğe eklenir mi? |Evet    |Belirtilen genişliğin içindedir|
|Border genişliğe eklenir mi? |Evet     |Belirtilen genişliğin içindedir|
|Margin genişliğe dahil mi?|Hayır       |Hayır              |
|Ölçü yönetimi  |Daha fazla hesaplama gerekebilir|Genellikle daha öngörülebilir|

### Neden border-box Tercih Edilir?
Gerçek projelerde kutunun belirtilen genişliğini korumak genellikle daha kolay bir ölçü yönetimi sağlar.

Bu nedenle yaygın bir başlangıç yaklaşımı aşağıdaki şekildedir:
```
    *,
    *::before,
    *::after {
        box-sizing: border-box;
    }
```

Burada:
- * → bütün elementleri,
- *::before → ::before pseudo-elementlerini,
- *::after → ::after pseudo-elementlerini hedefler.

Bu kullanım proje genelinde daha öngörülebilir bir kutu modeli sağlar.

**Not:** border-box, elementin hiçbir koşulda taşmayacağını garanti etmez. İçeriğin minimum boyutları, uzun kelimeler, flex/grid davranışları ve diğer CSS kuralları hâlâ taşmaya neden olabilir.

## outline - Anahat
outline, bir elementin çevresinde çizilen görsel bir hattır.

Örneğin:
```
    .button {
        outline: 2px solid blue;
    }
```

İlk bakışta border'a benzeyebilir. Ancak önemli bir fark vardır: `Outline, Box Model'in boyut hesaplamasına dahil değildir.`

Yani outline eklemek elementin border-box genişliğini veya yüksekliğini değiştirmez.

### Outline Özellikleri
```
    outline-width
    outline-style
    outline-color
```

Örneğin:
```
    .button {
        outline-width: 2px;
        outline-style: solid;
        outline-color: #2563eb;
    }
```

Shorthand:
```
    .button {
        outline: 2px solid #2563eb;
    }
```

### outline ve Erişilebilirlik
Outline'ın önemli kullanım alanlarından biri klavye ile gezinme sırasında focus göstergesi oluşturmaktadır.

Örneğin kullanıcı Tab tuşuyla bir butona geldiğinde hangi elementin odakta olduğunu görebilmelidir.
```
    .button:focus-visible {
        outline: 2px solid #2563eb;
    }
```

Burada **:focus-visible**, tarayıcının görünür bir focus göstergesinin uygun olduğuna karar verdiği durumları hedefler. Özellikle klavye kullanıcıları için önemlidir.

### outline-offset
Outline ile element arasındaki mesafeyi belirlemek için `outline-offset` kullanılır.

Örneğin:
```
    .button:focus-visible {
        outline: 2px solid #2563eb;
        outline-offset:3px;
    }
```
Bu kullanım focus göstergesini butonun kenarından biraz uzaklaştırır.

### outline: none Neden Dikkatli Kullanılmalı?
Şu kullanım:
```
    .button:focus {
        outline: none;
    }
```
tarayıcının varsayılan focus göstergesini kaldırabilir.

Eğer yerine görünür bir alternatif sağlanmazsa klavye kullanıcıları hangi elementin odakta olduğunu anlamakta zorlanabilir.

Bu nedenle focus göstergesini tamamen kaldırmak yerine erişilebilir bir görünümle özelleştirmek daha doğru bir yaklaşımdır.

### Border ve Outline Farkı
|Özellik            |border             |outline                |
|-------------------|-------------------|-----------------------|
|Box Model'in parçası mı?|Evet          |Hayır                  |
|Boyut hesaplamasını etkiler mi?|Evet kutu modeline göre|Hayır  |
|Ayrı ayrı dört kenar tanımlanabilir mi?|Evet       |Normal outline'da hayır|
|Yaygın kullanım    |Kart ve alan sınırları |Focus göstergesi   |
|outline-offset benzeri mesafe özelliği| Yok    |Var            |

## box-shadow - Kutu Gölgesi
box-shadow, elementin kutusuna gölge efekti eklemek için kullanılır.

Örneğin:
```
    .card{
        box-shadow: 0 4px 12px rgb(0 0 0 / 12%);
    }
```
Bu kullanım kartın altında yumuşak bir gölge oluşturur.

### Box-Shadow Sözdizimi
Yaygın Kullanım: `box-shadow: [inset] offset-x offset-y blur-radius spread-radius color;`

Köşeli parantez içindeki `inset` isteğe bağlıdır. blur-radius ve spread-radius yazılmazsa 0 kabul edilir.

Örneğin:
```
    .card {
        box-shadow: 2px 4px 10px 0 rgb(0 0 0 / 15%);
    }
```

Burada:
```
    2px → Yatay kaydırma
    4px → Dikey kaydırma
    10px → Bulanıklık yarıçapı
    0 → Yayılma yarıçapı
    rgb(0 0 0 / 15%) → Gölge rengi
```
tanımlanır.

### 1. offset-x
Gölgenin yatay yönde ne kadar kayacağını belirler.

`box-shadow: 10px 0 0 black;`

Pozitif değer gölgeyi sağa, negatif değer sola kaydırır.

### 2. offset-y
Gölgenin dikey yönde ne kadar kayacağını belirler.

`box-shadow: 0 10px 0 black;`

Pozitif değer gölgeyi aşağı, negatif değer yukarı kaydırır.

### 3. blur-radius
Gölgenin ne kadar bulanık olacağını belirler.

`box-shadow: 0 4px 16px rgb(0 0 0 / 15%);`

Bulanıklık arttıkça gölgenin kenarları daha yumuşak görünür. blur-radius negatif değer alamaz.

### 4. spread-radius
Gölgenin yayılma miktarını belirler.

`box-shadow: 0 0 0 4px #dddddd;`

Bu örnekte bulanıklık olmadan kutunun çevresinde yayılan bir gölge oluşur. Pozitif spread gölgeyi genişletirken negatif spread gölgenin yayılımını daraltır.

### 5. inset - İç Gölge
Normal box-shadow, varsayılan olarak dış gölge oluşturur. *inset* kullanıldığında gölge kutunun iç tarafında çizilir.
```
    .input {
        box-shadow: inset 0 2px 4px rgb(0 0 0 / 10%);
    }
```
Bu kullanım bazı alanlarda içe gömülmüş görünüm oluşturmak için tercih edilebilir.

### 6. Birden Fazla Gölge
Bir elemente birden fazla gölge eklenebilir.
```
    .card {
        box-shadow:
            0 2px 4px rgb(0 0 0 / 6%),
            0 8px 24px rgb(0 0 0 / 10%);
    }
```

Gölge değerleri virgülle ayrılır. Bu yaklaşım daha katmanlı ve doğal görünümlü gölgeler oluşturabilir.

### Box-Shadow Layout'u Etkiler mi?
Hayır. box-shadow, kutunun layout hesaplamalarındaki genişliğini veya yüksekliğini artırmaz. Ancak gölge görsel olarak kutunun dışına taşabilir.

Örneğin parent üzerinde overflow: hidden kullanılıyorsa taşan gölgenin bir kısmı görünmeyebilir.

## Box Model'i Tarayıcıda İncelemek
Box Model'i öğrenmenin en etkili yollarından biri tarayıcının geliştirici araçlarını kullanmaktır.

Chrome, Edge veya Firefox gibi tarayıcılarda DevTools aracılığıyla elementlerin ölçülerini inceleyebiliriz.

**Nasıl İncelenir?**
1. İncelemek istediğimiz web sayfasını açarız.
2. Element üzerinde sağ tıklayıp **İncele (Inspect)** seçeneğini kullanırız.
3. DevTools içerisinden ilgili elementi seçeriz.
4. **Computed** veya **Layout** bölümündeki Box Model görünümünü inceleriz. Panelin konumu tarayıcıya göre değişebilir.

Burada genellikle: `Margin → Border → Padding → Content` alanları farklı renklerle gösterilir.

Örneğin:
```
    .card{
        width: 300px;
        padding: 20px;
        border: 2px solid black;
        margin: 24px;
    }
```
tanımlandığında DevTools üzerinden bu değerlerin hangi katmanlara uygulandığını görebiliriz. Ayrıca box-sizing değerini değiştirerek toplam genişliğin nasıl hesaplandığını incelemek oldukça öğreticidir.

## Sık Yapılan Hatalar
### 1. Padding ve Border'ın Toplam Boyutu Etkilediğini Unutmak
```
    .card {
        width: 300px;
        padding: 20px;
        border: 2px solid black;
    }
```
Varsayılan content-box davranışında border-box genişliği 344px olur. Bu nedenle beklenenden büyük bir kutu görüntülenebilir.

Çözüm olarak şu şekilde kullanılabilir:
```
    .card {
        box-sizing: border-box;
        width: 300px;
        padding: 20px;
        border: 2px solid black;
    }
```

### 2. Padding ve Margin'i Karıştırmak
```
    .card {
        padding: 20px;
    }
```
iç boşluk oluşturur.
```
    .card {
        margin: 20px;
    }
```
dış boşluk oluşturur.

İkisi aynı amaçla kullanılmaz.

### 3. Margin Collapse Davranışını Unutmak
```
    .first {
        margin-bottom: 30px;
    }

    .second {
        margin-top: 20px;
    }
```
Normal blok akışındaki uygun koşullarda aradaki boşluk 50px değil, 30px olabilir. Bu nedenle margin'lerin her zaman toplandığını varsaymamalıyız.

### 4. Shorthand Sıralamasını Karıştırmak
```
    padding: 10px 20px 15px 5px;
```
Sıralama:
```
    TOP
    RIGHT
    BOTTOM
    LEFT
```
şeklindedir.

Aynı sıralama margin için de geçerlidir.

### 5. Focus Göstergesini Tamamen Kaldırmak
```
    button:focus {
        outline: none;
    }
```
görünür bir alternatif sağlanmadığında erişilebilirlik sorunu oluşturabilir.

Daha uygun örnek:
```
    button:focus-visible {
        outline: 2px solid #2563eb;
        outline-offset: 3px;
    }
```

### 6. Sabit height Kullanıp İçeriğin Taşmasına Şaşırmak
```
    .card {
        height: 150px;
    }
```
İçerik uzadığında veya kullanıcının yazı boyutu büyüdüğünde bu yükseklik yeterli olmayabilir.

İhtiyaca göre:
```
    .card {
        min-height: 150px;
    }
```
daha esnek bir çözüm olabilir.

### 7. Gölgeyi Elementin Gerçek Boyutunun Parçası Sanmak
```
    .card {
        box-shadow: 0 8px 24px rgb(0 0 0 / 12%);
    }
```
Gölge görsel olarak dışarı uzanabilir ancak elementin layout boyutunu değiştirmez.

## Kısaca Özet
CSS Box Model, elementlerin boyutlarını ve çevresindeki boşlukları anlamamızı sağlar.

### Box Model Katmanları
```
    ┌─────────────────────────────────┐
    │             MARGIN              │
    │  ┌───────────────────────────┐  │
    │  │          BORDER           │  │
    │  │  ┌─────────────────────┐  │  │
    │  │  │       PADDING       │  │  │
    │  │  │  ┌───────────────┐  │  │  │
    │  │  │  │    CONTENT    │  │  │  │
    │  │  │  └───────────────┘  │  │  │
    │  │  └─────────────────────┘  │  │
    │  └───────────────────────────┘  │
    └─────────────────────────────────┘
```

### Temel Property'ler

|Property           |Görevi         |
|-------------------|---------------|
|width              |Genişlik       |
|height             |Yükseklik      |
|padding            |İç boşluk      |
|border             |Kenarlık       |
|margin             |Dış boşluk     |
|box-sizing         |Kutu boyutunun hesaplanma biçimi   |
|outline            |Layout'u etkilemeyen anahat        |
|box-shadow         |Kutu gölgesi   |

### content-box ve border-box

|Özellik            |content-box            |border-box             |
|-------------------|-----------------------|-----------------------|
|width              |Content genişliği      |Border-box genişliği   |
|Padding            |Genişliğe eklenir      |Genişliğe dahildir     |
|Border             |Genişliğe eklenir      |Genişliğe dahildir     |
|Margin             |Dahil değildir         |Dahil değildir         |

### Border ve Outline  

|border                         |outline                        |
|-------------------------------|-------------------------------|
|Box Model'in parçasıdır        |Box Model'in parçası değildir  |
|Boyut hesaplamasına katılır    |Boyut hesaplamasına katılmaz   |
|Görsel sınır oluşturur         |Görsel anahat oluşturur        |
|Kartlarda ve alan sınırlarında kullanılır|Özellikle focus göstergelerinde kullanılır|

### Akılda Kalması Gerekenler
```
    Content → İçeriğin bulunduğu alan
    Padding → İçerik ile kenarlık arasındaki boşluk
    Border → Kutunun kenarlığı
    Margin → Kutunun dışındaki yerleşim boşluğu
    Box-Sizing → Width ve height hesaplama modeli
    Outline → Layout'u değiştirmeyen anahat
    Box-Shadow → Layout'u değiştirmeyen görsel gölge
```
Bu bölümün en önemli noktası: CSS'te bir elementin kapladığı alan yalnızca width ve height değerlerinden ibaret değildir. Padding, border, margin ve box-sizing davranışı birlikte değerlendirilmelidir.

Box Model'i doğru anlamak, ilerleyen konulardaki Display, Positioning, Flexbox, Grid ve Responsive Layout yapılarını öğrenmek için güçlü bir temel oluşturur.