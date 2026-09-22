# HTML'de Erişilebilirlik - Accessibility (A11y)
Web erişilebilirliği, web sitelerinin ve uygulamalarının **farklı yeteneklere, ihtiyaçlara ve kullanım biçimlerine sahip kişiler tarafından kullanılabilir olması** anlamına gelir.

Bir kullanıcı web sitesini fare yerine klavyeyle kullanabilir, ekran okuyucu kullanabilir, görselleri göremeyebilir veya içeriği büyüterek görüntüleyebilir.

Bu nedenle erişilebilirlik yalnızca sayfanın nasıl göründüğüyle değil, **içeriğin nasıl yapılandırıldığı ve nasıl kullanılabildiğiyle** de ilgilidir.

Erişilebilirlik için sıkça **A11y** kısaltması kullanılır.
```
    Accessibility
    A + 11 harf + y
        ↓
        A11y
```

## Erişilebilirlik Neden Önemlidir?
Bir web sayfası görsel olarak başarılı olabilir ancak herkes tarafından kullanılamıyorsa kullanıcı deneyimi eksik kalır.

Örneğin, fare kullanan bir kullanıcı için çalışıyor olabilir.
```
    <div onclick="save()">
        Kaydet
    </div>
```

Ancak bu element semantic olarak bir buton değildir. Klavye ve yardımcı teknolojiler açısından beklenen davranışları kendiliğinden sağlamaz.

Bunun yerine aşağıdaki gibi kullanmak daha doğru bir başlangıçtır.
```
    <button type="button">
        Kaydet
    </button>
```

Tarayıcı `<button>` elementinin bir **etkileşimli kontrol** olduğunu zaten bilir.

Erişilebilir HTML'in temelinde de bu düşünce bulunur:

**`Mümkün olduğunda yapılmak istenen işi zaten ifade eden doğru HTML elementini kullan.`**

## Semantic HTML ve Erişilebilirlik
Daha önce Semantic HTML konusunda `<header>`, `<nav>`, `<main>`, `<article>` ve `<button>` gibi elementleri incelemiştik.

Bu elementler yalnızca kodun okunabilirliğini artırmaz. Sayfanın yapısı hakkında tarayıcılara ve yardımcı teknolojilere de anlam sağlar.

Örneğin:
```
    <div class="navigation">
        ...
    </div>
```
yerine:
```
    <nav>
        ...
    </nav>
```
kullanmak navigasyon alanının amacını HTML seviyesinde ifade eder.

Benzer şekilde:
```
    <div class="button">
        Kaydet
    </div>
```
yerine:
```
    <button type="button">
        Kaydet
    </button>
```
kullanılması daha anlamlıdır.

Bu nedenle erişilebilirliğin önemli bir bölümü aslında **doğru HTML yazmakla başlar.**

## `lang` Attribute'u
Sayfanın dilini belirtmek erişilebilirlik açısından temel ama sıkça atlanan bir noktadır.
```
    <html lang="tr">
        ...
    </html>
```
`lang` attribute'u sayesinde ekran okuyucu içeriği doğru telaffuzla okuyabilir. Dil belirtilmezse ekran okuyucu varsayılan dil ayarına göre okuma yapar ve bu da yanlış telaffuza yol açabilir.

Sayfa içinde farklı dilde bir bölüm varsa o bölüme de ayrıca `lang` eklenebilir:
```
    <p lang="en">
        This is an English sentence.
    </p>
```
Böylece yardımcı teknoloji o kısmı doğru dilde okuyabilir.

## Başlık Hiyerarşisi
Başlıklar yalnızca metni büyük ve kalın göstermek için kullanılmaz. Sayfanın içerik yapısını oluştururlar.

Örneğin:
```
    <h1>Frontend Öğrenme Rehberi</h1>

    <h2>HTML</h2>

    <h3>Semantic HTML</h3>
    <h3>Formlar</h3>

    <h2>CSS</h2>

    <h3>Flexbox</h3>
    <h3>Grid</h3>
```

Bu yapı içerik hiyerarşisini açık şekilde gösterir:
```
    Frontend Öğrenme Rehberi
    │
    ├── HTML
    │   ├── Semantic HTML
    │   └── Formlar
    │
    └── CSS
        ├── Flexbox
        └── Grid
```

Ekran okuyucu kullanıcıları başlıklar arasında gezinerek sayfanın yapısını anlayabilir. Bu nedenle başlık seviyeleri **görsel boyuta göre değil, içerik hiyerarşisine göre** seçilmelidir.

## Görsellerde Erişilebilirlik
### `alt` Attribute'u
Erişilebilirlik açısından görsellerde en önemli konulardan biri `alt` metnidir.

Anlamlı bir görsel:
```
    <img
        src="product.jpg"
        alt="Kahverengi deri omuz çantası"
    >
```

Görseli göremeyen bir kullanıcıya içeriğin ne olduğu hakkında bilgi sağlanabilir. Ancak `alt="resim"` veya `alt="fotoğraf"` gibi ifadeler genellikle yeterli bilgi sağlamaz. `alt` metni görselin **bulunduğu bağlamdaki anlamını** aktarmalıdır.

### Dekoratif Görseller
Bir görsel yalnızca dekorasyon amacıyla kullanılıyorsa boş `alt` kullanılabilir:
```
    <img
        src="decorative-shape.svg"
        alt=""
    >
```
Böylece yardımcı teknolojilere görselin içerik açısından anlam taşımadığı belirtilebilir.

Burada temel ayrım:
```
    Anlamlı görsel → Açıklayıcı alt

    Dekoratif görsel → alt=""
```

## Bağlantılarda Erişilebilirlik

### Anlaşılır Link Metinleri
Link metni, kullanıcıya bağlantının nereye götürdüğü hakkında mümkün olduğunca anlamlı bilgi vermelidir.

Örneğin:
```
    <a href="/projects">
        Buraya tıklayın
    </a>
```
yerine:
```
    <a href="/projects">
        Projelerimi inceleyin
    </a>
```
daha açıklayıcıdır.

Özellikle bağlantılar bağlam dışında listelendiğinde:
```
    Buraya tıklayın
    Devamını oku
    Buraya tıklayın
    Detay
```
gibi metinler neye bağlandığını anlamayı zorlaştırabilir. Link metninin tek başına da yeterince anlamlı olması iyi bir yaklaşımdır.

### `<a>` ve `<button>` Ayrımı
Erişilebilirlik açısından önemli konulardan biri de link ve butonların doğru amaçlarla kullanılmasıdır. 

Temel ayrım: 
```
    <a> → Bir yere götürür

    <button> → Bir işlem gerçekleştirir
```

Örneğin başka bir sayfaya gitmek:
```
    <a href="/products">
        Ürünleri Gör
    </a>
```

Form göndermek:
```
    <button type="submit">
        Kaydet
    </button>
```

Modal açmak:
```
    <button type="button">
        Filtreleri Aç
    </button>
```

Bir elementi CSS ile buton gibi göstermek, onu semantic olarak buton yapmaz.
```
    <a href="/login" class="button">
        Giriş Yap
    </a>
```

Burada görünümü buton gibi olsa bile element hala bir bağlantıdır. Eğer kullanıcıyı `/login` sayfasına götürüyorsa bu zaten doğru olabilir. `Elementi görünüşüne göre değil, **yaptığı işe göre seçmeliyiz.**`

## Klavye ile Kullanım
Bir web sitesinin temel etkileşimlerinin yalnızca fareye bağlı olmaması önemlidir. Kullanıcılar klavyedeki `Tab` tuşuyla etkileşimli elementler arasında hareket edebilir. 

Örneğin: 
```
    <a href="/">Ana Sayfa</a>

    <input type="text">

    <button type="submit">
        Gönder
    </button>
```
gibi doğal olarak etkileşimli HTML elementleri klavye kullanımına yönelik yerleşik davranışlara sahiptir.

Kullanıcı genellikle aşağıdaki şekilde ilerleyebilir:
```
    Tab → Bağlantı

    Tab → Input

    Tab → Buton
```

Bu nedenle: 
```
    <div onclick="openMenu()">
        Menü
    </div>
```
gibi özel yapılar oluşturmak yerine uygun olduğunda:
```
    <button type="button">
        Menü
    </button>
```
kullanmak klavye erişilebilirliği açısından da avantaj sağlar.

### Focus Nedir?
**Focus**, kullanıcının o anda hangi etkileşimli element üzerinde bulunduğunu ifade eder. Örneğin klavyeyle `Tab` tuşuna bastığınızda tarayıcı odaklanan elementi görsel olarak belirtebilir.

CSS'te bununla sıkça karşılaşırız:
```
    button:focus {
        outline: 2px solid;
    }
```
Modern CSS'te klavye odağı gibi durumlar için `:focus-visible` da kullanılabilir:
```
    button:focus-visible {
        outline: 2px solid;
    }
```
Focus göstergesi özellikle klavye kullanıcılarının `Şu anda sayfanın neresindeyim?` sorusunu cevaplayabilmesi açısından önemlidir. Bu nedenle focus görünümünü kaldırırken dikkatli olunmalıdır.

Örneğin:
```
    *:focus {
        outline: none;
    }
```
yazıp hiçbir alternatif focus göstergesi sağlamamak erişilebilirlik açısından sorun oluşturabilir.

### `tabindex`
`tabindex`, bir elementin klavye focus davranışını etkileyebilir. En sık karşılaşılan değerler: `tabindex="0"`

Elementi doğal belge sırasına göre klavye focus sırasına dahil edebilir.
```
    <div tabindex="0">
        ...
    </div>
```

**tabindex="-1"**

Element normal `Tab` sırasına dahil edilmez ancak örneğin JavaScript ile programatik olarak focus verilebilir.
```
    <div tabindex="-1">
        ...
    </div>
```

### Pozitif `tabindex`
Şöyle kullanımlar teknik olarak mümkündür:
```
    <button tabindex="3">Kaydet</button>
    <button tabindex="1">Geri</button>
    <button tabindex="2">İleri</button>
```
Ancak pozitif değerlerle özel Tab sırası oluşturmak genellikle önerilmez. Çünkü sayfanın doğal gezinme sırasını karmaşıklaştırabilir. İyi bir HTML yapısında çoğu zaman elementlerin DOM sırası zaten mantıklı bir klavye sırası sağlamalıdır. **Önce doğru HTML sırası oluşturulmalı; tabindex ile kötü bir yapıyı düzeltmeye çalışılmamalıdır.**

## Formlarda Erişilebilirlik
Formlar erişilebilirlik açısından özellikle önemlidir.

Örneğin:
```
    <label for="email">
        E-posta
    </label>

    <input
        type="email"
        id="email"
        name="email"
    >
```
`for` ve `id` ilişkisi sayesinde label ilgili form kontrolüyle programatik olarak ilişkilendirilir.

### Placeholder, Label Değildir
Şu kullanım label'ın yerini tam olarak tutmaz.
```
    <input
        type="email"
        placeholder="E-posta"
    >
```

Daha doğru yaklaşım:
```
    <label for="email">
        E-posta
    </label>

    <input
        type="email"
        id="email"
        name="email"
        placeholder="ornek@mail.com"
    >
```
Placeholder yardımcı bir ipucu olabilir ancak alanın kalıcı açıklaması olarak düşünülmemelidir.

### `fieldset` ve `legend`

Birbiriyle ilişkili form kontrollerini gruplamak için:
```
    <fieldset>

        <legend>İletişim Tercihiniz</legend>

        <input
            type="radio"
            id="emailOption"
            name="contact"
            value="email"
        >

        <label for="emailOption">
            E-posta
        </label>

        <input
            type="radio"
            id="phoneOption"
            name="contact"
            value="phone"
        >

        <label for="phoneOption">
            Telefon
        </label>

    </fieldset>
```
kullanılabilir.

Burada `<legend>` radio seçeneklerinin hangi soruya ait olduğunu açıklar.

### Hata Mesajlarını `aria-describedby` ile İlişkilendirmek
Bir form alanı için hata mesajı gösterildiğinde bu mesajın yalnızca görsel olarak alanın yakınında durması yeterli değildir. Ekran okuyucu kullanıcısının da mesajın o alana ait olduğunu anlayabilmesi gerekir.

```
    <label for="email">
        E-posta
    </label>

    <input
        type="email"
        id="email"
        name="email"
        aria-describedby="emailError"
        aria-invalid="true"
    >

    <span id="emailError">
        Geçerli bir e-posta adresi girin.
    </span>
```

`aria-describedby`, input'u hata mesajını içeren elementin `id`'siyle ilişkilendirir. Böylece ekran okuyucu alana odaklanıldığında hata mesajını da okuyabilir. `aria-invalid="true"` ise alanın geçersiz bir değer içerdiğini ayrıca belirtir.

## Tablolarda Erişilebilirlik
Tablolarda başlık hücrelerinin doğru kullanılması önemlidir.

Örneğin:
```
    <table>

        <caption>Ürün Stok Durumu</caption>

        <thead>
            <tr>
                <th scope="col">Ürün</th>
                <th scope="col">Stok</th>
            </tr>
        </thead>

        <tbody>
            <tr>
                <th scope="row">Akıllı Saat</th>
                <td>12</td>
            </tr>

            <tr>
                <th scope="row">Kulaklık</th>
                <td>8</td>
            </tr>
        </tbody>

    </table>
```
Buradaki `scope` değerleri başlıklarla veriler arasındaki ilişkiyi daha açık hale getirir.
```
    scope="col" → Sütun başlığı

    scope="row" → Satır başlığı
```
`<caption>` ise tablonun genel olarak ne hakkında olduğunu açıklar.

## Ekran Okuyucu Nedir?
**Screen reader (ekran okuyucu)**, ekrandaki veya erişilebilirlik ağacındaki içeriği kullanıcıya çoğunlukla sesli ya da Braille çıktısıyla aktaran yardımcı teknolojidir.

Örneğin ekran okuyucu:
- Başlıkları
- Bağlantıları
- Butonları
- Form alanlarını ve label'larını
- Görsellerin alternatif metinlerini
- Sayfadaki belirli yapısal bölgeleri
kullanıcının anlamlandırmasına yardımcı olabilir.

Bu nedenle:
```
    <button>
        Sepete Ekle
    </button>
```
gibi doğru HTML kullanımı yalnızca kod kalitesi değildir; yardımcı teknolojilerin elementin ne olduğunu anlayabilmesine de katkı sağlar.

## ARIA Nedir?
**ARIA, Accessible Rich Internet Applications** ifadesinin kısaltmasıdır.

HTML'in tek başına yeterli erişilebilirlik bilgisini sağlayamadığı özel arayüzlerde yardımcı teknolojilere ek bilgiler vermek için kullanılabilecek attribute'lar ve roller sunar.

Örneğin yalnızca ikon bulunan bir buton düşünelim:
```
    <button type="button">
        <svg>
            ...
        </svg>
    </button>
```
Görsel olarak bunun bir kapatma butonu olduğu anlaşılabilir. Ancak erişilebilir bir isim yoksa yardımcı teknoloji açısından amacı belirsiz olabilir.

Bu durumda:
```
    <button
        type="button"
        aria-label="Pencereyi kapat"
    >
        <svg aria-hidden="true">
            ...
        </svg>
    </button>
```
kullanılabilir.

Burada:
```
    aria-label → Butona erişilebilir bir isim sağlar.
```
SVG dekoratif olduğu için burada ayrıca yardımcı teknolojilerden gizlenmiştir.

### `role` Nedir?
**role**, bir elementin erişilebilirlik açısından hangi role sahip olduğunu belirtmek için kullanılabilir.

Örneğin:
```
    <div role="button">
        Kaydet
    </div>
```
Bu yapı yardımcı teknolojiye elementin bir buton olarak değerlendirilmesi gerektiğini söyleyebilir. Ancak burada önemli bir problem vardır. Zaten HTML'de gerçek bir:
```
    <button type="button">
        Kaydet
    </button>
```
elementi vardır.

`role="button"` eklemek `<div>` elementine gerçek `<button>` elementinin tüm davranışlarını otomatik olarak kazandırmaz. Klavye etkileşimi, focus davranışı ve diğer özelliklerin ayrıca doğru şekilde uygulanması gerekebilir.

Bu yüzden temel kural **`Uygun native HTML elementi varsa önce onu kullan.`**

Yani `<div role="button">` yerine mümkün olduğunda `<button>` kullanmak daha doğrudur.

### ARIA, Semantic HTML'in Yerine Geçmez
ARIA konusunda başlangıç seviyesinde bilinmesi gereken en önemli noktalardan biri budur. 

Örneğin `<div role="navigation">` kullanılabilir.

Ancak zaten `<nav>` elementimiz vardır.

Benzer şekilde `<div role="button">` yerine `<button>` kullanabiliriz.

Bu nedenle genel yaklaşım aşağıdaki gibi olmalıdır.
```
    Önce → Native / Semantic HTML

    Yetmiyorsa → Gerekli erişilebilirlik bilgisini ekle

    Gerekiyorsa → ARIA
```

ARIA'yı her elemente eklemek sayfayı otomatik olarak daha erişilebilir yapmaz. Yanlış ARIA kullanımı aksine yanlış veya çelişkili bilgi oluşturabilir.

### `aria-hidden`
`aria-hidden="true"` bir içeriğin yardımcı teknolojiler tarafından göz ardı edilmesini istemek için kullanılır.

Örneğin dekoratif bir ikon:
```
    <button type="button">

        <span aria-hidden="true">
            ♥
        </span>

        Favorilere Ekle

    </button>
```
Kalp sembolü burada yalnızca görsel destek sağlıyorsa ekran okuyucunun ayrıca bunu okuması gerekmeyebilir.

### `hidden` ile `aria-hidden` Aynı Şey Değildir
Bu ikisini birbirinden ayırmak önemlidir.

**`hidden`**

```
    <div hidden>
        İçerik
    </div>
```
Elementin kullanıcıya sunulmamasını sağlar; normalde görsel olarak da gösterilmez ve erişilebilirlik ağacında da yer almaz.

**`aria-hidden="true"`**

```
    <div aria-hidden="true">
        İçerik
    </div>
```
İçerik görsel olarak sayfada bulunmaya devam edebilir ancak yardımcı teknolojilerden gizlenir.

Temel olarak:
```
    hidden → İçeriği genel olarak gizler.
    aria-hidden="true" → İçeriğe erişilebilirlik ağacından gizler, ancak görsel olarak görünmeye devam edebilir.
```

`aria-hidden` özellikle odaklanabilir/etkileşimli içeriklerde dikkatsizce kullanılmamalıdır; görünür ve kullanılabilir bir kontrolü yardımcı teknolojilerden gizlemek erişilebilirlik problemi oluşturabilir.

## Sık Yapılan Erişilebilirlik Hataları
HTML tarafında sık karşılaşılan bazı hataları birlikte görelim.

### Her şeyi `<div>` ile yapmak
```
    <div onclick="submitForm()">
        Gönder
    </div>
```
yerine:
```
    <button type="submit">
        Gönder
    </button>
```

### Görsellerde alt bilgisini düşünmemek
`<img src="product.jpg">`

yerine anlamlı bir görselse:
```
    <img
        src="product.jpg"
        alt="Siyah deri kayışlı kol saati"
    >
```

### Placeholder'ı label olarak kullanmak
`<input placeholder="E-posta">`

yerine:
```
    <label for="email">E-posta</label>

    <input
        type="email"
        id="email"
        name="email"
    >
```

### Focus görünümünü tamamen kaldırmak
```
    button:focus {
        outline: none;
    }
```
kullanılıyorsa klavye kullanıcısının odağı anlayabileceği uygun bir alternatif focus göstergesi sağlanmalıdır.

### Link ve button'ı yalnızca görünüşlerine göre seçmek
Navigasyon:
```
    <a href="/products">
        Ürünler
    </a>
```

İşlem:
```
    <button type="button">
        Sepete Ekle
    </button>
```

### Gereksiz ARIA kullanmak
Şunun yerine:
```
    <div role="button">
        Kaydet
    </div>
```
mümkünse:
```
    <button type="button">
        Kaydet
    </button>
```
kullanmak daha doğru ve daha basittir.

## Erişilebilir HTML İçin Temel Kontrol Listesi
Bir HTML sayfası oluşturduktan sonra kendimize birkaç soru sorabiliriz:
- Sayfanın başlık hiyerarşisi anlamlı mı?
- İçerik için uygun semantic HTML elementlerini kullandım mı?
- Sayfa temel işlevleriyle klavyeden kullanılabiliyor mu?
- Focus edilen element anlaşılabiliyor mu?
- Anlamlı görsellerin uygun alt metinleri var mı?
- Dekoratif görseller doğru şekilde ele alınmış mı?
- Form alanlarının uygun label'ları var mı?
- Link metinleri nereye gittiğini anlatıyor mu?
- İşlem yapan yerlerde button, navigasyon yapan yerlerde link kullandım mı?
- Tablolarda başlık-veri ilişkileri anlaşılır mı?
- ARIA'yı gerçekten ihtiyaç olduğu yerde mi kullandım?

Bu soruların amacı erişilebilirliği birkaç attribute ezberine dönüştürmek değil, HTML'i kullanıcının nasıl etkileşime gireceğini düşünerek yazma alışkanlığı kazanmaktır.

## Kısaca Özet
HTML erişilebilirliğinin temelinde karmaşık tekniklerden önce doğru HTML kullanımı bulunur.
```
    Semantic HTML → Anlamlı sayfa yapısı
    Doğru başlık hiyerarşisi → Anlaşılır içerik yapısı
    alt → Görsel alternatifleri
    label → Anlaşılır form alanları
    Klavye + Focus → Fare dışındaki kullanım yöntemleri
    Native HTML → Yerleşik anlam ve davranışlar
    ARIA → Gerektiğinde ek erişilebilirlik bilgisi
```
Bu konunun en önemli prensibini şöyle özetleyebiliriz:

`Önce doğru ve semantic HTML'i kullan. Erişilebilirliği sonradan eklenen bir özellik olarak değil, HTML yapısının doğal bir parçası olarak düşün. ARIA'yı ise native HTML'in yeterli olmadığı durumlarda bilinçli şekilde kullan.`