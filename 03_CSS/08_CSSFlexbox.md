# CSS Flexbox (Esnek Kutu Yerleşimi)
CSS Flexbox, bir kapsayıcı içerisindeki elementlerin yerleşimini ve hizalanmasını yönetmek için kullanılan **tek boyutlu (one-dimensional) bir layout sistemidir.** 

Tek boyutlu olması, Flexbox'ın elementleri temel olarak bir ana eksen (satır veya sütun) üzerinde düzenlemesi anlamına gelir.

Flexbox sayesinde:
- Elementleri yatay veya dikey hizalayabiliriz.
- Elementler arasındaki boşlukları kontrol edebiliriz.
- İçeriği yatay ve dikey olarak ortalayabiliriz.
- Elementlerin büyüme ve küçülme davranışlarını yönetebiliriz.
- Farklı ekran genişliklerine uyum sağlayan düzenler oluşturabiliriz. 
- Navbar, kart listesi,buton grubu ve form alanları gibi bileşenleri kolayca tasarlayabiliriz.

## Flexbox Nedir ve Neden Kullanılır?
Normal belge akışında blok elementler genellikle alt alta yerleşir.
```
    <div class="container">
        <div class="box">1</div>
        <div class="box">2</div>
        <div class="box">3</div>
    </div>
```

Varsayılan görünüm:
``` 
    ┌─────────────────────────┐
    │            1            │
    ├─────────────────────────┤
    │            2            │
    ├─────────────────────────┤
    │            3            │
    └─────────────────────────┘
```

Flexbox kullanarak bu elementleri yan yana yerleştirebiliriz.
```
    .container {
        display: flex;
    }
```

Sonuç:
```
    ┌────────┬────────┬────────┐
    │   1    │   2    │   3    │
    └────────┴────────┴────────┘
```

Flexbox'ın önemli avantajı, elementlerin yalnızca yan yana yerleşmesini sağlaması değildir.

Aynı zamanda elementlerin kullanılabilir alanı nasıl paylaşacağını ve farklı boyutlara nasıl uyum sağlayacağını da yönetir.

### Flexbox Ne Zaman Kullanılır?
Flexbox özellikle aşağıdaki arayüzlerde kullanışlıdır:
- Navbar ve menüler
- Buton grupları
- Form alanları
- İkon ve metin hizalaması
- Kart içeriği düzenleri
- Header ve footer bileşenleri
- Yatay veya dikey merkezleme
- Responsive bileşen yerleşimleri

**Önemli:** Flexbox genel olarak tek boyutlu düzenler için uygundur. Satır ve sütunların birlikte kontrol edilmesi gereken iki boyutlu düzenlerde CSS Grid daha uygun olabilir.

## Flex Container ve Flex Item
Flexbox sisteminde iki temel kavram bulunur:
1. Flex Container: *display: flex* veya *display: inline-flex* uygulanan kapsayıcıdır.
2. Flex Item: Flex container'ın doğrudan çocuklarıdır.

Örnek:
```
    <div class="container">
        <div class="item">1</div>
        <div class="item">2</div>
        <div class="item">3</div>
    </div>

    .container {
        display: flex;
    }
```
Yapı:
```
    FLEX CONTAINER
    ┌─────────────────────────────────┐
    │                                 │
    │ ┌────────┐ ┌────────┐ ┌────────┐│
    │ │ Item 1 │ │ Item 2 │ │ Item 3 ││
    │ └────────┘ └────────┘ └────────┘│
    │                                 │
    └─────────────────────────────────┘
```

### Flex Container Özellikleri
Kapsayıcı üzerinde kullanılan temel özellikler:
``` 
    .container {
        display: flex;
        flex-direction: row;
        flex-wrap: nowrap;
        justify-content: flex-start;
        align-items: stretch;
        align-content: normal;
        gap: 16px;
    }
```

### Flex Item Özellikleri
Doğrudan çocuk elementlerde kullanılan özellikler:
```
    .item {
        flex-grow: 0;
        flex-shrink: 1;
        flex-basis: auto;

        align-self: auto;
        order: 0;
    }
```

Flex item'lar üzerinde ayrıca flex shorthanf property'si kullanılabilir. 

**Dikkat:** Flex container içerisindeki bir elementin torunları otomatik olarak aynı container'ın flex item'ı olmaz.
```
    <div class="container">
        <div class="item">
            <span>Metin</span>
        </div>
    </div>
```
Burada .item bir flex item'dır. Ancak span, .container açısından doğrudan flex item değildir.

## Main Axis ve Cross Axis
Flexbox'ı doğru kullanabilmek için iki ekseni anlamamız gerekir.
1. Main Axis (Ana Eksen) : flex item'larını temel yerleşim yönünü belirler.
2. Cross Axis (Çapraz Eksen) : main axis'e dik olan eksendir.

