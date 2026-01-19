# JavaScript Array Methodları

Bu dokümanda JavaScript’te sık kullanılan `filter()`, `map()` ve `sort()` dizi metotları açıklanmaktadır.

Bu metotlar yinelemeli (iterative) metotlardır ve diziler üzerinde işlem yaparken orijinal diziyi değiştirip değiştirmemelerine göre farklı davranırlar.

## `filter()` Method
`filter()` metodu, verilen dizinin **sığ (shallow) bir kopyasını** oluşturur ve bu yeni dizi, **sağlanan koşulu (testi) geçen elemanları** içerir.

Orijinal diziyi **değiştirmez**.

### Kullanım Amacı
- Belirli bir koşula uyan elemanları seçmek
- Bir diziyi elemek / filtrelemek
- Sonuç olarak daha küçük bir dizi elde etmek

### Örnek : 

    const words = ["spray", "elite", "exuberant"];
    const result = words.filter((word) => word.length === 5);

### Sonuç : 

    ["spray", "elite"]

### Parametreler : 

    filter(callbackFn)
    filter(callbackFn, thisArg)

### `callbackFn`

Dizideki **her eleman** için çalıştırılan fonksiyondur. Elemanın yeni dizide kalabilmesi için:

- true (truthy) → diziye eklenir
- false (falsy) → diziye eklenmez

Callback fonksiyonu şu argümanlarla çağrılır:
- element → Şu anda işlenen eleman
- index → Elemanın indeksi
- array → filter() metodunun çağrıldığı dizi

### `thisArg` (opsiyonel)

`callbackFn` içinde `this` olarak kullanılacak değeri belirtir.

### Dönüş Değeri
- Koşulu geçen elemanlardan oluşan yeni bir dizi
- Eğer hiçbir eleman koşulu geçmezse boş bir dizi ([])

### Önemli Notlar
- `filter()` yinelemeli bir metottur
- Seyrek (sparse) dizilerde boş elemanlar için çalışmaz
- Orijinal diziyi değiştirmez
- Sadece koşulu sağlayan elemanları döndürür

---

## `map()` Method
`map()` metodu, bir dizinin her bir elemanını belirli bir işlemden geçirerek yeni bir dizi oluşturur.

Orijinal diziyi **değiştirmez.**

### Kullanım Amacı

- Dizideki tüm elemanları dönüştürmek
- Her eleman üzerinde aynı işlemi uygulamak
- Aynı uzunlukta ama farklı değerlere sahip bir dizi üretmek

### Örnek
    const array = [1, 4, 9, 16];
    const mapped = array.map((x) => x * 2);

## Sonuç :
    [2, 8, 18, 32]

## Parametreler
    map(callbackFn)
    map(callbackFn, thisArg)

### `callbackFn`

Fonksiyonun **dönüş değeri**, yeni dizinin bir elemanı olur.

Callback şu argümanlarla çağrılır:
- element → Şu anda işlenen eleman
- index → Elemanın indeksi
- array → map() metodunun çağrıldığı dizi

### `thisArg` (opsiyonel)
Callback içinde `this` olarak kullanılacak değer.

### Dönüş Değeri
- Callback fonksiyonunun dönüş değerlerinden oluşan yeni bir dizi

### Önemli Notlar
- `map()` yinelemeli bir metottur
- Seyrek dizilerde boş elemanlar için çalışmaz
- Orijinal diziyi değiştirmez
- Yeni dizi döndürdüğü için, sonucu kullanmadan çağırmak anti-pattern’dir
(Bu durumda `forEach` veya `for...of` tercih edilmelidir)