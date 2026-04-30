# Test Güdümlü Geliştirme (TDD - Test Driven Development)
TDD, yazılım geliştirirken koddan önce test yazmayı, sonra bu testi geçecek kodu geliştirmeyi temel alan bir yaklaşımdır. Kent Beck tarafından popülerleştirilen bu yaklaşım, yazılım geliştirme döngüsünü köklü biçimde değiştirir. Özellikle modern yazılım süreçlerinde, örneğin Agile gibi çevik yaklaşımlarda sıkça kullanılır.

Klasik akış:

    Kod → Test

TDD'de kullanılan akış:

    Test → Kod → İyileştirme

Bu yaklaşım sayesinde daha güvenilir, sürdürülebilir ve hatası daha az olan yazılımlar geliştirilir.

## TDD'nin Temel Döngüsü (Red - Green - Refactor)

TDD'nin temel döngüsü (Red - Green - Refactor) tek bir küçük davranışı kapsar. Döngü bitmeden yeni özelliğe geçilmez.
TDD aslında çok basit ama net bir döngüye dayanır.

### 1. Red (Kırmızı - Test Yaz)
Henüz hiç kod yokken, beklenen davranışı tanımlayan bir test yazılır.
    
    Test çalıştırılır → ❌ başarısız olur (çünkü kod yok)
    Bu aşama sana şunu söyler: "Ne yapmam gerekiyor?"

Yani test = gereksinim

### 2. Green (Yeşil - Kodu Yaz)
Sadece testi geçecek kadar minimum kod yazılır. En basit, hatta "çirkin" kod bile kabul edilir. Bu disiplin fazla mühendislik yapmayı önler.

Amaç : Mükemmel kod değil testi geçmesi

Bu aşamada önemli olan "Çalışıyor mu?" sorusudur.

### 3. Refactor (İyileştir - Kodu Temizle)
Kod çalışıyor ama iyileştirilmeli:
- Kod tekrarlarını kaldır
- Daha okunabilir hale getir
- Gereksiz karmaşıklığı azalt
Ama önemli kural:
- Testler hâlâ geçiyor olmalı

Testler güvenlik ağı görevi görür, herhangi bir kırılma anında fark edilir.

## Basit Bir Örnek (Javascript)
Bir fonksiyon yazılacak. Fonksiyon da ise 2 sayı toplansın.

### 1.Test yaz
```
    test("iki sayıyı toplar", () => {
        expect(sum(2, 3)).toBe(5);
    });
```

- Bu test çalıştırıldığında hata verecek çünkü `SUM` fonksiyonu yok.

### 2.Minimum kod yaz
```
    function sum(a, b) {
        return a + b;
    }
```

- Test artık geçerli

### 3.Refactor
- Şu an gerek yok ama karmaşık olsaydı düzenlerdik.

## TDD'nin Sağladığı Avantajlar
- Daha Az Hata
    - Kod daha yazılırken test edildiği için bug’lar erken yakalanır.
- Daha Temiz Kod
    - Refactor aşaması seni daha iyi kod yazmaya zorlar.
- Güvenli Geliştirme
    - Yeni bir özellik eklediğinde eski kodu bozup bozmadığını testler sayesinde anlarsın.
- Canlı Dokümantasyon
    - Testler, kodun nasıl çalıştığını anlatan bir rehber gibidir.
    - Testler → “Bu kod ne yapıyor?” sorusunun cevabıdır.

## TDD'nin Deazavantajları
TDD her zaman kolay değildir:
- Başlangıçta yavaş hissettirebilir
- Öğrenmesi zaman alır
- Her senaryoya uygun değildir (özellikle UI/animasyon)
Ama uzun vadede ciddi zaman kazandırır.

## TDD vs Klasik Geliştirme
|Yaklaşım       |Süreç                  |
|---------------|-----------------------|
|Klasik         |Kod → Test             |
|TDD        	|Test → Kod → Refactor  |

## Frontend Geliştiriciler için TDD
Frontend tarafında TDD kullanımı biraz daha seçicidir.

**TDD'nin en çok uygun olduğu yerler:**
- Utility fonksiyonlar (formatlama vs.)
- API işlemleri
- State yönetimi
- Business logic

**Daha az uygun olduğu yerler**
- UI tasarım
- Animasyonlar
- Pixel-perfect işler

**React tarafında genelde:**
- Jest
- React Testing Library kullanılır.

# TDD Mantığını Doğru Anlamak
TDD'nin özü şu:
```
    Kodu yazmadan önce, kodun nasıl davranması gerektiğini tanımla.
```

Bu yaklaşım:
- Daha planlı
- Daha kontrollü
- Daha profesyonel bir geliştirici yapar

# Sonuç olarak
Test Güdümlü Geliştirme ilk başta alışılması zor bir yaklaşım olabilir. Ama bir kez mantığını kavradığında şunu fark edersin:
```
    Kod yazmıyorsun, aslında davranış tasarlıyorsun.
```
