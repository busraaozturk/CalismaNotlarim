# HTML'de Başlık Hiyerarşisi

HTML'de `<h1>` ile `<h6>` arasındaki etiketler, sayfadaki başlıkları ve içerik hiyerarşisini oluşturmak için kullanılır.

```
    <h1>Ana Başlık</h1>
    <h2>Alt Başlık</h2>
    <h3>Daha Alt Başlık</h3>
```

Buradaki `h` harfi **heading (başlık)** anlamına gelir. 1 ile 6 arasındaki değerler ise başlığın hiyerarşi seviyesini belirtir.
```
    h1 → En üst seviye
    h2 → İkinci seviye
    h3 → Üçüncü seviye
    ...
    h6 → Altıncı seviye
```

## Başlıklar Sadece Yazı Boyutu Değildir

Tarayıcılar varsayılan olarak `<h1>` elementini büyük, `<h6>` elementini ise daha küçük gösterir.

Ancak başlık etiketlerinin kullanım amacı yazının büyüklüğünü belirlemek değildir.

Örneğin yalnızca daha küçük görünsün diye: `<h4>Ürünlerimiz</h4>` kullanmak doğru bir yaklaşım değildir.

Başlığın seviyesine sayfadaki konumuna ve içerik ilişkisine göre karar verilmelidir. Görünümü ise CSS ile değiştirebiliriz.
```
    h2 {
        font-size: 24px;
    }
```
Yani: `HTML başlığın anlamını ve seviyesini, CSS ise nasıl görüneceğini belirler.`

## `<h1>` Nasıl Kullanılır?
`<h1>` sayfanın ana başlığını temsil eder.

Örneğin bir ürün detay sayfasında; `<h1>Akıllı Saat</h1>`

Bir blog sayfasında; `<h1>JavaScript Nedir?</h1>`

Bir kategori sayfasında; `<h1>Kadın Ayakkabı</h1>` kullanılabilir.

Pratikte bir sayfanın tek ve açık ana `<h1>` başlığına sahip olması, içerik yapısını anlaşılır tutmak açısından iyi bir yaklaşımdır.

## `h1 → h2 → h3` İlişkisi
Başlıkları bir kitabın içindekiler bölümü gibi düşünebiliriz.
```
    <h1>Frontend Geliştirme</h1>

    <h2>HTML</h2>

    <h3>Semantic HTML</h3>
    <h3>HTML Formları</h3>

    <h2>CSS</h2>

    <h3>Flexbox</h3>
    <h3>Grid</h3>
```

Buradaki yapı şöyledir:
```
    Frontend Geliştirme
    │
    ├── HTML
    │   ├── Semantic HTML
    │   └── HTML Formları
    │
    └── CSS
        ├── Flexbox
        └── Grid
```

HTML ve CSS, ana konunun alt başlıklarıdır. Semantic HTML ise HTML konusunun altında bulunan daha alt seviyedeki bir başlıktır. Bu nedenle başlık seviyelerini mümkün olduğunca mantıksal sırayla kullanmak gerekir.

## Semantic HTML ile İlişkisi
Başlık hiyerarşisi, semantic HTML yapısını daha anlaşılır hale getirir.
Örneğin;
```
<main>

    <h1>Frontend Eğitimleri</h1>

    <section>
        <h2>HTML</h2>

        <article>
            <h3>Semantic HTML</h3>
            <p>...</p>
        </article>
    </section>

    <section>
        <h2>CSS</h2>

        <article>
            <h3>Flexbox</h3>
            <p>...</p>
        </article>
    </section>

</main>
```

Burada semantic elementler sayfanın bölümlerini, başlıklar ise bu bölümler arasındaki içerik hiyerarşisini oluşturur.

Bu yapı aynı zamanda ekran okuyucu kullanan kişilerin sayfadaki başlıklar arasında gezinmesini ve içeriğin organizasyonunu anlamasını kolaylaştırır.

## Yanlış ve Doğru Kullanım
Başlıkları yalnızca görünüşlerine göre seçmek:
```
    <!-- Yanlış yaklaşım -->

    <h1>Frontend Eğitimleri</h1>

    <h4>HTML</h4>

    <h2>Semantic HTML</h2>
```

Burada başlık seviyeleri arasında mantıklı bir hiyerarşi bulunmuyor.

Daha düzenli yapı aşağıdaki şekildedir.
```
    <h1>Frontend Eğitimleri</h1>

    <h2>HTML</h2>

    <h3>Semantic HTML</h3>
```

## Kısaca
HTML başlık etiketleri, `<h1>...</h1>` metni büyük veya küçük göstermek için değil, sayfadaki içerik hiyerarşisini belirtmek için kullanılır.

Temel mantık:
```
    h1 → Sayfanın ana konusu
    ↓
    h2 → Ana konunun bölümleri
    ↓
    h3 → Bölümlerin alt konuları
    ↓
    h4, h5, h6 → Gerektiğinde daha alt seviyeler
```
Başlığın görünümü CSS'in, başlığın anlamı ve hiyerarşisi ise HTML'in sorumluluğundadır.