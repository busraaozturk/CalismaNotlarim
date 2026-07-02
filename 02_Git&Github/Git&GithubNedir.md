# Sürüm Kontrolleri / Git ve Github

## Sürüm Kontrolleri Nedir?
- **Sürüm Kontrol Sistemleri (Version Control Systems - VCS),** yazılım projelerinde kaynak kodundaki değişiklikleri takip etmek, yönetmek ve kaydetmek için kullanılan araçlardır.
- **Kaynak kontrolü (Source control)** olarak da bilinirler.
-	Sürüm Kontrollerinin temel amaçları : 
    - Her değişikliği tarih, zaman ve geliştirici bilgisiyle kaydetmek
    - Proje üzerinde eş zamanlı ve çakışmasız çalışmasını sağlamak
    - Yazılım ekiplerinin daha hızlı, daha güvenli ve daha organize çalışmasına yardımcı olur.
    - Kaynak koddaki değişiklikleri yönetmesine yardımcı olur
    - Kim tarafından, ne zaman ve neden değişiklik yapıldığının izlenebilmesini sağlamak

## Git Nedir ?
- 2005 yılında Linux’un kurucusu Linus Torvalds tarafından geliştirilmiş, açık kaynaklı, dağıtık bir sürüm kontrol sistemidir.
- Projede yapılan tüm değişiklikleri kayıt altına alır, takip etmeyi, geri almayı ve ekip üyeleriyle kodu güvenli ve senkronize şekilde çalışmasını sağlar.
- **Dağıtık Yapıdadır:** Her geliştiricinin bilgisayarında projenin bir kopyası bulunur, internet olmasa bile geçmiş sürümlerle çalışılabilir.
- **Değişiklik Geçmişini Saklar:** Hangi dosyanın ne zaman kim tarafından değiştirildiği kayıt altında tutulur.
- **Geri Dönüş (Revert) Yapmayı Sağlar:** Önceki sürümlere kolayca geri dönülebilir.
- **Ekip Çalışmasını Kolaylaştırır:** Aynı dosyada birden fazla kişi çalışabilir
- **Terminal / Komut Satırı Üzerinden Çalışır:** Terminal, Powershell veya Command Prompt üzerinden komutlarla kullanılır.
- **Hızlı ve Güvenli Ölçeklenebilirdir:** Küçük projelerden dev şirket projelerine kadar her ölçekte kullanılır.
- **Git = Düzenli Proje Yönetimi + Zaman Kazancı + Ekip Koordinasyonu**

## Github Nedir ? 
- Git tabanlı bir platformdur ve kod barındırma, işbirliği ve proje yönetimi için kullanılır.
- Projeleri bulut ortamında saklamaya, yönetmeye ve ekiple ortak çalışma imkanı sağlar.
- Git projelerini internette saklayan ve paylaşmanı sağlayan bir platform.
- Git ile projeyi yönetirsin sonra Github’a yüklenir
- GitHub’ın sunduğu temel avantajlar:
    - Projelerin bulutta saklanması ve yedeklenmesi
    - Her yerden erişim
    - Ekip içi ortak çalışma
    - Açık kaynak projelerine katkı
    - Pull request ve kod inceleme (code review)
    - Proje yönetimi araçları (Issue, Projects, Wiki)
    - Pipeline ve otomasyon (Github Actions)
- Github, hem bireysel geliştiriciler hem de büyük şirketler tarafından yaygın olarak kullanılır.

## Git’in Temel Kavramları
### Repository (Repo / Depo)
- Projenin saklandığı yerdir.
- Bir klasörü git deposuna dönüştürdüğünde, artık git o klasörde yapılan tüm değişiklikleri takip etmeye başlar.
- Git deposu şu şekilde oluşturulur: 
    - *git init*
    - Bu komut, bulunduğu klasörü bir git deposuna dönüştürür ve içinde **.git** isimli bir gizli klasör oluşturur. Bu klasör Git’in tüm geçmiş bilgilerini sakladığı yerdir.

### Commit
- Proje üzerinden yapılan değişiklikleri kaydetmektedir.
- Her commit **tarih, saat, değişikliği yapan geliştiriciyi, açıklama notunu ve değişem dosyaları** kaydeder.
- **Örneğin:**
    - *git commit -m “Login sayfası düzenlendi.”*

### Branch (Dal)
- Projeyi paralel olarak geliştirmek için kullanılır.
- Ana kodu (main veya master) bozmadan farklı bir dalda geliştirilir.
- Branch kullanımı şu durumlarda idealdir:
    - Yeni özellik geliştirme
    - Hata düzeltme
    - Deneme çalışmaları
    - Büyük refactor işlemleri
- **Örneğin:** *git branch login*

### Merge
- Branch’de yapılan değişiklikleri başka bir branch’e birleştirmektedir.
- Kodlar test edilip main’e merge edilir
- **Örneğin :**
    - *git checkout main*
    - *git merge login*

### Push / Pull
- **Push:** Yerelde yapılan commitleri uzak sunucuya gönderir (Örn: Github)
    - **Örneğin:** *git push origin main*
- **Pull:** Uzak sunucudaki son değişiklikleri indirip kendi branch’ine uygular.
- **pull = fetch + merge**
- **Örnek:** *git pull origin main*

## Git & Github İlişkisi - Birlikte Nasıl Çalışır?
- **Git** ve **Github** çoğu zaman birlikte kullanılsa da aslında farklı amaçlara hizmet eden iki ayrı yapıdır.
    - **Git:** Projeyi bilgisayarda (local) takip etmeyi sağlar
    - **Github:** Projeyi bulutta (internet üzerinde) depolamayı ve paylaşmayı sağlar.
- Git ile yapılan işlemler GitHub olmadan da yapılabilir. Ama GitHub projeyi saklamak, paylaşmak ve ekip çalışması yapmak için kullanılır.
- Birlikte çalışma süreçleri şöyle işler:
    - Projeyi bilgisayarda Git ile takip edilir
    - Değişiklikleri commit edilir
    - GitHub üzerinde bir repo oluşturulur
    - Projeyi Github’a gönderilir (Push)
    - Github bunu internette bir depolar ve yönetir.

## En Sık Kullanılan Git Komutları
- **git init**
    - Yeni bir git deposu başlatır.
    - .git klasörü oluşturur ve sürüm kontrolü başlamış olur.
- **git clone <url>**
    - Uzak (remote) bir git deposunu bilgisayarına indirir ve projeyi çalışmaya hazır hale getirir.
    - **Örneğin:**
        - *git clone https://github.com/kullanici/proje.git*
- **git add .**
    - Tüm değişiklikleri ‘staging area’ ya ekler.
    - Commit işlemine hazırlık yapar.
    - *git add dosya.js* = Sadece bir dosyayı ekler
- **git commit -m “mesaj”**
    - Staging area’daki dosyaları bir commit olarak kaydeder.
    - Commit mesajı değişikliğin neden yapıldığını açıklar.
- **git status**
    - Çalışma dizinindeki değişmiş, eklenmiş, takip edilmeyen tüm dosyaları gösterir.
    - Hangi dosyaların commit’e hazır olduğunu anlamanı sağlar.
- **git log**
    - Projedeki commit geçmişini listeler.
    - Her commit için şunları gösterir.
        - Commit Id (SHA)
        - Yazar
        - Tarih
        - Mesaj
- **git branch**
    - Mevcut branch listesini gösterir
    - Hangi branch’te olduğunu belirtir
- **git checkout <branch>**
    - Başka bir branch’e geçmeni sağlar
    - **Örneğin:** *git checkout main*
- **git merge <branch>**
    - Belirtilen branch’i aktif branch’e birleştiri.
    - **Örneğin:**
        - git checkout main
        - git merge feature-branch
- **git push**
    - Yerelde yapılan commit’leri GitHub gibi uzak depoya gönderir.
    - **Örneğin:**
        - *git push origin main* 
- **git pull**
    - Uzak depodaki son değişiklikleri indirir ve mevcut branch’e uygular
    - **Pull = fetch + merge**
    - **Örneğin:**
        - *git pull origin main*

## Git Kurulumu
- Terminal aç (Finder - Uygulamalar - Terminal)
- Git kurulu mu kontrol et
    - *git —version*
    - Eğer kurulu değilse macOs pencere açıp yükle der.
    - Install tuşuna bas ve git otomatik kurulur
- Git’e kim olduğunu tanımlama, bu bilgiler commitlerde gözükecek
    - *git config --global user.name "Ad Soyad"*
    - *git config --global user.email "email@gmail.com"*
- Github hesabı oluşturma (Git config ile belirtilen email ile aynı olması önerilir)

## Klasörü Git Projesine Dönüştürme
- **Terminali Klasöre Aç**
    - *cd ~/Desktop/Javascript*
- **Git’i başlat (Klasörü git projesine dönüştürme)**
    - *git init*
    - Projeye gizli bir .git klasörü oluşturulur
    - Bu klasör git tarafından izlenmeye başlar
    - Git geçmişi tutmaya hazır hale gelir ve proje git projesi olur.
- **Projede Dosya Oluşturma**
    - echo “# Benim İlk Projem” > README.md 
    - Dosya klasörün içerisinde oluşturulur
- **Git Durumuna Bak (Çok Kullanılan Komut)**
    - *git status*
    - Değişikliklerin hangi durumda olduğunu gösterir (eklenmiş, eklenmemiş, takip edilmeyen dosyalar)
- **Dosyayı Git’e Ekle (Staging Area)**
    - İlk kez dosya git’e işleniyor
        - *git add README.md*
    - Veya tüm dosyalar için
        - *git add .*
    - (Dosya yeşile döner işlenmiş oluyor)
- **Projenin İlk Kaydı (İlk Commit)**
    - *git commit -m “Readme eklendi”*
    - Projenin bu halini kaydetti

## Github’da Yeni Repo Oluşturma
- Githuba giriş yap - “New Repository”
- RepositoryName : Projenin adı
- Description: İsteğe bağlı
- Public/Private seçimi
    - **Public :** Herkes görebilir
    - **Private :** Sadece kullanıcı görür
- Create Repository butonuna tıkla ve repo hazır
- Github’ın gösterdiği bağlantıyı kopyala

## Projenin Github’a Bağlanması
- Terminalden projeni aç
- Github’ı projeye bağla
    - *git remote add origin https://…*
    - Proje “origin” adlı uzak bir depoya bağlandı artık bilgisayardaki proje nereye push edileceğini biliyor
- Ana branch adını main yap (Standart)
    - *git branch -M main*
    - GitHub genelde “main” isminde ana branch kullanır
- Projeyi Githuba Gönder (push)
    - *git push -u origin main*
    - İlk defa push yaparken:
        - Kullanıcı adı isteyebilir
        - Şifre yerine personal access token ister

## Github’daki Repo’yu Bilgisayara İndirme
- Github’da oluşturulan repositoryi masaüstüne indirme (Clone etme)
    - git clone https://…

## Yeni Readme Oluşturma Örneği
- Readme.md dosyası oluşturma
    - echo “# 30 Days Javascript” > Readme.md
    - > dosyayı oluşturur (varsa sıfırlar)
    - >> dosyaya ekleme yapar
- Dosyayı git’e ekle
    - *git add Readme.md*
- Commit yap
    - *git commit -m “Readme oluşturuldu”*
- Github’a gönder (push)
    - *git push*
- Eğer ilk kez gönderiliyorsa:
    - *git push -u origin main*

## Vs Code’da Projeyi Açıp Düzenleme
- Vs Code da projeyi aç ve dosyaları düzenleyip ekleyip yeniden githuba gönder.
    - *git add .*
    - *git commit -m "Güncelleme"*
    - *git push*

## Yeni Branch Oluşturmak
- Yeni dal (branch) açmak için
    - *git branch jsclock* = Dal oluşturur ama o dala geçmez
    - *git checkout jsclock* = Oluşturulan dala geçer
    - *git push -u origin jsclock* = Dalı githuba gönder
- Ana dala (main) geri dönmek
    - *git checkout main*
- Güncel hali indirmek için
    - *git pull*
- Github’da branch oluşmadıysa 
    - *git push --set-upstream origin array_1* (array_1 oluşturulan dal)