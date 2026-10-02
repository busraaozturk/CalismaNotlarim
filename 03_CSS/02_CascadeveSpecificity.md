# Cascade ve Specificity
Bir önceki bölümde CSS selector'larının HTML etikerlerini nasıl hedeflediğini öğrendik.

Örneğin:
```
    .card { 
        color:black;
    }
``` 
ve
```
    #featured-card {
        color:red;
    }
```
gibi farklı selector'lar oluşturabiliriz. Ancak aynı HTML elementi birden fazla CSS kuralıyla eşleşebilir.

Örneğin:
```
    <div
        id="featured-card"
        class="card"
    >
        Öne Çıkan Ürün
    </div>
```
CSS:
```
    .card {
        color: black;
    }

    #featured-card {
        color: red;
    }
```

Burada aynı element için iki farklı **color** değeri tanımlanmıştır:
```
    .card → color: black;
    #featured-card → color: red;
```

Peki tarayıcı hangisini uygular? 

İşte bu sorunun cevabı CSS'in en önemli temel kavramlarından biri olan **Cascade** mekanizmasında bulunur.

Bu bölümde aşağıdaki konuları inceleyeceğiz:
```
    Cascade ve Specificity
    │
    ├── 1. Cascade Nedir?
    │
    ├── 2. Cascade'i Belirleyen Faktörler
    │   ├── Importance
    │   ├── Specificity
    │   └── Source Order
    │
    ├── 3. Specificity Nasıl Hesaplanır?
    ├── 4. Specificity Örnekleri
    ├── 5. Source Order
    ├── 6. !important
    ├── 7. Inline Style
    ├── 8. Sık Yapılan Hatalar
    └── 9. Kısaca
```

## Cascade - Basamaklanma Nedir?
CSS'in açılımını `Cascading Style Sheets` olarak öğrenmiştik. Buradaki **Cascading** kelimesi CSS'in temel çalışma mekanizmalarından birini ifade eder. Bir HTML elementi aynı anda birden fazla CSS kuralıyla eşleşebilir.

Örneğin:
```
    <p class="description">
        Ürün açıklaması
    </p>
```

CSS:
```
    p {
        color: gray;
    }

    .description {
        color: black;
    }
```

Burada aynı element `p` selector'ıyla da `description` selector'ıyla da eşleşmektedir. Her iki kural da aynı property'yi değiştirmeye çalışmaktadır: `color` Tarayıcının bu çakışmayı çözmesi gerekir.

İşte **cascade**, bir element için birden fazla CSS declaration'ı geçerl, olduğunda hangi declaration'ın kullanılacağını belirleyen mekanizmadır.

Basitçe şu şekilde düşünebiliriz:
```
    Bir element
        ↓
    Birden fazla CSS kuralıyla eşleşiyor
        ↓
    Aynı property için farklı değerler var
        ↓
    Cascade
        ↓
    Hangi declaration kullanılacak?
```

### Her Kural Birbiriyle Çakışmaz
Önemli bir ayrım yapalım. 

Şu CSS:
```
    .card{
        color:black;
    }

    .card {
        padding:20px;
    }
```

bir problem oluşturmaz. Çünkü kurallar farklı property'leri tanımlamaktadır.

Sonuçta element:
```
    color: black;
    padding: 20px;
```
değerlerinin ikisini de kullanabilir. Asıl karşılaştırma aynı property için birden fazla uygun declaration olduğunda önem kazanır.

Örneğin:
```
    .card {
        color: black;
    }

    .card {
        color: red;
    }
```
Burada iki farklı color değeri vardır. Tarayıcının bunlardan hangisinin kullanılacağını belirlemesi gerekir.

## Cascade'i Belirleyen Temel Faktörler
Başlangıç seviyesinde cascade mantığını anlamak için üç temel kavrama odaklanabiliriz:
```
    Cascade
    │
    ├── Importance
    │
    ├── Specificity
    │
    └── Source Order
```
Basitleştirilmiş düşünce şu şekildedir:
```
    Öncelik / Importance
            ↓
    Specificity
            ↓
    Source Order
```
Ancak bu `Tarayıcı her durumda yalnızca bu üç satıra bakar.` anlamına gelmez. 

Modern CSS cascade mekanizmasında:
- Stil kaynağı (origin),
- Cascade layer,
- Importance,
- Specificity,
- Scope gibi başka ayrıntılar da bulunabilir.

Bunların tamamını başlangıç seviyesinde öğrenmek gerekli değildir. Şimdilik kendi yazdığımız normal CSS kuralları arasındaki çakışmaları anlamaya odaklanacağız.

### 1. Importance — Önem
Normal bir CSS declaration şu şekilde yazılır:
```
    .card {
        color: black;
    }
```

CSS'te bir declaration `!important` ile önemli olarak işaretlenebilir.

Örneğin:
```
    .card {
        color: black !important;
    }
```
Bu declaration normal declaration'lardan farklı bir cascade önceliğine sahip olur.

Örneğin:
```
    .card {
        color: black !important;
    }

    #featured-card {
        color: red;
    }
```

Burada yalnızca `ID selector daha güçlüdür.` diyerek karar veremeyiz. Çünkü ilk declaration `!important` olarak işaretlenmiştir.

Dolayısıyla cascade değerlendirmesinde normal declaration ile important declaration aynı seviyede değerlendirilmez.

### 2. Specificity — Özgüllük
Birden fazla uygun CSS kuralı aynı cascade önceliğinde yarışıyorsa selector'ların specificity değerleri karşılaştırılır. Specificity'yi basitçe `Bir selector'ın hedefini ne kadar özgül tanımladığını gösteren karşılaştırma sistemi` olarak düşünebiliriz.

Örneğin:
```
    p {
        color: gray;
    }
```
bütün p elementlerini hedefler.

Ancak:
```
    .description {
        color: black;
    }
```
belirli bir class'a sahip elementleri hedefler.

Bu nedenle `.description` selector'ı `p` selector'ından daha yüksek specificity'ye sahiptir.

### 3. Source Order — Kaynak Sırası
Eğer iki kuralın cascade bağlamı ve specificity değeri eşitse, kaynak sırası devreye girebilir.

Örneğin:
```
    .card {
        color: black;
    }

    .card {
        color: red;
    }
```
Her iki selector da aynıdır `.card` Dolayısıyla specificity değerleri eşittir. Bu durumda daha sonra gelen declaration kazanır:
```
    .card {
        color: red;
    }
```
Sonuç `color: red;` olur. Bu nedenle CSS'te `Son yazılan her zaman kazanır.` demek doğru değildir.

Doğrusu: `Cascade'in önceki aşamalarında eşitlik varsa kaynak sırası belirleyici olabilir.`

## Specificity Nasıl Hesaplanır?
Specificity hesaplamasını anlamak için selector'ları temel olarak kategorilere ayırabiliriz. Başlangıç seviyesinde şu dört seviyei düşünebiliriz:
- Inline Style
- ID
- Class / Attribute / Pseudo-Class
- Element / Pseudo-Element

Örneğin:
```
    style=""
    #header
    .card
    [type="text"]
    :hover
    p
    ::before
```
aynı specificity seviyesinde değildir.

### Specificity Şeması
Specificity genellikle şu yapıyla gösterilebilir: `A - B - C`

Burada:
```
    A
    ↓
    ID selector sayısı

    B
    ↓
    Class
    Attribute
    Pseudo-Class sayısı

    C
    ↓
    Element
    Pseudo-Element sayısı
```

Inline style ise normal selector specificity'sinin dışında, element üzerinde doğrudan tanımlanan stil olarak daha yüksek öncelikli bir konumda düşünülebilir.

Öğrenirken bunu pratik olarak dört sütunlu şekilde de gösterebiliriz. `Inline | ID | Class/Attribute/Pseudo-Class | Element/Pseudo-Element`

Örneğin: 

Bir element selector'ını : `0 | 0 | 0 | 1`
Bir class selector'ını : `0 | 0 | 1 | 0`
Bir ID selector'ını temsil eder: `0 | 1 | 0 | 0`

### Element Selector
Örneğin:
```
    p{
        color:gray;
    }
```

Burada: `p → 1 element selector` Specificity: `0 | 0 | 0 | 1` olarak düşünülebilir.