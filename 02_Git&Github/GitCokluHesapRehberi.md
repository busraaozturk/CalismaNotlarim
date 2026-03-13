# Çoklu GitHub Hesabı Kullanımı ve Sık Karşılaşılan Git Çözümleri
İki github hesabını da sorunsuz ve aktif bir şekilde bir arada kullanmak isteniyorsa, ilgili projenin klasöründe şu iki işlemi birlikte yapılmalı :

### 1. Projeye Özel Yazar Kimliğini Ayarlamak
* Projenin olduğu klasörde terminali aç ve birinci hesabın bilgilerini gir.
*(Dikkat : --global kelimesi kullanılmayacak, böylece bilgisayardaki diğer projeler 2. hesapta kalmaya devam eder.)*

* Terminale tek tek yazılacak kodlar :

    ```bash
    git config user.name "Birinci Hesabın Kullanıcı Adı"
    git config user.email "birincihesap@mail.com"
### 2. Projeye Özel Giriş İznini Belirlemek
* Projeyi pushlarken birinci hesabın anahtarını kullanmak gerekli.
* Token veya SSH yöntemlerinden biriyle projenin remote url adresini güncelleyerek yapılabilir.

* Terminale yazılacak kod :

    ```bash
    git remote set-url origin https://<ALDIGIN_TOKEN>@[github.com/](https://github.com/)<BIRINCI_HESABIN_KULLANICI_ADI>/<REPO_ADI>.git
## Giriş İzni İçin Github Üzerinden Token Alma
Github artık güvenlik nedeniyle şifre yerine Token kullanıyor.

1. Tarayıcıdan **birinci hesaba giriş yap.**
2. **Settings (Ayarlar)** menüsüne gir.
3. Menünün en altındaki **Developer settings** seçeneğine tıkla
4. **Personal access tokens > Tokens (classsic)** yolunu izle.
5. Sağ üstteki **Generate new token (classic)** butonuna tıkla
6. Note kısmına "Projem için" gibi bir isim yaz. *Expiration (Geçerlilik süresi)* kısmını istersen *"No expiration" (Süresiz)* yapabilirsin.
7. Aşağıdaki kutucuklardan sadece **repo** yazan ana kutuyu işaretle (bu, projeye kod gönderme yetkisi verir) ve en alttan **Generate token** butonuna bas.
8. Ekranda `ghp_` ile başlayan uzun bir şifre çıkacak. **Bu şifreyi kopyala** (sayfayı yenilersen bir daha göremezsin).

### Token'ı Projeye Tanımlamak
Token'ı aşağıdaki koda yerleştirerek terminalde çalıştır:

    git remote set-url origin https://<KOPYALADIGIN_TOKEN>@[github.com/](https://github.com/)<BIRINCI_HESABIN_KULLANICI_ADI>/<REPO_ADI>.git

### Kodları Göndermek İçin

    git add .
    git commit -m "Commit Text"
    git push -u origin main
*(Ana dalın adı master ise main yerine master kullanılmalı.)*

### Git'in Kök Klasörünü Bulmak
Bir git deposunun içindeyken ama tam olarak hangi üst klasörde git init yapıldığını bulmak isteniyorsa şu komut kullanılabilir :

    git rev-parse --show-toplevel

*Bu komut .git gizli klasörünün bulunduğu tam dosya yolunu söyler.*

***Küçük Bir İpucu :*** Vite veya Next.js gibi modern araçlarla proje oluşturduğunda, bu araçlar kurulum bittikten sonra otomatik olarak git init komutunu senin yerine çalıştırır.

## Gönderilen ve Github Reposunun Geçmişlerinin Aynı Olmaması Durumu
Bu durum genellikle GitHub'da depoyu oluştururken içine otomatik olarak *README* veya *.gitignore* dosyası eklendiğinde ya da zaten içinde başka projeler olan var olan bir depoya, bilgisayardaki yeni bir proje gönderilmeye çalışıldığında yaşanır.
Bunu çözmek için önünde iki farklı yol var:

### 1. Geçmişleri Birleştirmeye İzin Ver (Güvenli Yol)
* Bilgisayardaki dosyaların githubdaki dosyaların yanına güvenli bir şekilde eklenmesi için git'e bu iki farklı geçmişin birleştirilmesi için izin verilmesi gerekir.
* Terminale yazılacak kod :

        git pull origin main --allow-unrelated-histories

    ***Önemli Not:** Bu komutu çalıştırdıktan sonra terminalde yazılarla dolu farklı bir ekran (Vim editörü) açılabilir. Bu ekran senden sadece bir "birleştirme mesajı" onaylamanı ister. Eğer böyle bir ekran gelirse klavyeden sırasıyla **:wq** yazıp **Enter**'a basarak o ekrandan başarıyla çıkabilirsin.*

* Bu birleştirme işlemi bittikten sonra kodlar GitHub'a normal bir şekilde gönderilebilir:
    ```
    git push -u origin main --force
### 2. Github'dakileri Ez ve Benim Kodumu Zorla Gönder (Hızlı Yol)
* GitHub'daki depoda **önemli hiçbir dosya yoksa** (örneğin sadece otomatik oluşmuş önemsiz bir README dosyası varsa) ve bilgisayardaki dosyaların oradaki her şeyi ezip üzerine yazılması isteniyorsa **"zorla"** gönderme yapılabilir.
* Terminale yazılacak kod :
    ```
    git push -u origin main --force
# Git Config Ayarı
Git bilgilerini her zaman baştan girmemek için bu ayarları bilgisayar genelinde (global) sabitlenir. Açılan her proje için git otomatik olarak bu bilgileri kullanır.

* **Global :** Tüm bilgisayarda geçerlidir
* **Local :** Sadece o klasörde geçerlidir ve her zaman global ayarı ezer.

Bilgisayarda global olarak hangi bilgilerin kayıtlı olduğunu görmek için : 

    git config --global --list

Global olarak git giriş bilgilerini kaydetmek için:

    git config --global user.name "Github Kullanıcı Adı"
    git config --global user.email "githuba.kayitli.mailin@email.com"