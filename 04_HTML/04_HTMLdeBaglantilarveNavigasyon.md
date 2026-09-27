# HTML'de Bağlantılar ve Navigasyon
Web sayfalarının en temel özelliklerinden biri, kullanıcıların **sayfalar ve içerikler arasında geçiş yapabilmesidir.** HTML'de bağlantı oluşturmak için `<a>` etiketi kullanılır. `a` **anchor** kelimesinden gelir.

En temel kullanımı şöyledir: `<a href="https://example.com">Siteyi Ziyaret Et</a>`

Burada:
- `<a>` → bağlantıyı oluşturur.
- `href` → bağlantının gideceği adresi belirtir.
- `Siteyi Ziyaret Et` → kullanıcının gördüğü ve tıklayabildiği bağlantı metnidir.

## `href` Nedir?
`href`, bağlantının hedefini belirleyen attribute'tur.
```
    <a href="/about">Hakkımızda</a>
```

Kullanıcı Hakkımızda bağlantısına tıkladığında `/about` adresine yönlendirilir.

`href` yalnızca başka web sitelerine gitmek için kullanılmaz. Farklı sayfalara, aynı sayfanın belirli bir bölümüne, telefon numarasına veya e-posta adresine bağlantı vermek için de kullanılabilir.

## Site İçi ve Site Dışı Bağlantılar
### Site İçi Bağlantılar
Aynı web sitesi içerisindeki başka bir sayfaya yönlendirme yapar. Bunlara **internal link** yani **iç bağlantı** denir.
```
    <a href="/about">Hakkımızda</a>

    <a href="/contact">İletişim</a>

    <a href="/products">Ürünler</a>
```

### Site Dışı Bağlantılar
Kullanıcıyı farklı bir web sitesine yönlendirir. Bunlara ise **external link** yani **dış bağlantı** denir.
```
    <a href="https://example.com">
        Example
    </a>
```

## Yeni Sekmede Bağlantı Açmak (target Attribute'u)
`target`, bir bağlantının hangi tarayıcı bağlamında açılacağını belirlemek için kullanılır. 

Temel kullanımı:
```
    <a href="/about" target="_blank">
        Hakkımızda
    </a>
```

`target`, için kullanılabilecek temel değerler şunlardır:
| Değer     | Görevi                                                           |
| --------- | ---------------------------------------------------------------- |
| `_self`   | Bağlantıyı mevcut sekmede/bağlamda açar. Varsayılan davranıştır. |
| `_blank`  | Bağlantıyı yeni bir sekme veya pencerede açar.                   |
| `_parent` | İç içe tarama bağlamlarında bağlantıyı üst bağlamda açar.        |
| `_top`    | Bağlantıyı en üst tarama bağlamında açar.                        |

### `target="_self"`
Bağlantıyı mevcut sayfanın bulunduğu bağlamda açar.
```
    <a href="/products" target="_self">
        Ürünler
    </a>
```

Bu zaten `<a>` elementinin varsayılan davranışı olduğu için genellikle ayrıca yazmaya gerek yoktur:
```
    <a href="/products">
        Ürünler
    </a>
```

İki kullanımda normal durumda aynı sonucu verir.

### `target="_blank"`
Bağlantının yeni bir sekmede veya tarayıcının danranışına bağlı olarak yeni bir pencerede açılmasını sağlar.
```
    <a
        href="https://example.com"
        target="_blank"
        rel="noopener noreferrer"
    >
        Example
    </a>
```
Özellikle kullanıcı mevcut sayfayı kaybetmeden harici bir kaynağı görüntüleyecekse kullanılabilir. Burada `target="_blank"` bağlantının nerede açılacağını belirlerken, `rel` bağlantı verilen kaynak ile mevcut sayfa arasındaki ilişki hakkında bilgi verir. 

Ancak her bağlantının `_blank` ile açılması önerilmez. Yeni sekme açmak kullanıcı deneyimini etkilediği için **gerçekten gerekli olduğunda** tercih edilmelidir.

**rel="noopener"**
Yeni açılan sayfanın, bağlantıyı açan sayfanın **window.opener** nesnesine erişmesini engellemeye yönelik bir güvenlik önlemidir.
```
    <a
        href="https://example.com"
        target="_blank"
        rel="noopener"
    >
        Example
    </a>
```
Modern tarayıcılarda `target="_blank"` kullanılan bağlantılar genellikle zaten `noopener` davranışıyla ele alınır. Yine de bu ifadeyle amaç kod içerisinde açıkça belirtilebilir.

**rel="noreferrer"**
Yeni sayfaya geçilirken tarayıcının HTTP `Referer` başlığı üzerinden **kaynak sayfanın adresini göndermemesini** ister.
```
<a
    href="https://example.com"
    target="_blank"
    rel="noreferrer"
>
    Example
</a>
```
Ayrıca `noreferrer`, `noopener` benzeri davranışı da sağlar.
Bu nedenle sıkça şu kullanımla karşılaşabiliriz.
```
<a
    href="https://example.com"
    target="_blank"
    rel="noopener noreferrer"
>
    Harici Siteyi Aç
</a>
```

Burada kavramları birbirinden ayırmak önemlidir:
```
    target="_blank"
        ↓
    Bağlantı nerede açılsın?

    rel="noopener"
        ↓
    Yeni sayfanın açan sayfaya erişimi nasıl olsun?

    rel="noreferrer"
        ↓
    Kaynak sayfa bilgisi gönderilsin mi?
```
**Not:** `rel="noopener noreferrer"` ifadesini `target="_blank"` kullanımının zorunlu bir parçası gibi ezberlemek yerine, her iki değerin ne yaptığını bilmek daha doğrudur. Özellikle `noreferrer`, yönlendirme/referral bilgisinin aktarılmasını etkileyebileceği için ihtiyaç doğrultusunda kullanılmalıdır.

### `target="_parent"`
Bağlantıyı mevcut bağlamın bir **üst tarama bağlamında** açar.

Bu özellik özellikle `<frame>` gibi iç içe tarama bağlamlarında anlam kazanır.

Örneğin:
```
    <iframe src="content.html"></iframe>
```

`content.html` içerisinde:
```
    <a href="/about" target="_parent">
        Hakkımızda
    </a>
```
bulunuyorsa bağlantı iframe'in kendi içerisinde açılmak yerine **iframe'i barındıran üst bağlamı** hedefler.

Sayfada böyle bir üst bağlam yoksa davranışı `_self` ile aynı hale gelir.

### `target="top"`
`_top`, bağlantıyı en üst seviyedeki tarama bağlamında açar.

Özellikle iç içe iframe yapıları düşünüldüğünde `_parent` ile arasındaki fark daha net anlaşılır:
```
    Ana Sayfa
    │
    └── iframe
        │
        └── iframe
                │
                └── bağlantı
```

En içteki bağlantı için `_parent` kullanılırsa **bir üst seviyeye** çıkılır.
```
    <a href="/about" target="_parent">
        Hakkımızda
    </a>
```

Eğer `_top` kullanılırsa **en üst tarama bağlamı** hedeflenir.
```
    <a href="/about" target="_top">
        Hakkımızda
    </a>
```

Kısaca:
```
    _self    → Bulunduğum bağlam
    _parent  → Bir üst bağlam
    _top     → En üst bağlam
    _blank   → Yeni bağlam
```

### Hangilerini Daha Çok Kullanırız?
Günlük frontend geliştirmede en sık karşılaşacağımız değerler aşağıdaki gibi olacaktır.
```
target="_self"
target="_blank"
```

`_parent` ve `_top` ise daha çok iframe veya iç içe tarama bağlamlarının bulunduğu özel durumlarda karşımıza çıkar.
Dolayısıyla başlangıç seviyesinde dört değerin de ne işe yaradığını bilmek, `_self` ve `_blank` kullanımını ise daha iyi öğrenmek yeterlidir.

## Sayfa İçindeki Bir Bölüme Gitmek
`<a>` etiketi yalnızca farklı sayfalara gitmek için kullanılmaz. Aynı sayfanın belirli bir bölümüne de yönlendirme yapılabilir. 

Öncelikle hedef elemente bir `ìd` verilir:
```
    <section id="projects">
        <h2>Projeler</h2>
    </section>
```

Daha sonra bağlantının `href`değerinde bu `id` kullanılır:
`<a href="projects">Projeler</a>`

Kullanıcı bağlantıya tıklandığında tarayıcı:
```
    #projects
        ↓
    id="projects"
```
eşleşmesini bulur ve ilgili bölümr gider.

Bu yöntem özellikle uzun sayfalarda ve tek sayfalık web sitelerinde kullanışlıdır.

## E-Posta Bağlantısı
Bir e-posta adresine bağlantı vermek için `mailto:` kullanılabilir.
```
    <a href="mailto:info@example.com">
        E-posta Gönder
    </a>
```

Kullanıcı bağlantıya tıkladığında cihazında tanımlı olan uygun e-posta uygulaması açılabilir.

## Telefon Bağlantısı
Telefon numaraları içim `tel:` kullanılabilir.
```
    <a href="tel:+905551234567">
        Bizi Arayın
    </a>
```
Özellikle mobil cihazlarda kullanıcı bağlantıya dokunduğunda telefon uygulamasının açılması sağlanabilir.

## Açıklayıcı Bağlantı Metinleri Kullanmak
Bağlantı metinlerinin kullanıcıya **nereye gideceğini veya ne yapacağını anlatması** önemlidir.

Örneğin:
```
    <a href="/html">
        Buraya tıklayın
    </a>
```
yerine:
```
    <a href="/html">
        HTML eğitimini inceleyin
    </a>
```
daha açıklayıcıdır.

Çünkü kullanıcı bağlantıyı tek başına gördüğünde bile neyle ilgili olduğunu anlayabilir. Bu yaklaşım hem kullanabilirlik hem de erişilebilirlik açısından daha doğru bir yapı oluşturur.

## `<a>` ve `<button>` Arasındaki Fark
Frontend geliştirmede sık karşılaşılan konulardan biri `<a>` ve `<button>` elementlerinin birbirinin yerine kullanılmasıdır.

İkisi ekranda benzer görünebilir ancak **aynı göreve sahip değildir.**

**`<a>` kullanıcıyı bir yere götürür**
```
    <a href="/products">
        Ürünleri Gör
    </a>
```
Burada kullanıcı başka bir sayfaya yönlendirilmektedir.

**`<button>` bir işlem gerçekleştirir**
```
    <button type="button">
        Sepete Ekle
    </button>
```
Burada kullanıcı başka bir sayfaya gitmez. Bunun yerine bir işlem gerçekleştirilir.

Örneğin:
```
    Ürün detayına git       → <a>
    İletişim sayfasına git  → <a>
    Projeleri görüntüle      → <a>

    Sepete ekle              → <button>
    Modal aç                 → <button>
    Menüyü aç/kapat          → <button>
    Formu gönder             → <button>
```
Bu ayrım özellikle **semantic HTML ve erişilebilirlik** açısından önemlidir.

Bir `<a>`elementini CSS ile buton gibi gösterebiliriz:
```
    <a href="/products" class="button">
        Ürünleri Gör
    </a>
```

Görsel olarak butona benzese bile yaptığı işlem navigasyon olduğu için HTML açısından hala `<a>`kullanılması doğrudur. **Elementi görünüşüne göre değil, gerçekleştirdiği göreve göre seçmeliyiz.**

## Bağlantılar ve `<nav>` İlişkisi
Bağlantılar Semantic HTML konusunda öğrendiğimiz `<nav>`elementi ile `<a>` elementi sıklıkla kullanılır.

Örneğin:
```
<nav>
    <a href="/">Ana Sayfa</a>
    <a href="/projects">Projeler</a>
    <a href="/about">Hakkımda</a>
    <a href="/contact">İletişim</a>
</nav>
```
Burada:
```
    <nav> → navigasyon bölümünü,
    <a> → navigasyon içerisindeki bağlantıları
```
temsil eder.
Her `<a>` elementinin `<nav>` içerisinde bulunması gerekmez. `<nav>` yalnızca önemli navigasyon bağlantılarının oluşturduğu bölümleri tanımlamak için kullanılır.

## Kısaca
HTML'de bağlantı oluşturmak için `<a>` elementi kullanılır:
```
    <a href="/projects">Projeler</a>
```
Bağlantının nereye gideceğini `href` belirler

Temel kullanım şekilleri:
```
    <!-- Başka bir sayfaya -->
    <a href="/about">Hakkımızda</a>

    <!-- Başka bir web sitesine -->
    <a href="https://example.com">Example</a>

    <!-- Sayfanın belirli bir bölümüne -->
    <a href="#projects">Projeler</a>

    <!-- E-posta -->
    <a href="mailto:info@example.com">E-posta Gönder</a>

    <!-- Telefon -->
    <a href="tel:+905551234567">Bizi Arayın</a>
```

bu konuda hatırlanması gereken en önemli noktalardan biri ise şudur: **`Bağlantı kullanıcıyı bir yere götürür; buton ise bir işlem gerçekleştirir.`**