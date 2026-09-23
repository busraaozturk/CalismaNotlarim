# HTML Etkileşimli ve Yardımcı Elementler
HTML yalnızca başlık, paragraf, bağlantı veya form alanları oluşturmaktan ibaret değildir.

Tarayıcının kendi davranışlarından yararlanarak bazı etkileşimleri ve durumları doğrudan HTML elementleriyle oluşturabiliriz.

Bu konuda özellikle şu elementleri inceleyeceğiz:
- <details>
- <summary>
- <dialog>
- <progress>
- <meter>
- <output>

Bu elementlerin ortak noktası, normal bir `<div>` kullanmaktan daha **anlamlı ve amaca uygun HTML yapıları** sunmalarıdır.

## `<details>` Elementi
`<details>`, kullanıcının açıp kapatabileceği bir içerik alanı oluşturmak için kullanılır. Örneğin;
```
    <details> 
        <summary>Kargo ve Teslimat</summary> 
        <p> Siparişiniz 2-4 iş günü içerisinde kargoya verilir. </p> 
    </details>
```
Tarayıcı burada temel açma/kapatma davranışını kendisi sağlar. Kullanıcı `<summary>` alanına tıkladığında içerik açılır.

Mantık:
```
    Kargo ve Teslimat
            |
          Tıkla
            |
    İçerik açılır / kapanır
```

Bunun için temel kullanımda ayrıca JavaScript yazmamız gerekmez.

### Nerelerde Kullanılabilir?
- Sıkça sorulan sorular
- Ürün detayları
- Teknik özellikler
- İade koşulları
- Açıklama alanları
gibi açılıp kapanabilen içeriklerde kullanılabilir.

## `<summary>` Elementi
`<summary>`, `<details>` elementinin görünen başlığını veya özetini oluşturur.

Örneğin:
```
    <details> 
        <summary>Ürün Özellikleri</summary> 
        <p>Paslanmaz çelik kasa.</p> 
        <p>Suya dayanıklı tasarım.</p> 
    </details>
```

Burada:
```
    <details> 
    │ 
    ├── <summary> 
    │       └── Kullanıcının gördüğü ve etkileşime girdiği başlık 
    │       
    └── İçerik 
            └── Açıldığında gösterilen bölüm
```
şeklinde düşünebiliriz.

`<summary>`, `<details>` yapısının kontrolüdür. Bu nedenle açılır alanın başlığı için ayrıca bir `<button>` oluşturmamız gerekir.

## `<open>` Attribute'u
Bir `<details>` alanı varsayılan olarak kapalıdır.
```
    <details>
        <summary>Ürün Açıklaması</summary>

        <p>Ürün açıklaması...</p>
    </details>
```
Sayfa ilk açıldığında içeriğin açık olmasını istiyorsak `open` kullanılabilir.
```
    <details open>
        <summary>Ürün Açıklaması</summary>

        <p>Ürün açıklaması...</p>
    </details>
```
open bir **boolean attribute**'dur.

Yani `<details open>` kullanımı yeterlidir.

## `<dialog>` Elementi
`<dialog>`, dialog veya modal benzeri arayüzler oluşturmak için kullanılan HTML elementidir.

Temel yapı:
```
    <dialog>
        <h2>Ürünü Sil</h2>

        <p>
            Bu ürünü silmek istediğinizden emin misiniz?
        </p>

        <button type="button">
            İptal
        </button>

        <button type="button">
            Sil
        </button>
    </dialog>
```
Ancak yalnızca `<dialog>` yazılması dialog'un otomatik olarak açılacağı anlamına gelmez. Dialog genellikle JavaScript ile kontrol edilir.

## Dialog Açma
Bir dialog JavaScript tarafında, `sialog.show();` veya `dialog.showModal();` ile açılabilir.

Örneğin:
```
    <button id="open-dialog" type="button"> Ürünü Sil </button> 
    
    <dialog id="delete-dialog"> 
        <h2>Ürünü Sil</h2> 
        <p> Bu ürünü silmek istediğinizden emin misiniz? </p> 
        <button id="close-dialog" type="button"> İptal </button> 
    </dialog>
```

JavaScript:
```
    const dialog = document.getElementById("delete-dialog"); 
    const openButton = document.getElementById("open-dialog"); 
    const closeButton = document.getElementById("close-dialog"); 

    openButton.addEventListener("click", () => { 
        dialog.showModal(); 
    }); 

    closeButton.addEventListener("click", () => { 
        dialog.close(); 
    });
```

Buradaki akış:
```
    Butona tıkla 
        ↓ 
    showModal() 
        ↓ 
    Dialog açılır 
        ↓ 
    close() 
        ↓ 
    Dialog kapanır
```

## `show()` ve `showModal()` Farkı
İki yöntem aynı değildir.

### `show()` 
Dialog'u modal olmayan şekilde açar. Bu durumda kullanıcı sayfanın diğer bölümleriyle etkileşime devam edebilir.
```
    dialog.show();
```

### `showModal()`
Dialog'u modal olarak açar.
```
    dialog.showModal();
```

Modal açıkken kullanıcıdan öncelikle bu dialog ile etkileşime girmesi beklenir ve belgenin geri kalanı modal etkileşimin dışında kalır.

Örneğin önemli bir silme onayı için bu daha uygun olabilir: `deleteDialog.showModal();`

## Dialog Kapatma
Dialog `dialog.close();` ile kapatılabilir.

Ayrıca dialog içerisinde `method=dialog` kullanılan bir form bulunabilir.
```
    <dialog id="confirm-dialog"> 
        <form method="dialog"> 
            <p> İşleme devam etmek istiyor musunuz? </p> 
            <button value="cancel"> İptal </button> 
            <button value="confirm"> Devam Et </button> 
        </form> 
    </dialog>
```
Bu yapı dialog içindeki kullanıcı seçimini yönetirken kullanılabilir. Buradaki `method="dialog"` normal bir sunucuya form gönderme işlemiyle aynı amaçta değildir; dialog etkileşimini tamamlayıp dialog'u kapatmak için kullanılır.

## `<progress>` Elementi
`<progress>`, bir işlemin ne kadarının tamamlandığını göstermek için kullanılır.

Örneğin: `<progress value="70" max="100"> %70 </progress>`
Burada `value=70`, `max=100` olduğu için işlem `%70 tamamlandı` anlamına gelir.

Örneğin:
```
    <label for="upload-progress"> Dosya yükleniyor: </label> 
    
    <progress id="upload-progress" value="65" max="100" > %65 </progress>
```

## Belirsiz İlerleme Durumu
Her zaman işlemin ne kadar süreceğini bilmiyor olabiliriz. Bu durumda `value` belirtilmeden kullaılabilir.

`<progress>İşlem devam ediyor...</progress>`

Bu kullanım, işlemin devam ettiğini fakat tamamlanma oranının bilinmediğini ifade eder.

Örneğin:
```
    Dosya yükleniyor.

    Ne kadar tamamlandı? → Henüz bilinmiyor.
```

## `<meter>` Elementi
`<meter>`, belirli bir aralık içerisindeki **ölçüm değerini** göstermek için kullanılır.

Örneğin:
```
    <meter min="0" max="100" value="75" > 75 </meter>

    Burada değer aşağıda şekildeki gibi düşünülebilir
    0 ─────────────────────── 100
                     ▲ 75
```

Örneğin:
```
    <label for="storage"> Depolama Kullanımı </label> 
    <meter id="storage" min="0" max="100" value="65" > %65 </meter>
```

`<meter>` özellikle bilinen bir aralık içerisindeki değeri ifade eder.

## `<meter>` İçin Ek Değerler
`<meter>` yalnızca `min`, `max` ve `value` ile sınırlı değildir.

Şu attribute'lar da kullanılabilir:
```
    low
    high
    optimum
```

Örneğin:
```
    <meter 
        min="0" 
        max="100" 
        low="30" 
        high="80" 
        optimum="50" 
        value="65" > 
        65 
    </meter>
```

Bunların temel görevleri:
- `min` → minimum değer
- `max` → maksimum değer
- `value` → mevcut değer
- `low` → düşük aralığın sınırı
- `high` → yüksek aralığın sınırı
- `optimum` → ideal kabul edilen değer
şeklinde düşünülebilir.

Bu değerlerin görsel olarak nasıl gösterileceği tarayıcıya göre değişebilir. Bu nedenle yalnızca elementin rengine veya varsayılan görünümüne güvenerek kullanıcıya anlam aktarmamak gerekir. 

## `<progress>` ve `<meter>` Farkı

### `<progress>`
Bir **işlemin ilerlemesini** gösterir.
```
    <progress value="60" max="100">
        %60
    </progress>

    Dosya Yükleme %60
```

### `<meter>`
Bir **ölçümün belirli bir aralıktaki mevcut değerini** gösterir.
```
    <meter min="0" max="100" value="60"> 60 </meter>

    Depolama kullanımı %60
```

Görsel olarak benzeseler bile anlamları farklıdır.
```
    İşlem devam ediyor mu?
            ↓
        <progress>

    Bir değer ölçülüyor mu?
            ↓
        <meter>
```

Örneğin:
```
    Dosya yükleme ilerlemesi → progress
    Kurulum ilerlemesi → progress
    Depolama kullanım oranı → meter
    Bir sınavdaki mevcut puanın belirli bir aralıktaki konumu → meter
```

## `<output>` Elementi
`<output>`, bir kullanıcı işlemi veya hesaplama sonucunda oluşan değeri temsil etmek için kullanılır.+-

Örneğin basit bir hesaplama düşünelim:
```
    5 + 10 = 15
             ↑
            sonuç
```
Bu sonuç `<output>` ile gösterilebilir.

```
    <form oninput="result.value = Number(first.value) + Number(second.value)" > 
        <input id="first" name="first" type="number" value="5" > 
        + 
        <input id="second" name="second" type="number" value="10" > 
        = 
        <output name="result" for="first second" > 15 </output> 
    </form>
```

Buradaki `<output>`:
```
    <output
        name="result"
        for="first second"
    >
        15
    </output>
```
hesaplamanın sonucunu temsil eder.

`for` attribute'u ise sonucun hangi alanlarla ilişkili olduğunu belirtmek için kullanılabilir.

Örnekteki inline JavaScript yalnızca `<output>` elementinin çalışma mantığını göstermek içindir. JavaScript'i düzenli şekilde HTML'e bağlama ve olay yönetimi JavaScript bölümünde ayrıca ele alınmalıdır.

## Neden Her Yerde <div> Kullanmıyoruz?
Teknik olarak birçok arayüzü `<div>` kullanarak oluşturabiliriz.

Örneğin:
```
    <div class="progress">
        ...
    </div>
```
Ancak HTML zaten belirli bir anlamı ifade eden element sunuyorsa onu kullanmak çoğu durumda daha doğru başlangıç noktasıdır.

Örneğin:
```
    <progress value="50" max="100">
        %50
    </progress>
```
HTML seviyesinde bunun bir ilerleme göstergesi olduğunu açıkça ifade eder.

Aynı mantık:
```
    <details>
    <dialog>
    <meter>
    <output>
```
için de geçerlidir.

Bu yaklaşım daha önce incelediğimiz **Semantic HTML** mantığının devamıdır.

## Bu Elementlerde Erişilebilirlik
Erişilebilirliğin genel kurallarını daha önce HTML Accessibility (A11y) konusunda inceledik. Bu nedenle burada yalnızca bu elementlerle ilgili temel noktaları hatırlamak yeterlidir.

### `<details>` / `<summary>`
`<summary>` açma-kapatma kontrolünü zaten sağladığı için bunu gereksiz yere başka etkileşimli elementlerle yeniden oluşturmamak gerekir.

### `<dialog>`
Modal açma ve kapatma kontrolünü zaten sağladığı için bunu gereksiz yere başka etkileşimli elementlerle yeniden oluşturmamak gerekir.

Native `<dialog>` kullanmak bu konuda tarayıcının sunduğu davranışlardan yararlanmayı sağlar; ancak oluşturduğumuz dialog'un içeriği ve kullanıcı akışı yine doğru tasarlanmalıdır.

### `<progress>` ve `<meter>`
Kullanıcının değeri anlayabilmesi için gerektiğinde açıklayıcı metin veya label ile birlikte kullanılabilir.

Örneğin:
```
    <label for="storage"> Depolama kullanımı </label> 
    
    <meter id="storage" min="0" max="100" value="65" > 65% </meter>
```
Erişilebilirliğin genel kurallarını burada tekrar etmiyoruz.

## Sık Yapılan Hatalar
Bu elementlerde dikkat edilmesi gereken temel hatalar şunlardır:
- `<details>` varken basit açılır içerikleri gereksiz `<div>` yapılarıyla oluşturmak.
- `<summary>` elementini `<details>` yapısından bağımsız düşünmek.
- `<dialog>` elementinin yalnızca HTML'e eklenmesiyle otomatik açılacağını düşünmek.
- `show()` ve `showModal()` arasındaki farkı göz ardı etmek.
- Her yüzde değerini `<progress>` ile göstermek.
- Ölçüm değerleri için `<progress>` kullanmak.
- İşlem ilerlemesini `<meter>` ile göstermek.
- `<meter>` değerlerinin varsayılan görsel rengine tek başına anlam yüklemek.
- `<output>` elementini sıradan her metin çıktısı için kullanmak.
- Semantik bir HTML elementi varken her yapıyı `<div>` ile oluşturmaya çalışmak

## Hangi Elementi Ne Zaman Kullanmalıyım?
| İhtiyaç       | Element       |
|---------------|---------------|
|Açılır/kapanır içerik| `<details>` + `<summary>`|
|Dialog/modal   | `<dialog>`|
|İşlem ilerlemesi|`<progress>`|
|Belirli aralıktaki ölçüm|`<meter>`|
|Hesaplama veya işlem sonucu|`<output>`|

Bunu basitçe şöyle düşünebiliriz:
```
    İhtiyacım ne?
    │
    ├── İçerik açılıp kapanacak
    │      └── details + summary
    │
    ├── Kullanıcının karşısına dialog açılacak
    │      └── dialog
    │
    ├── Bir işlem ne kadar tamamlandı?
    │      └── progress
    │
    ├── Bir değer hangi seviyede?
    │      └── meter
    │
    └── Bir işlemin sonucu gösterilecek
        └── output
```

## Genel Örnek
Bir ürün sayfasında bu elementlerden birkaçını birlikte kullanabiliriz:
```
    <section>

        <h1>Akıllı Saat</h1>

        <details>
            <summary>Teknik Özellikler</summary>

            <ul>
                <li>Paslanmaz çelik kasa</li>
                <li>Suya dayanıklı</li>
                <li>Bluetooth bağlantısı</li>
            </ul>
        </details>

        <details>
            <summary>Teslimat ve İade</summary>

            <p>
                Siparişiniz 2-4 iş günü içerisinde
                kargoya verilir.
            </p>
        </details>

        <p>
            Depolama kullanımı:
        </p>

        <meter
            min="0"
            max="100"
            value="65"
        >
            %65
        </meter>

        <button
            id="delete-button"
            type="button"
        >
            Ürünü Sil
        </button>

        <dialog id="delete-dialog">

            <form method="dialog">

                <h2>Ürünü Sil</h2>

                <p>
                    Bu ürünü silmek istediğinizden
                    emin misiniz?
                </p>

                <button value="cancel">
                    İptal
                </button>

                <button value="confirm">
                    Sil
                </button>

            </form>

        </dialog>

    </section>
```
Dialog'u açmak için:
```
    const dialog =
        document.getElementById("delete-dialog");

    const deleteButton =
        document.getElementById("delete-button");

    deleteButton.addEventListener("click", () => {
        dialog.showModal();
    });
```

## Kontrol Listesi
Bu elementleri kullanırken:
- Açılır içerik için `<details>` ve `<summary>` uygun mu?
- İçeriğin başlangıçta açık olması gerekiyorsa `open` kullanıldı mı?
- Dialog için native `<dialog>` değerlendirildi mi?
- Modal gerekiyorsa `showModal()` kullanılıyor mu?
- İşlem ilerlemesi için `<progress>` kullanılıyor mu?
- Ölçüm değeri için `<meter>` kullanılıyor mu?
- `<progress>` ve `<meter>` birbirine karıştırılıyor mu?
- Hesaplama veya işlem sonucu için `<output>` uygun mu?
- Native HTML elementi varken gereksiz `<div>` tabanlı çözüm oluşturuluyor mu?
- Kullanıcı elementin ne ifade ettiğini yalnızca görsel görünümünden değil, içerikten de anlayabiliyor mu?

## Kısaca Özet
HTML'in etkileşimli ve yardımcı elementleri bazı yaygın arayüz ihtiyaçlarını daha anlamlı HTML ile çözmemizi sağlar.
```
    <details> + <summary> → Açılır / kapanır içerik
    <dialog> → Dialog / modal
    <progress> → İşlem ilerlemesi
    <meter> → Aralık içerisindeki ölçüm
    <output> → İşlem / hesaplama sonucu
```
Buradaki temel amaç bu elementlerin tamamını ezberlemek değildir. Önemli olan:
`HTML belirli bir ihtiyacı karşılayan semantik/native bir element sunuyorsa, her şeyi ``<div>`` ve JavaScript ile sıfırdan oluşturmadan önce o elementi değerlendirmektir.`