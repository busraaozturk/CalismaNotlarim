# HTML Embedded Content - Harici İçerik Gömme
Bir web sayfasında her içerik doğrudan kendi HTML dosyamızın içerisinde bulunmak zorunda değildir. Başka bir kaynaktan gelen içerikleri de sayfamızın içerisinde gösterebiliriz.

Örneğin:
- Youtube videosu
- Google Maps haritası
- Başka bir web sayfası
- Harici bir uygulama veya widget

gibi içerikler sayfaya **gömülebilir (embed).**

HTML'de bu amaçla karşılaşabileceğimiz başlıca elementler:
```
    <iframe>
    <embed>
    <object>
```
şeklindedir.

Modern web geliştirmede bunların arasında en sık karşılaşacağımız element `<iframe>`'dir.

## `<iframe>` Nedir?
`<iframe> yani Inline Frame`, mevcut HTML sayfasının içerisinde başka bir HTML belgesi veya harici web içeriği göstermek için kullanılır.

Temel kullanım: `<iframe src="https://example.com"></iframe>`

Mantığını şöyle düşünebiliriz:
```
    Bizim Web Sayfamız
    │
    ├── Header
    │
    ├── Main
    │   │
    │   ├── İçeriklerimiz
    │   │
    │   └── <iframe>
    │       │
    │       └── Harici içerik
    │
    └── Footer
```
Yani iframe'in içerisindeki belge, ana sayfamızdan ayrı bir belge olarak yüklenir.

## Temel <iframe> Kullanımı
Örneğin:
```
    <iframe
        src="https://example.com"
        title="Örnek web sitesi"
    >
    </iframe>
```
Burada:
```
    iframe
    │
    ├── src
    │   └── Gösterilecek içeriğin adresi
    │
    └── title
        └── İçeriğin ne olduğunu açıklar
```
`src`, iframe içerisinde hangi kaynağın gösterileceğini belirtir.

## `title` Kullanımı
Iframe kullanırken içeriğin ne olduğunu açıklayan bir `title` değeri verilmelidir.

Örneğin:
```
    <iframe
        src="..."
        title="Mağaza konum haritası"
    >
    </iframe>
```
veya:
```
    <iframe
        src="..."
        title="Ürün tanıtım videosu"
    >
    </iframe>
```
Bunun yerine:
```
    <iframe
        src="..."
        title="iframe"
    >
    </iframe>
```
gibi içeriği açıklamayan bir ifade kullanmak anlamlı değildir.

`title`, özellikle yardımcı teknolojilerin iframe'in ne içerdiğini anlayabilmesine yardımcı olur.

## YouTube Videosu Gömme

<iframe> kullanımının en yaygın örneklerinden biri YouTube videolarıdır.

Temel olarak şöyle bir yapı ile karşılaşabiliriz:

<iframe
    src="https://www.youtube.com/embed/VIDEO_ID"
    title="Ürün tanıtım videosu"
    allowfullscreen
>
</iframe>

Burada önemli bir ayrım vardır.

Normal video adresi ile gömme adresi aynı olmak zorunda değildir.

Örneğin kullanıcıların tarayıcıda açtığı normal video bağlantısı yerine servis tarafından sağlanan **embed URL** kullanılır.

Bu nedenle YouTube gibi servislerde genellikle platformun sunduğu **Embed / Gömme** kodunun kullanılması daha doğru olur.

## Google Maps Haritası Gömme

Bir başka yaygın kullanım Google Maps gibi harita servisleridir. Örneğin yapı genel olarak şöyle görünebilir:
```
    <iframe
        src="HARITA_EMBED_URL"
        title="Mağaza konumu"
    >
    </iframe>
```
Burada da normal harita bağlantısını doğrudan kullanmak yerine servis tarafından sağlanan gömme adresi kullanılır. Mantık yine aynıdır:
```
    Harici servis
        ↓
    Embed URL
        ↓
    <iframe>
        ↓
    Bizim sayfamız
```

## `width` ve `height`
Iframe'in genişliği ve yüksekliği belirtilebilir.
```
    <iframe
        src="..."
        title="Tanıtım videosu"
        width="560"
        height="315"
    >
    </iframe>
```
Ancak günümüzde responsive tasarımlarda iframe boyutlarının yalnızca sabit HTML değerlerine bırakılması her ekran için yeterli olmayabilir.

Örneğin CSS ile:
```
    iframe {
        max-width: 100%;
    }
```
gibi düzenlemeler yapılabilir.

Video gibi belirli bir en-boy oranının korunması gereken içeriklerde CSS tarafındaki `aspect-ratio` özelliği de kullanılabilir. Örneğin:
```
    .video-frame {
        width: 100%;
        aspect-ratio: 16 / 9;
        border: 0;
    }
```
HTML:
```
    <iframe
        class="video-frame"
        src="..."
        title="Tanıtım videosu"
    >
    </iframe>
```

## `loading="lazy"`
Iframe'ler harici içerik yüklediği için sayfanın yüklenme maliyetini artırabilir. Ekranın aşağısında bulunan ve başlangıçta hemen görülmeyen bir iframe için:
```
    <iframe
        src="..."
        title="Mağaza konumu"
        loading="lazy"
    >
    </iframe>
```
kullanılabilir.

`loading="lazy"` tarayıcıya bu kaynağın yüklenmesini kullanıcı içeriğe yaklaşana kadar erteleme imkânı verir. Bu özellikle sayfada birden fazla:
```
    video,
    harita,
    harici widget
```
bulunduğunda performans açısından faydalı olabilir. Ancak sayfanın ilk görünen bölümündeki kritik içeriklerde `lazy loading` kullanımı her zaman gerekli değildir.

## `allowfullscreen`
Video gibi içeriklerin tam ekran gösterilmesine izin verilmesi gereken durumlarda:
```
    <iframe
        src="..."
        title="Tanıtım videosu"
        allowfullscreen
    >
    </iframe>
```
ile karşılaşabiliriz.

`allowfullscreen` bir **boolean attribute**'dur. Bu nedenle `allowfullscreen` şeklinde yazılması yeterlidir.

## `allow`
`allow`, iframe içerisindeki içeriğin belirli tarayıcı özelliklerini kullanmasına ilişkin izin politikalarını tanımlamak için kullanılabilir. Örneğin gömme kodlarında şöyle yapılarla karşılaşabiliriz:
```
    <iframe
        src="..."
        title="Tanıtım videosu"
        allow="autoplay; fullscreen"
    >
    </iframe>
```
Buradaki izinler kullanılan servise ve içeriğin ihtiyacına göre değişebilir. Bu nedenle özellikle YouTube gibi üçüncü taraf servislerden alınan gömme kodlarında platformun sağladığı `allow` değerlerini rastgele silmek veya değiştirmek yerine ne işe yaradıklarını anlamak gerekir.

`allow` oldukça geniş bir konu olduğu için temel HTML seviyesinde tüm izin politikalarını ezberlemeye gerek yoktur.

Bilmemiz gereken temel nokta: `allow, iframe içerisindeki içeriğe belirli tarayıcı özellikleri için izin tanımlamak amacıyla kullanılabilir.`

## sandbox
`sandbox`, iframe içerisindeki içeriğe çeşitli kısıtlamalar uygulamak için kullanılan önemli bir attribute'dur.

Temel kullanım:
```
    <iframe
        src="..."
        title="Harici içerik"
        sandbox
    >
    </iframe>
```
`sandbox` tek başına kullanıldığında iframe içerisindeki içeriğe çeşitli güvenlik kısıtlamaları getirir. Gerektiğinde belirli yeteneklere tekrar izin verilebilir.

Örneğin:
```
    <iframe
        src="..."
        title="Harici içerik"
        sandbox="allow-scripts"
    >
    </iframe>
```
Bu örnekte script çalıştırılmasına izin verilir. Başka izin değerleri de bulunmaktadır. Ancak bunların tamamını HTML öğrenirken ezberlemek gerekli değildir.

Temel mantık:
```
    iframe
    ↓
    Harici içerik
    ↓
    sandbox
    ↓
    İçeriğin yapabileceklerini sınırlandır
```
şeklindedir.

`sandbox` değerleri güvenlik davranışını değiştirdiği için rastgele eklenmemeli veya kaldırılmamalıdır.

## Her Web Sitesi `<iframe>` İçinde Açılabilir mi?
Hayır. Şöyle bir iframe yazmamız:
```
    <iframe
        src="https://example.com"
        title="Örnek"
    >
    </iframe>
```
o web sitesinin kesin olarak sayfamız içerisinde görüntüleneceği anlamına gelmez. Web sitesi kendi güvenlik politikaları aracılığıyla başka siteler içerisinde iframe olarak gösterilmesini engelleyebilir.

Bu nedenle: `Bir URL'nin tarayıcıda normal şekilde açılması, o URL'nin iframe içerisinde de açılabileceği anlamına gelmez.`

YouTube veya harita servisleri gibi platformların özel **embed URL** sunmasının nedenlerinden biri de budur.

## `<iframe>` Kullanırken Güvenlik
Iframe ile başka bir kaynaktan içerik yüklediğimizi unutmamamız gerekir. Bu nedenle özellikle bilinmeyen kaynaklardan gelen içeriklerin doğrudan sayfaya gömülmesi konusunda dikkatli olunmalıdır.

Temel olarak:
- Güvenilir kaynaklar kullanılmalı.
- Gereksiz izinler verilmemeli.
- `sandbox` ihtiyacı değerlendirilmelidir.
- Üçüncü taraf gömme kodlarının ne yaptığı bilinmelidir.

Güvenlik politikalarının ayrıntıları temel HTML konusunun kapsamından daha geniştir. Burada öğrenmemiz gereken temel düşünce:
```
    Harici içerik
            ↓
    Başka bir kaynaktan geliyor
            ↓
    İzinleri ve kaynağı kontrol et
```

## `<iframe>` ve Performans
Iframe içerisinde yüklenen içerik ayrı kaynaklara ihtiyaç duyabilir.

Örneğin bir video iframe'i:
```
    Bizim sayfamız
            ↓
    iframe
            ↓
    Harici servis
            ↓
    HTML + CSS + JavaScript + medya
```
gibi ek kaynakların yüklenmesine neden olabilir.

Bu yüzden çok sayıda iframe kullanmak sayfa performansını etkileyebilir. Bu noktada, `loading="lazy"` gibi özelliklerden yararlanılabilir. Ancak performans optimizasyonunun detayları HTML'in temel kapsamının dışındadır.

## `<embed>` Elementi
`<embed>`, harici bir içeriği belgeye gömmek için kullanılan bir HTML elementidir.

Temel yapı:
```
    <embed
        src="file.pdf"
        type="application/pdf"
    >
```
Örneğin bir PDF içeriği gömmek için kullanılabilir. Burada:
```
    src → Kaynağın adresi
    type → İçeriğin MIME türü
```
şeklinde düşünülebilir.

Ancak modern web uygulamalarında `<embed>`, `<iframe>` kadar sık karşılaşacağımız bir element değildir. Bu nedenle temel seviyede, **`<embed>`, harici içerikleri sayfaya gömmek için kullanılabilen elementlerden biridir.** bilgisi yeterlidir.

## `<object>` Elementi
`<object>` da harici bir kaynağı HTML belgesi içerisinde temsil etmek için kullanılabilir.

Örneğin:
```
    <object
        data="document.pdf"
        type="application/pdf"
    >
        <p>
            PDF görüntülenemedi.
        </p>
    </object>
```
Burada:
```
data
↓
Gösterilecek kaynak

type
↓
Kaynağın türü
```
belirtilir.

`<object>` içerisinde alternatif içerik de bulunabilir. Örneğin kaynak görüntülenemezse, `<p>PDF görüntülenemedi.</p>` içeriği kullanılabilir.

Modern frontend geliştirmede `<object>` ile de `<iframe>` kadar sık karşılaşmayız. Bu nedenle ayrıntılı kullanımını ezberlemek yerine ne amaçla var olduğunu bilmek yeterlidir.

## `<iframe>`, `<embed>` ve `<object>` Farkı
Temel seviyede farkları şöyle düşünebiliriz:

|Element        |Temel Kullanım     |
|---------------|-------------------|
|`<iframe>`     |Başka bir HTML belgesi veya harici web içeriği|
|`<embed>`      |Harici medya/belge kaynağı|
|`<object>`     |Harici bir kaynağı belge içerisinde temsil etme|

Günlük frontend geliştirmede özellikle `<iframe>` ile karşılaşma ihtimalimiz daha yüksektir. Bu nedenle `<embed>` ve `<object>` elementlerinin tüm ayrıntılarını öğrenmek şu aşamada gerekli değildir.

## `<iframe>` ile `<video>` Aynı Şey Değildir
Daha önce HTML Images & Media konusunda `<video>` elementini görmüştük. Örneğin kendi video dosyamız:
```
    <video controls>
        <source
            src="video.mp4"
            type="video/mp4"
        >
    </video>
```
ile gösterilebilir.

YouTube gibi harici bir serviste bulunan video ise genellikle:
```
    <iframe
        src="..."
        title="Tanıtım videosu"
    >
    </iframe>
```
ile gömülür.

Temel fark:
``` 
    Kendi medya dosyamız → <video>
    Harici platformun gömülü oynatıcısı → <iframe>
```
Bu nedenle her video için iframe kullanmak gerekmez.

## Sık Yapılan Hatalar
Harici içerik gömerken dikkat edilmesi gereken yaygın hatalar şunlardır:
- `<iframe>` elementine açıklayıcı `title` vermemek.
- Normal bir URL'nin her zaman iframe içerisinde çalışacağını düşünmek.
- Servisin embed URL'si yerine normal sayfa URL'sini kullanmak.
- Çok sayıda iframe'i gereksiz yere aynı sayfada yüklemek.
- Ekranın aşağısındaki iframe'lerde gerektiğinde `loading="lazy"` kullanımını değerlendirmemek.
- Bilinmeyen kaynaklardan alınan iframe kodlarını kontrol etmeden kullanmak.
- Gereksiz iframe izinleri vermek.
- `sandbox` değerlerini ne yaptığını bilmeden değiştirmek.
- Kendi video dosyamız için gereksiz yere iframe kullanmak.
- `<embed>` ve `<object>` gibi daha az kullanılan elementlerin bütün ayrıntılarını ezberlemeye çalışmak.

## Genel Örnek
Basit bir iletişim sayfasında harita ve video kullandığımızı düşünelim:
```
    <section> 
        <h1>Mağazamız</h1> 
        <h2>Konum</h2> 
        <iframe src="MAP_EMBED_URL" title="Mağazamızın haritadaki konumu" loading="lazy" > 
        </iframe> 
        
        <h2>Mağazamızı Tanıyın</h2> 
        <iframe class="video-frame" src="VIDEO_EMBED_URL" title="Mağaza tanıtım videosu" loading="lazy" allow="fullscreen" allowfullscreen > 
        </iframe> 
    </section>
```

Burada iki farklı harici servis aynı HTML sayfası içerisinde gösterilebilir. Ancak içerikler bizim HTML belgemizin doğrudan bir parçası değildir.
```
    Bizim HTML
    │
    ├── Başlık
    │
    ├── iframe
    │      └── Harita servisi
    │
    └── iframe
        └── Video servisi
```

## Kontrol Listesi
Harici içerik eklerken:
- Gerçekten iframe kullanılması gerekiyor mu?
- Kaynak güvenilir mi?
- Servisin özel **embed URL**'si var mı?
- `<iframe>` için açıklayıcı bir `title` kullanıldı mı?
- İçerik responsive tasarıma uygun mu?
- Ekranın aşağısındaki iframe için `loading="lazy"` değerlendirildi mi?
- Gereksiz izinler veriliyor mu?
- `sandbox` gerekiyorsa doğru şekilde yapılandırıldı mı?
- Harici servis iframe içerisinde gösterilmeye izin veriyor mu?
- Kendi medya dosyamız için `<video>` veya `<audio>` daha uygun olabilir mi?

## Kısaca Özet
HTML içerisinde başka kaynaklardan gelen içerikleri sayfamıza gömebiliriz.
En önemli element `<iframe>` elementidir.

Temel mantık:
```
    Harici İçerik
        ↓
    Embed URL
        ↓
    <iframe>
        ↓
    Web Sayfamız
```

`<iframe>` kullanırken özellikle:
```
    src
    title
    loading
    allow
    allowfullscreen
    sandbox
```
gibi özelliklerle karşılaşabiliriz.

`<embed>` ve `<object>` da harici içerik gömmek için kullanılabilen elementlerdir ancak modern frontend geliştirmede` <iframe>` kadar sık kullanılmazlar.

Bu konudaki en önemli nokta: **Harici bir içeriği sayfaya gömmek yalnızca görsel bir işlem değildir. Kaynağın güvenilirliği, izinler, erişilebilirlik ve performans da değerlendirilmelidir.**