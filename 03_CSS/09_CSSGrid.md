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
 