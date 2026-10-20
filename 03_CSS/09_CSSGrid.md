# CSS Grid (Izgara Yerleşim Sistemi)
CSS Grid, HTML elementlerini **satırlar (rows) ve sütunlar (columns)** üzerinde düzenlememizi sağlayan iki boyutlu (two-dimensional) bir CSS layout sistemidir.

Grid sayesinde sayfanın ana yerleşimini, ürün listelerini, dashboard bileşenlerini ve galeri düzenlerini daha kontrollü biçimde oluşturabiliriz.

Bu bölümde Grid'in temel kavramlarını, kullanılan CSS özelliklerini, responsive davranışlarını ve gerçek projelerdeki kullanımını inceleyeceğiz.

## Grid Nedir ve Neden Kullanılır?
CSS Grid, elementlerin satır ve sütunlardan oluşan bir ızgara üzerinde konumlandırılmasını sağlar. Örneğin üç sütun ve iki satırdan oluşan bir düzen düşünelim:
```
    ┌──────────┬──────────┬──────────┐
    │  Kart 1  │  Kart 2  │  Kart 3  │
    ├──────────┼──────────┼──────────┤
    │  Kart 4  │  Kart 5  │  Kart 6  │
    └──────────┴──────────┴──────────┘
```

Bu düzeni CSS Grid ile oluşturabiliriz.
```
    <div class="container">
        <div class="item">1</div>
        <div class="item">2</div>
        <div class="item">3</div>
        <div class="item">4</div>
        <div class="item">5</div>
        <div class="item">6</div>
    </div>

    .container {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 16px;
    }
```

Burada:
- display: grid kapsayıcıyı Grid container yapar.
- grid-template-column sütunların yapısını belirler.
- repeat (3, 1fr) üç çeşit paylı sütun oluşturur.
- gap hücreler arasında boşluk oluşturur.

Altı element otomatik olarak üç sütuna dağıtılır ve iki satır meydana gelir.

### Grid ile Flexbox Arasındaki Fark
Flexbox ve Grid, CSS'in iki farklı yerleşim sistemidir.
|Özellik        |Flexbox        |Grid           |
|---------------|---------------|---------------|
|Yerleşim modeli|Tek boyutlu    |İki boyutlu    |
|Temel kontrol  |Ana eksen      |Satır ve sütun |
|İçerik akışı   |Genellikle içerik odaklı   |İçerik veya düzen odaklı   |
|Navbar         |Çok uygun      |Kullanılabilir |
|Kart içeriği   |Çok uygun      |Kullanılabilir |
|Ürün ızgarası  |Kullanılabilir |Genellikle daha uygun  |
|Dashboard      |Kullanılabilir |Genellikle daha uygun  |
|Sayfa iskeleti |Kullanılabilir |Genellikle daha uygun  |

Flexbox'ta bir satırdaki elementlerin genişlikleri, diğer satırdaki elementlerle doğrudan aynı sütun çizgilerini paylaşmak zorunda değildir.

Grid'de ise sütun çizgileri üzerinden daha tutarlı bir yerleşim oluşturabiliriz.

Temel yaklaşım:
- Tek bir yönde içerik hizalaması gerekiyorsa Flexbox,
- Satır ve sütunların birlikte yönetilmesi gerekiyorsa Grid tercih edilebilir.

Bu konuya ilişkin temel karşılaştırma 08_CSSFlexbox.md bölümünde de ele alınmıştır.

### Grid Ne Zaman Kullanılır?
CSS Grid özellikle şu alanlarda kullanışlıdır:
- Header, sidebar, main ve footer içeren sayfa iskeletleri
- E-ticaret ürün listeleri
- Yönetim panelleri (dashboard)
- Fotoğraf galerileri
- Blog kartları
- Farklı boyutlardaki içerik kutuları
- Responsive kart ızgaraları

## Temel Kavramlar
Grid'in çalışma mantığını anlamak için öncelikle kullanılan terimleri öğrenmeliyiz.

### 1. Grid Container ve Grid Item
**Grid Container:** display:grid veya display: inlinegrid uygulanan kapsayıcıdır.

**Grid Item:** Grid container'ın doğrudan çocuklarıdır.
```
    <div class="container">
        <div class="item">Kart 1</div>
        <div class="item">Kart 2</div>
        <div class="item">Kart 3</div>
    </div>

    .container {
        display: grid;
    }
```

Burada .containerGrid container, .item elementleri Grid item'dır.

Ancak şu örneğe dikkat edelim:
```
    <div class="container">
        <article class="card">
            <h2>Başlık</h2>
            <p>Açıklama</p>
        </article>
    </div>
```

Burada:
- .card bir Grid item'dr.
- h2 ve p, .container açısından doğrudan Grid item değildir.

.card elementine ayrıca display:grid uygularsak kendi çocukları için yeni bir Grid container oluşturabiliriz.

### 2. Grid Line (Izgara Çizgisi)
Grid line, saırları ve sütunları birbirinden ayıran çizgilerdir. Üç sütunlu bir Grid'de dört dikey çizgi bulunur.
```
     1          2          3          4
     │          │          │          │
     │ Sütun 1  │ Sütun 2  │ Sütun 3  │
     │          │          │          │
```

Benzer şekilde iki satır için üç yatay çizgi bulunur. Çizgi numaraları, item'ların nerede başlayıp nerede biteceğini belirlemek için kullanılır.

**Önemli:** Grid'de çizgi numaraları 1'den başlar. Sütun sayısı ile çizgi sayısı aynı değildir.

### 3. Grid Track (Izgara İzi)
Grid track, iki komşu grid line arasındaki satır veya sütundur.

Örneğin:
```
    .container{
        display: grid;
        grid-template-columns: 20px 1fr 1fr;
    }
```

Bu Grid'de üç sütun Track'i vardır.

Birinci sütun 200px, diğer iki sütun ise kalan alanın uygun paylarını kullanır.

### 4. Grid Cell (Izgara Hücresi)
Grid cell, bir satır ve bir sütunun kesişiminde oluşan en küçük yerleşim birimidie.

```
    ┌──────────┬──────────┐
    │ Hücre 1  │ Hücre 2  │
    ├──────────┼──────────┤
    │ Hücre 3  │ Hücre 4  │
    └──────────┴──────────┘
```

Bir Grid itemi bir hücreyi veya birden fazla hücreyi kaplayabilir.

### 5. Grid Area (Izgara Alanı)
Grid area, dört grid line ile sınırlandırılan dikdörtgen bir bölgedir. Bir item birden fazla satır ve sütunu kaplayabilir.

```
    ┌───────────────────────┬───────────┐
    │                       │           │
    │       Grid Area       │  Kart 2   │
    │                       │           │
    ├───────────────────────┼───────────┤
    │         Kart 3        │  Kart 4   │
    └───────────────────────┴───────────┘
```

Grid area, çizgi numaralarıyla veya isimlendirilmiş alanlarla tanımlanabilir.

### 6. Explicit Grid ve Implict Grid
Explicit Grid, bizim doğrudan tanımladığımız satır ve sütunlardan oluşur.
```
    .container {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-template-rows: 100px 100px;
    }
```

Burada üç sütun ve iki satır açıkça tanımlanmıştır.

**Implicit Grid,** tanımladığımız ızgaranın dışında yeni track'lere ihtiyaç duyulduğunda tarayıcı tarafından oluşturulur.

Örneğin yukarıdaki Grid'e dokuz element eklersek üçüncü bir satır gerekebilir. Tarayıcı bu satırı otomatik oluşturur.

### 7. Negatif Çizgi Numaraları
Explicit Grid çizgilerine sondan başlayarak negatif numaralarla da erişebiliriz.

Üç sütunlu bir Grid için:
```
    Pozitif:     1       2       3       4
                │       │       │       │
                │       │       │       │
    Negatif:    -4      -3      -2      -1
```

Örneğin:
```
    .item {
        grid-column: 1 / -1;
    }
```

Item, explicit Grid'in ilk sütun çizgisinden son sütun çizgisine kadar uzanır. Bu kullanım özellikle tam genişlik kaplayan header veya footer gibi elementlerde kullanışlıdır.

Not: -1, explicit Grid'in son çizgisini ifade eder; otomatik oluşmuş bütün implict sütunların en sonunu ifade etmek zorunda değildir.

## display: grid ve display: inline-grid
Grid container oluşturmanın iki temel yolu vardır.

### display: grid
```
    .container {
        display:grid;
    }
```

Element dış yerleşimde block-level davranış gösterirken çocuklarını Grid sistemiyle düzenler.

Genellikle sayfa bölümleri ve kart ızgaraları için kullanılır.

### display: inline-grid
```
    .container {
        display: inline-grid;
    }
```

Element dış yerleşimde inline-level davranış gösterir. İçeride ise yine Grid sistemi kullanılır.

Örneğin küçük bir ikon ve metin bileşeni:
```
    <span class="status">
        <span>✓</span>
        <span>Aktif</span>
    </span>
```
```
    .status {
        display: inline-grid;
        grid-template-columns: auto auto;
        align-items: center;
        gap: 6px;
    }
```

### Karşılaştırma
|Özellik            |grid                       |inline-grid                |
|-------------------|---------------------------|---------------------------|
|İç yerleşim        |Grid                       |Grid                       |
|Dış yerleşim       |Block-level                |Inline-level               |
|Yaygın kullanım    |Sayfa ve kart düzenleri    |Küçük satır içi bileşenler |

Bu ayrım Flexbox bölümündeki flex ve inline-flex ayrımıyla aynı mantıktadır.

## Satır ve Sütun Tanımlama
Grid'de satır ve sütunların boyutlarını iki temel property ile belirleriz.

```
    grid-template-columns
    grid-template-rows
```

### 1. grid-template-columns
Sütun sayısını ve sütun genişliklerini belirler.
```
    .container {
        display:grid;
        grid-template-columns: 200px 300px 200px;
    }
```

Bu örnekte üç sütun oluşur:
```
    ┌────────────┬────────────────┬────────────┐
    │   200px    │     300px      │   200px    │
    └────────────┴────────────────┴────────────┘
```

Sütunlar farklı ölçülerle tanımlanabilir.
```
    .container {
        grid-template-columns: 25% 50% 25%;
    }
```
Ancak yüzde değerleriyle birlikte gap kullanıldığında toplam genişlik kapsayıcıyı aşabilir. Bu nedenle esnek yerleşimlerde fr birimi sıkça tercih edilir.

### 2. grid-template-rows
Satır yüksekliklerini belirler.
```
    .container {
        display: grid;
        grid-template-rows: 100px 200px;
    }
```
Bu kullanım iki explicit satır tanımlar. İki satır 100px, ikinci satır 200px yüksekliğindedir.

### 3. fr Birimi
fr, Grid'e özgü esnek bir ölçü birimidir. Kullanılabilir alanın paylaştırılmasını sağlar.

```
    .container {
        display:grid;
        grid-template-columns: 1fr 1fr 1fr;
    }
```

Bu kullanım üç eşit paylı sürun oluşturur. Başka bir örnek:
```
    .container {
        grid-template-columns: 1fr 2fr 1fr;
    }
```

Uygun boyutlandırma koşullarında alana 1:2:1 oranında paylaştırılır.
```
    ┌─────────┬──────────────────┬─────────┐
    │   1fr   │       2fr        │   1fr   │
    └─────────┴──────────────────┴─────────┘
```

### fr ve % Farkı
%, kapsayıcının ilgili boyutuna göre hesaplanır.

fr ise Grid boyutlandırma algoritmasında kullanılabilir esnek alanı paylaştırır.

Örneğin:
```
    .container {
        display:grid;
        grid-template-columns: 1fr 1fr;
        gap:20px;
    }
```

İki sütun arasında 20px boşluk ayrıldıktan sonra kalan alan eşit paylaştırılabilir.

Buna karşılık:
```
    .container {
        display: grid;
        grid-template-columns: 50% 50%;
        gap: 20px;
    }
```
kullanımında iki yüzde sütun zaten kapsayıcı genişliğinin tamamını kapladığı için gap taşmaya neden olabilir.

**Önemli:** 1fr, her koşulda minimum boyutu sıfır olan bir sütun anlamına gelmez. İçeriklerin minimum boyutları sonucu etkileyebilir.

Bu konuyu 04 — CSS Birimleri bölümündeki göreli ölçü birimleriyle birlikte değerlendirebiliriz.

### 4. repeat() Fonksiyonu
Tekrarlanan satır ve sütun tanımlarını daha kısa yazmamızı sağlar.
```
    .container {
        grid-template-columns: 1fr 1fr 1fr;
    }
```
Yerine şu şekilde yazabiliriz:
```
    .container {
        grid-template-columns: repeat(3, 1fr);
    }
```

Farklı değerler de tekrar edilebilir.
```
    .container {
        grid-template-columns: repeat(2, 100px 200px);
    }
```

Bu kullanım dört sütun oluşturur : `100px | 200px | 100px | 200px`

### 5. minmax() Fonksiyonu
minmax(), bir Grid track'i için minimum ve maksimum boyut sınırlarını tanımlar.
```
    .container {
        grid-template-columns: minmax(200px, 1fr);
    }
```

İlk sütunun minimum boyutu 200px olarak belirlenir ve uygun koşullarda esnek şekilde büyüyebilir. Responsive Grid düzenlerinde sıkça kullanılır.
```
    .container{
        grid-template-columns: repeat(3, minmax(0, 1fr));
    }
```
Burada **minmax(0, 1fr)** sütunların içerik kaynaklı otomatik minimum genişlik kısıtına takılmadan küçülebilmesini sağlayabilir.

### 6. auto, min-content ve max-content
Grid track'lerinin boyutlandırılmasında içerik odaklı değerler de kullanılabilir.

**auto**
```
    .container {
        grid-template-columns: auto 1fr;
    }
```
auto, Grid boyutlandırma kurallarına göre içeriği ve kullanılabilir alanı dikkate alır. Her durumda yalnızca içerik kadar genişlik oluşturduğu varsayılmamalıdır.

**min-content**
```
    .container {
        grid-template-columns: min-content 1fr;
    }
```
İçeriğin kendi kurallarına göre ulaşabildiği en küçük içsel boyutunu kullanır. Örneğin metin, izin verilen satır kırılma noktalarından bölünerek daralabilir.

**max-content**
```
    .container {
        grid-template-columns: max-content 1fr;
    }
```
İçeriğin mümkün olan satır kırılmalarına zorlanmadan ihtiyaç duyduğu içsel boyutu temel alır. Uzun içeriklerde taşmaya yol açabilir.

### Kısa Karşılaştırma
|Değer                  |Temel davranış                         |
|-----------------------|---------------------------------------|
|px                     |Sabit boyut                            |
|%                      |Kapsayıcıya göre oransal boyut         |
|fr                     |Esnek alan payı                        |
|auto                   |Grid algoritmasına göre otomatik boyut |
|min-content            |Minimum içsel boyut                    |
|max-content            |Maksimum içsel boyut                   |
|minmax()               |Minimum ve maksimum sınır              |
|repeat()               |Tekrarlanan track tanımı               |

## gap, row-gap ve column-gap
Grid item'ları arasında boşluk oluşturmak için **gap** kullanılır.
```
    .container {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 20px;
    }
```
Bu kullanım satır ve sütun aralıklarını 20px yapar.

### Farklı Satır ve Sütun Boşlukları
```
    .container {
        row-gap: 24px;
        column-gap: 16px;
    }
```

Kısaltılmış kullanım:
```
    .container {
        gap: 24px 16px;
    }
```

İlk değer satır, ikinci değer sütun boşluğudur. Bu özelliklerin temel mantığı Flexbox bölümünde anlatılan gap kullanımıyla aynıdır. 

**Not:** gap, Grid container'ın dış kenarlarında otomatik olarak padding oluşturmaz. Boşluk track'ler arasında uygulanır.

## Item'ları Yerleştirme - Çizgi Tabanlı Yerleşim
Grid item'larını belirli satır ve sütun çizgileri arasına yerleştirebiliriz. Bunun için dört temel property bulunur:
- grid-column-start
- grid-column-end
- grid-row-start
- grid-roe-wnd

### 1. Sütun Çizgilerine Göre Yerleştirme
Üç sütunlu bir Grid düşünelim:
```
    .container {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
    }
```

Çizgiler:
```
    1         2         3         4
    │         │         │         │
    ├─────────┼─────────┼─────────┤
    │ Sütun 1 │ Sütun 2 │ Sütun 3 │
    └─────────┴─────────┴─────────┘
```

Bir item'ın iki sütun kaplamasını sağlayalım.
```
    .item {
        grid-column-start: 1;
        grid-column-end: 3;
    }
```
Item, birinci çizgide başlar ve üçüncü çizgide biter. Yani iki sütun kaplar.

### 2. grid-column Kısaltması
Aynı işlemi daha kısa yazabiliriz.
```
    .item {
        grid-column:1/3;
    }
```

Tam genişlik kaplamak için:
```
    .item {
        grid-column: 1 / -1;
    }
```

### 3. Satır Çizgilerine Göre Yerleştirme
```
    .item{
        grid-row-start: 2;
    }
```
Bu item ikinci yatay çizgiden dördüncü yatay çizgiye kadar uzanır. Kısaltılmış hali:
```
    .item {
        grid-row: 2 /4 ;
    }
```
İki satır kaplar.

### 4. span Anahtar Kelimesi
span, item'ın kaç track boyunca uzanacağını belirtir.
```
    .item {
        grid-column: span 2;
    }
```
Bu kullanım item'ın iki sütun kaplamasını ister. 

Başlangıç çizgisi otomatik yerleşim algoritması tarafından belirlenebilir.

Belirli bir çizgiden başlatmak için:
```
    .item {
        grid-column: 2 / span 2;
    }
```
Bu durumda item ikinci çizgiden başlayarak iki sütun boyunca uzanır. Benzer şekilde:
```
    .item {
        grid-row: span 3;
    }
```
item'ın üç satır kaplamasını sağlar.

### 5. grid-area - Dört Değerli Kullanım
grid-area, satır ve sütun yerleşimini tek property üzerinden tanımlayabilir.

Sıralama: `grid-area: row-start / column-start / row-end / column-end;`

Örneğin:
```
    .item {
        grid-area: 2 / 1 / 4 / 3;
    }
```

Açılımı:
```
    .item {
        grid-row-start: 2;
        grid-column-start: 1;
        grid-row-end: 4;
        grid-column-end: 3;
    }
```
Bu item iki satır ve iki sütun kaplar.

**Önemli:** grid-ares dört değerli çizgi tabanlı yerleşim için kullanılabildiği gibi, isimlendirilmiş Grid alanlarına bağlanmak için de kullanılabilir.

## grid-template-areas ile İsimlendirilmiş Alanlar
Grid'in güçlü özelliklerinden biri, sayfa yerleşimini isimlendirilmiş alanlar üzerinden tanımlayabilmemizdir.

Örneğin şu sayfa iskeletini oluşturalım:
```
    ┌───────────────────────────────┐
    │            HEADER             │
    ├───────────┬───────────────────┤
    │           │                   │
    │  SIDEBAR  │       MAIN        │
    │           │                   │
    ├───────────┴───────────────────┤
    │            FOOTER             │
    └───────────────────────────────┘
```

HTML:
```
    <div class="layout">
        <header class="header">Header</header>
        <aside class="sidebar">Sidebar</aside>
        <main class="main">Main</main>
        <footer class="footer">Footer</footer>
    </div>
```

CSS:
```
    .layout {
        display: grid;

        grid-template-columns: 240px minmax(0, 1fr);

        grid-template-areas:
            "header header"
            "sidebar main"
            "footer footer";

        gap: 20px;
    }

    .header {
        grid-area: header;
    }

    .sidebar {
        grid-area: sidebar;
    }

    .main {
        grid-area: main;
    }

    .footer {
        grid-area: footer;
    }
```

Burada her satır, Grid'in bir satırıno temsil eder. 

```
    "header header"
```
Header iki sütunu kaplar.

```
    "sidebar main"
```
Sidebar birinci sütuna, main ikinci sütuna yerleşir.

```
    "footer footer"
```
Footer iki dütunu kaplar.

### Boş Hücre İçin .  Kullanımı
Bazı hücreleri boş bırakmak isteyebiliriz.
```
    .layout {
        grid-template-areas:
            "header header"
            "sidebar main"
            ". footer";
    }
```

Burada son satırın ilk hücresi isimlendirilmiş bir alan içermez. `.` işareti boş alan hücresini belirtir.

### Alanların Dikdörtgen Olma Zorunluluğu
Bir isimlendirilmiş alanın hücreleri tek bir dikdörtgen oluşturmalıdır.

Geçerli kullanım:
```
    grid-template-areas:
        "header header"
        "main main";
```
Geçersiz kullanım:
```
    grid-template-areas:
        "header header"
        "header main";
```
Çünkü header alanı L şeklinde tanımlanmıştır. Bu tür bir tanım geçersizdir ve ilgili declaration uygulanmaz.

### Responsive Alan Değişimi
Media query ile sayfa iskeletini değiştirebiliriz.
```
    @media (max-width: 768px) {
        .layout {
            grid-template-columns: 1fr;

            grid-template-areas:
                "header"
                "main"
                "sidebar"
                "footer";
        }
    }
```

Böylece mobilde içerikler tek sütun halinde gösterilebilir.

**Erişilebilirlik notu:** grid-template-areas, elementlerin görsel konumunu değiştirebilir ancak HTML kaynak sırasını değiştirmez. Klavye gezinme ve anlamlı okuma sırası için DOM sırası doğru tasarlanmalıdır.

## Implicit Grid ve Otomatik Yerleşim
Grid'de bütün satır ve sütunları önceden tanımlamak zorunda değiliz. Tarayıcı gerektiğinde implicit track'ler oluşturabilir.

### 1. grid-auto-rows
Otomatik oluşturulan satırların boyutunu belirler.
```
    .container {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-auto-rows: 150px;
    }
```

Bu örnekte otomatik oluşturulan satırlar 150px yüksekliğinde olur.

İçeriğe göre büyüyebilen satırlar için:
```
    .container {
        grid-auto-rows: minmax(120px, auto);
    }
```
kullanılabilir.

Böylece otomatik satırlar en az 120px olacak şekilde boyutlandırılır ve gerekli koşullarda içerikle büyüyebilir.

### 2. grid-auto-columns
Otomatik oluşturulan sütunların boyutunu belirler.
```
    .container {
        display:grid;
        grid-auto-columns: 200px;
    }
```

Örneğin sütun yönünde otomatik yerleşim kullanıyorsak:
```
    .container {
        display:grid;
        grid-auto-flow:column;
        grid-auto-columns: 200px;
    }
```
Yeni sütunlar otomatik olarak oluşturulabilir.

### 3. grid-auto-flow
Grid item'ların otomatik yerleşim yönünü belirler. Yaygın değerler:
- grid-auto-flow: row;
- grid-auto-flow: column;
- grid-auto-flow: row dense;
- grid-auto-flow: column dense;

### - row -
Varsayılan değerdir.
```
    .container {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-auto-flow: row;
    }
```
Otomatik yerleşim satır yönünde ilerler.
```
    ┌─────┬─────┬─────┐
    │  1  │  2  │  3  │
    ├─────┼─────┼─────┤
    │  4  │  5  │  6  │
    └─────┴─────┴─────┘
```
Gerektiğinde yeni implicit sütunlar oluşturulabilir.

### - dense - 
```
    .container {
        grid-auto-flow: row dense;
    }
```
dense, otomatik yerleşimde daha önce boş kalmış uygun hücreleri sonrki item'larla doldurmaya çalışır.

Örneğin farklı sütun genişlikleri kaplayan kartlarda boşlukları azaltabilir. Ancak önemli bir sonucu vardır: `Görsel sıralama, HTML kaynak sırasından farklı hale gelebilir.`

Bu durum özellikle klavye ile gezinme ve ekran okuyucu deneyimi açısından sorun oluşturulabilir. Bu nedenle dense, görsel sıranın anlam taşımadığı dekoratif galeri düzenlerinde daha uygun olabilir.

## Grid'de Hizalama
Grid'de hizalama özellikleri üç farklı düzeyde değerlendirilir:
- 1. Grid item'ların kendi alanları içerisindekik hizalaması
- 2. Tek bir item'ın bireysel hizalaması
- 3. Grid track'lerinin container içerisindeki hizalaması

Grid'de yatay ve dikey eksenler için `justify-*` ve `align-*` özellikleri kullanılır.

Varsayılan yatay yazı yönünde:
- justify-* inline ekseni, genellikle yatay ekseni kontrol eder.
- align-* block ekseni, genellikle dikey ekseni kontrol eder.

Yazı modu değiştirğinde bu eksenlerin fizikseş yönler, de değişebilir.

### 1. justify-items
Grid item'ların kendi grid alanları içerisindeki inline eksen hizalamasını belirler.
```
    .container {
        display: grid;
        justify-items: center;
    }
```
Item'lar kendi alanlarında yatay olarak ortalanır (normal yatay yazı düzeninde).

### 2. align-items
Grid item'ların kendi grid alanları içerisindeki block eksen hizalamasını belirler.
```
    .container {
        display: grid;
        align-items: center;
    }
```
Normal yatay yazı düzeninde dikey hizalamayı etkiler.

### 3. place-items

align-items ve justify-items özelliklerini birleştirir.

.container {
    display: grid;
    place-items: center;
}

Açılımı:

.container {
    align-items: center;
    justify-items: center;
}

Bu sayede item'lar kendi Grid alanları içerisinde iki eksende ortalanır.

### 4. justify-self
Tek bir Grid item'ın inline eksen hizalamasını belirler.
```
    .item {
        justify-self: end;
    }
```

### 5.align-self
Tek bir Grid item'ın block eksen hizalamasını belirler.
```
    .item {
        align-self: center;
    }
```

### 6. place-self
Tek bir item için align-self ve justify-self özelliklerini birleştirir.
```
    .item {
        place-self: center;
    }
```

Açılımı:
```
    .item {
        align-self: center;
        justify-self:center;
    }
```

### 7. justify-content
Grid track'lerinin tamamını inline eksen üzerinde hizalar veya uygub bol alanı dağıtır.
```
    .container {
        display: grid;
        grid-template-columns: 100px 100px;
        justify-content: center;
    }
```
Kapsayıcı sütunlardan daha genişse, sütun grubu ortalanabilir.

### 8. align-content
Grid track'lerinin tamamını block eksen üzerinde hizalar veya uygun boş alanı dağıtır.
```
    .container {
        display: grid;
        grid-template-rows: 100px 100px;
        height: 400px;

        align-content: center;
    }
```
Satır grubu dikey olarak ortalanabilir.

### 9. place-content
align-content ve justify-content özelliklerini birleştirir.
```
    .container {
        place-content: center;
    }
```

### Hizalama Özellikleri Tablosu
|Property           |Uygulandığı yer       |Etkilediği şey         |Eksen          |
|-------------------|----------------------|-----------------------|---------------|
|justify-items      |Container             |Item'ların alan içi hizalaması|Inline  |
|align-items        |Container             |Item'ların alan içi hizalaması|Block   |
|place-items        |Container             |İki eksende item hizalaması   |Her ikisi|
|justify-self       |Item                  |Tek item'ın hizalaması  |Block         |
|place-self         |Item                  |Tek ıtem'ın iki eksende hizalaması|Her ikisi|
|justify-content    |Container             |Grid track grubunun dağılımı  |Inline   |
|align-content      |Container             |Grid track grubunun dağılımı    |Block  |
|place-content      |Container             |Grid track grubunun iki eksende dağılımı|Her ikisi|

### place-items: center ile Ortalama
```
    <div class="container">
        <div class="box">Merhaba</div>
    </div>
```
```
    .container {
        display: grid;
        place-items: center;

        min-height: 300px;
    }
```

Tek bir item için bu kullanım yatay ve dikey ortalama sağlamanın kısa yollarından biridir.

**Dikkat:** place-items: center, Grid track grubunu değil, item'ları kendi Grid alanları içerisinde ortalar. Grid'in tamamını hizalamak için place-content kullanılabilir.

## Responsive Grid — auto-fill ve auto-fit
Responsive Grid oluştururken her ekran genişliği için ayrı sütun sayısı yazmak zorunda değiliz.

Bunun için **repeat(), auto-fit, auto-fill ve minmax()** birlikte kullanılabilir.

### 1. auto-fit
En sık kullanılan responsive Grid desenlerinden biri:
```
    .container {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 20px;
    }
```
Bu kullanımda tarayıcı, kapsayıcıya sığabilecek sayıda en az 250px temel genişlikli sütun oluşturur.

Boş kalan tekrar sütunları daraltılarak mevcut item'ların kullanılabilir alanı paylaşması sağlanabilir.

Örneğin:
```
    Geniş ekran:

    ┌──────────┬──────────┬──────────┐
    │  Kart 1  │  Kart 2  │  Kart 3  │
    └──────────┴──────────┴──────────┘


    Orta ekran:

    ┌──────────────┬──────────────┐
    │    Kart 1    │    Kart 2    │
    ├──────────────┴──────────────┤
    │           Kart 3            │
    └─────────────────────────────┘


    Dar ekran:

    ┌──────────────────────┐
    │        Kart 1        │
    ├──────────────────────┤
    │        Kart 2        │
    ├──────────────────────┤
    │        Kart 3        │
    └──────────────────────┘
```
Bu şema sütun sayısının değişimini temsil eder. Gerçekte ikinci satırdaki tek kart, auto-fit kullanımında mevcut sütunlardan birine yerleşir; otomatik olarak iki sütunu birden kaplamaz.