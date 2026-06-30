# Meta Tag'lar ve SEO Nedir?

Meta tag'lar, bir web sayfasının `<head>`bölümünde yer alan ve sayfanın içeriği hakkında tarayıcılara ve arama motorlarına bilgi veren küçük kod parçalarıdır.
Kullanıcı bunları sayfada görmez, ama Google bu bilgileri okuyarak sayfanın ne hakkında olduğunu anlar ve arama sonuçlarında nasıl görüneceğine karar verir.
Örneğin başlık (title) ve açıklama (description) meta'ları, kullanıcının Google'da arama yaptığında gördüğü mavi başlık ve altındaki kısa açıklama metnidir.
Doğru kullanılan meta tag'lar hem sıralamayı (ranking) hem de tıklanma oranını (CTR) doğrudan etkilediği için SEO'nun en temel ve en çok ihmal edilen parçalarından biridir.

## SEO Açısından En Sık Yapılan Hatalar : 
- Meta description'ı boş bırakmak
- Tüm sayfalarda aynı Title
- Schema’yı partial içinde veya sayfaya basmak
- Product schema'yı ana sayfada kullanmak

# Google'ın En Önem Verdiği Meta Tag'lar
## <title></title>
- Sıralamayı etkiler
- 50-60 karakter (yaklaşık bir kuraldır, Google aslında piksel genişliğine bakar — harfe göre değişebilir)
- Marka sona
- Her sayfa benzeersiz
- **Örnek :**
    <title>Notlar | Html - Css Notları</title>

## <meta name="description">
- CTR'yi etkiler (Tıklanma oranı)
- 140-160 karakter
- Ana anahtar kelime 1 kez
- Kopya olmamalı
- **Örnek :**
    <meta name="description" content="Html ve Css notlarının paylaşıldığı bir blok sayfası." />

## <link rel="canonical">
- Detaylı anlatım dokümanın sonunda (bkz. "Canonical Nedir?" bölümü)

## Robots Meta
- *Yanlış kullanılırsa siteyi yok eder, dikkat!*
- **Örnek :**
    <meta name="robots" content="index, follow" />

# Google'ın Sinyal Olarak Kullandığı Meta'lar
## Viewport (mobile SEO)
- <meta name="viewport" content="width=device-width, initial-scale=1" />
## Content-Type / Charset
- <meta charset="utf-8" />
## Language (HTML Tag Üzerinden)
- Meta değil ama çok önemli
- <html lang="tr">
## Hreflang (Çok Dilli Siteler İçin)
- <link rel="alternate" hreflang="tr" href="https://site.com/tr/" />
- Google'a hangi dildeki sayfanın hangi kullanıcıya gösterileceğini söyler
- Çok dilli/çok bölgeli sitelerde önemli bir sinyaldir

# Sosyal + Dolaylı SEO Etkili Meta'lar
## Open Graph (Google Dolaylı Server)
- Google sıralamayı etkilemez ama:
    - Paylaşım kalitesi
    - Trafik artışı
## Twitter Card

# Google'ın Kullanmadığı Meta'lar
Bu meta'lar eskiden SEO'da kullanılırdı ama Google artık bunları yok sayıyor, sadece bilgi amaçlı tutuluyor.
- Bunlar SEO'ya katkı sağlamaz
    - <meta name="keywords">
    - <meta name="author">
    - <meta http-equiv="refresh">
    - <meta name="generator">
    - <meta name="revisit-after">

# Net Yol Haritası
- _Layout.cshtml -> temel meta'lar
- Controller -> sayfa bazlı ViewBag
- Schema -> sadece uygun sayfada
- Search Console -> Url denetleme

# <link rel="canonical"> Nedir?
- Aynı içeriğe sahip birden fazla url varsa
- Google hangisini esas alacağını buradan öğrenir

## Neden Gerekli?
- Google için şu Url'ler ayrı sayfalardır.
```
    /urun/altin-yuzuk
    /urun/altin-yuzuk?ref=instagram
    /urun/altin-yuzuk?color=gold
    /urun/altin-yuzuk/
```
Ama içerik aynıdır.
- **Canonical Yoksa :**
    - SEO gücü bölünür 
    - Duplicate content oluşur
    - Sıralama düşebilir
- **Canonical Varsa :**
    - Tüm güç **tek URL'de** toplanır

## Google Canonical'ı Nasıl Kullanır?
- **Google canonical'i :**
    - Talep olarak görünür.
    - %100 zorunlu değildir.
    - Ama doğruysa çoğunlukla uyar.
- **Google şuna bakar:**
    - Canonical Url erişilebilir mi?
    - 200 dönüyor mu?
    - İçerik gerçekten aynı mı?

## Doğru Canonical Nasıl Olmalı?
- Mutlaka **<head>** içinde olmalı
- Mutlak (absolute) URL olmalı
    - **Yanlış :** <link rel="canonical" href="/urun/altin-yuzuk" />
    - **Doğru :** <link rel="canonical" href="https://www.ahlatcistore.com.tr/urun/altin-yuzuk" />
- Sayfa kendisini canonical göstermeli (self-referencing)
    - Ana sayfa bile : <link rel="canonical" href="https://www.ahlatcistore.com.tr/" />

## Hangi Sayfalarda Kullanılmalı?

| Sayfa Türü   | Canonical Durumu |
|---------------|------------------|
| Ana Sayfa     | ✅ |
| Ürün Detay    | ✅ |
| Kategori      | ✅ |
| Blog          | ✅ |
| Filtreli URL  | Canonical → Ana URL |
| Sayfalama     | Özel Durum |

**Sayfalama (Pagination) Detayı:**
- Eskiden rel="next"/"prev" kullanılırdı, Google artık bunu dikkate almıyor
- Her sayfalama sayfası (2., 3. sayfa vs.) kendi URL'ini canonical göstermeli
- Sayfalama sayfalarını ana kategoriye canonical ile yönlendirmek, o sayfaların indexlenmesini engeller — bu çoğu zaman istenmeyen bir durumdur

## En Sık Yapılan Canonical Hataları :
- Yanlış URL
- Tüm sayfalara aynı canonical 
- HTTP - HTTPS uyumsuzluğu
- Slash / non-slash tutarsızlığı
- Kategoriye canonical atayıp ürüne değil

## MVC Projede Doğru Kullanım
- **_Layout.cshtml**
    - <link rel="canonical" href="@ViewBag.Canonical" />
- **Ana Sayfa**
    - ViewBag.Canonical = "https://www.ahlatcistore.com.tr/";

**Bilgi !**
***Canonical ≠ Redirect***

| **Canonical**             | **Redirect** |
|---------------------------|--------------|
| Sayfa açık kalır          | URL değişir  |
| SEO sinyali birleştirir   | Kullanıcıyı taşır |
| Duplicate için            | URL değişimi için |

**Not:** Canonical yanlışsa SEO yanlış çalışır.