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

Özellikle kullanıcı mevcut sayfayı kaybetmeden harici bir kaynağı görüntüleyecekse kullanılabilir.

Ancak her bağlantının `_blank` ile açılması önerilmez. Yeni sekme açmak kullanıcı deneyimini etkilediği için **gerçekten gerekli olduğunda** tercih edilmelidir.

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

En içteki bağlantı için kullanılırsa bir üst seviyeye çıkılır.
```
    <a href="/about" target="_parent">
        Hakkımızda
    </a>
```