# HTML'de Tablolar
HTML tabloları, **birbiriyle ilişkili verileri satır ve sütunlar halinde düzenli bir şekilde göstermek** için kullanılır.

Örneğin ürün ve fiyat bilgileri, ders programları, karşılaştırma verileri veya rapor sonuçları tablo yapısıyla gösterilebilir.

Basit bir tablo:
```
    <table>
        <tr>
            <th>Ürün</th>
            <th>Fiyat</th>
            <th>Stok</th>
        </tr>

        <tr>
            <td>Akıllı Saat</td>
            <td>4.500 TL</td>
            <td>12</td>
        </tr>

        <tr>
            <td>Kulaklık</td>
            <td>2.000 TL</td>
            <td>8</td>
        </tr>
    </table>
```

Buradaki temel yapı:
```
    <table> → Tablo
    │
    └── <tr> → Satır
            │
            ├── <th> → Başlık hücresi
            └── <td> → Veri hücresi
```
Şimdi bu elementleri ayrı ayrı inceleyelim.

## `<table>` Elementi
`<table>`, tablonun tamamını kapsayan ana elementtir.
```
    <table>
        ...
    </table>
```
Tabloya ait satırlar, başlıklar ve veriler bu yapı içerisinde bulunur. `<table>` tek başına görünür bir tablo oluşturmak için değildir. İçerisinde tabloyu meydana getiren diğer elementler kullanılır.

## `<tr>` Tablo Satırı
`<tr>`, **table row** yani tablo satırı anlamına gelir. Tablodaki her yatay satır bir `<tr>` ile oluşturulur.
```
    <table>

        <tr>
            ...
        </tr>

        <tr>
            ...
        </tr>

    </table>
```

Örneğin:
```
    <tr>
        <td>Akıllı Saat</td>
        <td>4.500 TL</td>
        <td>12</td>
    </tr>
```

Tek bir tablo satırını temsil eder.

## `<th>` Başlık Hücresi
`<th>`, **table header** yani tablo başlık hücresidir. Tablodaki sütun veya satırların ne anlama geldiğini belirtmek için kullanılır.
```
    <tr>
        <th>Ürün</th>
        <th>Fiyat</th>
        <th>Stok</th>
    </tr>
```

Tarayıcılar `<th>` içerisindeki metinleri varsayılan olarak genellikle kalın ve ortalanmış gösterebilir. Ancak `<th>` kullanmamızın nedeni  **metni kalın göstermek değildir.** `<th>` semantik olarak şu anlamı taşır:

`Bu hücre diğer tablo verilerini açıklayan bir başlıktır.`

Görsel tasarım gerektiğinde CSS ile değiştirilmelidir.

## `<td>` Veri Hücresi
`<td>` **table data** anlamına gelir ve tablodaki gerçek verileri temsil eder.
```
    <tr>
        <td>Akıllı Saat</td>
        <td>4.500 TL</td>
        <td>12</td>
    </tr>
```

Burada:
```
    Akıllı Saat → Ürün
    4.500 TL    → Fiyat
    12          → Stok
```

Dolayısıyla temel ayrım şu şekildedir:
```
    <th> → Başlık

    <td> → Veri
```

## `<thead>`, `<tbody>` ve `<tfoot>`
Tablolar büyüdükçe farklı bölümleri birbirinden ayırmak faydalı olur. HTML bunun için üç temel element sağlar.
```
    <thead>  → Tablo başlığı

    <tbody>  → Tablo verileri

    <tfoot>  → Tablo alt/özet bölümü
```

Örneğin:
```
<table>

    <thead>
        <tr>
            <th>Ürün</th>
            <th>Fiyat</th>
            <th>Adet</th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <td>Akıllı Saat</td>
            <td>4.500 TL</td>
            <td>1</td>
        </tr>

        <tr>
            <td>Kulaklık</td>
            <td>2.000 TL</td>
            <td>2</td>
        </tr>
    </tbody>

    <tfoot>
        <tr>
            <th>Toplam</th>
            <td>8.500 TL</td>
            <td>3</td>
        </tr>
    </tfoot>

</table>
```

Bu yapıyı şöyle düşünebiliriz:
```
    TABLE
    │
    ├── THEAD
    │     └── Başlıklar
    │
    ├── TBODY
    │     └── Asıl veriler
    │
    └── TFOOT
        └── Özet / toplam gibi bilgiler
```

Bu elementler tablonun yapısını daha anlaşılır hale getirir.

Her tabloda mutlaka üçünü birden kullanmak zorunda değiliz. Özellikle `<tfoot>`, yalnızca tablonun gerçekten bir alt bilgi veya özet bölümü varsa kullanılmalıdır.

## `<caption>` Tablo Başlığı 
`<caption>`, tablonun **ne hakkında olduğunu açıklayan başlığı** belirtir.

```
    <table>

        <caption>Ürün Stok Durumu</caption>

        <thead>
            <tr>
                <th>Ürün</th>
                <th>Fiyat</th>
                <th>Stok</th>
            </tr>
        </thead>

        <tbody>
            <tr>
                <td>Akıllı Saat</td>
                <td>4.500 TL</td>
                <td>12</td>
            </tr>
        </tbody>

    </table>
```

Burada `<caption>Ürün Stok Durumu</caption>` tablonun tamamının neyi temsil ettiğini açıklar.

`caption`, tablo içerisindeki sütun başlıklarından farklıdır.
```
    caption → Tablonun tamamını açıklar.

    th → Belirli bir satır veya sütunu açıklar.
```

## `scope` Attribute'u
`<th>` elementlerinde başlığın hangi verilerle ilişkili olduğunu daha açık belirtmek için `scope` kullanılabilir. Örneğin sütun başlıklarında:
```
    <thead>
        <tr>
            <th scope="col">Ürün</th>
            <th scope="col">Fiyat</th>
            <th scope="col">Stok</th>
        </tr>
    </thead>
``` 
`scope="col"` bu başlıkların **sütun başlığı** olduğunu belirtiir.

Örneğin: 
```
    Ürün      Fiyat       Stok
    ↓          ↓           ↓
    Saat      4.500 TL      12
    Kulaklık  2.000 TL       8
```
Satır başlıklarında ise `scope="row"` kullanılabilir:
```
    <tr>
        <th scope="row">Akıllı Saat</th>
        <td>4.500 TL</td>
        <td>12</td>
    </tr>
```

Burada **Akıllı Saat** bulunduğu satırdaki diğer verilerin başlığıdır.

Temel ayrım:
```
    scope="col" → Sütun başlığı

    scope="row" → Satır başlığı
```

Özellikle ekran okuyucuların tablo içerisindeki başlık ve veri ilişkilerini anlamasına yardımcı olduğu için erişilebilir tablolar oluştururken önemlidir.

## `colspan` Birden Fazla Sütunu Birleştirmek
Bazen bir hücrenin birden fazla sütunu kapsaması gerekebilir. Bunun için `colspan` kullanılır.

Örneğin:
```
    <table>

        <tr>
            <th colspan="3">Ürün Bilgileri</th>
        </tr>

        <tr>
            <th>Ürün</th>
            <th>Fiyat</th>
            <th>Stok</th>
        </tr>

    </table>
```

Burada `colspan="3"` hücrenin **3 sütun genişliğinde alan kaplamasını** sağlar.

Mantığı:
```
    Normal:

    | Ürün | Fiyat | Stok |


    colspan="3":

    |      Ürün Bilgileri      |
    | Ürün | Fiyat | Stok |
```

## `rowspan` Birden Fazla Satırı Birleştirmek
`rowspan` ise bir hücrenin birden fazla satırı kapsamasını sağlar. Örneğin:
```
<table>

    <tr>
        <th rowspan="2">Frontend</th>
        <td>HTML</td>
    </tr>

    <tr>
        <td>CSS</td>
    </tr>

</table>
```
Burada `rowspan="2"` Frontend hücresinin iki satırı kapsamasını sağlar.

Mantığı:
```
    |          | HTML |
    | Frontend |------|
    |          | CSS  |
```

Kısaca:
```
    colspan → Sütunları birleştirir.

    rowspan → Satırları birleştirir.
```

## Tablolar Ne Zaman Kullanılmalıdır?
Tablolar **tablosal veri** göstermek için kullanılmalıdır. Yani veriler arasında satır ve sütun ilişkisi varsa `<table>` kullanılması anlamlıdır. Örneğin:
**Ürün Karşılaştırması**
```
    Ürün           Fiyat       Stok
    --------------------------------
    Akıllı Saat    4.500 TL     12
    Kulaklık       2.000 TL      8
```
**Ders Programı**`
```
    Saat       Pazartesi      Salı
    ---------------------------------
    09:00      Matematik      Türkçe
    10:00      Fizik          Tarih
```
**Sipariş Raporu**
```
    Sipariş     Tarih          Tutar
    -----------------------------------
    #1024       20.09.2026     2.500 TL
    #1025       21.09.2026     1.200 TL
```
Bunların hepsinde veriler arasında doğal bir **satır-sütun ilişkisi** vardır.

## Tablolar Layout Oluşturmak İçin Kullanılmamalıdır
Eskiden web sayfalarının tasarımını oluşturmak için tablolar kullanılabiliyordu.

Örneğin:
```
    <!-- Sayfa tasarımı oluşturmak için kullanılmamalı -->

    <table>
        <tr>
            <td>Menü</td>
            <td>Ana İçerik</td>
            <td>Sidebar</td>
        </tr>
    </table>
```

Bu yaklaşım modern web geliştirmede doğru değildir. Çünkü `<table>` elementinin semantik anlamı tablosal veri sunmaktır. Sayfa düzenleri için CSS'in:
```
    Flexbox
    Grid
```
gibi layout sistemleri kullanılmalıdır.

Örneğin:
```
    <div class="layout">
        <main>...</main>
        <aside>...</aside>
    </div>
    .layout {
        display: grid;
        grid-template-columns: 1fr 300px;
    }
```

HTML içeriğin anlamını, CSS ise yerleşimini yönetir. Bu, daha önce Semantic HTML konusunda gördüğümüz temel prensiple aynıdır.

## Basit ve Doğru Bir Tablo Örneği 
Öğrendiklerimizi tek bir örnekte birleştirelim:
```
    <table>

        <caption>Frontend Eğitimleri</caption>

        <thead>
            <tr>
                <th scope="col">Konu</th>
                <th scope="col">Seviye</th>
                <th scope="col">Süre</th>
            </tr>
        </thead>

        <tbody>

            <tr>
                <th scope="row">HTML</th>
                <td>Başlangıç</td>
                <td>4 Saat</td>
            </tr>

            <tr>
                <th scope="row">CSS</th>
                <td>Başlangıç</td>
                <td>6 Saat</td>
            </tr>

            <tr>
                <th scope="row">JavaScript</th>
                <td>Orta</td>
                <td>12 Saat</td>
            </tr>

        </tbody>

    </table>
```

Yapıyı incelediğimizde:
```
    <table>
    │
    ├── <caption>
    │     └── Tablonun açıklaması
    │
    ├── <thead>
    │     │
    │     └── <tr>
    │          └── <th> → Sütun başlıkları
    │
    └── <tbody>
        │
        ├── <tr>
        │    ├── <th> → Satır başlığı
        │    └── <td> → Veriler
        │
        └── <tr>
            ├── <th> → Satır başlığı
            └── <td> → Veriler
```

Tablonun HTML yapısından bile veriler arasındaki ilişki anlaşılabilir.

## Sık Yapılan Hatalar
Tablolarda dikkat edilmesi gereken birkaç temel hata vardır.

**Başlık hücrelerinde gereksiz yere `<td>` kullanmak:**
```
    <!-- Daha az anlamlı -->
    <tr>
        <td>Ürün</td>
        <td>Fiyat</td>
    </tr>
```

Başlık oldukları için şu şekilde kullanılması daha doğrudur:
```
    <tr>
        <th scope="col">Ürün</th>
        <th scope="col">Fiyat</th>
    </tr>
```

**Tabloyu yalnızca görsel düzen oluşturmak için kullanmak** da semantic açıdan yanlış bir yaklaşımdır.

Ayrıca `colspan` ve `rowspan` değerlerini gereğinden fazla kullanarak tabloyu karmaşıklaştırmak, özellikle erişilebilirliği ve bakımını zorlaştırabilir. Karmaşık bir tablo gerekiyorsa başlık-veri ilişkilerinin açık kalmasına dikkat edilmelidir.

# Kısaca Özet
HTML tabloları **satır ve sütun ilişkisine sahip verileri göstermek** için kullanılır. 

Temel elementler:
| Element     | Görevi                      |
| ----------- | --------------------------- |
| `<table>`   | Tablonun tamamı             |
| `<tr>`      | Tablo satırı                |
| `<th>`      | Başlık hücresi              |
| `<td>`      | Veri hücresi                |
| `<thead>`   | Başlık bölümü               |
| `<tbody>`   | Ana veri bölümü             |
| `<tfoot>`   | Alt bilgi/özet bölümü       |
| `<caption>` | Tablonun açıklayıcı başlığı |

Ayrıca:
```
    scope="col" → Sütun başlığını belirtir.
    scope="row" → Satır başlığını belirtir.

    colspan → Birden fazla sütunu kapsar.
    rowspan → Birden fazla satırı kapsar.
```

Tablolar konusunda hatırlanması gereken en önemli kural ise şudur: **`<table>` bir tasarım aracı değil, tablosal veriyi anlamlı bir şekilde ifade eden HTML yapısıdır.**
