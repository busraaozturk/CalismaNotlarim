# HTML'e JavaScript Eklemek
**00_HTMLTemelleri** bölümünde JavaScript'in bir HTML belgesine `<script>` etiketiyle eklendiğini ve bu etiketin genellikle `</body>` kapanış etiketinden hemen önce yazıldığını görmüştük.

Bu bölümde ise şu sorulara cevap arayacağız:
- `<script>` etiketinin yeri neden önemlidir?
- Tarayıcı bir script ile karşılaştığında ne yapar?
- `defer` ve `async` ne işe yarar, aralarındaki fark nedir?
- `type="module"` neyi değiştirir?
- JavaScript kapalıysa ne olur?

```
    HTML'e JavaScript Eklemek
    │
    ├── 1. <script> Elementi
    │   ├── Harici script
    │   └── Belge içi (inline) script
    │
    ├── 2. Tarayıcı Script'i Nasıl İşler?
    │   └── Parser-blocking kavramı
    │
    ├── 3. Script'in Yeri
    │
    ├── 4. defer
    │
    ├── 5. async
    │
    ├── 6. defer ve async Farkı
    │
    ├── 7. type="module"
    │
    ├── 8. <noscript>
    │
    └── 9. Inline Event Handler'lar
```

## 1. `<script>` Elementi
JavaScript kodu HTML belgesine `<script>` elementiyle eklenir. İki temel kullanımı vardır.

**- Harici Script**
```
    <script src="app.js"></script>
```
JavaScript kodu ayrı bir `.js` dosyasında tutulur ve `src` attribute'uyla bağlanır.

**- Belge İçi (Inline) Script**
```
    <script>
        console.log("Sayfa yüklendi.");
    </script>
```
Kod doğrudan `<script>` etiketinin içerisine yazılır.

Büyük projelerde harici dosya kullanmak tercih edilir. Çünkü:
- Kod HTML'den ayrı tutulur,
- Aynı dosya birden fazla sayfada kullanılabilir,
- Tarayıcı dosyayı önbelleğe (cache) alabilir.

**- `<script>` Bir Void Element Değildir**

`<script>` elementinin kapanış etiketi **zorunludur.** `src` kullanıldığında içerik boş olsa bile `</script>` yazılmalıdır.
```
    Yanlış:
    <script src="app.js" />

    Doğru:
    <script src="app.js"></script>
```
`<script src="app.js" />` yazımında tarayıcı `/` karakterini yok sayar ve bunu kapanmamış bir açılış etiketi olarak algılar. Bu durumda sonraki HTML içeriği script'in içeriği gibi okunabilir.

**- `src` ve İçerik Birlikte Kullanılmaz**
```
    <script src="app.js">
        console.log("Bu kod çalışmaz.");
    </script>
```
`src` attribute'u bulunan bir `<script>` elementinin içerisine yazılan kod **çalıştırılmaz.** Tarayıcı yalnızca harici dosyayı kullanır.

## 2. Tarayıcı Script'i Nasıl İşler?
**00_HTMLTemelleri** bölümünde tarayıcının HTML kodunu yukarıdan aşağıya okuyarak (parse ederek) DOM ağacı oluşturduğunu görmüştük.

Tarayıcı bu okuma sırasında `defer` veya `async` içermeyen normal bir `<script>` ile karşılaştığında:
```
    HTML okunuyor
    ↓
    <script src="app.js"> ile karşılaşıldı
    ↓
    HTML okuması DURUR
    ↓
    app.js indirilir
    ↓
    app.js çalıştırılır
    ↓
    HTML okuması kaldığı yerden devam eder
```
Bu davranışa **parser-blocking**, yani **HTML ayrıştırmasını engelleyen script** denir.

**Neden Böyle Çalışır?**

JavaScript, sayfanın DOM yapısını değiştirebilir. Tarayıcı, script'in sayfaya ne ekleyeceğini veya neyi değiştireceğini bilmeden HTML okumaya devam ederse yanlış bir yapı oluşturabilir. Bu nedenle varsayılan olarak önce script'in çalışmasını bekler.

**Bu Neden Sorun Olabilir?**

Script dosyası büyükse veya yavaş bir bağlantıyla indiriliyorsa:
- Sayfanın görünür içeriği gecikir,
- Kullanıcı bir süre boş veya yarım bir sayfa görür.

## 3. Script'in Yeri
**- `<head>` İçerisinde Normal Script**
```
    <head>
        <script src="app.js"></script>
    </head>

    <body>
        <button id="cartButton">Sepete Ekle</button>
    </body>
```
`app.js` içerisinde:
```
    const button = document.getElementById("cartButton");
    button.addEventListener("click", addToCart);
```
yazılmış olsun.

Burada iki sorun oluşur:
1. Script çalışırken HTML okuması durduğu için sayfa içeriği gecikir.
2. Script çalıştığı anda `<body>` henüz okunmamıştır. `cartButton` DOM'da bulunmadığı için `button` değişkeni `null` olur ve kod hata verir.

**- `</body>` Öncesinde Normal Script**
```
    <body>
        <button id="cartButton">Sepete Ekle</button>

        <script src="app.js"></script>
    </body>
```
Bu kullanımda script çalıştığında sayfa içeriği zaten okunmuştur. Bu yüzden uzun süre yaygın bir yöntem olarak kullanılmıştır.

Ancak tarayıcı script dosyasının varlığını ancak HTML'in sonuna geldiğinde fark eder ve indirmeye o zaman başlar.

Modern yaklaşımda bu iki sorunun ikisini de çözen `defer` attribute'u tercih edilir.

## 4. `defer`
`defer`, Türkçede **ertelemek** anlamına gelir.
```
    <head>
        <script src="app.js" defer></script>
    </head>
```
`defer` kullanıldığında:
```
    HTML okunuyor ──────────────────────────→ HTML okuması bitti
         │                                            │
         └── app.js arka planda indiriliyor           ↓
                                               app.js çalıştırılır
```
Burada:
- Script, HTML okunurken **paralel olarak indirilir.**
- HTML okuması **durmaz.**
- Script, HTML'in tamamı okunduktan **sonra** çalıştırılır.
- Birden fazla `defer` script varsa **HTML'de yazıldıkları sırayla** çalıştırılır.

Örneğin:
```
    <script src="library.js" defer></script>
    <script src="app.js" defer></script>
```
`app.js` dosyası daha önce inse bile önce `library.js` çalıştırılır. Bu nedenle birbirine bağımlı script'lerde güvenle kullanılabilir.

**- `defer` ve `DOMContentLoaded`**

Tarayıcı HTML'i okumayı bitirip DOM ağacını oluşturduğunda `DOMContentLoaded` adlı bir olay (event) tetiklenir. `defer` script'ler bu olaydan **hemen önce** çalışır. Yani `defer` ile çalışan bir script'te sayfanın bütün elementlerine erişilebilir.

**- `defer` Yalnızca Harici Script'lerde Çalışır**
```
    <script defer>
        console.log("defer burada etkisizdir.");
    </script>
```
`src` attribute'u olmayan klasik bir inline script'e `defer` eklemek bir şey değiştirmez.

**Temel öneri:** Sayfanın DOM'u ile çalışan script'ler için `<head>` içerisinde `defer` kullanmak modern ve güvenli bir yaklaşımdır.

## 5. `async`
`async`, **asynchronous**, yani **eşzamansız** kelimesinin kısaltmasıdır.
```
    <script src="analytics.js" async></script>
```
`async` kullanıldığında:
```
    HTML okunuyor ─────────┐ DURUR ┌───────────→ HTML okuması devam eder
         │                 │       │
         └── analytics.js  │ çalış │
             indiriliyor ──┘       │
```
Burada:
- Script, HTML okunurken **paralel olarak indirilir.**
- İndirme biter bitmez **hemen çalıştırılır.**
- Script çalışırken HTML okuması **kısa süreliğine durur.**
- Birden fazla `async` script varsa **hangisinin önce çalışacağı garanti değildir.** Hangisi önce inerse o çalışır.

Bu yüzden `async`:
- Sayfanın diğer kodlarına bağımlı olmayan,
- Sayfadaki elementlerin hazır olmasını beklemeyen,
- Çalışma sırası önemli olmayan

script'ler için uygundur. Analitik, reklam veya ölçüm script'leri buna örnek verilebilir.

**- `async` ile Sık Yapılan Hata**
```
    <script src="library.js" async></script>
    <script src="app.js" async></script>
```
`app.js`, `library.js` içerisindeki bir fonksiyonu kullanıyorsa bu yapı **bazen çalışır, bazen hata verir.** Çünkü hangi dosyanın önce ineceği bağlantıya göre değişebilir. Sıranın önemli olduğu durumlarda `defer` kullanılmalıdır.

## 6. `defer` ve `async` Farkı
```
    Normal script
    HTML ████████░░░░░░░░░░░░████████
    JS           ▓▓▓▓▓▓ ▒▒▒▒▒
                 indir  çalıştır
    → HTML okuması script inip çalışana kadar bekler.

    defer
    HTML ████████████████████████████
    JS       ▓▓▓▓▓▓                  ▒▒▒▒▒
             indir                   çalıştır
    → HTML hiç beklemez, script en sonda çalışır.

    async
    HTML ████████████░░░░░███████████
    JS       ▓▓▓▓▓▓ ▒▒▒▒▒
             indir  çalıştır
    → HTML yalnızca script çalışırken bekler.
```

| Özellik                        | Normal         | `defer`            | `async`             |
|--------------------------------|----------------|--------------------|---------------------|
| İndirme sırasında HTML durur mu? | Evet         | Hayır              | Hayır               |
| Ne zaman çalışır?              | İndirilince hemen | HTML okunduktan sonra | İndirilince hemen |
| Çalışma sırası korunur mu?     | Evet           | Evet               | Hayır               |
| DOM hazır mı?                  | Script'in yerine bağlı | Evet       | Garanti değil       |
| Uygun kullanım                 | -              | Sayfa script'leri  | Bağımsız script'ler |

Karar vermek için basit bir yol:
```
    Script sayfadaki elementlerle çalışıyor mu
    veya başka bir script'e bağımlı mı?
        │
        ├── Evet → defer
        │
        └── Hayır, tamamen bağımsız → async
```

## 7. `type="module"`
Modern JavaScript'te kodu `import` ve `export` ile birden fazla dosyaya bölebiliriz. Bu yapıdaki bir dosyayı HTML'e eklemek için `type="module"` kullanılır.
```
    <script type="module" src="main.js"></script>
```
`main.js` içerisinde:
```
    import { formatPrice } from "./utils.js";

    console.log(formatPrice(1500));
```

Module script'lerin normal script'lerden farkları:
- **Varsayılan olarak `defer` gibi davranırlar.** Ayrıca `defer` yazmaya gerek yoktur.
- İsteğe bağlı olarak `async` eklenebilir.
- `import` ve `export` kullanılabilir.
- Dosyada tanımlanan değişkenler **global değildir**; yalnızca o modül içerisinde geçerlidir.
- Otomatik olarak **strict mode** ile çalışırlar.
- Aynı modül sayfada birden fazla kez eklense bile **bir kez** çalıştırılır.

**- Dikkat: Dosyayı Doğrudan Açmak**

Module script'ler, HTML dosyasını tarayıcıda çift tıklayarak (`file://` adresiyle) açtığımızda çoğu tarayıcıda **çalışmaz.** Güvenlik kuralları nedeniyle sayfanın bir sunucu üzerinden açılması gerekir. Geliştirme sırasında VS Code'un Live Server eklentisi veya Vite gibi bir geliştirme sunucusu kullanılabilir.

**- `type="application/ld+json"` Bir Script Çalıştırmaz**

`<script>` elementi yalnızca JavaScript için kullanılmaz. **17_StructuredData** bölümünde gördüğümüz:
```
    <script type="application/ld+json">
        { "@context": "https://schema.org", ... }
    </script>
```
yapısında tarayıcı içeriği **çalıştırmaz**; yalnızca veri olarak tutar. `type` değeri tarayıcının içeriği nasıl ele alacağını belirler.

## 8. `<noscript>`
`<noscript>`, kullanıcının tarayıcısında JavaScript **kapalıysa veya desteklenmiyorsa** gösterilecek içeriği tanımlar.
```
    <noscript>
        <p>
            Bu sayfanın düzgün çalışabilmesi için JavaScript'i etkinleştirmeniz gerekir.
        </p>
    </noscript>
```
JavaScript açıksa `<noscript>` içeriği görünmez.

Ancak asıl hedef, `<noscript>` ile uyarı göstermekten çok **sayfanın temel içeriğinin JavaScript olmadan da erişilebilir olmasıdır.** Örneğin bir ürün listesi, bir makale veya iletişim bilgileri JavaScript yüklenemediğinde de görünebilmelidir. Bu yaklaşıma **progressive enhancement**, yani **aşamalı geliştirme** denir:
```
    HTML → Temel içerik herkes için çalışır.
    CSS → Görünüm iyileştirilir.
    JavaScript → Etkileşim eklenir.
```

## 9. Inline Event Handler'lar
HTML elementlerine doğrudan JavaScript kodu yazılabildiğini görebiliriz:
```
    <button onclick="addToCart()">Sepete Ekle</button>
```
Bu kullanım çalışsa da genellikle tercih edilmez. Çünkü:
- HTML ve JavaScript birbirine karışır,
- Aynı davranışı birden fazla yerde tekrarlamak gerekir,
- Kodun yönetilmesi ve test edilmesi zorlaşır,
- **11_HTMLEmbeddedContent** bölümünde gördüğümüz **CSP (Content Security Policy)** kullanan sitelerde inline kodlar varsayılan olarak engellenir.

Bunun yerine HTML yalnızca yapıyı tanımlar, davranış JavaScript dosyasında eklenir:
```
    <button id="cartButton">Sepete Ekle</button>
```
```
    const button = document.getElementById("cartButton");

    button.addEventListener("click", addToCart);
```
Bu, **00_HTMLTemelleri** bölümünde gördüğümüz görev dağılımının bir uygulamasıdır:
```
    HTML → Bu bir buton.
    JavaScript → Butona basıldığında bunu yap.
```

**Not:** React ve Next.js'teki `onClick={addToCart}` yazımı HTML'deki `onclick` attribute'u değildir. JSX içerisinde yazılan bu yapı React tarafından olay dinleyicisine dönüştürülür.

## Sık Yapılan Hatalar
**1. `<head>` İçerisinde `defer` Olmadan DOM'a Erişmeye Çalışmak**
```
    <head>
        <script src="app.js"></script>
    </head>
```
Script çalıştığında elementler henüz oluşmadığı için `document.getElementById(...)` gibi seçimler `null` döner. Çözüm: `defer` kullanmak.

**2. Birbirine Bağımlı Script'lerde `async` Kullanmak**

`async` çalışma sırasını garanti etmez. Sıranın önemli olduğu yerlerde `defer` kullanılmalıdır.

**3. `<script>` Etiketini `/>` ile Kapatmak**
```
    Yanlış: <script src="app.js" />
    Doğru:  <script src="app.js"></script>
```

**4. `src` Olan Script'in İçerisine Kod Yazmak**

İçerideki kod çalıştırılmaz.

**5. Inline Script'e `defer` Eklemek**

`defer` yalnızca `src` ile eklenen klasik script'lerde etkilidir.

**6. Module Script'i Sunucu Olmadan Açmaya Çalışmak**

`type="module"` kullanan sayfalar `file://` ile açıldığında çalışmayabilir.

**7. Her Davranışı `onclick` Gibi Inline Attribute'larla Yazmak**

Davranışlar JavaScript dosyasında `addEventListener` ile eklenmelidir.

## Kısaca Özet
```
    <script src="app.js"></script>
    → Parser-blocking. HTML okuması script inip çalışana kadar durur.

    <script src="app.js" defer></script>
    → Paralel indirilir, HTML okunduktan sonra yazılış sırasıyla çalışır.

    <script src="analytics.js" async></script>
    → Paralel indirilir, inince hemen çalışır, sıra garanti değildir.

    <script type="module" src="main.js"></script>
    → import/export kullanılabilir, varsayılan olarak defer gibi davranır.

    <noscript>...</noscript>
    → JavaScript kapalıyken gösterilecek içerik.
```

Modern bir sayfada temel yapı şu şekilde olabilir:
```
    <!DOCTYPE html>
    <html lang="tr">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Ürünler</title>

        <link rel="stylesheet" href="style.css">

        <script src="app.js" defer></script>
        <script src="analytics.js" async></script>
    </head>

    <body>
        <h1>Ürünler</h1>

        <button id="cartButton">Sepete Ekle</button>

        <noscript>
            <p>Sepet işlemleri için JavaScript'i etkinleştirmeniz gerekir.</p>
        </noscript>
    </body>
    </html>
```

Bu bölümden çıkarmamız gereken temel fikir:

`<script> etiketinin nereye ve hangi attribute ile yazıldığı, sayfanın ne kadar hızlı göründüğünü ve JavaScript kodunun sayfadaki elementlere erişip erişemeyeceğini doğrudan etkiler.`
