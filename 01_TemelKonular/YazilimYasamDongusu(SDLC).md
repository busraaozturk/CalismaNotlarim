# YAZILIM YAŞAM DÖNGÜSÜ (SDLC - Software Development Life Cycle)
`Bir fikrin çalışan bir yazılıma dönüşme yolculuğu.`

Bir yazılım projesinin başlangıcından sonuna kadar geçtiği aşamaların bütünüdür.
Amaç, yüksek kaliteli yazılımı planlı, ölçülebilir ve tekrarlanabilir bir süreçte üretmektir.

Yazılım yaşam döngüsü, bir yazılımın:
- fikir aşamasından başlayıp
- geliştirilip
- test edilip
- yayınlanıp
- bakımının yapılmasına kadar geçen sürecin tamamıdır.
Yani kısaca, `Bir yazılım nasıl doğar, büyür ve yaşar?` sorusunun cevabıdır.

Bir yazılım; fikir, analiz, planlama, tasarım, geliştirme, test ve bakım süreçlerinin birleşimidir. Bu süreçlerin tamamına **Yazılım Yaşam Döngüsü (SDLC)** denir.

Bu döngüyü anlamadan yazılım geliştirmek, temelsiz bina yapmaya benzer. Ayakta durabilir ama sürdürülebilir olmaz.

Yazılım geliştirme süreci şu adımlardan oluşur:
```
    Planlama → Analiz → Tasarım → Geliştirme → Test → Yayınlama → Bakım
```
Bu adımlar bir defa çalışıp bitmez. Özellikle modern projelerde bu süreç sürekli tekrar eder.

## Temel Aşamalar
### Planlama (Planing)
`Bu projeyi nasıl yöneteceğiz?`
`Nasıl ve Ne zaman yapılacak?`

Pllanlama, yazılım sürecinin yönünü belirleyen aşamadır. Burada henüz teknik detaylara girilmez; asıl odak, **projenin nasıl ilerleyeceğini** organize etmektir. Projenin kapsamı, kaynakları, maliyeti ve zaman çizelgesi belirlenir. Fizibilite analizi yapılır.

Bu aşamada ekip şunu netleştirir:
- Projenin kapsamı nedir?
- Ne kadar sürecek?
- Kim hangi sorumluluğu alacak?
- Hangi riskler var?
Yani planlama, yazılımın kendisini değil, **yazılımın üretim sürecini tasarlar.**

**Gerçek Hayattan Örnek**
Bir proje için şöyle bir plan yapılabilir:
- 1.hafta → Gereksinim analizi
- 2–3. hafta → Tasarım
- 4–6. hafta → Geliştirme
- 7.hafta → Test ve dağıtım
Aynı zamanda görev dağılımı yapılır:
- Frontend → UI geliştirme
- Backend → API ve veri yönetimi

**Bu Aşamanın Çıktısı**
- Proje zaman planı (timeline)
- Görev listeleri
- Risk Analizi
Eğer planlama yapılmazsa, proje ya uzar ya da kontrolsüz büyür.

### Gereksinim Analizi (Requirement Analysis)
`Gerçekten neye ihtiyacımı var?`
`Ne yapılacak?`

Müşteri ve paydaşlardan ihtiyaçlar toplanır. Sorulara yanıt aranır. Fonksiyonel ve fonksiyonel olmayan gereksinimler belgelenir. Plan yaptıktan sonra, artık ürünün kendisine odaklanılır. Burada yapılan en büyük hata, yüzeysel düşünmektir. Çünkü kullanıcı çoğu zaman ne istediğini net ifade edemez. Bu yüzden ihtiyaçlar **derinlemesine analiz edilir.**

Bu aşamada yapılanlar:
- Kullanıcı senaryoları yazılır
- Fonksiyonel gereksinimler belirlenir
- Sistemden beklenen davranışlar tanımlanır

**Bu Aşamanın Çıktısı**
- Gereksinim dokümanı (SRS)
- Kritik gerçek:
    - Yanlış analiz = doğru kod bile yanlış ürün üretir.

### Tasarım (Design)
`Bu sistemi nasıl kuracağız ve nasıl görünecek?`
`Sistemin görünümü ve yapısı nasıl olacak?`
`Nasıl yapılacak?`

Sistem mimarisi, veritabanı yapısı, kullanıcı arayüzü ve teknik altyapı tasarlanır. 

Tasarım aşaması genelde ikiye ayrılır ve genelde UI tasarımı görünür ama arka planda çok daha fazlası vardır.

**1. Kullanıcı Arayüzü (UI / UX)**

Burada kullanıcı ile yazılım arasındaki etkileşim planlanır.
- Kullanıcı ilk ne görecek?
- Butonlar nerede olacak?
- Hangi işlem hangi akışı takip edecek?

Amaç sadece güzel görünmek değil, kullanıcının düşünmeden kullanabileceği bir deneyim oluşturmak.

Bu aşamada:
- Ekranlar çizilir (Figma vs.)
- Kullanıcı deneyimi planlanır

Araçlar:
- Figma
- Adobe XD

**2. Sistem Tasarımı (Architecture)**
Bu aşamada yazılımın teknik yapısı kurulur:
- Katmanlı mimari mi olacak? (MVC mi? Microservice mi?)
- API yapısı nasıl olacak?
- Veri akışı nasıl ilerleyecek?
Bu kısım yazılımın iskeletidir.

**Örneğin:** (Dosya yükleme uygulaması)

Frontend tarafında:
- Upload component
- Progress state yönetimi
- API entegrasyonu
Backend tarafında:
- Dosya upload endpoint
- Veritabanı kayıtları

Bu aşamada:
- UI tasarımı
- Mimari diyagramlar
- API tanımları

```
    İyi tasarım = kolay geliştirme + az hata
    Yanlış mimari = ileride refactor kabusu
```

### Geliştirme (Development / Kodlama)
`Tasarımları gerçeğe dönüştürme.`

Tasarım dokümanlarına göre yazılım kodlanır. Geliştiriciler modülleri yazar ve entegre eder. Kritik olan şey sadece kod yazmak değil, doğru yapıyı koruyarak kod yazmaktır.

Burada sadece kod yazılmaz, aynı zamanda:
- Önceden planlanan yapıya sadık kalınır
- Modüler ve okunabilir kod yazılır
- Takım içinde uyum sağlanır

İyi kod:
- Okunabilir
- Modüler
- Genişletilebilir olmalıdır

Bu aşamada yapılanlar:
- Frontend geliştirme
- Backend geliştirme
- Veritabanı işlemleri
- API entegrasyonu

Frontend açısından:
- UI kodlanır
- API entegrasyonu yapılır
- Kullanıcı etkileşimleri yönetilir
Backend açısından:
- İş mantığını yazar
- Veritabanı ile iletişim kurar

Bu aşamada:
- Çalışan yazılım (ama henüz canlı değil)

```
    İyi developer = Sadece çalışan kod yazan değil, okunabilir ve sürdürülebilir kod yazandır.
```

### Test (Testing)
`Gerçekten çalışıyor mu?`
Kod yazıldıktan sonra en kritik aşamalardan biri testtir. Test yapılmadan yayınlanan bir yazılım *kullanıcıyı tester yapar.* Yazılım, hata ve eksikliklere karşı çeşitli testlerden geçirilir.

Test Türleri:
- Unit Test (Birim Test) : Kodun en küçük parçaları test edilir. Tek bir fonksiyon test edilir.
- Entegrasyon Testi (Integration Test): Modüllerin birbirleriyle uyumunun testi.
- Kullanıcı Kabul Testi (UAT): Son kullanıcının beklentilerinin karşılanıp karşılanmadığı test edilir.

```
    Test yapılmazsa Bug dolu ürün çıkar.
```

### Dağıtım (Deployment)
`Yazılım kullanıcıya açılması`

Yazılım geliştirme ortamından çıkar yani test edilen yazılım canlı ortama alınır ve gerçek kullanıcıyla buluşur.

Yapılan işlemler:
- Sunucuya yüklenir
- Domain bağlanır
- Ortam ayarları (production config)
- Canloya alınır (CI/CD süreçleri / otomatik deploy)

**Örnek:**
- Localhost → gerçek domain
- Test ortamı → canlı ortam

```
    **'Çalışıyor'** demek yerine **'Her ortamda çalışıyor'** olmalı.
```

**Bu aşamada:**
- Kullanılabilir
- Erişilebilir sistem

### Bakım ve İyileştirme (Maintenance & Improvement)
`Yazılımı canlı tutmak`

Yazılım canlıya çıktıktan sonra döngü sona ermez.

Bu aşamada yazılım:
- Geliştirilir : Yeni özellikler eklenir (Upgrade)
- Güncellenir : Kullanıcıdan gelen geri bildirimlerle
- İyileştirilir : Sistem performansı izlenir ve optimize edilir

Yazılım yayınlandıktan sonra süreç bitmez, aksine başlar. Güncel ve yaşayan yazılım vardır.

```
    Yazılım en uzun süresi (%60-70) bu aşamada geçer.
```

## Sonuç : Bu Bir Döngüdür
Bu süreç sürekli tekrar eder:
- Yeni ihtiyaç çıkar
- Tekrar analiz edilir
- Yeniden geliştirilir
Yani :
- Yazılım Geliştirme = Sürekli evrim

![alt text](/01_TemelKonular/images/yazilimyasamdongususemasi.png)

# YAYGIN KULLANILAN SDLC MODELLERİ
Yazılım geliştirme sürecini nasıl yöneteceğini belirleyen yaklaşımlar
Yazılım yaşam döngüsünü öğrendikten sonra ortaya şu soru çıkar:

`Tamam, bu aşamalar var… ama bunları nasıl uygulayacağız?`

İşte bu sorunun cevabı SDLC modelleridir.

Her model, aynı aşamaları içerir ama:
- sırası
- esnekliği
- geri dönüş şekli
- risk yönetimi farklıdır.

## 1. Waterfall Model (Şelale Modeli)
**Adım adım sırayla ilerler, geri dönüşü zor klasik yaklaşım.**

Waterfall modeli, yazılım dünyasının en eski ve en geleneksel modelidir. Mantığı oldukça basittir. Bu aşama bitmeden diğerine geçilmez, katıdır.

### Süreç nasıl işler?
- Gereksinimler toplanır
- Tasarım yapılır
- Geliştirme başlar
- Test edilir
- Yayınlanır
Her aşama tamamlanmadan diğerine geçmek **mümkün değildir.**

### Ne zaman kullanılır?
- Gereksinimler çok net ve değişmeyecekse
- Küçük ve basit projelerde
- Regülasyon gerektiren sistemlerde (örneğin bankacılık)

### Dezavantajları
- Değişiklik yapmak çok zordur
- Hatalar geç fark edilir
- Kullanıcı geri bildirimi geç gelir
- Esnek değildir, test aşaması en sonda olduğu için hataları düzeltmek maliyetlidir.

```
    Waterfall modeli, teoride düzenli görünür ama gerçek hayatta **'İhtiyaçlar değişir'** gerçeğine pek dayanamaz.
```

## 2. Agile Model (Çevik Model)
**Esneklik ve sürekli gelişim odaklı modern yaklaşım**

Günümüz yazılım dünyasının en çok kullanılan yaklaşımıdır. Temel mantığı, **`Büyük projeyi küçük parçalara böl ve sürekli geliştir.`**

### Nasıl çalışır?
- Proje küçük parçalara bölünür (feature / task)
- Her parça kısa sürede geliştirilir (Sprint)
- Kullanıcıdan geri bildirim alınır
- Süreç tekrar eder

### Sprint nedir?
Genelde:
- 1–2 haftalık geliştirme döngüsü
- Her sprint sonunda **çalışan bir parça ortaya çıkar.**

### Avantajları
- Değişime açıktır
- Hatalar erken yakalanır
- Kullanıcı sürece dahil olur
- Hızlı geri bildirim

### Dezavantajları
- Sürekli iletişim gerektirir
- Plansız ekiplerde kaosa dönüşebilir

```
Agile şunu kabul eder:

    'Başta her şeyi bilemezsin, süreç içinde öğrenirsin.'
```

## 3. Scrum
**Agile’ın en yaygın kullanılan uygulama yöntemi**

Scrum aslında başlı başına bir model değil, Agile’ın nasıl uygulanacağını anlatan bir çerçevedir. Scrum sadece teknik değil, aynı zamanda ekip yönetim modelidir

### Roller
- Product Owner → Ne yapılacağını belirler
- Scrum Master → Süreci yönetir
- Developer Team → Geliştirir

### Süreç
- Sprint planlanır
- Geliştirme yapılır
- Daily meeting yapılır
- Sprint sonunda demo yapılır
- Retrospective ile süreç değerlendirilir

## 4. Iterative Model (Yinelemeli Model)
**Küçük parçalarla gelişen yaklaşım.**

Bu modelde yazılım tek seferde değil, **parça parça geliştirilir.**

### Mantık:
- İlk versiyon yapılır (basit)
- Üzerine ekleme yapılır
- Sürekli iyileştirilir

**Örnek:**
1. Versiyon → sadece upload
2. Versiyon → progress bar
3. Versiyon → hata yönetimi

### Avantaj
- Erken çalışan sistem elde edilir
- Gelişim kontrollüdür

### Dezavantaj
- Başta iyi plan yapılmazsa sistem dağılır

## Incremental Model
**Parça parça ama planlı büyüme**

Iterative ile karıştırılır ama farkı şudur:
- Her parça bağımsız bir modül olarak geliştirilir

### Mantık:
- Sistem modüllere bölünür
- Her modül ayrı geliştirilir
- Sonra birleştirilir

**Örnek:**
- Modül 1 → Login
- Modül 2 → Upload
- Modül 3 → Dashboard

### Avantaj
- Paralel geliştirme yapılabilir
- Daha hızlı sonuç alınır

## Spiral Model
**Risk odaklı gelişmiş model**

Spiral model, özellikle büyük ve riskli projeler için kullanılır.

### Her döngüde:
- Planlama
- Risk analizi
- Geliştirme
- Test

### Avantaj
- Riskler erken fark edilir
- Büyük projelerde güvenlidir

### Dezavantaj
- Karmaşıktır
- Küçük projeler için gereksizdir

```
    Risk büyükse, kontrol de büyük olmalı
```

## 5. DevOps Model
**Geliştirme + operasyon birleşimi**

Modern yazılım dünyasında DevOps çok kritik hale gelmiştir.

### Mantık:
- Geliştirme ve deployment süreci entegre edilir

### Süreç:
- Kod yazılır
- Otomatik test edilir
- Otomatik deploy edilir
- Sürekli izlenir
### Araçlar:
- CI/CD pipelines
- Docker
- Kubernetes
### Avantaj
- Hızlı release
- Daha az hata
- otomasyon
```
    Kod yazmak yetmez, onu sürekli çalıştırabilmek gerekir.
```

## 6. Model Seçimi Nasıl Yapılır? 
En kritik soru:
- "Hangi model daha iyi?" değil
- "Hangi model bu projeye uygun?" olmalı

Basit bir rehber :
| Durum                     | Model       |
| ------------------------- | ----------- |
| Gereksinimler net         | Waterfall   |
| Değişim çok               | Agile       |
| Ekip organizasyonu        | Scrum       |
| Küçük parçalarla ilerleme | Iterative   |
| Modüler geliştirme        | Incremental |
| Büyük ve riskli proje     | Spiral      |
| Sürekli yayın             | DevOps      |


## Sonuç Olarak
SDLC modelleri şunu öğretir:
- Yazılım geliştirmek sadece teknik değil
- Aynı zamanda stratejik bir süreçtir

Eğer bu modeller anlaşılırsa:
- Projeye göre doğru yaklaşım seçilir
- Daha az hata yapılır
- Profesyonel düşünmeye başlanır

## SDLC Modelleri Karşılaştırma Tablosu

![alt text](/01_TemelKonular/images/sdlcmodelleri.png)