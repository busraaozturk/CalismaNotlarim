# HTML Formları
HTML formları, kullanıcıdan veri almak için kullanılan yapılardır. Bir web sitesinde kullanıcıdan bilgi girmesini veya bir seçim yapmasını istediğimiz birçok yerde form yapılarıyla karşılaşırız. 

Örneğin:
- Giriş ve kayıt ekranları
- İletişim formları
- Arama alanları
- Adres bilgileri
- Ödeme formları
- Filtreleme alanları
- Anketler
- Dosya yükleme alanları

Basit bir giriş formu şu şekilde olabilir:
```
    <form>
        <label for="email">E-posta</label>
        <input type="email" id="email" name="email">

        <label for="password">Şifre</label>
        <input type="password" id="password" name="password">

        <button type="submit">Giriş Yap</button>
    </form>
```

Burada `<form>` bütün form alanlarını bir araya getirirken `<input>` kullanıcıdan veri alır, `<label>` alanın ne olduğunu açıklar ve `<button>` formun gönderilmesini sağlar.

## 1. `<form>` Elementi
Bir HTML formunun temel kapsayıcı `<form>` elementidir.
```
    <form>
        <!-- Form alanları -->
    </form>
```

Ancak gerçek bir formda yalnızca alanları göstermek yeterli değildir. Genellikle form gönderildiğinde verilerin nereye ve hangi yöntemle gönderileceğinin de belirtilmesi gerekir.

Burada `action` ve `method` karşımıza çıkar.
```
    <form action="/register" method="post">
        ...
    </form>
```
Bu yapıyı temel olarak şöyle okuyabiliriz: `Kullanıcının doldurduğu form verilerini **/register** adresine **POST** yöntemiyle gönder.`

## 2. `action` Attribute'u
`action`, form gönderildiğinde verilerin ***hangi adrese gönderileceğini** belirtir.
```
    <form action="/register">
        ...
    </form>
```

Örneğin bir iletişim formumuz olduğunu düşünelim:
```
    <form action="/contact" method="post">
        ...
    </form>
```
Kullanıcı formu gönderdiğinde form verileri `/contact` adresine gönderilir.

`action` değerinin tam olarak nasıl karşılanacağı kullanılan backend teknolojisine göre değişebilir. HTML tarafında bilmeniz gereken temek nokta şudur; `action → Form verisinin gönderileceği adresi belirtir.`

## 3. `method` Attribute'u
`method`, form verilerinin **hangi HTTP yöntemiyle gönderileceğini** belirtir.

HTML formlarında temel olarak iki yöntemle karşılaşırız:
```
    GET
    POST
```

Örneğin:

`<form action="/search" method="get">` veya `<form action="/register" method="post">`

### GET
GET, genellikle sunucudan bir şey **istemek veya görüntülemek** amacıyla kullanılan işlemlerde tercih edilir.

Örneğin bir arama formu:
```
    <form action="/search" method="get">
        <label for="search">Arama</label>

        <input
            type="search"
            id="search"
            name="q"
        >

        <button type="submit">Ara</button>
    </form>
```
Kullanıcı `html` yazıp formu gönderdiğinde yaklaşık olarak şöyle olabilir: `/search?q=html`

Buradaki `q=html` formdan gelen veridir. Bu nedenle GET ile gönderilen form verileri URL'nin **query string** bölümünde görülebilir. GET özellikle arama ve filtreleme gibi URL ile ifade edilmesi anlamlı olan işlemlerde sık kullanılır.

### POST
POST, ise genellikle sunucuya veri **gönderen veya bir işlem gerçekleştiren** formlarda kullanılır.

Örneğin:
```
    <form action="/register" method="post">

        <label for="name">Ad Soyad</label>
        <input
            type="text"
            id="name"
            name="name"
        >

        <label for="email">E-posta</label>
        <input
            type="email"
            id="email"
            name="email"
        >

        <button type="submit">
            Kayıt Ol
        </button>

    </form>
```

Bu durumda form verileri URL'nin query string bölümüne eklenmek yerine **HTTP isteğinin gövdesinde (request body)** gönderilir. Temel olarak:
| GET                                           | POST                                                   |
| --------------------------------------------- | ------------------------------------------------------ |
| Veri genellikle URL'de görünür                | Veri request body'de gönderilir                        |
| Arama ve filtreleme gibi işlemlerde yaygındır | Kayıt, giriş, veri oluşturma gibi işlemlerde yaygındır |
| URL paylaşılabilir/bookmark yapılabilir       | Form verileri URL'nin parçası değildir                 |

Ancak burada önemli bir nokta var: `POST kullanmak veriyi otomatik olarak güvenli veya şifrelenmiş hale getirmez.`

İletişimin şifrelenmesi için HTTPS gerekir. Ayrıca şifre, ödeme bilgisi gibi hassas verilerin güvenliği yalnızca HTML formunun `method` seçimine bağlı değildir; sunucu tarafında da doğru güvenlik önlemleri gerekir.

Başlangıç seviyesinde şu ayrımı bilmemiz yeterlidir:
```
    Arama / filtreleme
            ↓
        GET


    Kayıt / giriş / veri gönderme
            ↓
        POST
```

Bu mutlak bir kural değil, kullanım amacını anlamayı kolaylaştıran genel bir yaklaşımdır.

## 4. `enctype` Nedir?
enctype, form verilerinin gönderilirken **nasıl kodlanacağını** belirtir. Özellikle dosya yükleme işlemlerinde önemlidir.

Normal bir formda genellikle varsayılan olarak; `application/x-www-form-urlencoded` kullanılır.

Ancak form üzerinden dosya gönderilecekse aşağıdaki şekilde kullanılır:
```
    <form
        action="/upload"
        method="post"
        enctype="multipart/form-data"
    >
```

Örneğin:
```
    <form
        action="/profile"
        method="post"
        enctype="multipart/form-data"
    >

        <label for="profilePhoto">
            Profil Fotoğrafı
        </label>

        <input
            type="file"
            id="profilePhoto"
            name="profilePhoto"
        >

        <button type="submit">
            Yükle
        </button>

    </form>
```
Burada temel olarak hatırlamamız gereken; **`Dosya yüklenen klasik HTML formlarında method="post" ile birlikte enctype="multipart/form-data" kullanılır.`

## 5. `<input>` Elementi
Formların en önemli elementlerinden biri `<input>` elementidir. Kullanıcıdan veri almak için kullanılır.

`<input type="text">` → `<input>` bir **void elementtir, yani kapanış etiketi bulunmaz.**

`<input type="text">` → Farklı türlerde veri almak için `type` attribute'u kullanılır.

Örneğin:
```
    <input type="text">
    <input type="email">
    <input type="password">
    <input type="number">
    <input type="date">
```

Buradaki type, input'un hangi tür veri için kullanılacağını belirtir.

## 6. `<label>` Etiketi
`<label>`, bir form alanının **ne anlama geldiğini açıklamak** için kullanılır.

Örneğin:
```
    <label for="email">E-posta Adresi</label>

    <input
        type="email"
        id="email"
        name="email"
    >
```
Burada kullanıcı hangi bilginin istendiğini açıkça görebilir. Label kullanımı yalnızca görsel açıklama açısından değil, **erişilebilirlik açısından da önemlidir.**

### `for` ve `id` İlişkisi
Label ile input arasında ilişki kurulması gerekir. Bunun için `<label for="email">` ile `<label id="email">` birbirine bağlanır.

Aşağıdaki şekilde betimlendiği gibi:
```
    <label for="email">
            │
            └────────────┐
                            ↓
                <input id="email">
```

Değerlerin aynı olması gerekir.
```
    <label for="username">Kullanıcı Adı</label>

    <input
        type="text"
        id="username"
        name="username"
    >
```

Bunun önemli bir kullanıcı deneyimi avantajı vardır: **Label'a tıkladığınızda ilişkili input alanı odaklanır.** Bu özellikle checkbox ve radio gibi küçük tıklama alanlarında daha da faydalıdır.

## 7. `id` ve `name` Aynı Şey Değildir
Formlarda başlangıçta en çok karıştırılan konulardan biri budur. Şöyle bir input düşünelim:
```
    <input
        type="email"
        id="userEmail"
        name="email"
    >
```
Burada `id="userEmail"` ve `name="email"` farklı amaçlara sahiptir.

### `id`
HTML belgesi içerisinde elementi tanımlar. Örneğin label ile ilişki kurabiliriz:
```
    <label for="userEmail">
        E-posta
    </label>

    <input
        id="userEmail"
        name="email"
        type="email"
    >
```
CSS ve JavaScript tarafından da elementi hedeflemek için kullanılabilir.

### `name`
`name` form gönderildiğinde **verinin hangi isimle gönderileceğini** belirler.

Örneğin:
```
    <input
        type="text"
        name="username"
        value="test"
    >
```

Form gönderildiğinde temel olarak `username=test` şeklinde bir isim-değer ilişkisi oluşur.

Bu nedenle, `id` elementi tanımlarken, `name` form verisinin anahtarını belirler.

Şöyle düşünebiliriz:
```
    id → Bu HTML elementi hangisi?

    name → Bu veri hangi isimle gönderilecek?
```

## 8. `value` Attribute'u
`value` form alanının değerini ifade eder.

Örneğin:
```
    <input
        type="text"
        name="username"
        value="Test"
    >
```

Input açıldığında içerisinde `Test` değeri bulunur.

Form gönderildiğinde de `username=Test` şeklinde gönderilebilir.

`value` özellikle radio, checkbox ve button gibi yapılarda da önemlidir.

## 9. `placeholder`
`placeholder`, input boşken kullanıcıya kısa bir ipucu göstermek için kullanılabilir.
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

Input boşken şu şekilde görünebilir:
```
    ┌─────────────────────────────┐
    │ ornek@mail.com              │
    └─────────────────────────────┘
```

Ancak önemli bir kural vardır, **`placeholder`, `<label>` yerine kullanılmamalıdır.**

Örneğin yalnızca:
```
    <input
        type="email"
        placeholder="E-posta adresiniz"
    >
```
kullanmak yerine:
```
    <label for="email">
        E-posta Adresi
    </label>

    <input
        type="email"
        id="email"
        name="email"
        placeholder="ornek@mail.com"
    >
```
daha doğru bir yapıdır.

Çünkü placeholder kullanıcı yazmaya başladığında kaybolur. Label ise alanın ne olduğunu açıklamaya devam eder ve erişilebilirlik açısından daha sağlam bir ilişki sağlar.

## 10. Temel Input Türleri
`<input>` elementinin davranışı büyük ölçüde `type` attribute'una bağlıdır.

### `text`
Tek satırlık normal metin girişi için kullanılır.
```
    <label for="name">Ad Soyad</label>

    <input
        type="text"
        id="name"
        name="name"
    >
```

### `email`
E-posta adresi almak için kullanılır.
```
    <label for="email">E-posta</label>

    <input
        type="email"
        id="email"
        name="email"
    >
```

Tarayıcı e-posta formatıyla ilgili temel doğrulamalar yapabilir. Mobil cihazlarda da e-posta girişine uygun klavye sunulabilir.

### `password`
Şifre girişleri için kullanılır. Girilen karakterler ekranda gizlenir.
```
    <label for="password">Şifre</label>

    <input
        type="password"
        id="password"
        name="password"
    >
```

Ancak, **`type="password"` şifreyi güvenli şekilde saklamaz veya şifrelemez.** Yalnızca kullanıcı arayüzünde karakterlerin görünümünü gizler.

### `number`
Sayısal girişler için kullanılabilir. Örneğin ürün adedi gibi gerçekten sayısal bir değerde anlamlıdır.
```
    <label for="quantity">Adet</label>

    <input
        type="number"
        id="quantity"
        name="quantity"
    >
```

Telefon numarası gibi yalnızca rakamlardan oluşabilen ama üzerinde matematiksel işlem yapılmayan bilgiler için `number` kullanmak doğru değildir. Telefon için `tel` daha uygundur.

### `tel`
Telefon numarası almak için kullanılır.
```
    <label for="phone">Telefon</label>

    <input
        type="tel"
        id="phone"
        name="phone"
    >
```

### `url`
Web adresi almak için kullanılabilir.
```
    <label for="website">
        Web Sitesi
    </label>

    <input
        type="url"
        id="website"
        name="website"
    >
```

### `date`
Tarih seçimi için kullanılır.
```
    <label for="birthDate">
        Doğum Tarihi
    </label>

    <input
        type="date"
        id="birthDate"
        name="birthDate"
    >
```
Tarayıcı uygun bir tarih seçim arayüzü sunabilir.

### `time`
Saat bilgisi almak için kullanılır.
```
    <label for="appointment">
        Randevu Saati
    </label>

    <input
        type="time"
        id="appointment"
        name="appointment"
    >
```

### `search`
Arama alanları için kullanılabilir. Semantik olarak alanın arama amacıyla kullanıldığını ifade eder.
```
    <label for="search">Ürün Ara</label>

    <input
        type="search"
        id="search"
        name="q"
    >
```

### `file`
Kullanıcının dosya seçebilmesini sağlar.
```
    <label for="cv">
        CV Yükle
    </label>

    <input
        type="file"
        id="cv"
        name="cv"
    >
```
Dosyanın klasik form gönderimiyle sunucuya yüklenmesi gerekiyorsa form tarafında genellikle şu şekilde kullanılır:
```
    <form
        method="post"
        enctype="multipart/form-data"
    >
```

### `hidden`
Kullanıcının görmediği ancak form ile birlikte gönderilebilecek bir değer tutar.
```
    <input
        type="hidden"
        name="productId"
        value="152"
    >
```
Bu alan ekranda görünmez ancak form gönderildiğinde `productId=152` değeri gönderilebilir.

`hidden` kullanmak veriyi **güvenli veya gizli hale getirmez**. Kullanıcı geliştirici araçları veya gönderilen istek üzerinden bu değeri görebilir ve değiştirebilir. Bu nedenle güvenlik açısından güvenilir bir veri kaynağı olarak kabul edilmemelidir.

## 11. Checkbox
`checkbox`, kullanıcının bir seçeneği işaretlemesini sağlar.
```
    <input
        type="checkbox"
        id="terms"
        name="terms"
        value="accepted"
    >

    <label for="terms">
        Kullanım koşullarını kabul ediyorum.
    </label>
```
Checkbox özellikle:
- Kullanım koşullarını kabul etme
- Birden fazla ilgi alanı seçme
- Bildirim tercihi
- Ayarları açıp kapatma
gibi durumlarda kullanılabilir.

Birden fazla seçenek aynı anda seçilebilir. Örneğin:
```
    <input
        type="checkbox"
        id="html"
        name="skills"
        value="html"
    >
    <label for="html">HTML</label>

    <input
        type="checkbox"
        id="css"
        name="skills"
        value="css"
    >
    <label for="css">CSS</label>
```
Kullanıcı hem HTML hem CSS seçebilir.

## 12. Radio Button
`radio`, seçeneklerden **yalnızca bir tanesinin seçilmesi** gereken durumlarda kullanılır.
```
    <input
        type="radio"
        id="junior"
        name="level"
        value="junior"
    >

    <label for="junior">
        Junior
    </label>

    <input
        type="radio"
        id="mid"
        name="level"
        value="mid"
    >

    <label for="mid">
        Mid
    </label>
```

Burada çok önemli bir ayrıntı vardır, `name="level"` iki radio inputunda da aynıdır. Tarayıcı radio butonlarını aynı `name` değerine göre aynı seçim grubu içerisinde değerlendirir.

Bu nedenle seçeneklerden yalnızca biri seçilebilir.
```
    () Junior
    () Mid
    () Senior
```

Kısaca:
```
    Checkbox →Birden fazla seçim yapılabilir.

    Radio → Bir gruptan tek seçim yapılır.
```

## 13. `checked`
Checkbox veya radio alanının başlangıçta seçili olmasını sağlar. `checked` bir **boolean attribute**'tur.
```
    <input
        type="checkbox"
        id="newsletter"
        name="newsletter"
        checked
    >

    <label for="newsletter">
        E-bültene abone ol
    </label>
```

Bu nedenle, `checked="true"` yazmak yerine `checked` kullanılması yeterlidir.

## 14. `<select>` ve `<option>`
Kullanıcıya seçeneklerden oluşan açılır bir liste sunmak için `<select>` kullanılır.
```
    <label for="city">Şehir</label>

    <select id="city" name="city">

        <option value="istanbul">
            İstanbul
        </option>

        <option value="ankara">
            Ankara
        </option>

        <option value="izmir">
            İzmir
        </option>

    </select>
```

Burada:
```
    <select>
    ↓
    Seçim alanı

    <option>
    ↓
    Her bir seçenek
```
`option` içerisindeki `value`, form gönderildiğinde kullanılacak değerdir.

Kullanıcı İstanbul'u seçerse `city=istanbul` gibi bir değer gönderilebilir.

### `selected`
Bir seçeneğin başlangıçta seçili olması için `selected` kullanılabilir. selected da **boolean attribute**'lardan biridir.
```
    <option value="istanbul" selected>
        İstanbul
    </option>
```

## 15. `<textarea>`
Uzun veya birden fazla satırdan oluşabilecek metinleri almak için `<textarea>` kullanılır. Örneğin iletişim formundaki mesaj alanı:
```
    <label for="message">Mesajınız</label>

    <textarea
        id="message"
        name="message"
    ></textarea>
```
`<input>` elementinden farklı olarak `<textarea>` kapanış etiketine sahiptir: `<textarea></textarea>`

Varsayılan içerik gerekiyorsa açılış ve kapanış etiketleri arasına yazılır:
```
    <textarea name="message">Varsayılan mesaj</textarea>
```

## 16. Form Butonları
Formlarda `<button>` elementiyle sıkça karşılaşırız. En önemli button türleri:
```
    submit
    button
    reset
```

### `submit`
Formu gönderir.
```
    <button type="submit">
        Kaydet
    </button>
```
Form içerisindeki `<button>` için varsayılan davranışın `submit` olabileceğini göz önünde bulundurarak `type` değerini açıkça yazmak iyi bir alışkanlıktır.

### `button`
Kendi başına form göndermez.
```
    <button type="button">
        Önizle
    </button>
```
Genellikle JavaScript ile özel bir işlem yapılacağı zaman kullanılabilir.

### `reset`
Form alanlarını başlangıç değerlerine döndürür.
```
    <button type="reset">
        Formu Temizle
    </button>
```
Gerçek kullanıcı arayüzlerinde `reset` her zaman gerekli değildir ve yanlışlıkla girilmiş verilerin silinmesine neden olabileceği için kullanım amacı dikkatli değerlendirilmelidir.

## 17. HTML Form Validation
HTML, bazı temel form doğrulamalarını JavaScript yazmadan gerçekleştirebilir.

### `required`
Bir alanın doldurulmasını zorunlu hale getirir.
```
    <input
        type="email"
        name="email"
        required
    >
```
Kullanıcı alanı boş bırakıp formu göndermeye çalışırsa tarayıcı gönderimi engelleyebilir ve doğrulama mesajı gösterebilir.

### `minlength` ve `maxlength`
Metnin minimum ve maksimum uzunluğunu belirlemek için kullanılabilir.
```
    <input
        type="text"
        name="username"
        minlength="3"
        maxlength="20"
    >
```
Burada kullanıcı adı belirlenen uzunluk sınırlarına göre doğrulanabilir.

### `min` ve `max`
Özellikle sayı ve tarih gibi uygun input türlerinde sınır belirlemek için kullanılabilir.
```
    <input
        type="number"
        name="age"
        min="18"
        max="100"
    >
```

### `step`
Sayısal değerlerin hangi artışlarla ilerleyebileceğini belirtir.
```
    <input
        type="number"
        name="quantity"
        min="1"
        step="1"
    >
```

### `pattern`
Girilen değerin belirli bir desene uymasını istemek için kullanılabilir.
```
    <input
        type="text"
        name="code"
        pattern="[A-Z]{3}"
    >
```

Bu örnekte üç büyük harften oluşan bir değer beklenmektedir.

`pattern` **düzenli ifadeler (regular expressions)** kullanır. Regex ayrı ve kapsamlı bir konu olduğu için burada ayrıntısına girmemiz gerekmiyor.

## 18. `readonly` ve `disabled`
Bu iki attribute başlangıçta birbirine benzer görünse de aynı değildir.

### `readonly`
Kullanıcı alanın değerini değiştiremez.
```
    <input
        type="text"
        name="username"
        value="busra"
        readonly
    >
```
Alan kullanılabilir durumdadır ancak değeri düzenlenemez. Başarılı form gönderiminde değeri gönderilebilir.

### `disabled`
Alan devre dışıdır.
```
    <input
        type="text"
        name="username"
        value="busra"
        disabled
    >
```
Kullanıcı alanla etkileşime giremez ve disabled form kontrolleri normal form gönderimine dahil edilmez.

Temel ayrım:
```
    readonly → Değer değiştirilemez ancak form verisine dahil olabilir.

    disabled → Alan devre dışıdır ve normal form gönderimine dahil edilmez.
```

## 19. `<fieldset>` ve `<legend>`
Uzun formlarda birbiriyle ilişkili alanları gruplandırmak için `<fieldset>` kullanılabilir. Grubun açıklaması ise `<legend>` ile verilir.

Örneğin:
```
    <fieldset>

        <legend>İletişim Bilgileri</legend>

        <label for="email">
            E-posta
        </label>

        <input
            type="email"
            id="email"
            name="email"
        >

        <label for="phone">
            Telefon
        </label>

        <input
            type="tel"
            id="phone"
            name="phone"
        >

    </fieldset>
```
Bu yapı özellikle radio gruplarında da oldukça anlamlıdır:
```
    <fieldset>

        <legend>Deneyim Seviyesi</legend>

        <input
            type="radio"
            id="junior"
            name="level"
            value="junior"
        >
        <label for="junior">Junior</label>

        <input
            type="radio"
            id="mid"
            name="level"
            value="mid"
        >
        <label for="mid">Mid</label>

    </fieldset>

```
Böylece seçeneklerin hangi soruya ait olduğu semantic olarak da ifade edilmiş olur.

## 20. Erişilebilir Form Oluşturmak
Formlarda erişilebilirlik sonradan eklenen ayrı bir özellik olarak değil, formun doğru HTML yapısının bir parçası olarak düşünülmelidir. Temel olarak birkaç kurala dikkat edebiliriz.

### Form alanlarının uygun label'ı olmalıdır
```
<label for="email">E-posta</label>

<input
    type="email"
    id="email"
    name="email"
>
```

### Placeholder label yerine kullanılmamalıdır
```
    <!-- Önerilmez -->
    <input
        type="email"
        placeholder="E-posta"
    >
```
Bunun yerine:
```
    <label for="email">E-posta</label>

    <input
        type="email"
        id="email"
        name="email"
        placeholder="ornek@mail.com"
    >
```

### Uygun type kullanılmalıdır

E-posta için: `<input type="email">`

Telefon için: `<input type="tel">`

Tarih için: `<input type="date">`

kullanmak hem formun anlamını hem de tarayıcının kullanıcıya sunabileceği deneyimi iyileştirir.

### Butonların amacı açık olmalıdır
```
    <button type="submit">
        Hesap Oluştur
    </button>
```
gibi açıklayıcı metinler:

```
    <button type="submit">
        Gönder
    </button>
```
gibi genel ifadelerden bazı durumlarda daha anlaşılır olabilir.

## Tam Bir Form Örneği
Şimdi öğrendiğimiz temel yapıları bir kayıt formunda bir araya getirelim:
```
    <form action="/register" method="post">

        <h2>Hesap Oluştur</h2>

        <div>
            <label for="name">
                Ad Soyad
            </label>

            <input
                type="text"
                id="name"
                name="name"
                autocomplete="name"
                required
            >
        </div>

        <div>
            <label for="email">
                E-posta
            </label>

            <input
                type="email"
                id="email"
                name="email"
                autocomplete="email"
                placeholder="ornek@mail.com"
                required
            >
        </div>

        <div>
            <label for="password">
                Şifre
            </label>

            <input
                type="password"
                id="password"
                name="password"
                autocomplete="new-password"
                minlength="8"
                required
            >
        </div>

        <div>
            <label for="birthDate">
                Doğum Tarihi
            </label>

            <input
                type="date"
                id="birthDate"
                name="birthDate"
            >
        </div>

        <fieldset>

            <legend>Deneyim Seviyesi</legend>

            <input
                type="radio"
                id="junior"
                name="level"
                value="junior"
            >
            <label for="junior">Junior</label>

            <input
                type="radio"
                id="mid"
                name="level"
                value="mid"
            >
            <label for="mid">Mid</label>

            <input
                type="radio"
                id="senior"
                name="level"
                value="senior"
            >
            <label for="senior">Senior</label>

        </fieldset>

        <div>
            <input
                type="checkbox"
                id="terms"
                name="terms"
                value="accepted"
                required
            >

            <label for="terms">
                Kullanım koşullarını kabul ediyorum.
            </label>
        </div>

        <button type="submit">
            Hesap Oluştur
        </button>

    </form>
```

Bu formun yapısını parçaladığımızda aşağıdaki gibi oldukça düzenli bir yapı elde ederiz:
```
    <form>
    │
    ├── label + input
    │      └── Ad Soyad
    │
    ├── label + input
    │      └── E-posta
    │
    ├── label + input
    │      └── Şifre
    │
    ├── label + input
    │      └── Doğum Tarihi
    │
    ├── fieldset
    │      ├── legend
    │      └── radio seçenekleri
    │
    ├── checkbox + label
    │
    └── submit button
```

## Formlarda Temel Mantık
Bu konudan özellikle şu ilişkileri anlamak önemli:
```
    <form> → Formun tamamını kapsar.

    <label> → Alanı kullanıcıya açıklar.

    <input> → Kullanıcıdan veri alır.

    id + for → Label ile form kontrolünü ilişkilendirir.

    name → Verinin hangi isimle gönderileceğini belirler.

    value → Gönderilecek değeri temsil eder.

    type → Form kontrolünün türünü belirler.

    action → Verinin nereye gönderileceğini belirtir.

    method → Verinin hangi HTTP yöntemiyle gönderileceğini belirtir.
```

Bunların içerisinde özellikle şu üçlü karıştırılmamalıdır:
```
    <label for="userEmail">E-posta</label>

    <input
        type="email"
        id="userEmail"
        name="email"
    >
```

Burada:
```
    for="userEmail" → label'ın hangi input'a ait olduğu

    id="userEmail" → HTML içerisindeki elementin kimliği

    name="email" → Form gönderildiğinde verinin adı
```

# Kısaca Özet
HTML formları yalnızca birkaç input'u yan yana koymaktan ibaret değildir.

Doğru bir form yapısında:
- `<form>` formu kapsar.
- `<label>` alanların ne olduğunu açıklar.
- `<input>` kullanıcıdan veri alır.
- `type` doğru veri türünü belirtir.
- `name` gönderilecek verinin adını belirler.
- `id` ve `for` label-input ilişkisini kurabilir.
- `required`, `min`, `max`, `minlength` gibi özelliklerle temel HTML doğrulaması yapılabilir.
- `<select>` seçenek listeleri oluşturur.
- `<textarea>` uzun metinleri alır.
- Checkbox birden fazla seçim için kullanılabilir.
- Aynı `name` grubundaki radio butonlar tek seçim yapılmasını sağlar.
- `<fieldset>` ve `<legend>` ilişkili alanları anlamlı şekilde gruplandırır.
- `action` ve `method` formun gönderim davranışını belirler.

Formlarda öğrenmemiz gereken temel prensip ise şudur:

`Kullanıcıdan hangi bilgiyi istediğimizi doğru HTML elementiyle ifade etmeli, alanların anlamını açıkça belirtmeli ve gönderilecek verinin yapısını doğru tanımlamalıyız.`

Böylece yalnızca çalışan değil; **anlaşılır, erişilebilir ve bakımı daha kolay formlar** oluşturabiliriz.