# HTTP NEDİR?
**HTTP (Hypertext Transfer Protocol / Köprü Metni Aktarım Protokolü)**, **istemci (client)** ve **sunucu (server)** arasında veri iletişimini sağlayan TCP/IP mimarisi üzerinde çalışan bir uygulama katmanı iletişim protokolüdür. 

İçeriğin internet üzerinden nasıl talep edildiğini ve iletildiğini tanımlar. Web sayfalarını yüklemek için kullanılır. 

HTTP’nin temel amacı : 
- Bir istemcinin (web tarayıcısının)
- Sunucudan bir kaynağı (web sayfası, veri dosyası vb.)
- Standart kurallar çerçevesinde talep etmesini ve almasını sağlamaktır.

### HTTP Ne İşe Yarar?
Http sayesinde : 
- Web sayfaları tarayıcıda görüntülenir.
- Sunucudan veri alınır.
- Sunucuya veri gönderilir.

Kısacası HTTP, web üzerindeki istemci-sunucu iletişiminin temelini oluşturur.

### HTTP Nerelerde Kullanılır?
HTTP yalnızca web siteleri için kullanılmaz. Aynı zamanda : 
- Web uygulamalarında
- Mobil uygulamalarda
- RESTful API’lerde
- Mikro servis mimarilerinde yaygın olarak kullanılır.

### HTTP Hangi Tür Verileri Taşır?
HTTP, farklı türde içeriklerin iletilmesini destekler : 
- HTML
- JSON
- XML
- Resim dosyaları
- Video ve ses dosyaları

Yani HTTP sadece metin değil her türlü dijital içeriği taşıyabilir.

### HTTP’nin Genel Özellikleri
- İstemci - sunucu mimarisiyle çalışır
- İstek - yanıt (request - response) mantığına dayanır
- Web’in temel iletişim protokolüdür
- Uygulama katmanında yer alır

### HTTP STATELESS (DURUMSUZLUK)
- HTTP **stateless (durumsuz)** bir protokoldür.
- HTTP, önceki isteklerle ilgili herhangi bir bilgiyi saklamadığı anlamına gelir.
- HTTP’de : 
    - Önceki istekler hatırlanmaz
    - Her HTTP isteği bağımsız olarak değerlendirilir
    - Sunucu, istemciye ait durumu kendiliğinden bilmez
- **Örneğin:**
    - Bir kullanıcı sisteme giriş isteği gönderdiğinde, bu istek başarılı olsa bile HTTP stateless olduğu için sunucu, sonraki istekte : 
        - Bu kullanıcı daha önce giriş yapmış mıydı?” Bilgisini otomatik olarak hatırlamaz.
        - Bu nedenle kullanıcıya ait durum bilgisinin yönetilebilmesi için HTTP’Nnin stateless yapısını destekleyen bazı ek mekanizmalara ihtiyaç duyulur. Bu mekanizmalar arasında : 
            - Cookie
            - Session
            - Token (JWT) yer alır.
        - Bu yapılar sayesinde, her HTTP isteğiyle birlikte kullanıcıya ait bilgiler sunucuya tekrar iletilir ve böylece **oturum (session)** yönetimi sağlanır.

        ![http](/01_TemelKonular/images/http-1.png)

## HTTP İSTEK BAŞLIKLARI NEDİR (REQUEST HEADERS)
HTTP başlıkları, anahtar - değer (key - value) çiftleri halinde gönderilen ve istemcinin isteğiyle ilgili ek bilgileri sunucuya ileten metin tabanlı bilgilerdir.
Bu başlıklar : 
- İstemcinin hangi tarayıcıyı kullandığını
- Hangi tür verileri gönderdiğini
- Hangi tür cevapları kabul ettiğini
- Kimlik doğrulama bilgilerinin olup olmadığını sunucuya bildirir.

HTTP istek başlıkları zorunlu veya isteğe bağlı olabilir.

- **Örnek Http İstek Başlıkları**

        Host: www.ornek.com
        User-Agent: Mozilla/5.0
        Accept: text/html
        Content-Type: application/json
        Authorization: Bearer token

    - **Content-Type :** Sunucuya gönderilen verinin türünü belirtir.
    - **Accept :** İstemcinin sunucudan kabul edebileceği yanıt türlerini belirtir.
    - **Authorization :** Kimlik doğrulama bilgilerini taşır (JWT, Bearer Token vb.)
    - **User-Agent :** İstemcinin tarayıcı ve işletim sistemi bilgisi
    - **Host :** İsteğin gönderildiği sunucu adresi
    - **Accept-Language :** Dil tercihi
    - **Accept-Encoding :** gzip, br vs.
    - **Referer :** İsteğin geldiği sayfa
    - **Cache-Control :** Cache davranışı

## HTTP YANIT BAŞLIKLARI NEDİR (RESPONSE HEADERS)
HTTP yanıt başlıkları, sunucunun, istemciden gelen bir HTTP isteğine karşılık olarak gönderdiği ve yanıtla ilgili ek bilgileri içeren metin tabanlı başlıklardır.
Bu başlıklar istemciye :
- Dönen içeriğin türünü
- Cache (önbellek) kurallarını
- Cookie bilgilerini
- Güvenlik politikalarını
- Yönlendirme bilgilerini bildirir.

**Response Headers Ne İşe Yarar?**

Response headers sayesinde istemci : 
- Gelen veriyi nasıl işleyeceğini
- Cache’leyip cache’lemeyeceğini
- Oturum (session) bilgisinin olup olmadığını 
- Başka bir Url’ye yönlendirilip yönlendirilmediğini anlar.
- **Örnek Http Response Headers**
    
        HTTP/1.1 200 OK
        Content-Type: application/json
        Content-Length: 348
        Set-Cookie: sessionId=abc123
        Cache-Control: no-cache
        Location: /login
    - **Content-Type :** Sunucunun döndürdüğü içeriğin türünü belirtir
    - **Set-Cookie :** Sunucunun istemciye cookie gönderdiğini belirtir (Session, kullanıcı bilgileri vb.)
    - **Cache-Control :** Yanıtın cache davranışını belirler (no-cache, max-age=360 vb.)
    - **Location :** Yönlendirme yapılacak yebi Url’i belirtir (Genellikle 301 / 302 durum kodlarıyla birlikte)
    - **Content-Length :** Yanıt gövdesinin byte cinsinden uzunluğunu belirtir.
    - **Server :** Yanıtı üreten sunucu yazılım bilgisi 

## Request ve Response Headers 
| Özellik          | Request Headers (İstek) | Response Headers (Yanıt) |
|-----------------|--------------------------|---------------------------|
| Kim Gönderir?   | İstemci (Client)         | Sunucu (Server)           |
| Amaç            | İsteği tanımlamak        | Yanıtı açıklamak          |
| Cookie          | Gönderir                 | Set eder                  |
| Content-Type    | Gönderilen veri türü     | Dönen veri türü           |

## HTTP İSTEK - YANIT (Request - Response) MODELİ
Http, istemci ile sunucu arasında istek - yanıt mantığıyla çalışan bir protokoldür. Bu modele göre : 
- İstemci sunucuya bir HTTP isteği (Request) gönderir.
- Sunucu bu isteği işler
- Sonuç olarak istemciye bir HTTP yanıtı (Response) döner.

HTTP’de tüm iletişim bu döngü üzerinden gerçekleşir.

### HTTP İSTEK (REQUEST) NEDİR?
HTTP isteği, istemcinin (örn. Web tarayıcısının) sunucudan bir kaynak talep etmek veya sunucuya veri göndermek için oluşturduğu mesajdır.

Bir HTTP isteği şunları içerebilir : 
- HTTP yöntemi (GET, POST vb.)
- URL
- HTTP başlıkları
- İsteğe bağlı HTTP gövdesi (Request Body)

### HTTP İSTEK GÖVDESİ (Request Body)
HTTP istek gövdesi, istemcinin sunucuya veri gönderdiği kısımdır.
- Genellikle POST / PUT / PATCH isteklerinde bulunur
- Form verileri veya JSON içerebilir

### HTTP YANIT (RESPONSE) NEDİR?
HTTP yanıtı, web istemcilerinin (tarayıcıların) bir HTTP isteğine karşılık olarak internet sunucusundan aldığı mesajdır.

Bu yanıtlar, HTTP isteğinde talep edilen bilgilere göre istemciye geri dönen verileri içerir.

Tipik bir HTTP yanıtı şunları içerir : 
- HTTP durum kodu
- HTTP yanıt başlıkları
- İsteğe bağlı HTTP gövdesi (Response Body)

### HTTP YANIT GÖVDESİ (RESPONSE BODY)
HTTP yanıt gövdesi, sunucunun istemciye geri döndürdüğü asıl içeriği içerir.
Bu içerik :
- HTML - JSON - XML - Dosya Resmi (resim, pdf, vb.) olabilir.

## HTTP DURUM KODLARI (STATUS CODES) NEDİR?
Bir HTTP isteğinin sunucu tarafından nasıl sonuçlandığını belirtmek için kullanılan 3 haneli sayısal kodlardır. 5 ana gruba ayrılmıştır : (xx , 00 ile 99 arasındaki sayıları ifade eder)
- **1xx Bilgilendirici (Informational)**
    - İsteğin alındığını ve işlenmeye devam ettiğini belirtir.
    - **Örn :** 100 Continue - İstek devam edebilir
- **2xx Başarı (Success)**
    - İsteğin başarıyla işlendiğini belirtir.
    - **Örn :** 200 Ok - İstek başarıyla tamamlandı
    - **Örn :** 201 Created - Yeni bir kaynak oluşturuldu
- **3xx Yönlendirme (Redirection)**
    - İstemcinin, isteği tanımlamak için başka bir url’e yönlendirilmesi gerektiğini belirtir.
    - **Örn :** 301 Moved Permanently 
    - **Örn :** 302 Found
- **4xx İstemci Hatası (Client Error)**
    - İsteğin istemci kaynaklı bir hata nedeniyle gerçekleştirilemediğini belirtir.
    - **Örn :** 401 Unauthorized - Kimlik doğrulama yapılmamış
    - **Örn :** 403 Forbidden - Yetki Yok
    - **Örn :** 404 Not Found - Kaynak bulunamadı
- **5xx Sunucu Hatası (Server Error)**
    - İsteğin sunucu tarafında oluşan bir hata nedeniyle tamamlanamadığını belirtir.
    - **Örn :** 500 Internal Server Error - Sunucu Hatası

        ![http-2](/01_TemelKonular/images/http-2.png)
        ![http-3](/01_TemelKonular/images/http-3.png)

### MVC / WEB API BAĞLANTISI
- Return Ok() - 200
- Return Created() - 201
- Return Unauthorized() - 401
- Return Forbid() - 403
- Return NotFound() - 404
- Return StatusCode(500) - 500

## HTTP METOTLARI
Http yöntemleri (methods), istemcinin sunucuya gönderdiği istekte ne yapmak istediğini ifade eder.

Yani kaynağı al mı, oluştur mu, güncelle mi, sil mi?

Http yöntemleri, Request satırında yer alır ve sunucunun isteği nasıl işleyeceğini belirler.
- **GET : Veri Okuma**
    - Sunucudan veri almak (okumak)
    - Sunucu üzerinde değişiklik yapmaz
    - Request Body içermez
    - Parametreler Url üzerinden gönderilir
    - Aynı isteği tekrar tekrar atmak sonucu değiştirmez (idempotent)
    - **Örn :** GET /products/5
    - **Kullanım Alanları :**
        - Sayfa görüntüleme
        - Listeleme
        - Detay sayfaları
- **POST : Veri göndermek**
    - Sunucuya yeni veri göndermek / oluşturmak
    - Request Body içerir
    - Sunucu tarafında durum değiştirir
    - Aynı istek tekrarlandığında farklı sonuçlar doğurabilir
    - Güvenlik açısından Get’ten daha uygundur
    - **Örn :** POST /users
- **PUT : Tüm kaynağı güncellemek**
    - Mevcut bir kaynağı tamamen güncellemek.
    - Request Body içerir
    - Kaynağın tamamı gönderilir
    - Aynı istek tekrarlandığında sonuç değişmez (idempotent)
    - Kaynağın tamamı gönderilmelidir.
    - **Örn :** PUT /users/5
- **PATCH : Kısmi güncelleme**
    - Mevcut bir kaynağın sadece belirli alanlarını güncellemek.
    - Request Body içerir
    - Küçük veri gönderir
    - Performans açısından daha verimlidir
    - Genellikle JSON formatında kullanılır
- **DELETE : Silmek**
    - Bir kaynağı silmek
    - Sunucu tarafında veri siler
    - Request Body genellikle yoktur
    - Aynı istek tekrarlandığında sonuç değişmez (idempotent)
    - **Örn :** DELETE /users/5
    - Put’ten farkı
    - **PUT** - Kaynağın tamamını günceller
    - **PATCH** - Sadece değişen alanları günceller
    - Sadece tek alan güncellenecekse kullanılır
    - Büyük objelerde gereksiz veri göndermek istenmiyorsa kullanılır
    - ASP.NET Core Web API’de sık kullanılır, klasik MVC’de nadirdir.
- **HEAD : Sadece header**
    - Bir kaynağın var olup olmadığını veya meta bilgisini öğrenmek
    - Response Body olmadan
    - GET gibidir ama body dönmez
    - Sadece response headers gelir
    - Hızlı ve hafiftir
    - **Ne işe yarar?**
        - Dosya boyutunu öğrenmek (Content-Length)
        - Cache kontrolü
        - Kaynak var mı diye kontrol etmek
- **OPTIONS : Sunucunun desteklediği metotlar**
    - Sunucunun bir URL için hangi HTTP method’larını desteklediğini öğrenmek
    - Body içermez
    - Tarayıcılar tarafından otomatik gönderilebilir
    - CORS işlemlerinde kritik rol oynar

## PUT vs POST
| Özellik      | POST            | PUT              |
|--------------|------------------|------------------|
| Amaç         | Kaynak oluşturma| Kaynak güncelleme |
| Body         | Var              | Var              |
| Idempotent   | Hayır            | Evet             |
| URL Örneği   | `/users`         | `/users/5`       |

## GET vs POST 
| Özellik        | GET                         | POST                        |
|---------------|-----------------------------|-----------------------------|
| Veri Gönderme | URL (Query String)          | Body                        |
| Cache         | Evet (cache edilebilir)     | Hayır                       |
| Güvenlik      | Düşük (URL görünür)         | Daha yüksek (Body gizli)    |
| Kullanım      | Okuma (Read)                | Yazma (Create / Submit)    |

## RESTful API & MVC EŞLEŞMESİ
| İşlem     | HTTP Method |
|-----------|-------------|
| Listele   | GET         |
| Detay    | GET         |
| Oluştur  | POST        |
| Güncelle | PUT         |
| Sil      | DELETE      |

## PATCH - HEAD - OPTIONS KARŞILAŞTIRMASI
| Method  | Amaç                    | Body | Kullanım               |
|---------|-------------------------|------|------------------------|
| PATCH   | Kısmi güncelleme        | Var  | Alan bazlı güncelleme  |
| HEAD    | Sadece header bilgisi   | Yok  | Durum / kontrol        |
| OPTIONS | Desteklenen metodlar    | Yok  | CORS / bilgi alma      |

## HTTP vs HTTPS NEDİR?
**HTTP (Hypertext Transfer Protocol)**
- HTTP, istemci (tarayıcı) ile sunucu arasında şifrelenmemiş veri iletişimi sağlayan bir protokoldür.

**HTTPS (Hypertext Transfer Protocol Secure)**
- HTTPS, HTTP ‘nin güvenli (secure) versiyonudur.
- İletişim SSL / TLS protokolü ile şifrelenir.

**HTTPS Nasıl Çalışır?**
- Tarayıcı, sunucuya bağlanmak ister.
- Sunucu, SSL sertifikasını gönderir.
- Tarayıcı sertifikayı doğrular
- Güvenli bir şifreleme anahtarı oluşturulur
- Tüm veri şifreli olarak iletir buna TLS Handshake denir.

**HTTPS NEYİ KORUR?**
- Kullanıcı adı ve şifre
- Token (JWT)
- Cookie
- Form verileri
- API trafiği

**HTTPS Kullanmazsak Ne Olur?**
- Tarayıcı “Not Secure” uyarısı gösterir
- Google SEO puanını düşürür
- Modern API’ler çalışmaz
- Kullanıcı güveni kaybolur

## HTTP ve HTTPS TEMEL FARK
| Özellik           | HTTP            | HTTPS           |
|------------------|-----------------|-----------------|
| Güvenlik         | Yok             | Var             |
| Veri Şifreleme   | Yok             | Var             |
| Sertifika        | Yok             | SSL/TLS Var     |
| Varsayılan Port  | 80              | 443             |
| URL Başlangıcı   | `http://`       | `https://`      |
| Tarayıcı Uyarısı | Yok             | Kilit simgesi   |
