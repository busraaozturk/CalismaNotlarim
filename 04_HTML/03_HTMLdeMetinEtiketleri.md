# HTML'de Metin Etiketleri
HTML'de metin oluştururken yalnızca içeriğin ekranda nasıl göründüğünü değil, **o içeriğin ne anlama geldiğini** de tanımlarız.

Örneğin bir metni kalın göstermek istediğimiz için doğrudan `<strong>` kullanmak doğru bir yaklaşım değildir. Önce şu soruyu sormamız gerekir:
```
    Bu metin neden vurgulanıyor ve içerikteki anlamı nedir?
```
HTML bize paragraflardan alıntılara, önemli ifadelerden silinmiş içeriklere kadar farklı anlamları ifade eden elementler sunar.

Bu bölümde temel metin elementlerini ve aralarındaki önemli farkları inceleyeceğiz.

## Metin Elementlerinin Görevi
HTML'in temel amacı içeriğin görünümünü değil, yapısını ve anlamını tanımlamaktır.

Örneğin: `<strong>Önemli bilgi</strong>` kullanırken amacımız, `"Bu metin kalın görünsün."` demek değildir.

Asıl ifade ettiğimiz: `"Bu içerik güçlü bir öneme sahip."` bilgisidir.

Metnin nasıl görüneceği CSS ile değiştirilebilir.

Bu nedenle HTML elementi seçerken, `Nasıl görünsün?` yerine, `Bu içerik ne anlama geliyor?` sorusunu sormak daha doğru bir yaklaşımdır.

### Block ve Inline Element Mantığı
Metin elementlerini öğrenirken **block ve inline** kavramlarını temel seviyede bilmek yararlıdır.

Örneğin `<p>` bir paragraf oluşturur:
```
    <p>Birinci paragraf.</p>
    <p>İkinci paragraf.</p>
```
Paragraflar normal akışta ayrı bloklar olarak yer alır. Buna karşılık `<strong>` metnin içerisinde kullanılabilir:
```
    <p>
        Siparişinizi tamamlamak için
        <strong>adres bilgilerinizi kontrol edin.</strong>
    </p>
```
Buradaki **strong**, paragrafın içerisinde kalır.

Basitçe:
```
    Block → Belge akışında ayrı bir blok oluşturur.

    p
    div
    ...

    Inline → Metin akışının içerisinde yer alır.

    strong
    em
    span
    ...
```
Ancak block ve inline ayrımını yalnızca görünüş üzerinden düşünmemek gerekir. CSS ile bir elementin görsel display davranışı değiştirilebilir.

Bu bölümdeki ayrım, elementlerin HTML içerisindeki doğal kullanımını anlamamıza yardımcı olmak içindir.

## Paragraf ve Ayırıcılar
Metin içeriği oluştururken en temel elementlerden üçü:
- p
- br
- hr elementleridir.

Fakat görevleri birbirinden farklıdır.

### 1.`<p>` — Paragraf
`<p>` elementi bir paragrafı temsil eder.

Örneğin:
```
    <p>
        HTML, web sayfalarının yapısını oluşturmak için kullanılan bir işaretleme dilidir.
    </p>
```
Birbirinden ayrı düşünceleri farklı paragraflara ayırabiliriz:
```
    <p>
        HTML sayfanın yapısını ve içeriğin anlamını tanımlar.
    </p>

    <p>
        CSS ise sayfanın görsel sunumunu yönetir.
    </p>
```
Bu kullanım yalnızca görsel olarak iki metin arasında boşluk oluşturmaz. Aynı zamanda `Bunlar iki ayrı paragraftır.` anlamını verir.

**`<p>` İçerisinde Her Element Kullanılabilir mi?**
Hayır. Örneğin bir paragrafın içerisine başka bir paragraf yerleştirilmez.

Yanlış:
```
    <p>
        Birinci paragraf.

        <p>
            İkinci paragraf.
        </p>
    </p>
```
Benzer şekilde:
```
    <p>
        Metin

        <div>
            İçerik
        </div>
    </p>
```
şeklinde bir yapı da doğru değildir.

Paragrafların içerisinde metin akışına uygun içerikler kullanılmalıdır.

Örneğin:
```
    <p>
        HTML öğrenirken
        <strong>semantik kullanıma</strong>
        dikkat etmek önemlidir.
    </p>
```
doğru bir kullanımdır.