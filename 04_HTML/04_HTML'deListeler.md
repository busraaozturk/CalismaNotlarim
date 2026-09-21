# HTML'de Listeler
HTML'de birbiriyle ilişkili içerikleri düzenli bir şekilde göstermek için liste elementleri kullanılır.

Örneğin teknolojiler, özellikler veya menü seçenekleri gibi sıralamanın önemli olmadığı içerikler liste halinde gösterilebilir. Benzer şekilde yapılacak işlemler veya adımlar gibi sıralamanın önemli olduğu içerikler de listelerle ifade edilebilir.

HTML'de temel olarak üç liste türü bulunur:
- Sırasız listeler: `<ul>`
- Sıralı listeler: `<ol>`
- Açıklama listeleri: `<dl>`

## Sırasız Listeler — <ul>
`<ul>` **(unordered list)**, öğelerin sıralamasının önemli olmadığı durumlarda kullanılır.

Listenin içerisindeki her öğe `<li>` **(list item)** elementiyle tanımlanır.
```
    <ul>
        <li>HTML</li>
        <li>CSS</li>
        <li>JavaScript</li>
    </ul>
```

Tarayıcı bu listeyi varsayılan olarak madde işaretleriyle gösterir:
```
    • HTML
    • CSS
    • JavaScript
```

Burada HTML, CSS ve JavaScript'in hangi sırada gösterildiği içeriğin anlamını değiştirmediği için `<ul>` kullanılması uygundur.

Başka bir örnek:
```
    <h2>Ürün Özellikleri</h2>

    <ul>
        <li>Suya dayanıklı</li>
        <li>Bluetooth bağlantısı</li>
        <li>Uzun pil ömrü</li>
    </ul>
```

## Sıralı Listeler — <ol>

`<ol>` **(ordered list)**, öğelerin sırasının anlam taşıdığı durumlarda kullanılır.
```
    <ol>
        <li>Projeyi bilgisayarınıza indirin.</li>
        <li>Bağımlılıkları yükleyin.</li>
        <li>Projeyi çalıştırın.</li>
    </ol>
```
Tarayıcı varsayılan olarak öğeleri numaralandırır:
```
    1. Projeyi bilgisayarınıza indirin.
    2. Bağımlılıkları yükleyin.
    3. Projeyi çalıştırın.
```
Burada işlemlerin sırası önemlidir. Bu nedenle `<ul>` yerine `<ol>` kullanılması daha anlamlıdır.

Temel ayrımı şöyle düşünebiliriz:
```
    Sıralama önemli mi?
            │
            ├── Hayır → <ul>
            │
            └── Evet  → <ol>
```

## `<li>` Elementi

`<li> (list item)`, bir listenin içerisindeki her bir öğeyi temsil eder.
```
    <ul>
        <li>Ana Sayfa</li>
        <li>Projeler</li>
        <li>Hakkımda</li>
    </ul>
```

`<li>` doğrudan `<ul>` veya `<ol>` gibi liste yapılarının içerisinde kullanılır.

Örneğin şu kullanım doğru değildir:
```
    <!-- Yanlış -->
    <ul>
        <p>HTML</p>
        <p>CSS</p>
    </ul>
```
Bunun yerine:
```
    <ul>
        <li>HTML</li>
        <li>CSS</li>
    </ul>
```
kullanılmalıdır.

Ancak `<li>` içerisinde yalnızca düz metin bulunmak zorunda değildir.
```
    <ul>
        <li>
            <h3>HTML</h3>
            <p>Web sayfalarının yapısını oluşturur.</p>
        </li>

        <li>
            <h3>CSS</h3>
            <p>Web sayfalarının görünümünü düzenler.</p>
        </li>
    </ul>
```
Liste öğelerinin içerisinde ihtiyaca göre farklı HTML elementleri bulunabilir.

## `<ol>` İçin Temel Attribute'lar
Sıralı listelerin numaralandırma davranışını değiştirmek için baxı HTML attribute'ları kullanılabilir.

### `start`
Listenin hangi sayıdan başlayacağını belirler.
```
    <ol start="5">
        <li>HTML</li>
        <li>CSS</li>
        <li>JavaScript</li>
    </ol>
```

Sonuç:
```
    5. HTML
    6. CSS
    7. JavaScript
```

Bu özellik özellikle daha önce başlamış bir listenin devamını göstermek gerektiğinde kullanılabilir.

### `reversed`
Listenin ters yönde numaralandırılmasını sağlar.
```
    <ol reversed>
        <li>Üçüncü</li>
        <li>İkinci</li>
        <li>Birinci</li>
    </ol>
```
Liste azalan numaralarla gösterilir.

`reserved`, bir **boolean** attribute örneğidir.

### `type`
Numaralandırmanın hangi biçimde gösterileceğini belirleyebilir.
```
    <ol type="A">
        <li>HTML</li>
        <li>CSS</li>
        <li>JavaScript</li>
    </ol>
```
Sonuç:
```
    A. HTML
    B. CSS
    C. JavaScript
```

Temel değerlerden bazıları:
| Değer | Görünüm    |
| ----- | ---------- |
| `1`   | 1, 2, 3    |
| `A`   | A, B, C    |
| `a`   | a, b, c    |
| `I`   | I, II, III |
| `i`   | i, ii, iii |

Örneğin:
```
    <ol type="I">
        <li>Giriş</li>
        <li>Gelişme</li>
        <li>Sonuç</li>
    </ol>
```

Ancak yalnızca görsel tasarım amacıyla liste işaretlerini değiştirmek gerekiyorsa bu işlemler CSS ile de yönetilebilir.

## İç İçe Listeler
Bir liste öğesinin içerisinde başka bir liste bulunabilir. Buna **nested list (iç içe liste)** denir.

Örneğin frontend konularını kategorilere ayıralım:
```
    <ul>

        <li>
            HTML

            <ul>
                <li>Semantic HTML</li>
                <li>Formlar</li>
                <li>Tablolar</li>
            </ul>
        </li>

        <li>
            CSS

            <ul>
                <li>Flexbox</li>
                <li>Grid</li>
            </ul>
        </li>

    </ul>
```

Bu yapının mantığı şöyledir:
```
    HTML
    ├── Semantic HTML
    ├── Formlar
    └── Tablolar

    CSS
    ├── Flexbox
    └── Grid
```

Burada alt liste, ilgili `<li>` elementinin içerisinde bulunur. İç içe listeler özellikle kategori yapılarında, dokümantasyon menülerinde ve hiyerarşik içeriklerde kullanılabilir.

## Açıklama Listeleri - `<dl>, <dt>, <dd>`
HTML'de daha az kullanılan ancak bilinmesi faydalı olan bir diğer yapı **description list (açıklama listesi)**dir.

Üç temel elementten oluşur:
```
    <dl> → Description List
    <dt> → Description Term
    <dd> → Description Details
```

Örneğin:
```
    <dl>

        <dt>HTML</dt>
        <dd>Web sayfalarının yapısını tanımlayan işaretleme dilidir.</dd>

        <dt>CSS</dt>
        <dd>Web sayfalarının görünümünü ve düzenini kontrol eder.</dd>

    </dl>
```

Burada:

`<dl>` → açıklama listesinin tamamını,

`<dt>` → açıklanan terimi,

`<dd>` → terime ait açıklamayı

temsil eder.

Mantığını şöyle düşünebiliriz:
```
    HTML
    └── Web sayfalarının yapısını tanımlayan işaretleme dilidir.

    CSS
    └── Web sayfalarının görünümünü ve düzenini kontrol eder.
```

Açıklama listeleri yalnızca sözlük oluşturmak için kullanılmaz. Bir isim ile ona ait açıklama/değer arasında ilişki kurulması gereken farklı içeriklerde de kullanılabilir.

## Navigasyonlarda Liste Kullanımı
Navigasyon alanlarında listelerle sıkça karşılaşırız.

Örneğin:
```
    <nav>
        <ul>
            <li>
                <a href="/">Ana Sayfa</a>
            </li>

            <li>
                <a href="/projects">Projeler</a>
            </li>

            <li>
                <a href="/contact">İletişim</a>
            </li>
        </ul>
    </nav>
```

Burada önceki konularda öğrendiğimiz semantic elementler birlikte kullanılmaktadır:
```
    <nav>
    ↓
    Navigasyon alanı

    <ul>
    ↓
    Navigasyon seçeneklerinin listesi

    <li>
    ↓
    Her bir seçenek

    <a>
    ↓
    Kullanıcıyı ilgili sayfaya götüren bağlantı
```

Ancak önemli bir nokta var; `<nav>` içerisinde mutlaka `<ul>` kullanılması zorunlu değildir.

Şu yapı da geçerli HTML'dir:
```
    <nav>
        <a href="/">Ana Sayfa</a>
        <a href="/projects">Projeler</a>
        <a href="/contact">İletişim</a>
    </nav>
```

Eğer navigasyon öğelerini **bir seçenekler listesi olarak ifade etmek** istiyorsak `<ul>` kullanabiliriz. Buradaki tercih içerik yapısına göre yapılmalıdır.

## Liste İşaretlerini HTML ile mi CSS ile mi Değiştirmeliyiz?
HTML içeriğin anlamını ve yapısını tanımlar. Listenin görsel olarak nasıl gösterileceği ise çoğunlukla CSS'in sorumluluğundadır.

Örneğin bir `<ul>` varsayılan olarak madde işaretleriyle gösterilebilir:
```
    • HTML
    • CSS
    • JavaScript
```

Ancak tasarımda bu işaretleri istemiyorsak HTML yapısını değiştirmek yerine CSS kullanabiliriz:
```
    ul {
        list-style: none;
    }
```

Bu nedenle; `<ul>` kullanmamızın nedeni ekranda madde işareti görmek değil, içeriğin sırasız bir liste olduğunu belirtmektir.

Bu ayrım semantic HTML açısından önemlidir.

## Hangi Listeyi Kullanmalıyım?
Liste türünü seçerken görünüşüne değil, içeriğin anlamına bakmalıyız.

### Sıralama Önemli Değilse → <ul>
```
    <ul>
        <li>HTML</li>
        <li>CSS</li>
        <li>JavaScript</li>
    </ul>
```

### Sıralama Önemliyse → <ol>
```
    <ol>
        <li>Dosyayı indirin.</li>
        <li>Dosyayı açın.</li>
        <li>Kurulumu başlatın.</li>
    </ol>
```

### Terim ve Açıklama Varsa → <dl>
```
    <dl>
        <dt>HTML</dt>
        <dd>HyperText Markup Language</dd>
    </dl>
```

## Sık Yapılan Hatalar
Listelerde yapılan temel hatalardan biri, yalnızca görsel olarak alt alta duran içerikleri liste olarak düşünmemektir.

Örneğin:
```
    <p>HTML</p>
    <p>CSS</p>
    <p>JavaScript</p>
```

İçerik gerçekten bir teknoloji listesi oluşturuyorsa aşağıdaki şekilde ifade etmek daha anlamlıdır.
```
    <ul>
        <li>HTML</li>
        <li>CSS</li>
        <li>JavaScript</li>
    </ul>
```

Diğer taraftan her alt alta bulunan içerik de otomatik olarak liste değildir.

Burada yine temel sorumuz: `Bu içerikler birbirleriyle ilişkili bir öğeler grubu mu?` olmalıdır.

# Kısaca Özet

HTML'de üç temel liste yapısı bulunur:
```
    <ul> → Sıralamanın önemli olmadığı listeler

    <ol> → Sıralamanın önemli olduğu listeler

    <dl> → Terim ve açıklama/değer ilişkisi bulunan listeler
```

`<ul>` ve `<ol>` içerisindeki öğeler `<li>` ile oluşturulur:
```
    <ul>
        <li>HTML</li>
        <li>CSS</li>
    </ul>
```
Açıklama listelerinde ise aşağıdakş gibi kullanılır:
```
    <dl>
        <dt>HTML</dt>
        <dd>Web sayfalarının yapısını oluşturur.</dd>
    </dl>
```

Liste türünü seçerken temel kriter **listenin ekranda nasıl görüneceği değil, içerik öğeleri arasındaki ilişkidir.**

Bu yaklaşım, daha önce öğrendiğimiz **Semantic HTML** mantığının listelerdeki karşılığıdır.