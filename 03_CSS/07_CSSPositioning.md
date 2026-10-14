# CSS Positioning (Konumlandırma)
Web sayfalarında elementler varsayılan olarak belirli bir düzene göre yerleşir. Ancak bazı tasarımlarda bu düzenin dışına çıkmamız gerekir.

Örneğin:
- Ürün kartının sağ üst köşesine indirim etiketi eklemek,
- Sayfa kaydırılırken bir menüyü üstte tutmak,
- Ekranın sağ alt köşesine yukarı çık butonu yerleştirmek,
- Bir görselin üzerine metin veya ikon eklemek,
- Açılır menüyü ilgili butonun altında konumlandırmak.

Bu tür ihtiyaçlar için **CSS'te Positioning (Konumlandırma)** özelliklerini kullanırız.

Temel property: `position` Bu property, elementin nasıl konumlandırılacağını ve hangi referans noktasına göre hareket edeceğini belirler.

##  Normal Akış (Flow Layout) Nedir?
Önceki Display bölümünde öğrendiğimiz gibi HTML elementleri, varsayılan olarak belge akışı içerisinde yerleşir.

Örneğin:
```
    <div>Birinci Kutu</div>
    <div>İkinci Kutu</div>
    <div>Üçüncü Kutu</div>
```
Bu elementler normal blok akışında alt alta yerleşir.
```
    ┌────────────────────┐
    │    Birinci Kutu    │
    └────────────────────┘

    ┌────────────────────┐
    │    İkinci Kutu     │
    └────────────────────┘

    ┌────────────────────┐
    │    Üçüncü Kutu     │
    └────────────────────┘
```
Bu yerleşime **Normal Flow (Normal Akış)** denir.

Normal akışta elementlerin yerleşimi HTML sırası, display davranışı ve diğer CSS yerleşim kurallarına göre hesaplanır.

**position property**'si, elementin bu akıştaki konumunu değiştirebilir veya elementi normal akışın dışına çıkarabilir. Ancak her position değeri elementi akıştan çıkarmaz. Bu ayrım, Positioning konusunun en önemli noktalarından biridir.

## position Property'sine Genel Bakış
CSS'te beş teöel position değeri bulunur:
```
    position: static;
    position: relative;
    position: absolute;
    position: fixed;
    position: sticky;
```

Her değer iki önemli soruyu farklı şekilde cevaplar:
1. Element normal akışta yer kaplamaya devam eder mi?
2. Element hangi noktaya göre konumlandırılır?

|Değer          |Temel davranışı                    |
|---------------|-----------------------------------|
|static         |Varsayılan yerleşim kurallarını kullanır   |
|relative       |Normal konumunu korur, görsel olarak kaydırılabilir    |
|absolute       |Normal akıştan çıkar, containing block'a göre konumlanır   |
|fixed          |Normal akıştan çıkar, genellikle viewport'a göre sabitlenir|
|sticky         |Normal akışta kalır, kaydırma sırasında belirlenen eşiğe yapışır   |

### Konumlandırma Property'leri
Positioning ile birlikte sık kullanılan dört özellik:
- top
- right
- bottom
- left

Bu özellikler, konumlandırılmış elementin ilgili referans alanına göre yerinin belirlenmesinde kullanılır.

Örneğin:
```
    .box {
        position: relative;
        top: 20px;
        left: 30px;
    }
```

Burada element:
- **top:** 20px ile normal konumundan aşağı,
- **left:** 30px ile normal konumundan sağa kaydırılır.

**Önemli:** top, right, bottom ve left değerlerinin etkisi kullanılan position türüne gçre değişir.

Ayrıca modern CSS'te yazı yönünden bağımsız konumlandırma için **inset, inset-inline ve inset-block** gibi özellikler de bulunur.

## position: static - Varsayılan Konumlandırma
HTML elementlerinin varsayılan position değeri: `position: static;` şeklindedir.

Bu değer kullanıldığında element, normal yerleşim kurallarına göre konumlanır.

Örneğin:
```
    <div class="box">Birinci</div>
    <div class="box">İkinci</div>

    .box {
        position: static;
        padding: 20px;
        margin-bottom: 10px;
        background-color: #f2f0eb;
    }
```
Elementler normal akışta yerleşmeye devam eder.

### top, right, bottom, left Neden Çalışmaz?
Örneğin:
```
    .box {
        position: static;
        top: 50px;
        left: 20px;
    }
```

Burada top ve left değerleri elementin konumunu değiştirmez. Çünkü bu offset özellikleri `position: static` üzerinde etkili değildir. Konumlandırma yapmak için uygun bir **position** değeri seçilmelidir.

**Kısaca:** static, özel konumlandırma uygulanmamış elementlerin temel davranışıdır.

## position: relative - Kendi Konumuna Göre Kaydırma
relative, elementi normal akıştan çıkarmadan görsel konumunu değiştirmemizi sağlar.

Örneğin: 
```
    <div class="box first">Birinci</div>
    <div class="box second">İkinci</div>
    <div class="box third">Üçüncü</div>

    .box {
        padding: 20px;
        margin-bottom: 10px;
        background-color: #f2f0eb;
    }

    .second {
        position: relative;
        top: 20px;
        left: 30px;
    }
```

Burada ikinci kutu normal konumuna göre:
- 20px aşağı
- 30px sağa kaydırılır.

### Relative Element Normal Akıştan Çıkar mı?
Hayır. Elementin normal akışta kapladığı alan korunur. Örneğin normal yerleşim:
```
    ┌──────────────────┐
    │     Birinci      │
    └──────────────────┘

    ┌──────────────────┐
    │     İkinci       │
    └──────────────────┘

    ┌──────────────────┐
    │     Üçüncü       │
    └──────────────────┘
```

İkinci kutuya `top: 20px` uygulandığında:
```
    ┌──────────────────┐
    │     Birinci      │
    └──────────────────┘

    ┌──────────────────┐
    │  İkinci'nin eski │
    │  yerleşim alanı  │
    └──────────────────┘
            │
            │ 20px aşağı
            ▼
        ┌──────────────────┐
        │     İkinci       │
        └──────────────────┘

    ┌──────────────────┐
    │     Üçüncü       │
    └──────────────────┘
```