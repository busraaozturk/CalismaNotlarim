# Web Hosting Nedir?

***Web Hosting (Web Barındırma)***, bir web sitesine ait dosyaların **internet üzerinden sürekli erişilebilir olan bir sunucuda** saklanmasını sağlayan hizmettir. Bir web sitesinin tarayıcılar üzerinden görüntülenebilmesi için, siteye ait tüm dosyaların 7/24 çalışan bir sunucuda barındırılması gerekir.

Web Hosting, web siteniz için internette kiralanmış bir **depo alanıdır.**

## WEB BARINDIRMA ASLINDA NASIL ÇALIŞIR
Bir web sitesinin internette görüntülenebilmesi için alan adı, DNS ve barındırma sunucusu birlikte çalışır. Süreç temel olarak şu adımlarla gerçekleşir: 
- Web sitesinin dosyaları (HTML, CSS, JavaScript, görseller vb.) bir barındırma sunucusuna yüklenir.
- Alan adı, DNS aracılığıyla bu sunucunun IP adresine yönlendirilir.
- Bir kullanıcı tarayıcıya alan adını yazdığında, tarayıcı DNS üzerinden ilgili sunucuyu bulur.
- Barındırma sunucusu, istenen web sitesi dosyalarını tarayıcıya gönderir.
- Tarayıcı bu dosyaları yorumlayarak web sitesini kullanıcıya görüntüler.

Web sitesinin hızı, güvenliği ve kesintisiz çalışması; kullanılan barındırma türüne, sunucu kaynaklarına ve yapılandırılmasına bağlıdır.

![alt text](/01_TemelKonular/images/hosting-1.png)

Yukarıdaki akışta, tarayıcı ile sunucu arasındaki iletişimin hızlı ve kesintisiz olması, sunucunun sahip olduğu kaynaklara bağlıdır. Bu kaynaklar CPU, RAM, depolama ve bant genişliğidir.

* CPU işleme görevlerini yerine getirir; daha fazla güç daha hızlı sayfa oluşturma anlamına gelir. Sunucunun beyni gibidir.
* RAM aktif verileri yönetir; daha fazla bellek daha sorunsuz performans anlamına gelir.
* Depolama, ne kadar içeriği barındırabileceğinizi ve ne kadar hızlı alınacağını belirler.
* Bant genişliği, ne kadar veri aktarılabileceğini kontrol eder; daha yüksek limitler, trafik artışları altında daha iyi çalışma süresi anlamına gelir.

![alt text](/01_TemelKonular/images/hosting-2.png)

## NE TÜR WEB BARINDIRMA TÜRLERİ VAR?

Her biri farklı performans, kontrol ve ölçeklenebilirlik seviyeleri için tasarlanmış birkaç farklı biçimde gelir. Ana barındırma türlerini anlamak, ihtiyaçlarınıza ve bütçenize uygun planı seçmenize yardımcı olur. 

Aşağıda en yaygın barındırma seçeneklerinin bir dökümü bulunmaktadır.

| Barındırma Türü             | Maliyet                    | Kontrol / Kök Erişimi      | Performans               | Ölçeklenebilirlik        | En İyisi                                          | Tipik Sınırlar                                                         |
| --------------------------- | -------------------------- | -------------------------- | ------------------------ | ------------------------ | ------------------------------------------------- | ---------------------------------------------------------------------- |
| **Paylaşımlı Hosting**      | En düşük                   | Sınırlı                    | Temel                    | Düşük                    | Yeni başlayanlar, küçük siteler, bloglar          | Sınırlı depolama, bant genişliği ve CPU; trafik artışlarında yavaşlama |
| **VPS (Sanal Özel Sunucu)** | Orta                       | Kısmi (kök erişimi mümkün) | İyi                      | Orta                     | Büyüyen siteler, küçük işletmeler, geliştiriciler | Sanal bölüm başına kaynak limitleri                                    |
| **Özel Sunucu (Dedicated)** | Yüksek                     | Tam / Full                 | Mükemmel                 | Düşük (manuel ölçekleme) | Büyük işletmeler, yüksek trafikli siteler         | Tek bir fiziksel sunucunun donanımsal sınırları                        |
| **Bulut Hosting (Cloud)**   | Değişken (kullandıkça öde) | Tam / Full                 | Yüksek                   | Çok Yüksek               | Startup’lar, SaaS, ölçeklenebilir uygulamalar     | Kullanım arttıkça maliyet artar; teknik kurulum bilgisi gerekir        |
| **Reseller Hosting**        | Orta                       | Panel araçlarıyla sınırlı  | İyi (ana sunucuya bağlı) | Orta                     | Ajanslar, web tasarımcılar                        | Ana sunucunun kaynak planı ve müşteri limitleri ile sınırlıdır         |

- **Paylaşımlı Hosting (Shared Hosting) :**
    - Birden fazla web sitesi aynı sunucu ve kaynakları paylaşır.
    - Kurulumu kolay ve maliyeti düşüktür ancak trafik arttığında performans sorunları yaşanabilir.
    - Yeni başlayanlar ve küçük projeler için uygundur.
- **VPS (Sanal Özel Sunucu)**
    - Fiziksel bir sunucunun sanal olarak bölünmesiyle oluşur ve her kullanıcıya ayrılmış kaynaklar sunar.
    - Paylaşımlı hosting’e göre daha stabil ve kontrol edilebilirdir.
    - Büyüyen siteler ve geliştiriciler için iyi bir ara çözümdür.
- **Özel Sunucu (Dedicated Server)**
    - Tüm sunucu kaynakları tek bir web sitesine aittir.
    - Yüksek performans ve tam kontrol sağlar ancak maliyeti yüksektir.
    - Yoğun trafikli ve kritik sistemler için tercih edilir.
- **Bulut Hosting (Cloud Hosting)**
    - Birden fazla sunucudan oluşan esnek bir altyapı üzerinde çalışır.
    - Trafik arttığında otomatik olarak ölçeklenebilir ve kesinti riski düşüktür.
    - Startup’lar ve ölçeklenebilir uygulamalar için idealdir.
- **Reseller Hosting**
    - Bir ana barındırma planı üzerinden alt hesaplar oluşturarak müşteri siteleri barındırmayı sağlar.
    - Sunucu yönetimiyle uğraşmadan hosting satışı yapılabilir.
    - Ajanslar ve web tasarımcılar tarafından sıkça kullanılır.

## DOĞRU WEB SUNUCUSUNU NASIL SEÇERİM?

Doğru web barındırma hizmetini seçmek; web sitenizin hızı, güvenliği, kullanıcı deneyimi ve uzun vadeli başarısı açısından kritik öneme sahiptir. Seçim yaparken aşağıdaki temel kriterler mutlaka değerlendirilmelidir.

- **Hız ve Performans**
    - İyi bir barındırma hizmeti, hızlı yükleme süreleri ve optimize edilmiş sunucu altyapısı sunmalıdır.
    - Hızlı siteler hem SEO performansını artırır hem de kullanıcı deneyimini iyileştirir.
    - Satın almadan önce sağlayıcının performans testlerine, uptime oranlarına ve sunucu teknolojilerine (SSD, NVMe, CDN desteği vb.) bakılması önerilir.
- **Güvenlik Özellikleri**
    - Modern web sunucuları güçlü ve yerleşik güvenlik önlemleri sunmalıdır. Aşağıdaki özellikler temel gereksinimlerdir:
        - Şifreli bağlantılar için **SSL sertifikası**
        - Yetkisiz erişimi engelleyen **güvenlik duvarları**
        - Kötü amaçlı yazılım ve virüs taramaları
        - Çalışma süresini korumak için **DDoS koruması**
        - Güvenlik açıklarını kapatmak için **düzenli yazılım güncellemeleri**
    - Güvenlik, sadece site sahibi için değil, ziyaretçiler için de kritik bir faktördür.
- **Maliyet**
    - Web barındırma fiyatları; sunulan kaynaklara, performansa ve ek hizmetlere göre büyük ölçüde değişiklik gösterir.
    - En ucuz seçenek her zaman en doğru seçenek olmayabilir. İhtiyaçlarınıza uygun fiyat–performans dengesi sunan planlar tercih edilmelidir.
- **Birden Fazla Alan Adı Barındırma**
    - Birden fazla web siteniz veya alan adınız varsa, tek bir hesap üzerinden ek alan adlarını (addon domain) destekleyen barındırma hizmetleri tercih edilmelidir.
    - Ayrıca sağlayıcının bu alan adları için ek ücret alıp almadığı da kontrol edilmelidir.
- **Ölçeklenebilirlik**
    - Web sitenizin trafiği ve kaynak ihtiyacı zamanla artabilir.
    - Bu nedenle paylaşımlı hosting → VPS → özel veya bulut hosting’e kesinti yaşamadan geçiş imkânı sunan bir sağlayıcı seçmek önemlidir.
    - Trafik ve kaynak kullanımını düzenli olarak izlemek, doğru zamanda yükseltme yapmanızı sağlar.
- **Kontrol Paneli**
    - cPanel veya benzeri bir kontrol paneli, web sitesi yönetimini büyük ölçüde kolaylaştırır.
    - Dosya yönetimi, e-posta ayarları ve veritabanı işlemleri gibi temel işlemler için teknik destek ihtiyacını azaltır.
    - Özellikle teknik bilgisi sınırlı kullanıcılar için büyük avantaj sağlar.

## WEB SİTESİ OLUŞTURMA ARAÇLARI ve HOSTİNG DESTEĞİ

Birçok web barındırma sağlayıcısı, web sitenizi kolayca oluşturabilmeniz için **web sitesi oluşturucuları** veya **CMS (İçerik Yönetim Sistemi)** desteği sunar. 

Hangi aracı seçeceğiniz; teknik bilginize, proje karmaşıklığına ve özelleştirme ihtiyacınıza bağlıdır.

Bu araçları ve barındırma altyapısını değerlendirirken aşağıdaki özellikler göz önünde bulundurulmalıdır:

| Özellik                             | Ne Aramalı                                                                |
| ----------------------------------- | ------------------------------------------------------------------------- |
| **Çalışma Süresi / SLA**            | %99,9 veya daha yüksek kullanılabilirlik garantisi                        |
| **Performans Yığını**               | NVMe SSD depolama, HTTP/3, LiteSpeed veya eşdeğeri web sunucusu           |
| **Veri Merkezleri / Gecikme**       | Daha hızlı bölgesel erişim için birden fazla küresel konum                |
| **Güvenlik**                        | WAF, otomatik yedeklemeler, kötü amaçlı yazılım taramaları, DDoS koruması |
| **Teknik Destek**                   | Sohbet, e-posta veya telefon yoluyla 7/24 teknik yardım                   |
| **Kontrol Paneli**                  | Kolay yönetim için cPanel veya eşdeğeri                                   |
| **Tek Tıklamayla Uygulamalar**      | WordPress, CMS’ler ve site oluşturucular için hızlı kurulum               |
| **E-posta Seçenekleri**             | Özel alan adı e-posta hesapları veya entegrasyon seçenekleri              |
| **Yükseltme Yolu**                  | VPS, Bulut veya Özel barındırmaya sorunsuz geçiş imkânı                   |
| **Şeffaf Fiyatlandırma / Yenileme** | Fiyatların ve yenileme koşullarının önceden net olması                    |


## ALAN ADI ve HOSTİNG ARASINDAKİ FARK NEDİR? 
Bir web sitesinin internette çalışabilmesi için **alan adı** ve **hosting (barındırma)** birlikte gerekir.
Ancak görevleri **tamamen farklıdır.**

- **Alan Adı (Domain) Nedir?**
    - Alan adı, web sitenizin internetteki adresidir.
    - Kullanıcıların tarayıcıya yazarak sitenize ulaşmasını sağlar.
    - **Örnek :** www.orneksite.com
    - İnsanların IP adresi yerine hatırlayabildiği isimdir
    - DNS sistemi üzerinden sunucunun IP adresine yönlendirilir
    - İçerik barındırmaz, sadece yol gösterir
    - **Alan Adı** = Adres
- **Hosting (Web Barındırma) Nedir?**
    - Hosting, web sitenizin tüm dosyalarının saklandığı ve çalıştığı yerdir.
    - İçerisinde: 
        - HTML, CSS, JavaScript dosyaları
        - Görseller, videolar
        - Veritabanları
        - E-postalar (çoğu zaman)
    - Hosting sunucusu, gelen isteklerde bu dosyaları kullanıcıya gönderir.
    - **Hosting** = Ev / Bina
- **Basit Bir Benzetme İle**
    **Not :** Adres olmadan evi bulamazsın, ev olmadan adresin anlamı yoktur.
    | Gerçek Hayat              | Web Dünyası                  |
    | ------------------------- | ---------------------------- |
    | **Ev Adresi**             | **Alan Adı (Domain)**        |
    | **Evin Kendisi**          | **Hosting (Web Barındırma)** |
    | **Adrese Gitmek**         | **DNS (Alan Adı Çözümleme)** |
    | **Evin İçindeki Eşyalar** | **Web Sitesi Dosyaları**     |
- **Birlikte Nasıl Çalışırlar?**
    - Kullanıcı tarayıcıya alan adını yazar
    - DNS, alan adını hosting sunucusunun IP adresine çevirir
    - Sunucu, web sitesi dosyalarını kullanıcıya gönderir
    - Site tarayıcıda görüntülenir
- **Kısaca :** 
    - Alan adı → Nereye gideceğini söyler
    - Hosting → Orada ne olduğunu barındırır
    - İkisi birlikte çalışır, biri olmadan diğeri işe yaramaz



