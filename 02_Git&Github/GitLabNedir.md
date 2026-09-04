# GitLab Nedir?

Gitlab, **Git tabanlı projelerin barındırılması, yönetilmesi ve ekipler tarafından ortak şekilde geliştirilmesi için kullanılan bir DevOps platformudur.**

GitLab da temelinde **Git kullanır**. Bu nedenle daha önce öğrenilen Git komutlarının büyük bölümü GitLab ile çalışırken de geçerlidir.

**Örneğin:**
- `git clone`
- `git add`
- `git commit`
- `git push`
- `git pull`
- `git branch`

Github kullanırken kullanılan bu komutlar GitLab'a geçildiğinde değişmez. Değişen temel olarak kodların gönderildiği ve geliştirme sürecinin yönetildiği platformdur.
```
    Git
    |
    |- GitHub
    |
    |- GitLab
```
Bu nedenle GitLab, Git'in alternatifi değildir. GitLab, Git ile yönetilen projelerin merkezi olarak saklanmasını ve yazılım geliştirme süreçlerinin ekip içerisinde yönetilmesini sağlayan platformlardan biridir.

## GitLab Ne İçin Kullanılır?

GitLab yalnızca kaynak kodların saklandığı bir alan değildir. Bir yazılım projesinin geliştirme sürecindeki birçok işlem GitLab üzerinden yönetilebilir.

**Başlıca kullanım alanları:**
- Projelerin merkezi bir repository üzerinde tutulması
- Ekip üyelerinin aynı proje üzerinde çalışması
- Branch'lerin yönetilmesi
- Kod değişikliklerinin incelenmesi
- Merge Request oluşturulması
- Görev ve hata takibinin yapılması
- CI/CD süreçlerinin yönetilmesi
- Otomatik test ve build işlemlerinin çalıştırılması
- Kullanıcı ve proje yetkilerinin yönetilmesi

Bu nedenle GitLab, yalnızca bir **Git repository hosting servisi değil**, aynı zamanda yazılım geliştirme süreçlerini destekleyen bir **DevOps platformudur.**

## GitLab'ın Genel Yapısı
GitLab kullanırken üç temel organizasyon kavramıyla karşılaşılabilir:
```
    GitLab
    |
    |- Group
        |
        |-Project
        |    |-Repository
        |
        |- Project
            |-Repository
```
Bu kavramların birbirinden ayrılması GitLab yapısını anlamayı kolaylaştırır.

### Group

**Group**, birden fazla projenin ve kullanıcının ortak bir yapı altında organize edilmesini sağlar.

Örneğin bir şirketin şu üç projesi olduğunu düşünelim:
```
    E-Commerce
     │
     ├── Store
     ├── Admin
     └── Backend
```

GitLab üzerinde şu şekilde organize edilebilir:
```
    E-Commerce Group
     │
     ├── Store Project
     ├── Admin Project
     └── Backend Project
```

- Group kullanılması özellikle çok sayıda proje bulunan şirket ve ekip yapılarında yönetimi kolaylaştırır.
- Group seviyesinde kullanıcılar ve erişim yetkileri de yönetilebilir.

**Not - Subgroup:** Büyük yapılarda Group içerisinde başka Group'lar oluşturulabilir. Bunlara **Subgroup** denir. Örneğin `Company` grubunun altında `Frontend`ve `Backend` subgroup'ları, onların altında da ilgili projeler bulunabilir. Bu yapı sayesinde projeler ekip veya departmanlara göre organize edilebilir.

### Project

- **Project**, GitLab üzerinde belirli bir yazılım projesinin yönetildiği çalışma alanıdır.
- Bir Project yalnızca kaynak kodlardan oluşmaz.
```
    Project
     │
     ├── Repository
     ├── Merge Requests
     ├── Issues
     ├── CI/CD
     ├── Deployments
     ├── Members
     └── Settings
```

- Repository ile Project aynı kavram değildir.
- Repository kaynak kod ve Git geçmişini temsil ederken Project bunun çevresindeki geliştirme süreçlerini de kapsar.

### Repository
- GitLab açısından önemli olan nokta, repository'nin GitLab Project içerisinde bulunmasıdır.
```
    Store Project
     │
     └── Repository
          ├── src/
          ├── public/
          ├── package.json
          └── README.md
```

- GitLab arayüzünden repository içerisindeki:
    - Dosyalar
    - Commit geçmişi
    - Branch'ler
    - Tag'ler incelenebilir.

## GitLab'da Proje Oluşturma

- GitLab üzerinde yeni bir proje oluşturulurken genel olarak **New Project** seçeneği kullanılır.

- Proje oluşturulurken:
| Alan                  | AÇIKLAMA                              | Örnek          |
|-----------------------|---------------------------------------|----------------|
|**Project Name**       |Projenin GitLab üzerinde görüntülenecek adıdır.|ecommerce-store|
|**Project URL**        |Projenin hangi kullanıcı veya Group altında bulunacağını belirler.| Company / ecommerce-store|
|**Visibility Level**   |Projeye kimlerin erişebileceğini belirler. | Private / Interval / Public|

**Visibilty Level seçenekleri:**
- **Private:** Yalnızca yetki verilen kullanıcılar projeye erişebilir.
- **Internal:** GitLab sunucusundaki doğrulanmış kullanıcıların erişebileceği proje türüdür.Kullanılabilirliği GitLab kurulumu ve ayarlarına bağlı olabilir.
- **Public:** Projeye herkes erişebilir.

- **Not:** Şirket projelerinde genellikle Private projeler kullanılır.

## GitLab'da Mevcut Bir Projeye Dahil Olmak
- Şirket ortamında çoğu zaman geliştirici GitLab üzerinde sıfırdan proje oluşturmaz. Bunun yerine mevcut bir projeye erişim yetkisi verilir.

- **Örneğin:**
```
    GitLab
    |
    |-Company
        │
        └── ecommerce-store
```
projesine geliştirici olarak dahil edilmiş olabilirsin.

- Projeye erişim sağlandıktan sonra repository bilgisayara alınabilir.Çalışma mantığı Git'teki clone işlemiyle aynıdır:
```
    git clone <gitlab-repository-adresi>
```

- Buradaki fark yalnızca remote repository'nin GitHub yerine GitLab üzerinde bulunmasıdır.

## GitLab Merge Request
- GitLab kullanırken bilinmesi gereken en önemli kavramlardan biri **Merge Request'tir.**
- Bir geliştirici kendi branch'inde yaptığı değişiklikleri başka bir branch'e aktarmak istediğinde **Merge Request (MR)** oluşturur.
```
    feature/header
        │
        │ Merge Request
        ▼
        develop
```
- Buradaki amaç yalnızca kodları birleştirmek değildir. Merge Request aynı zamanda değişikliklerin:
    - İncelenmesini
    - Tartışılmasını
    - Test edilmesini
    - Onaylanmasını sağlayan bir çalışma alanıdır.
- GitHub'da daha önce görülen **Pull Request** yapısının **GitLab'daki** karşılığı olarak düşünülebilir.
```
    GitHub : Pull Request
    GitLab : Merge Request
```
- Temel amaçları benzerdir; ancak platformların sunduğu iş akışı ve özellikler farklılaşabilir.

- **Not — Fork:** Açık kaynak projelerde geliştiriciler genellikle projeye doğrudan erişim yetkisine sahip olmaz. Bu durumda proje **fork**'lanır (kendi hesabına kopyalanır), değişiklik yapılır ve Merge Request kaynak proje üzerinden değil, fork edilen proje üzerinden açılır. Şirket içi private projelerde bu adıma genelde gerek kalmaz; doğrudan bir feature branch yeterlidir.

## Merge Request Nasıl Çalışır?

- Örneğin geliştirici `feature/mobile-header` branch'inde bir geliştirme gerçekleştirmiş olsun.

- Geliştirme GitLab'a gönderildikten sonra:
```
    feature/mobile-header
            │
            ▼
    Merge Request
            │
            ▼
    develop
```
şeklinde bir Merge Request oluşturulabilir. Merge Request oluşturulurken iki branch önemlidir:
**1) Source Branch:** Değişikliklerin bulunduğu branch'tir. (`feature/mobile-header`)
**2) Target Branch:** Değişikliklerin aktarılmak istendiği branch'tir. (`develop`)

```
    Source Branch (feature/mobile-header)
        ↓
    Target Branch (develop)
```
- **Not — Merge Conflict:** Source branch ile target branch aynı dosyanın aynı satırında farklı değişiklikler içeriyorsa GitLab bunu otomatik birleştiremez ve **conflict (çakışma)** oluşur. Bu durumda MR ekranında "conflict var" uyarısı gösterilir; geliştirici ilgili dosyaları elle düzenleyip çakışmayı çözmeden merge işlemi tamamlanamaz.

## Merge Request İçerisinde Neler Bulunur?
Bir Merge Request içerisinde genel olarak şu bilgiler bulunabilir:
- Başlık
- Açıklama
- Source Branch
- Target Branch
- Assignee
- Reviewer
- Commit'ler
- Yapılan değişiklikler
- Yorumlar
- Pipeline durumu

- Bu bilgiler geliştirme sürecinin ekip içerisinde takip edilmesini kolaylaştırır.

## Merge Request Rolleri ve Onay Süreci
 
Merge Request içerisinde farklı sorumluluklar tanımlanabilir:
 
| Rol | Açıklama |
|---|---|
| **Author** | Geliştirmeyi yapan kişi |
| **Assignee** | Merge Request'in takibinden sorumlu kişi |
| **Reviewer** | Yapılan kod değişikliklerini inceleyen kişi |
 
Ekiplerin kullandığı süreçlere göre bu rollerin kullanımı farklılık gösterebil

## Code Review
- Merge Request oluşturulduktan sonra yapılan değişiklikler ekip üyeleri tarafından incelenebilir. Bu işleme **Code Review** denir. Code Review sırasında şu konular değerlendirilebilir:
    - Kod standartları
    - Proje mimarisine uygunluk
    - Olası hatalar
    - Kod okunabilirliği
    - Performans
    - Güvenlik
    - Testler

- Reviewer doğrudan değiştirilmiş bir kod satırı üzerine yorum bırakabilir (örneğin: *"Bu component ortak yapıdan kullanılabilir mi?"*). Geliştirici gerekli düzenlemeleri yaptıktan sonra aynı branch'e yeni değişiklikleri gönderir; Merge Request otomatik olarak güncellenir, yeni bir Merge Request oluşturulması gerekmez.

## Approval
- Bazı projelerde Merge Request'in birleştirilebilmesi için belirli kişiler tarafından onaylanması gerekebilir. Bu işlem **Approval** olarak adlandırılır. Bir veya birden fazla reviewer'ın onayı zorunlu hale getirilebilir; bu kurallar proje ve ekip standartlarına göre değişebilir.

```
    Merge Request
         │
         ▼
    Code Review
         │
         ▼
    Approval
         │
         ▼
    Merge
```

## Protected Branch
- GitLab'da önemli branch'ler koruma altına alınabilir. Bunlara **Protected Branch** denir. Örneğin `main`, `develop`, `release` gibi branch'ler korunabilir.

- Bu durumda geliştiricilerin doğrudan `main` branch'ine değişiklik göndermesi sınırlandırılabilir. Bunun yerine kontrollü bir süreç kullanılır:
 
```
    Feature Branch
          │
          ▼
    Merge Request
          │
          ▼
    Code Review
          │
          ▼
    Approval
          │
          ▼
    Main / Develop
```
- Protected Branch kullanımı kritik branch'lerin yanlışlıkla veya kontrolsüz şekilde değiştirilmesini önlemeye yardımcı olur.

## Issues
- GitLab yalnızca kaynak kod yönetmek için kullanılmaz. Projedeki görevler ve hatalar **Issues** üzerinden takip edilebilir.
- Örneğin:
```
    Issue #128
    Başlık: Header mobil görünümü düzenlenecek
    Assignee: Frontend Developer
    Label: frontend
```
- Bir Issue içerisinde şu bilgiler bulunabilir:
    - Açıklama
    - Sorumlu kişi
    - Etiketler
    - Yorumlar
    - Tarihler
    - İlgili Merge Request
- Issue kullanımı ekip içerisindeki işlerin merkezi olarak takip edilmesini sağlar.

## GitLab CI/CD
- GitLab'ın önemli özelliklerinden biri yerleşik **CI/CD** desteğidir. CI/CD, yazılım geliştirme sürecindeki belirli kontrollerin ve yayınlama işlemlerinin otomatikleştirilmesini sağlar.
- Örneğin GitLab'a yeni bir geliştirme gönderildiğinde:
```
    Kod GitLab'a gönderildi
            │
            ▼
         Pipeline
            │
       ┌────┼────┐
       ▼    ▼    ▼
     Lint  Test Build
```
gibi otomatik işlemler çalıştırılabilir. Bu sayede kodun ana projeye alınmadan önce belirli kontrollerden geçmesi sağlanabilir.
 
Bu pipeline'ın hangi adımlardan oluşacağı, proje kök dizinine eklenen **`.gitlab-ci.yml`** dosyasıyla tanımlanır. Basit bir örnek:
 
```yaml
    stages:
    - lint
    - test
    - build
    
    lint-job:
    stage: lint
    script:
        - echo "Kod standartları kontrol ediliyor"
    
    test-job:
    stage: test
    script:
        - echo "Testler çalıştırılıyor"
    
    build-job:
    stage: build
    script:
        - echo "Proje derleniyor"
```
 
Her `stage`, pipeline diyagramındaki bir adıma karşılık gelir; `script` altında ise o adımda çalıştırılacak komutlar tanımlanır.

## Pipeline
- GitLab CI/CD içerisinde otomatik olarak çalışan işlem zincirine **Pipeline** denir.

**Başarılı bir pipeline:**
```
    Lint      ✅
    Test      ✅
    Build     ✅
```

**Başarısız bir pipeline:**
```
    Lint      ✅
    Test      ❌
    Build     -
```

- Bu durumda proje kurallarına bağlı olarak Merge Request'in merge edilmesi engellenebilir.
- Başlangıç seviyesinde Pipeline için bilinmesi gereken temel nokta şudur: Pipeline, GitLab'a gönderilen kod üzerinde tanımlanmış otomatik kontrollerin ve işlemlerin çalıştırıldığı süreçtir.

-**Not — GitLab Runner:** Pipeline içerisindeki `lint`, `test`, `build` gibi işlemler soyut kalmaz; bunları fiilen çalıştıran bileşene **Runner** denir. Runner, GitLab tarafından sağlanabileceği gibi şirketin kendi sunucusunda da kurulabilir. Bir işin çalışabilmesi için o iş türünü destekleyen bir Runner'ın mevcut olması gerekir.

## Members ve Yetkilendirme

GitLab projelerinde herkes aynı yetkilere sahip olmak zorunda değildir. Proje veya Group içerisinde kullanıcılara farklı roller atanabilir.
- Guest
- Reporter
- Planner
- Developer
- Maintainer
- Owner 

Bu roller kullanıcının proje içerisinde hangi işlemleri yapabileceğini belirler. Örneğin bir geliştirici repository'yi görüntüleyebilir, branch oluşturabilir, kod gönderebilir ve Merge Request oluşturabilir; ancak proje ayarlarını değiştirme veya kritik branch'leri yönetme yetkisine sahip olmayabilir. Yetkiler proje ve Group yapılandırmasına göre değişebilir.

## GitLab'da Temel Ekip Çalışma Akışı

GitLab'ın çalışma mantığını anlamanın en kolay yollarından biri gerçek bir geliştirme sürecini incelemektir. Örneğin bir frontend geliştiriciyemobil header geliştirilecek" görevi verilmiş olsun.

```
    Görev / Issue
          │
          ▼
    Feature Branch
          │
          ▼
    Geliştirme
          │
          ▼
    GitLab'a gönderme
          │
          ▼
    Merge Request
          │
          ├──────────────┐
          ▼              ▼
     Code Review      Pipeline
          │              │
          └───────┬──────┘
                  ▼
               Approval
                  │
                  ▼
                Merge
```
- Burada GitLab, geliştirme sürecinin farklı aşamalarını tek bir platform üzerinde birbirine bağlamaktadır.

## GitLab Arayüzünde Sık Kullanılan Alanlar
- Bir geliştirici GitLab projesinde genellikle aşağıdaki alanlarla sık karşılaşır:

| Alan	            | Açıklama                                      |
|-------------------|-----------------------------------------------|
| Repository	    | Projenin kaynak kodlarını görüntüleme         |
| Branches	        | Projedeki branch'leri görüntüleme ve yönetme  |
| Merge Requests	| Kod değişikliklerini inceleme ve birleştirme  |
| Issues	        | Görev ve hata takibi                          |
| CI/CD	            | Otomasyon süreçlerinin yönetimi               |
| Pipelines	        | Çalıştırılan otomatik işlemlerin sonuçları    |
| Members	        | Projeye erişimi olan kullanıcılar             |
| Settings	        | Proje yapılandırmaları                        |

- Başlangıç seviyesinde özellikle **Repository, Branches, Merge Requests, Issues ve Pipelines** alanlarının anlaşılması GitLab'ın temel kullanım mantığını kavramak için yeterlidir.

## GitLab'ın Yazılım Geliştirme Sürecindeki Yeri

GitLab'ı yalnızca "kodların internette saklandığı bir platform" olarak değerlendirmek eksik olur. GitLab, Git tabanlı projelerin barındırılması ve ekipler tarafından geliştirilmesinin yanında, daha geniş bir yazılım geliştirme sürecini de yönetebilir:

```
    Planlama
    │
    ▼
    Issue
    │
    ▼
    Geliştirme
    │
    ▼
    Repository
    │
    ▼
    Merge Request
    │
    ▼
    Code Review
    │
    ▼
    Pipeline
    │
    ▼
    Approval
    │
    ▼
    Merge
```
- Bu nedenle GitLab özellikle ekip çalışmalarında kaynak kod yönetimi ile geliştirme süreçlerinin merkezi bir noktada yönetilmesini sağlar.

- GitLab öğrenirken ilk aşamada aşağıdaki yapıların anlaşılması yeterlidir:
 
```
    GitLab
    │
    ├── Group
    │
    └── Project
        │
        ├── Repository
        ├── Branches
        ├── Issues
        ├── Merge Requests
        │     ├── Code Review
        │     └── Approval
        │
        ├── Pipelines
        └── Members
```
 
- Daha önce Git konusunda öğrenilen `commit`, `branch`, `push`, `pull`, `clone` ve `merge` gibi kavramlar GitLab'da da kullanılmaya devam eder.
 
- GitLab öğrenirken asıl yeni odak; **GitLab'ın proje organizasyonu, Merge Request süreci, Code Review, Issue yönetimi, yetkilendirme ve CI/CD entegrasyonudur.**