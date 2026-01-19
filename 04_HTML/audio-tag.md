# `<audio>` HTML Öğesi

## Genel Tanım

`<audio>` öğesi, HTML belgelerine **ses içeriği eklemek** için kullanılır.  
Web sayfalarında müzik, ses efekti, anlatım veya benzeri seslerin oynatılmasını sağlar.

Ses kaynağı, `src` özniteliği kullanılarak veya `<audio>` etiketi içinde bir ya da birden fazla `<source>` öğesi tanımlanarak belirtilir. Tarayıcı, desteklediği **en uygun ses kaynağını otomatik olarak seçer**.

Açılış ve kapanış (`<audio></audio>`) etiketleri arasındaki içerik, `<audio>` öğesini desteklemeyen tarayıcılarda **yedek (fallback) içerik** olarak gösterilir.

## Temel Attribute’lar

Aşağıdaki attribute’lar, `<audio>` etiketiyle en sık kullanılan ve frontend öğrenen biri için **bilinmesi yeterli** olan özelliklerdir.

### `autoplay`

Ses dosyasının, tamamının indirilmesini beklemeden mümkün olan en kısa sürede otomatik olarak çalmaya başlamasını sağlar.  
Modern tarayıcılarda genellikle kullanıcı etkileşimi olmadan sesli autoplay engellenir.

### `controls`

Tarayıcının kendi oynatıcı kontrollerini göstermesini sağlar.  
Bu kontroller sayesinde kullanıcı:

    - Sesi oynatabilir veya duraklayabilir
    - Sesi ileri - geri sarabilir
    - Ses seviyesini ayarlayabilir

### `loop`

Ses dosyası sona ulaştığında, otomatik olarak baştan tekrar çalmaya başlar.

### `muted`

Sesin başlangıçta sessize alınmış şekilde başlatılacağını belirtir.  
Varsayılan değeri `false`’tur.

### `preload`

Ses dosyasının ne zaman yükleneceği konusunda tarayıcıya ipucu verir.

Alabileceği değerler:

    - `none` → Ses önceden yüklenmez
    - `metadata` → Yalnızca süre gibi temel bilgiler yüklenir
    - `auto` → Tarayıcı gerekli görürse tüm dosyayı yükleyebilir

Genellikle performans açısından `metadata` tercih edilir.

### `src`

Gömülecek ses dosyasının URL’ini belirtir.  
Alternatif olarak, `<audio>` etiketi içinde `<source>` öğeleri kullanılarak da ses kaynakları tanımlanabilir.

## İleri Seviye Attribute’lar (Opsiyonel)

Aşağıdaki özellikler, daha ileri kullanım senaryoları içindir.  
İlk aşamada bilinmesi şart değildir.

    - `crossorigin` → CORS ayarlarıyla ilişkili çapraz kaynak kullanımı  
    - `controlsList` → Tarayıcının gösterdiği kontrol türlerini sınırlandırma  
    - `disableRemotePlayback` → Harici cihazlarda uzaktan oynatmayı kapatma  
