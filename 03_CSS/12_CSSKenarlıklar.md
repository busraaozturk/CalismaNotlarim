# CSS Kenarlıklar, Outline ve Gölgeler (Borders, Outline & Shadows)

CSS'te bir elementin görünümünü yalnızca arka plan rengi veya boyutları belirlemez. Elementin çevresindeki kenarlıklar, köşelerin şekli, odak göstergeleri ve gölgeler de tasarımın önemli parçalarıdır.

Örneğin bir ürün kartında ince bir kenarlık, bir butonda yuvarlatılmış köşeler veya bir form alanında klavye odağını gösteren bir outline kullanılabilir.

Bu bölümde CSS'in border, outline ve box-shadow özelliklerini, aralarındaki farkları ve gerçek projelerde nasıl kullanıldıklarını inceleyeceğiz.

```
    .card {
        padding: 24px;
        background-color: #ffffff;

        border: 1px solid #e5e2da;
        border-radius: 12px;

        box-shadow: 0 4px 16px rgba(0, 0, 0, 0.08);
    }
```

Bu örnekte:
- border kartın kenarlığını oluşturur.
- border-radius köşeleri yuvarlatır.
- box-shadow kartın çevresine gölge ekler.

## CSS Kenarlıklar Nedir?
**CSS'te border** bir elementin padding alanı ile margin alanı arasında bulunan kenarlık bölgesini kontrol eder. 

Bu alanı 05_CSSBoxModel konusunda incelemiştik.
```
    ┌────────────────────────────────┐
    │             MARGIN             │
    │  ┌──────────────────────────┐  │
    │  │          BORDER          │  │
    │  │  ┌────────────────────┐  │  │
    │  │  │      PADDING       │  │  │
    │  │  │   ┌────────────┐   │  │  │
    │  │  │   │  CONTENT   │   │  │  │
    │  │  │   └────────────┘   │  │  │
    │  │  └────────────────────┘  │  │
    │  └──────────────────────────┘  │
    └────────────────────────────────┘
```

Kenarlıklar üç temel özellik üzerinden tanımlanır.

|Özellik                               |Görevi                                |
|--------------------------------------|--------------------------------------|
|border-width                          |Kenarlığın kalınlığını belirler       |
|border-style                          |Kenarlığın çizgi stilini belirler     |
|border-color                          |Kenarlığın rengini belirler           |

Bu özellikler ayrı ayrı kullanılabildiği gibi border shorthand ile tek satırda da yazılabilir.

### Temel Kullanım
```
    .box{
        border-width: 2px;
        border-style: solid;
        border-color: #7d8570;
    }
```

Aynı tanımın kısa hali: 
```
    .box{
        border: 2px solid #7d8570;
    }
```

**Önemli:** Kenarlığın görünmesi için genellikle *border-style* özelliğinin none dışında bir değer alması gerekir. Çünkü varsayılan değeri *none*'dır.

## `border-width` - Kenarlık Kalınlığı
`border-width`, elementin kenarlığının kalınlığını belirler.

### Temel Kullanım
```
    .box{
        border-style: solid;
        border-width:2px;
    }
```
Burada elementin dört kenarında 2px kalınlığında bir kenarlık oluşturulur.

### Kullanılabilecek Değerler
```
    .box-1 {
        border-width: 1px;
    }

    .box-2 {
        border-width: 0.2rem;
    }

    .box-3 {
        border-width: thin;
    }

    .box-4 {
        border-width: medium;
    }

    .box-5 {
        border-width: thick;
    }
```

|Değer          |Açıklama                                     |
|---------------|---------------------------------------------|
|thin           |İnce kenarlık                                |
|medium         |Orta kalınlıkta kenarlık                     |
|thick          |Kalın kenarlık                               |
|px,rem vb.     |Uzunluk birimleriyle belirlenen kalınlık     |

thin, medium ve thick değerlerinin kesin piksel karşılıkları tarayıcıya bağlıdır.

Daha kontrollü bir tasarım için genellikle uzunluk değerleri tercih edilir.

### Farklı Kenarlara Farklı Kalınlık
```
    .box{
        border-style: solid;
        border-width: 1px 2px 3px 4px;
    }
```

Dört değer sırasıyla şu kenarlara uygulanır:
```
            1px
            TOP
        ┌───────────┐
    4px │           │ 2px
    LEFT │           │ RIGHT
        └───────────┘
            3px
            BOTTOM
```

Bu sıralama CSS'teki margin ve padding shorthand mantığıyla aynıdır.

### Bir, İki, Üç ve Dört Değer Kullanımı
|Kullanım                       |Davranış                     |
|-------------------------------|-----------------------------|
|border-width: 2px;             |Dört kenar                   |
|border-width: 2px 4px;         |Üst-alt 2px, sağ-sol 4px     |
|border-width: 2px 4px 6px;     |ÜĞst 2px, sağ-sol 4px, alt 6px|
|border-width: 1px 2px 3px 4px  |Üst, sağ, alt, sol           |

Bu kuralı hatırlamak için saat yönünde ilerlediğimzi düşünebiliriz: `Top - Right - Bottom - Left`

### `border-style` - Kenarlık Stilleri
`border-style`, kenarlığın hangi çizgi biçiminde görüntüleneceğini belirler.

### Yaygın Değerler
|Değer      |Açıklama       |
|-----------|---------------|
|none       |Kenarlık çizilmez|
|hidden     |Kenarlığı gizler; tablo kenarlık çakışmalarında özel davranışı vardır|
|solid      |Düz çizgi      |
|dashed     |Kesikli çizgi  |
|dotted     |Noktalı çizgi  |
|double     |Çift çizgi     |
|groove     |Oyuk görünümü  |
|ridge      |Kabartma görünümü  |
|inset      |İçe gömülü görünüm |
|outset     |Dışa çıkıntılı görünüm |

### Örnekler
```
    .box-1 {
        border: 2px solid #333;
    }

    .box-2 {
        border: 2px dashed #333;
    }

    .box-3 {
        border: 2px dotted #333;
    }

    .box-4 {
        border: 4px double #333;
    }
```

Görünümün birleştirilmesi şeması:
```
    solid    ──────────────────

    dashed   ─── ─── ─── ─── ──

    dotted   · · · · · · · · · ·

    double   ══════════════════
```

**groove, ridge, inset** ve **outset** stilleri kenarlığın rengine ve tarayıcının çizim biçimine bağlı olarak üç boyutlu bir etki oluşturabilir.

Modern arayüzlerde en sık karşılaşılan stiller genellikle **solid, dashed ve dotted** değerleridir.


### Kenarlara Farklı Stil Uygulamak
```
    .box {
        border-width: 2px;
        border-color: #333;
        border-style: solid dashes dotted double;
    }
```

Bu örnekte üst, sağ, alt ve sol kenarlarda farklı stiller kullanılır.

## `border-color`- Kenarlık Rengi
`border-color`, kenarlığın rengini belirler.

### Temel Kullanım
```
    .card {
        border-style: solid;
        border-width: 1px;
        border-color: #e5e2da;
    }
```

CSS'te geçerli olan renk biçimleri kenarlıklar için de kullanılabilir.
```
    .box-1 {
        border: 2px solid red;
    }

    .box-2 {
        border: 2px solid #7d8570;
    }

    .box-3 {
        border: 2px solid rgb(125, 133, 112);
    }

    .box-4 {
        border: 2px solid rgba(125, 133, 112, 0.5);
    }
```

### Farklı Kenarlara Farklı Renk
```
    .box {
        border-style: solid;
        border-width: 2px;

        border-color: red green blue orange;
    }
```
Sıralama yine üst, sağ, alt ve sol şeklindedir.

### `currentColor`Kullanımı
currentColor, elementin color özelliğinin hesaplanan değerini temsil eder.
```
    .button {
        color: #7d8570;
        border: 1px solid currentColor;
    }
```
Bu örnekte butonun yazı rengi ile kenarlık rengi aynı olur.
```
    .button:hover {
        color: #26251f;
    }
```

Yazı rengi değiştiğinde `currentColor` kullanan kenarlık da aynı renge uyum sağlar. Bu yöntem özellikle tekrar eden renk talimatlarını azaltmak için yararlıdır.

## border Shorthand
border, kenarlık kalınlığını, stilini ve rengini tek satırda tanımlamak için kullanılır.

### Genel Sözdizimi
`border: width style color;`

Örnek:
```
    .card {
        border: 1px solid #e5e2da;
    }
```

Şema: 
```
    border: 1px solid #e5e2da;
            │   │     │
            │   │     └── Color
            │   └──────── Style
            └──────────── Width
```

Bu üç değerin yazım sırası zorunlu değildir; ancak *width style color* sıralaması okunabilirlik açısından yaygın kullanılır.

### Değerlerin Hepsi Zorunlu Mu?
Hayır.
```
    .box {
        border: solid;
    }
```

Bu kullanım geçerlidir. Kalınlık ve renk, ilgili başlangıç değerlerinden belirlenir. Ancak gerçek projelerde daha öngörülebilir bir sonuç için genellikle üç değer birlikte yazılır.

### Shorthand Kullanırken Dikkat
```
    .box {
        border-color: red;
        border: 2px solid blue;
    }
```
İkinci tanım önceki kenarlık rengi ayarını değiştirir. Ayrıca border shorthand, ilgili kenarlık alt özelliklerini sıfırlayabilir. Bu nedenle aynı element üzerinde hem shorthand hem de uzun özellikler kullanılırken sıralamaya dikkat edilmelidir.

## Yönlere Özel Kenarlıklar
Her zaman elementin dört tarafına da kenarlık uygulamak istemeyebiliriz. Örneğin bir menü öğesinin yalnızca altına çizgi eklemek veya kartın sol kenarını vurgulamak isteyebiliriz.

Bunun için yönlere özel özellikler kullanılır.
|Özellik            |Uygulandığı Kenar      |
|-------------------|-----------------------|
|border-top         |Üst                    |
|border-right       |Sağ                    |
|border-bottom      |Alt                    |
|border-left        |Sol                    |

### Alt Kenarlık
```
    .nav-link {
        border-bottom: 2px solid transparent;
    }

    .nav-link:hover {
        border-bottom-color: #7d8570;
    }
```

Bu örnekte kenarlık için önceden alan ayrılır. Böylece hover sırasında yeni bir kenralık eklenmesinden kaynaklanabilecek boyut değişimi önlenir.

### Sol Kenarlık ile Vurgu
```
    .notice {
        padding: 16px;
        background-color: #f2f0eb;

        border-left: 4px solid #7d8570;
    }
```
Bu kullanım bildirim, açıklama veya bilgi kutularında tercih edilebilir.

### Tek Bir Kenarın Özelliklerini Ayrı Tanımlamak
```
    .box {
        border-bottom-width: 2px;
        border-bottom-style: solid;
        border-bottom-color: #7d8570;
    }
```
Bu üç tanımın kısa karşılığı:
```
    .box {
        border-bottom: 2px solid #7d8570;
    }
```

### Mantıksal Kenarlık Özellikleri
CSS'te fiziksel yönlere ek olarak yazı yönüne uyum sağlayan mantıksal özellikler de vardır.
```
    .notice {
        border-inline-start: 4px solid #7d8570;
    }
```

`border-inline-start`, soldan sağa yazılan yatay metinlerde genellikle sol kenarı ifade eder. Sağdan sola yazılan yatay metinlerde ise sağ kenara karşılık gelir.

Bu özellik çok dilli arayüzlerde daha esnek tasarımlar oluşturmak için kullanılabilir.

## border-radius - Köşeleri Yuvarlatma
border-radius, bir elementin köşelerini yuvarlatmamızı sağlar. En sık kullanılan CSS özelliklerinden biridir.

### Temel Kullanım
```
    .card {
        border: 1px solid #e5e2da;
        border-radius: 12px;
    }
```
Burada kartın dört köşesi de 12px yarıçapla yuvartılır.

### Farklı Değerler
```
    .box-1 {
        border-radius: 0;
    }

    .box-2 {
        border-radius: 8px;
    }

    .box-3 {
        border-radius: 16px;
    }

    .box-4 {
        border-radius: 50%;
    }
```

### Görsel Mantık
```
    border-radius: 0

    ┌──────────────┐
    │              │
    └──────────────┘


    border-radius: 12px

    ╭──────────────╮
    │              │
    ╰──────────────╯
```

Bu çizimler yalnızca temel görünüm farkını temsil eder.

### Dairesel Element Oluşturmak
```
    .avatar {
        width: 80px;
        height: 80px;
        border-radius: 50%;
    }
```

Genişlik ve yükseklik eşitse 50% değeri dairesel bir görünüm oluşturabilir. Ancak genişlik ve yükseklik farklıysa sonuç daire değil, elips olabilir.

### Farklı Köşelere Farklı Değer
```
    .card {
        border-radius: 8px 16px 24px 32px;
    }
```

Sıralama: `Üst sol - Üst sağ - Alt sağ - Alt sol`
Bu sıralama *border-width* gibi kenar özelliklerinden farklıdır; burada kenarlar değil köşeler tanımlanır.

### Köşeleri Ayrı Ayrı Tanımlamak
```
    .card {
        border-top-left-radius: 12px;
        border-top-right-radius: 12px;
        border-bottom-right-radius: 0;
        border-bottom-left-radius: 0;
    }
```
Bu örnekte yalnızca üst köşeler yuvarlatılır.

### Eliptik Köşeler
*border-radius*, iki farklı yarıçap grubuyla da kullanılabilir.

```
    .box {
        border-radius: 30px / 15px;
    }
```

/ işaretinden önceki değer yatay, sonraki değer dikey yarıçapı belirler. Bu yöntem daha özel köşe şekilleri oluşturmak için kullanılabilir.

### border-radius İçeriği Keser mi?
Her zaman değil.
```
    .card {
        border-radius: 16px;
    }
```

Bu tanım, elementin kendi arka plan ve kenarlık görünümünü yuvarlatır. Ancak taşan çocuk içerikleri otomatik olarak kesmek zorunda değildir.

Örneğin kartın içindeki görselin de köşelere uygun biçimde kesilmesi gerekiyorsa:
```
    .card{
        border-radius: 16px;
        overflow: hidden;
    }
```
kullanılabilir.

**Dikkat:** `overflow: hidden`, taşan içerikleri ve bazı görsel efektleri kesebilir. Bu nedenle her kartta otomatik olarak kullanılmamalıdır.