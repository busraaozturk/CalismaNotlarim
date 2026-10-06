# CSS Renkler - Colors
Web arayüzlerinin görsel tasarımında en temel özelliklerden biri **renklerdir.**

CSS ile:
- Metin,
- Arka plan,
- Kenarlık,
- Gölge,
- İkon, 
- Dekoratif öğeler,

gibi birçok yapının rengini kontrol edebiliriz.

Örneğin: `h1 {color:darkgreen;}` Burada:
```
    color → Property
    darkgreen → Color Value
```
şeklinde bir yapı vardır.

Ancak CSS'te renkleri yalnızca isimleriyle tanımlamayız. Aynı renk farklı renk formatlarıyla ifade edilebilir.
```
    CSS Colors
    │
    ├── Named Colors
    ├── Hex
    ├── RGB
    ├── HSL
    └── Alpha / Transparency
```

Bu bölümde bu renk formatlarını ve aralarındaki farkları inceleyeceğiz.

## CSS'te Renk Nedir?
CSS'te renkleri kontrol etmek için farklı property'ler kullanılabilir. En temel property `color` property'sidir.

**color**, temel olarak elementin temel rengini belirler.

Örneğin:
```
    p{
        color:darkgreen;
    }
```

HTML:
```
    <p>
        CSS öğreniyorum.
    </p>
```
Bu paragrafın metin rengi darkgreen olur.

### Renk Yalnızca Metin İçin Kullanılmaz
CSS'te birçok property bir renk değeri kabul edebilir.

Örneğin:
```
    .card {
        color:black;
        background-color: white;
        border-color: gray;
    }
```

Burada:
```
    color → Metin rengi
    background-color → Arka plan rengi
    border-color → Kenarlık rengi
```
belirlenmektedir.

Başka CSS property'lerinde de renk değerleriyle karşılaşacağız. Örneğin ilerleyen konularda:
```
    box-shadow
    text-shadow
    outline-shadow
```
gibi yapılarda da renk kullanabiliriz.

### CSS'te Renk Nasıl Yazılır?
CSS aynı rengi farklı biçimlerde ifade etmemize izin verir.

Örneğin kırmızı, `color:red;` şeklinde yazılabileceği gibi; `color: #ff0000;` veya `color:rgb(255,0,0);` veya `color: hsl(0, 100%, 50%)` şeklinde yazılabilir.

Bunların hepsi aynı temel rengi farklı renk modelleri veya sözdizimleriyle ifade eder.

## Named Colors - İsimli Renkler
CSS içerisinde önceden tanımlanmış renk isimleri bulunur.

Örneğin: 
```
    color:red;
    color:blue;
    color:black;
    color:white;
    color:darkgreen;
```
Bunlara **named colors**, yani **isimli renkler** denir.

Örneğin:
```
    h1 {
        color:darkgreen;
    }
```
Burada tarayıcı **darkgreen** anahtar kelimesinin hangi renk değerini temsil ettiğini bilir.

### Named Colors'ın Avantajı
İsimli renkler oldukça okunaklıdır. Örneğin: `color:red;` kodunu gördüğümüzde hangi rengin kullanılacağını hemen anlayabiliriz. Bu nedenle:
- Eğitim örneklerinde,
- Hızlı denemelerde,
- Basit prototiplerde kullanışlı olabilir.

### Named Colors'ın Sınırlılığı
Named colors belirli hazır renkleri temsil eder. Ancak gerçek bir tasarımda çoğu zaman çok daha hassas renk tonlarına ihtiyaç duyarız.

Örneğin tasarımda; `#7d8570` gibi özel bir renk kullanılması istenebilir.

Bunun  yerine yalnızca `color:green;` veya `color:darkgreen;`
kullanmak tasarımdaki tam rengi karşılamayabilir.

Bu nedenle gerçek projelerde özel renk değerleri için Hex, RGB veya HSL gibi formatlarla sıkça karşılaşırız.

## Hex - Hexadecimal Renkler
Web tasarımında en sık karşılaşacağımız renk gösterimlerinden biri **Hexadecimal**, kısaca **Hex** renklerdir.

Örneğin: `color: #ff0000;` Hex renkler genellikle: `#RRGGBB` formatında yazılır.

Burada: 
```
    RR → Red
    GG → Green
    BB → Blue
```
değerlerini temsil eder.

Yani:
```
    # RR GG BB
    │  │  │
    │  │  └── Blue
    │  └───── Green
    └──────── Red
```

### Hexadecimal Ne Demektir?
Günlük hayatta kullandığımız sayı sistemi genellikle onluk sistemdir:`0 1 2 3 4 5 6 7 8 9 `

Hexadecimal sistem ise 16 farklı sembol kullanır:`0 1 2 3 4 5 6 7 8 9 A B C D E F`

Burada:
```
    A → 10
    B → 11
    C → 12
    D → 13
    E → 14
    F → 15
```
anlamına gelir.

Hex renklerde her renk kanalının değeri:
```
    00 → En düşük
    FF → En yüksek
```
aralığında ifade edilir.

### Temel Hex Renk Örnekleri
Tam kırmızı: `color: #ff0000`

Çünkü:
```
    Red   → FF
    Green → 00
    Blue  → 00
```

Tam yeşil: `color: #00ff00;`

Tam mavi: `color:#0000ff;`

Siyah: `color:#000000;` Çünkü bütüm renk kanalları minimumdadır.

Beyaz: `color: #ffffff;` Çünkü bütün renk kanalları maksimumdadır.

### Büyük ve Küçük Harf
Hex değerler, `#FF0000` veya `#ff0000` şeklinde yazılabilir. İkisi de aynı rengi ifade eder. Proje içerisinde tutarlı bir uapı biçimi kullanmak kod okunabilirliği açısından daha iyidir.

Örneğin tüm renkleri küçük harfle yazmayı tercih edebiliriz: `coloe: #7d8570;`

### Üç Haneli Hex Kullanımı
Bazı Hex renkler kısa biçimde yazılabilir.

Örneğin: `color: #ff0000;` şu şekilde kısaltılabilir, `color:#f00`.  Çünkü `#f00 → #ff0000` olarak genişletilir. Benzer şekilde:
```
    #fff → #ffffff
    #000 → #000000
    #abc → #aabbcc
```
olur. Ancak her altı haneli Hex kod üç haneye indirgenemez.

Örneğin: `#7d8570` şu şekilde çift tekrar eden hanelerden oluşmadığı için üç haneli biçime kısaltılamaz.

## RGB Renkler
RGB `Red Green Blue` kelimelerinin baş harflerinden oluşur. CSS'te klasik RGB yazımı , `color: rgb(255, 0, 0)` şeklindedir.

Burada: 
```
    rgb {
        Red,
        Green,
        Blue,
    }
```
mantığı kullanılır.

### RGB Değer Aralığı
Klasik sayısal RGB kullanımında her kanal :
```
    0 → minimum
    255 → maksimum
```
arasında değer alır.

Örneğin: `color:rgb(255, 0, 0);` şu anlama gelir:
```
    Red   → 255
    Green → 0
    Blue  → 0
```
Sonuç: `Kırmızı` olur.

### Temel RGB Örnekleri
Kırmızı: `color: rgb(255, 0, 0);`

Yeşil: `color: rgb(0, 255, 0);`

Mavi: `color: rgb(0, 0, 255);`

Siyah: `color: rgb(0, 0, 0);`

Beyaz: `color: rgb(255, 255, 255);`

### RGB'de Yüzde Kullanımı
RGB kanalları yüzde değerleriyle de ifade edilebilir. 

Örneğin: `color: rgb(100%, 0%, 0%);` kırmızıyı ifade eder.

Yani:
```
    100% → maksimum kanal yoğunluğu
    0% → minimum kanal yoğunluğu
```
şeklinde düşünülebilir.

Başlangıçta çoğumlukla 0 - 255 arasındaki sayısal RGB gösterimiyle karşılaşacağız.

### Hex ve RGB Aynı Rengi İfade Edebilir
Örneğin `color:"#ff0000;"` ile `color: rgb(255, 0, 0); ` aynı kırmızıyı ifade eder.

Karşılaştırırsak:
```
    HEX
    # FF 00 00
    │  │  │
    R  G  B

    RGB
    rgb(255, 0, 0)
        │    │  │
        R    G  B
```

Temelde her iki gösterimde de kırmızı, yeşil ve mav, kanallarının miktarı tanımlanmaktadır.

Fark kullanılan sayı gösterimi ve sözdizimidir.

## HSL Renkler
CSS'te kullanabileceğimiz başka bir renk modeli **HSL**'dir.

**HSL (Hue Saturation Ligthness)** kelimelerinden oluşur.

Türkçe olarak aşağıdaki şekilde düşünebiliriz:
```
    Hue → Renk tonu
    Saturation → Doygunluk
    Lightness → Açıklık
```

Örnek: `color: hsl(120, 100%, 25%);`

### Hue - Renk Tonu
Hue, rengin renk çemberindeki konumunu ifade eder. Genellikle derece mantığıyla düşünülür:
```
    0° / 360°  → Kırmızı
    120°       → Yeşil
    240°       → Mavi
```

Basitleştirilmiş renk çemberi:
```
                0°
            Kırmızı
                │
                │
    240° ───────┼─────── 120°
    Mavi                  Yeşil
                │
                │
                360°
            Kırmızı
```

Örneğin:
`color: hsl(0, 100%, 50%);` kırmızı, ` color: hsl(120, 100%, 50%);` yeşil, `color: hsl(240, 100%, 50%);` mavi verir.

### Saturation - Doygunluk
Saturation rengin ne kadar canlı veya griye yakın olduğunu kontrol eder.
```
    0%      → Doygunluk yok
    100%    → Tam doygunluk
```

Örneğin: `color: hsl(120, 100%, 50%)` yüksek doygunluğa sahip canlı bir yeşildir. Doygunluk azaldıkça renk daha gri bir görünüme yaklaşır.

### Lightness - Açıklık
Ligthness rengin açıklık seviyesini ifade eder. 
```
    0% → Siyah
    50% → Rengin temel görünüm bölgesi
    100% → Beyaz
```

Örneğin: `color: hsl(120, 100%, 25%);` daha koyu bir yeşildir. `color: hsl(120, 100%, 50%);` daha açık bir yeşildir.

### HSL'nin Avantajı
HSL'nin önemli avantajlarından biri renk üzerinde düşünmenin bazı durumlarda daha kolay olmasıdır. 

Örneğin ana rengimiz `color: hsl(120, 40%, 40%);` olsun. Daha açık bir varyasyon için lightness değerini değiştirebiliriz: `color:hsl(120, 40%, 60%);` Daha koyu bir varyasyon için: `color: hsl(120, 40%, 30%);` 

Renk tonu aynı kalırken açıklık seviyesini değiştirmiş oluruz.
```
    Hue → aynı
    Saturation → aynı
    Lightness → değişiyor
```

Bu nedenle HSL özellikle renk varyasyonlarını düşünürken okunabilir bir model olabilir.

## Alpha Kanalı - Saydamlık
Bazı durumlarda rengin tamamen opak olmasını istemeyebiliriz.
Örneğin:
- Overlay,
- Yarı saydam arka plan,
- Gölge,
- Dekoratifkatman oluşturmak isteyebiliriz.

Bunun için renk değerlerinde **alpha** kanalından yararlanabiliriz. Alpha temel olarak rengin opaklık seviyesini belirler.

Basit düşünce:
```
    0 → Tamamen saydam
    0.5 → Yarı saydam
    1 → Tamamen opak
```

### RGBA
Geleneksel olarak RGB renklerine alpha değeri eklemek için: `rgba()` kullanımıyla sıkça karşılaşırız.

Örneğin: `background-color: rgba(0, 0, 0, 0.5);`

Burada:
```
    R → 0
    G → 0
    B → 0
    A → 0.5
```
olduğu için sonuö yarı saydam siyahtır. Bu kullanım özellikle overlay gibi yapılarda sık görülür.

Örneğin:
```
    overlay {
        background-color:rgba(0, 0, 0, 0.5);
    }
```

### HSLA
HSL renklerinde alpha değeri için geleneksel olarak `hsla()` fonksiyonu kullanılabilir.

Örneğin: `background-color: hsla(120, 100%, 25½, 0.5);` Buradaki son değer: `0.5` alpha değeridir.

### Modern CSS'te Alpha Yazımı
Modern CSS'te alpha değeri kullanmak için mutlaka **rgba()** veya **hsla()** fonksiyonlarına geçmek gerekmez.

rgb() ve hsl() fonksiyonları da alpha değeri kabul eder. Modern syntax örneği: `background-color:rgb(0 0 0 / 50%);` ve `background-color: hsl(120, 100%, 25% / 50%);` Buradaki `/ →Alpha değerini ayırır` şeklinde düşünülebilir.

Dolayısıyla güncel CSS'te `rgba(0, 0, 0, 0.5);` gibi geleneksel kullanımlarla da `rgb(0 0 0 / 50%);` gibi modern kullanımlarla da karşılaşabiliriz.