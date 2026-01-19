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