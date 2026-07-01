# OPEN GRAPH (OG) NEDİR?
**Open Graph,** bir sayfa sosyal medyada paylaşıldığında:
``` Başlık - Açıklama - Görsel - Url```
gibi bilgilerin nasıl görüneceğini belirleyen meta etiketleridir. Bu etiketler olmadan da bir link paylaşılabilir, ama platform o zaman sayfadan tahminle bilgi toplamaya çalışır (ilk bulduğu başlığı, ilk bulduğu görseli vs. kullanır) ve sonuç genelde kötü görünür. Open Graph bu tahmin işini ortadan kaldırıp, `kartın tam olarak şöyle görünmesini istiyorum` demenizi sağlar.
- Facebook tarafından 2010 yılında geliştirilmiştir.
- Ama **Instagram, Whatsapp, Linkedin, Slack, Discord, Telegram, Pinterest** gibi birçok platform tarafından kullanılır.
- Teknik olarak bu etiketler sayfanın `<head>` bölümüne yazılır.

## Neden SEO ile Birlikte Düşünülür?
- Paylaşım kartı düzgün görünürse
- Kullanıcı daha çok tıklar (CTR artar)
- Sayfaya daha fazla trafik gelir
- Bu da Google'a olumlu kullanıcı sinyali gönderir.

Dolaylı Seo etkisi buradan gelir.

**Önemli:** Open Graph, Google sıralamasını (ranking) doğrudan etkileyen bir faktör değildir. Google bu etiketleri "sıralama sinyali" olarak kullanmaz. 
**Etkisi tamamen dolaylıdır**; daha iyi görünen bir kart → daha çok tıklama → daha çok trafik ve paylaşım. Bunu net ayırmak önemli, çünkü bazı kaynaklar OG'yi doğrudan bir SEO faktörüymüş gibi anlatır, bu yanlıştır.

## Open Graph Meta Tag'leri Tek Tek Açıklama
### **Og:title** : Paylaşım başlığı
- Paylaşıldığında kalın büyük başlık olarak görünür
- Kısa - Markalı - Net
- İdeal uzunluk 40-60 karakter
- `<title>` etiketiyle aynı olmak zorunda değildir; sosyal medya için ayrı, daha "tıklanabilir" bir başlık yazılabilir

### **Og:description** : Alt açıklama
- Başlığın altında çıkan gri küçük metin
- Kullanıcıya "Bu link ne anlatıyor?" sorusunun cevabı
- İdeal uzunluk 110 - 160 karakter
- Reklam gibi değil net ve güven veren bir dil kullanılmalı

### **Og:image** : Paylaşım görseli
- Görsel Kuralları:
    - 1200 x 630px ideal
    - Jpg veya png (webp bazı platformlarda sorun çıkarabilir)
    - Https olmalı - Http bazeb yüklenmez
    - Sunucuda herkesin erişebileceği url (login gerektiren bir sayfadaki görsel çalışmaz)
    - Küçük görsel kırpılır veya hiç gösterilmeyebilir (minimum 200x200px, ama 600x315px altı önerilmez)
    - Relative path (örn: /images/og.jpg) çoğu platformda görünmez, mutlaka tam url (https://site.com/images/og.jpg) yazılmalı
    - Dosya boyutu mümkünse 1MB altında tutulmalı, bazı platformlar büyük dosyaları reddeder
    - Ek olarak şu etiketler de eklenebilir:
    ```
        <meta property="og:image:width" content="1200" />
        <meta property="og:image:height" content="630" />
        <meta property="og:image:alt" content="Görselin açıklaması" />
    ```
    - og:image:width/height yazılmazsa, bazı platformlar görseli indirip boyutunu kendi hesaplamak zorunda kalır; bu da kartın bazen geç veya hatalı görünmesine sebep olabilir.

### **Og:url** : Paylaşılan link
- Sosyal medya şunu sorar; "Bu içerik hangi sayfaya ait?"
- Cannonical gibi düşün:
    - Aynı içerik farklı Url'lerde varsa (örn. ?utm_source=... gibi parametrelerle)
    - Asıl (temiz) url'yi belirtir
- Bu sayede paylaşım sayısı (like/share count) tüm varyasyonlar için tek url'de toplanır, dağılmaz

### **Og:type** : İçerik türü
- "Bu sayfa ne tür bir içerik?" sorusunun cevabı

| **Tür**          | **Nerede**          |
|------------------|---------------------|
| website          | Ana sayfa, kategori |
| article          | Blog yazısı         |
| product          | Ürün sayfası        |
| profile          | Kişi profili        |
| video.other      | Video içerikleri    |
| music.song       | Müzik içerikleri    |

- og:type "article" seçilirse, ek olarak şu etiketler de kullanılabilir:

```
    <meta property="article:published_time" content="2026-06-01T10:00:00+03:00" />
    <meta property="article:modified_time" content="2026-06-15T14:30:00+03:00" />
    <meta property="article:author" content="Yazar Adı" />
    <meta property="article:section" content="Teknoloji" />
    <meta property="article:tag" content="seo, open graph" />
```

### **Og:site_name** : Marka adı
- Kartta bazen:
    - `Kaynak:TestSitesi` şeklinde görünür
- Güven hissi verir
- Marka bilinirliği sağlar

### **Og:locale** : Dil / bölge bilgisi (sık unutulan bir etiket)
```
    <meta property="og:locale" content="tr_TR" />
```
- Sayfanın hangi dilde / bölgede olduğunu belirtir.
- Format: dil_ÜLKE (örn: tr_TR, en_US)
- Site birden fazla dilde yayın yapıyorsa og:locale:alternate ile diğer diller de belirtilebilir:
```
    <meta property="og:locale:alternate" content="en_US" />
```

### **og:video / og:audio** — Video ve ses içerikleri (opsiyonel)
- Sayfa bir video veya ses barındırıyorsa, bunu doğrudan oynatılabilir şekilde kart içine gömmek için kullanılır:
```
    <meta property="og:video" content="https://site.com/video.mp4" />
    <meta property="og:video:type" content="video/mp4" />
    <meta property="og:video:width" content="1280" />
    <meta property="og:video:height" content="720" />
```

### **fb:app_id** (Facebook özelinde, opsiyonel)
- Facebook'ta paylaşım analitiklerini (insights) görebilmek için bazen istenir:
```
    <meta property="fb:app_id" content="1234567890" />
```
- Zorunlu değildir, sadece Facebook üzerinden detaylı istatistik takibi isteyenler için önemlidir.

## Instagram - Facebook - Whatsapp Farkı Var Mı? 
- Ayrı ayrı meta yazılmaz, open graph (og) meta tag'larını kullanır.
- Hepsi og okur
    - **Facebook:** Open Graph
    - **Instagram:** Facebook altyapısını, yani og'yi kullanır (Instagram linklerde tıklanabilir kart göstermez ama Story/DM paylaşımlarında ve bio linklerde og bilgisi kullanılır)
    - **WhatsApp / LinkedIn / Messenger:** Facebook OG kullanır
    - **Hepsi için yeterli:** <meta property="og:*" />
- Teknik olarak fark yok, görsel sunum farkı var

| **Konu**          | **Facebook**          | **Instagram**          |
|-------------------|-----------------------|------------------------|
| Meta standardı    | Open Graph            | Open Graph             |
| Görsel önceliği   | Yüksek                | Çok yüksek             |
| Description       | Görünür               | Çoğu zaman kısaltılır  |
| Cache             | Var                   | Var                    |

### Twitter için:
- Twitter og'yi okur
- Ama kendi etiketleriyle daha iyi render eder

```
    <meta name="twitter:card" content="summary_large_image" />
    <meta name="twitter:title" content="Ahlatcı Kuyumculuk | Altın & Pırlanta" />
    <meta name="twitter:description" content="Altın, pırlanta ve özel tasarım takılar." />
    <meta name="twitter:image" content="https://www.ahlatcistore.com.tr/images/og-home.jpg" />
```

## Facebook & Instagram Open Graph Nasıl Çalışır?
Bir url paylaşıldığında:
- Facebook botu (crawler) sayfayı ziyaret eder
- `<head>` içindeki `og:` meta'ları okur
- Sonucu kendi sunucusunda cache'ler (sayfayı her paylaşımda yeniden okumaz)
- Paylaşım kartını oluşturur
- Instagram da aynı sistemi kullanır

## Cache Sorunu (sık karşılaşılan bir problem)
- Open Graph etiketlerini değiştirdiğinizde, Facebook/WhatsApp eski görseli/başlığı göstermeye devam edebilir. Bunun sebebi cache'dir. Çözüm için:
    - Facebook Sharing Debugger (`developers.facebook.com/tools/debug`) üzerinden url girilip "Scrape Again" (yeniden tara) butonuna basılmalı
    - WhatsApp kendi cache'ini tutar, bazen sadece linki farklı şekilde (örn. sonuna `?v=2` ekleyerek) tekrar paylaşmak gerekebilir

## Twitter Card Nedir?
- Twitter (X) için özel meta'lardır.
- Ama çoğu platform OG'si yoksa Twitter Card'a bakar.

### **twitter:card**
- **Örnek :** <meta name="twitter:card" content="summary_large_image" />
- Paylaşım kartının görsel boyutunu belirler.
- **Türler :**

| **Değer**             | **Anlam**                         |
|-----------------------|-----------------------------------|
| summary               | Küçük görsel                      |
| summary_large_image   | Büyük görsel (önerilem)           |
| app                   | Mobil uygulama tanıtım kartı      |
| player                | Video/ses oynatıcı gömülü kart    |

### **twitter:title**
- **Örnek :** <meta name="twitter:title" content="Test Sitesi" />
- Twitter'da görünen başlık
- OG title yoksa burayı kullanır

### **twitter:description**
- **Örnek :** <meta name="twitter:description" content="Test içeriği" />

### **twitter:image**
- **Örnek :** <meta name="twitter:image" content="https://site.com/og.jpg" />

### twitter:site / twitter:creator (opsiyonel ama önerilir)
```
    <meta name="twitter:site" content="@markaadi" />
    <meta name="twitter:creator" content="@yazaradi" />
```
- `twitter:site` : içeriğin ait olduğu markanın Twitter hesabı
- `twitter:creator` : içeriği yazan kişinin twitter hesabı

## Open Graph Protokolü Teknik Detay: prefix Tanımı

Standartlara tam uyum için `<html>` etiketine bir "namespace" (isim alanı) eklenmesi önerilir. Zorunlu değildir, çoğu platform bunsuz da çalışır, ama W3C standardına göre doğrusu budur:
```
    <html prefix="og: https://ogp.me/ns#">
```
## Test ve Doğrulama Araçları (çok önemli, sık atlanan bir adım)

Meta etiketleri yazdıktan sonra mutlaka şu araçlarla kontrol edilmeli:
- Facebook Sharing Debugger — developers.facebook.com/tools/debug (Facebook + Instagram + WhatsApp için)
- Twitter Card Validator — cards-dev.twitter.com/validator
- LinkedIn Post Inspector — linkedin.com/post-inspector

Bu araçlar hem hata varsa gösterir hem de cache'i temizleyip kartı yeniden tarar.

## Sık Yapılan Hatalar
- Görsel url'sini relative (/img/og.jpg) yazmak — mutlaka tam url olmalı
og:image boyutunun çok küçük veya orantısız olması
- Değişiklik yaptıktan sonra debugger ile cache'i yenilememek
og:title ve `<title>` etiketini karıştırıp ikisini de aynı yazmak zorunda hissetmek (aslında farklı amaçlara hizmet edebilirler)
- og:url yazmamak — bu durumda paylaşım sayıları farklı url varyasyonlarına dağılabilir
- Sadece anasayfa için OG yazıp diğer sayfaları (blog, ürün vs.) boş bırakmak — her sayfanın kendine ait, o sayfaya özel OG etiketleri olmalı

## Open Graph - Meta - Schema Farkı
- Birbirinin yerine geçmezler.

| **Yapı**              | **Amaç**                      |
|-----------------------|-------------------------------|
|Meta title/description	| Google arama                  |
|Open Graph             | Sosyal paylaşım               |
|Twitter Card           | Twitter / X                   |
|Schema                 | Arama motoru anlamlandırma    |

- Kısa Özet:
    - Open graph = sosyal vitrin
    - Görsel en önemli parça
    - Canonical ile uyum şart
    - Seo'ya dolaylı katkı sağlar.

## Örnek: Tam Bir Head Bloğu
Tüm konuyu tek bir örnekte toplarsak, gerçek bir sayfada `<head>` içi şöyle görünür:
```
    <html prefix="og: https://ogp.me/ns#">
    <head>
    <title>Ahlatcı Kuyumculuk | Altın & Pırlanta</title>
    <meta name="description" content="Altın, pırlanta ve özel tasarım takılar." />

    <meta property="og:title" content="Ahlatcı Kuyumculuk | Altın & Pırlanta" />
    <meta property="og:description" content="Altın, pırlanta ve özel tasarım takılar." />
    <meta property="og:image" content="https://www.ahlatcistore.com.tr/images/og-home.jpg" />
    <meta property="og:image:width" content="1200" />
    <meta property="og:image:height" content="630" />
    <meta property="og:url" content="https://www.ahlatcistore.com.tr/" />
    <meta property="og:type" content="website" />
    <meta property="og:site_name" content="Ahlatcı Kuyumculuk" />
    <meta property="og:locale" content="tr_TR" />

    <meta name="twitter:card" content="summary_large_image" />
    <meta name="twitter:title" content="Ahlatcı Kuyumculuk | Altın & Pırlanta" />
    <meta name="twitter:description" content="Altın, pırlanta ve özel tasarım takılar." />
    <meta name="twitter:image" content="https://www.ahlatcistore.com.tr/images/og-home.jpg" />
    </head>
```

## Kısa Özet
- Open Graph = sosyal vitrin
- Görsel en önemli parça
- Canonical/og:url ile uyum şart
- SEO'ya doğrudan değil, dolaylı katkı sağlar (tıklama oranı üzerinden)
- Her sayfanın kendine ait OG etiketleri olmalı, tek bir genel etiket seti yetmez
- Değişiklik sonrası mutlaka Facebook Sharing Debugger / Twitter Card Validator ile test edilmeli, aksi halde eski (cache'li) kart görünmeye devam eder