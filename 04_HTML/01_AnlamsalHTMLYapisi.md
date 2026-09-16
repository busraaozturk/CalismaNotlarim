# Anlamsal HTML Yapısı Nedir?
HTML, bir web sayfasında yalnızca içerikleri ekrana yerleştirmek için kullanılmaz. Aynı zamanda bu içeriklerin **ne olduğunu, hangi görevi üstlendiğini ve birbirleriyle nasıl ilişkilendiğini** tanımlar.

Bu noktada **Anlamsal HTML (Semantic HTML)** kavramı ortaya çıkar.

**Anlamsal HTML**; bir içeriği oluştururken, o içeriğin görevini ve anlamını en doğru şekilde ifade eden HTML elementinin kullanılmasıdır.

Örneğin bir web sayfasının navigasyon alanını şu şekilde oluşturabiliriz:
```
    <div class="navigation">
        <a href="/">Ana Sayfa</a>
        <a href="/about">Hakkında</a>
    </div>
```

Bu kod çalışır. Ancak `<div>` elementinin kendisi bize içerisindeki içeriğin ne olduğunu söylemez. Bunun bir navigasyon olduğunu yalnızca `navigation` sınıfından anlayabiliriz.

Aynı alanı anlamsal HTML kullanarak şöyle oluşturabiliriz:
```
    <nav>
        <a href="/">Ana Sayfa</a>
        <a href="/about">Hakkında</a>
    </nav>
```

Burada `<nav>` elementi doğrudan; `Bu bölüm kullanıcıların sayfa içerisinde veya sayfalar arasında gezinmesini sağlayan bir navigason alanıdır.` anlamını taşır.

Dolayısıyla semantic HTML'in temel amacı **daha fazla HTML etiketi kullanmak değil, doğru içeriği doğru HTML elementiyle ifade etmektir.**

## Semantic ve Non-Semantic Elementler
HTML elementlerini taşıdıkları anlam açısından iki grupta değerlendirebiliriz.

### Semantic Elementler
Semantic elementler, içerisinde bulunan içeriğin görevini kendi isimleriyle ifade eder.

Örneğin:
```
    <header></header>
    <nav></nav>
    <main></main>
    <section></section>
    <article></article>
    <aside></aside>
    <footer></footer>
```
Bu elementleri gördüğümüzde genel olarak hangi amaçla kullandıklarını anlayabiliriz.

Örneğin; `<nav></nav>` bir navigasyon alanını ifade eder.

### Non-Semantic Elementler
Non-semantic elementler ise içerisindeki içeriğin ne anlama geldiğini belirtmez.

En yaygın örnekleri:
```
    <div></div>
    <span></span>
```

Örneğin:
```<div class="products"> ... </div>```

Buradaki `<div>` bize içeriğin ürünlerden oluşturğunu söylemez. Bunu ancak class isminden anlayabiliriz.

Bu durum `<div>` veya `<span>` kullanımının yanlış oldupu anlamına gelmez.

Bu elementler özellikle gruplama, CSS düzeni oluşturma veya Javascript işlemleri için genel amaçlı kapsayıcı gerektiğinde oldukça kullanışlıdır.

Temel yaklaşım şu olmalıdır:
```
    İçeriğin anlamını karşılayan uygun bir HTML elementi varsa onu kullan; özel bir anlam taşımayan yapısal bir kapsayıcı gerekiyorsa `<div>` veya `<span>`kullan.
```

## En Sık Kullanılan Anlamsal HTML Etiketleri
| Etiket         | Anlamı                                          |
| -------------- | ----------------------------------------------- |
| `<header>`     | Sayfanın veya bir bölümün giriş/üst alanı       |
| `<nav>`        | Navigasyon ve menü bağlantıları                 |
| `<main>`       | Sayfanın ana içeriği                            |
| `<section>`    | Belirli bir konuya ait içerik bölümü            |
| `<article>`    | Tek başına anlam ifade eden bağımsız içerik     |
| `<aside>`      | Ana içeriği destekleyen veya ikincil içerik     |
| `<footer>`     | Sayfanın veya bölümün alt alanı                 |
| `<figure>`     | Görsel, grafik, kod örneği gibi bağımsız içerik |
| `<figcaption>` | `<figure>` içerisindeki içeriğin açıklaması     |
| `<time>`       | Tarih veya zaman bilgisi                        |

## Temel Anlamsal HTML Elementleri
### <header>
Bir web sayfasının veya belirli bir içerik bölümünün **giriş alanını** temsil eder.

Genellikle içerisinde logo, başlık, navigasyon, arama veya kullanıcı işlemleri gibi öğeler bulunabilir.

```
    <header>
        <a href="/">Frontend Notes</a>

        <nav>
            <a href="/">Ana Sayfa</a>
            <a href="/articles">Yazılar</a>
            <a href="/about">Hakkında</a>
        </nav>
    </header>
```

Burada dikkat edilmesi gereken önemli nokta, <header> elementinin yalnızca web sitesinin en üst kısmı olmadığıdır. Örneğin bir makalenin de kendi header alanı olabilir:

```
    <article>

        <header>
            <h2>Semantic HTML Nedir?</h2>
            <p>Yazar: Ad Soyad</p>
        </header>

        <p>
            Semantic HTML, web içeriğinin anlamına uygun
            HTML elementleri kullanılarak oluşturulmasıdır.
        </p>

    </article>
```

Buradaki <header> tüm web sitesinin değil, **article içerisindeki içeriğin giriş bölümüdür.**

### <nav>
`<nav>`, kullanıcıların sayfalar veya sayfanın önemli bölümleri arasında hareket etmesini sağlayan **navigasyon bağlantılarını** temsil eder.

```
    <nav>
        <a href="/">Ana Sayfa</a>
        <a href="/projects">Projeler</a>
        <a href="/about">Hakkımda</a>
        <a href="/contact">İletişim</a>
    </nav>
```

Ancak sayfada bulunan her bağlantı `<nav>` içerisine alınmamalıdır.

Örneğin:
```
    <p>
        Daha fazla bilgi için
        <a href="/html">HTML Temelleri</a>
        yazısını inceleyebilirsiniz.
    </p>
```

Buradaki bağlantı normal bir içerik bağlantısıdır. Ayrı bir navigasyon bölgesi oluşturmadığı için `<nav>` kullanılması gerekmez.

`<nav>` daha çok ana menü, bölüm menüsü, breadcrumb veya önemli navigasyon gruplarında kullanılır.

### <main>
<main>, sayfanın asıl içeriğini temsil eder.

```
    <body>

        <header>
            ...
        </header>

        <main>

            <h1>Frontend Eğitim Notları</h1>

            <p>
                HTML, CSS ve JavaScript üzerine hazırlanmış
                eğitim içerikleri.
            </p>

        </main>

        <footer>
            ...
        </footer>

    </body>
```

Header, navigasyon ve footer gibi alanlar farklı sayfalarda tekrar edebilir. `<main>` içerisindeki içerik ise temel olarak o sayfaya özgü ana içeriği ifade eder.

Bir belgede genel olarak tek bir görünür `<main>` alanı bulunmalıdır.

### `<section>`, `<article>`, `<div>` Arasındaki Fark
Semantic HTML öğrenirken en fazla karıştırılan konulardan biri bu üç elementin ne zaman kullanılacağıdır. Üçü de içerikleri gruplamak için kullanılabilir ancak **amaçları aynı değildir.**

### <section>
Aynı konu veya amaç etrafında bir araya gelen içeriklerden oluşan **anlamlı bir bölümü** temsil eder. Örneğin bir portföy sayfasını düşünelim:
```
    <main>

        <section>
            <h2>Hakkımda</h2>
            ...
        </section>

        <section>
            <h2>Projelerim</h2>
            ...
        </section>

        <section>
            <h2>İletişim</h2>
            ...
        </section>

    </main>
```

Buradaki her <section> farklı bir konuyu temsil eder.

`section` kullanıp kullanmamaya karar cerirken şu soruyu sorabiliriz:
```
    Bu içerik sayfa içerisinde kendi konusu olan, isimlendirilebilir bit bölüm mü?
```

Cevap evetse `<section>` kullanılması uygun olabilir.

Bu nedenle section'ların genellikle bir başlığa sahit plması beklenir.
```
    <section>
        <h2>Son Projeler</h2>
    </section>
```

### <article>
Bulunduğu sayfadan bağımsız olarak da anlam ifade edebilen **bağımsız bir içerik parçasını** temsil eder.

Örneğin:
- blog yazıları,
- haberler,
- forum gönderileri,
- kullanıcı yorumları,
- bağımsız içerik kartları
article olarak değerlendirilebilir.

Bir blog sayfasını düşünelin:
```
    <section>

        <h2>Son Yazılar</h2>

        <article>
            <h3>Semantic HTML Nedir?</h3>
            <p>
                Semantic HTML kullanımının temel prensipleri...
            </p>
        </article>

        <article>
            <h3>CSS Flexbox Nedir?</h3>
            <p>
                Flexbox ile modern sayfa düzenleri oluşturmak...
            </p>
        </article>

    </section>
```

Burada aşağıdaki şekilde bir ilişki vardır:
```
    section
    └── Son Yazılar bölümü

    article
    ├── Semantic HTML yazısı
    └── CSS Flexbox yazısı
```

Article kullanırken şu soru oldukça yardımcıdır:
```
    Bu içeriği bulunduğu sayfadan çıkarııp başka bir yerde tek başına yayınlasam hala anlamlı olur mu?
```

Cevap evetse <article> kullanılması uygun olabilir.

### <div>
Herhangi bir özel anlam taşımayann genel amaçlı bir kapsayıcıdır.

Özellikle:
-CSS layout oluşturmak,
-Flexbox/Grid container oluşturmak,
-elementleri gruplamak,
-stil uygulamak,
-JavaScript ile belirli bir alanı yönetmek
gibi durumlarda kullanılabilir.

Örneğin:
```
    <section>

        <h2>Projeler</h2>

        <div class="project-grid">
            ...
        </div>

    </section>
```
Buradaki `project-grid` yeni bir içerik bölümü değildir.

Sadece projelerin ekranda belirli bir düzende gösterilmesini sağlayan **yapısal bir kapsayıcıdır.**

Dolayısıyla <div> kullanımı burada doğrudur.

### Aralarındaki Farkı Özetlersek
| Element     | Ne zaman kullanılır?                           |
| ----------- | ---------------------------------------------- |
| `<section>` | Belirli bir konuya ait anlamlı bir bölüm varsa |
| `<article>` | İçerik bağımsız olarak anlam taşıyabiliyorsa   |
| `<div>`     | Sadece gruplama, stil veya layout amacı varsa  |

### <aside>
Ana içerikle ilişkili fakat ana içeriğin temel akışından ayrı değerlendirilebilecek tamamlayıcı veya ikincil içerikleri temsil eder.

Örneğin:
```
    <main>

        <article>

            <h1>HTML Öğrenmeye Nereden Başlanmalı?</h1>

            <p>
                HTML öğrenirken öncelikle belge yapısını
                anlamak gerekir...
            </p>

        </article>

        <aside>

            <h2>İlgili Konular</h2>

            <a href="/css">CSS Temelleri</a>
            <a href="/javascript">JavaScript Temelleri</a>

        </aside>

    </main>
```

Burada önemli bir ayrım vardır.

`<aside>` : “Sayfanın sağ tarafındaki alan” demek değildir.

Semantic HTML elementleri görsel konuma göre değil, içeriğin anlamına göre seçilir.

CSS ile aside sağda, solda veya başka bir yerde gösterilebilir.

### <footer>
Bir sayfanın veya belirli bir içerik bölümünün alt bilgi alanını temsil eder.

Örneğin:
```
    <footer>

        <p>© 2026 Frontend Notes</p>

        <nav>
            <a href="/privacy">Gizlilik</a>
            <a href="/contact">İletişim</a>
        </nav>

    </footer>
```

Footer içerisinde telif bilgileri, iletişim bağlantıları, yasal bağlantılar veya yardımcı navigasyonlar bulunabilir.

Tıpkı `<header>` gibi `<footer>` da yalnızca tüm web sitesine ait olmak zorunda değildir.

Bir article'ın kendi footer'ı bulunabilir:
```
    <article>

        <h2>Semantic HTML</h2>

        <p>
            ...
        </p>

        <footer>
            <p>Yayınlanma tarihi: 15 Eylül 2026</p>
        </footer>

    </article>
```

## Diğer Yararlı Semantic Elementler
Semantic HTML yalnızca sayfa bölümlerini oluşturan elenemntlerden ibaret değildir. İçeriğin türünü daha doğru ifade etmek için kullanabileceğimiz başka semantic elementler de vardır.

**<figure> ve <figcaption>** : Görsel, grafik, diyagram veya benzeri bağımsız içerikleri açıklamasıyla birlikte gruplamak için kullanılabilir.

```
    <figure>

        <img
            src="semantic-html.png"
            alt="Semantic HTML sayfa yapısı"
        >

        <figcaption>
            Semantic HTML ile oluşturulmuş örnek sayfa yapısı.
        </figcaption>

    </figure>
```

Burada `<figure>` içeriği, `<figcaption>` ise bu içeriğe ait açıklamayı temsil eder.

**<time>** : Tarih veya zaman bilgisini semantik olarak belirtmek için kullanılabilir.
```
    <time datetime="2026-09-15">
        15 Eylül 2026
    </time>
```

Kullanıcının gördüğü tarih ile makinenin okuyabileceği standart tarih bilgisi birlikte sunulabilir.

## Semantic HTML Görsel Tasarımla İlgili Değildir
Semantic HTML öğrenirken yapılabilecek en önemli hatalardan biri, HTML elementlerini **ekrandaki konumlarına veya görünümlerine göre seçmektir.**

Örneğin:
```
    **<header>** “Ekranın üstünde bulunan alan” anlamına gelmez.
    **<aside>** “Ekranın sağında bulunan alan” anlamına gelmez.
```

Semantic HTML elementleri içeriğin görevini belirtir. Genel olarak:
- **HTML → İçerik ve yapı**
- **CSS → Görünüm ve yerleşim**
- **JavaScript → Davranış ve etkileşim**

ayrımını düşünmek faydalıdır.

Örneğin <nav> HTML açısından navigasyondur. Bunun yatay mı, dikey mi, mobil menü mü veya açılır menü mü olacağı CSS ve gerektiğinde JavaScript ile belirlenebilir.

## Gerçek Bir Sayfa Üzerinden Semantic HTML
Bir e-ticaret sitesinin ürün detay sayfasını ele alalım. Sayfanın genel HTML yapısı şöyle olabilir:

```
    <body>

        <header>

            <nav>
                <!-- Ana navigasyon -->
            </nav>

        </header>

        <main>

            <article>

                <header>
                    <h1>Akıllı Saat</h1>
                    <p>Ürün kodu: SW-001</p>
                </header>

                <section>
                    <h2>Ürün Görselleri</h2>
                    ...
                </section>

                <section>
                    <h2>Ürün Özellikleri</h2>
                    ...
                </section>

                <section>
                    <h2>Ürün Açıklaması</h2>
                    ...
                </section>

            </article>

            <aside>

                <h2>Benzer Ürünler</h2>
                ...

            </aside>

        </main>

        <footer>
            ...
        </footer>

    </body>
```

Kodun içerisindeki gerçek içerikleri çıkardığımızda bile sayfanın yapısı anlaşılabilir:
```
    Sayfa
    │
    ├── Header
    │   └── Navigation
    │
    ├── Main
    │   │
    │   ├── Article
    │   │   ├── Header
    │   │   ├── Ürün Görselleri
    │   │   ├── Ürün Özellikleri
    │   │   └── Ürün Açıklaması
    │   │
    │   └── Aside
    │       └── Benzer Ürünler
    │
    └── Footer
```

İyi oluşturulmuş bir HTML yapısının önemli özelliklerinden biri budur:

`Sayfanın görsel tasarımını görmeden bile içeriğin hiyerarşisini ve bölümler arasındaki ilişkiyi anlayabilmek.`

## Anlamsal HTML Neden Önemlidir?
Semantic HTML yalnızca kodun daha düzenli görünmesi için kullanılan bir yöntem değildir. Doğru kullanıldığında web sayfasının birçok yönüne katkı sağlar.

**- Kodun Okunabilirliğini Artırır**

HTML'in kendisi yapıyı açıklamaktadır. Bu durum özellikle ekip çalışmakarında ve uzun süre geliştirilen projelerde kodun anlaşılmasını kolaylaştırır.

**- Erişilebilirliği Destekler**
Ekran okuyucular ve diğer yardımcı teknolojiler semantic elementlerden yararlanarak sayfanın yapısını daha iyi yorumlayabilir.

Örneğin <nav> bir navigasyon bölgesini, <main> ise sayfanın temel içeriğini belirtir.

Bu nedenle semantic HTML, erişilebilir web uygulamaları geliştirmenin temel parçalarından biridir.

**- Arama Motorlarının İçeriği Anlamasına Yardımcı Olur**
Arama motorları bir sayfayı incelerken yalnızca ekranda nasıl göründüğüne bakmaz; HTML yapısını da değerlendirir.

Semantic HTML, içeriğin yapısının ve bölümler arasındaki ilişkinin daha açık ifade edilmesine yardımcı olur.

Ancak burada önemli bir ayrım vardır:
```
    Semantic HTML tek başına SEO çalışması değildir ve yüksek sıralama garantisi vermez. Doğru yapılandırılmış bir web sayfasının temel parçalarından biridir.
```

**- Bakım ve Geliştirme Sürecini Kolaylaştırır**
Kodun amacı açık olduğunda başka bir geliştiricinin projeye dahil olması veya aylar sonra aynı kod üzerinde tekrar çalışılması daha kolay hale gelir.

Bu nedenle semantic HTML yalnızca kullanıcı veya arama motorları için değil, **kodu geliştiren ekip için de önemlidir.**

## Element Seçerken Nasıl Düşünmeliyiz?
Semantic HTML öğrenirken bütün elementleri ezberlemek yerine **doğru soruları sormayı öğrenmek** daha faydalıdır.

Bir alan oluştururken şu sırayla düşünülebilir:
```
    Bu içerik sayfanın ana içeriği mi?
            ↓
        <main>

    Bir konuya ait anlamlı bir bölüm mü?
            ↓
        <section>

    Tek başına anlam taşıyan bağımsız bir içerik mi?
            ↓
        <article>

    Ana içeriği destekleyen ikincil içerik mi?
            ↓
        <aside>

    Navigasyon bağlantılarından mı oluşuyor?
            ↓
        <nav>

    Özel bir anlamı yok, sadece layout/gruplama için mi gerekiyor?
            ↓
        <div>
```
Bu yaklaşım semantic HTML'in temel mantığını özetler.

## Yaygın Yapılan Hatalar
- Her yerde `<div>` kullanmak.
- Her kapsayıcıyı `<section>` yapmak
    - Semantic HTML kullanmak, <div> elementlerini tamamen kaldırıp her şeyi <section> yapmak anlamına gelmez.
    - Örneğin `<section class="flex-container">` yalnızca Flexbox uygulamak amacıyla kullanılıyorsa semantic açıdan gereksiz olabilir. Bunun yerine `<div class="flex-container">` daha doğru olabilir.
    - `section` kullanmak için içeriğin anlamlı bir bölüm oluşturması gerekir.
- Elementleri görünüşüne göre seçmek
    - Bir alan sağ tarafta diye `<aside>`, üst tarafta diye `<header>` kullanılmaz.
    - Önce `Bu içerik neyi temsil ediyor?` sorusu sorulmalıdır. Ardından uygun HTML elementi seçilmelidir.
    