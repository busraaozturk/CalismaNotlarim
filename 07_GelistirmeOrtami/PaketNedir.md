# Paket Nedir?
Package Manager'ın paketleri yöneten araç olduğunu önceki notlarda anlatmıştık. Şimdi yönettiği şeyin, yani **paketin** ne olduğunu inceleyelim.

En temel tanımıyla:

`Paket; belirli bir işi gerçekleştirmek üzere hazırlanmış, başka projelerde kutulup kullanılabilen ve dağıtıma uygun hale getirilmiş kod bütünüdür.``

Bir paket yalnızca tek bir JavaScript dosyasından oluşmak zorunda değildir. İçerisinde kaynak kodları, tür tanımları, yapılandırmalar, dokümantasyon ve başka dosyalar bulunabilir.

## Neden Paket Kullanırız?
Bir yazılım geliştirirken ihtiyaç duyduğumuz her özelliği sıfırdan yazmamız gerekmez. Örneğin bir projede:
- Tarihleri biçimlendirmek,
- Form verilerini doğrulamak,
- Slider oluşturmak,
- İkon kullanmak,
- Kod kalitesini kontrol etmek,
- Kullanıcı arayüzü geliştirmek
isteyebiliriz.

Bu özelliklerin tamamını kendimiz yazabiliriz. Ancak bu durum:
- Geliştirme süresini uzatır.
- Hata yapma ihtimalini artırır.
- Bakım maliyetini yükseltir.
- Daha önce çözülmüş problemlerin yeniden çözülmesine neden olur.

Bunun yerine, ilgili konuda hazırlanmış ve test edilmiş bir paket kullanabiliriz.

Örneğin çalıştığımız projelerde karşılaşabileceğimiz bazı paketler şunlardır:
| Paket        | Kullanım amacı                              |
| ------------ | ------------------------------------------- |
| `react`      | Kullanıcı arayüzü oluşturmak                |
| `next`       | React tabanlı web uygulamaları geliştirmek  |
| `typescript` | JavaScript’e tip güvenliği eklemek          |
| `eslint`     | Kod kalitesi ve kurallarını denetlemek      |
| `zod`        | Dışarıdan gelen verileri doğrulamak         |
| `swiper`     | Slider ve carousel oluşturmak               |
| `clsx`       | CSS sınıflarını koşullu olarak birleştirmek |

Bu paketlerin her biri belirli bir problemi çözmek için geliştirilmiştir.

## Günlük hayattan paket benzetmesi
Bir mobilya yapmak istediğimizi düşünelim. Mobilyanın vidasını, menteşesini, boyasını ve kulpunu sıfırdan üretmek yerine hazır olarak satın alırız. Daha sonra bunları kendi tasarımımıza uygun şekilde bir araya getiririz.

Yazılım geliştirmede de benzer bir süreç vardır:
| Mobilya örneği             | Yazılım karşılığı |
| -------------------------- | ----------------- |
| Yapılan mobilya            | Proje             |
| Hazır vida veya menteşe    | Paket             |
| Yapı planı                 | Proje kodları     |
| Malzemeleri getiren sistem | Package manager   |
| Malzeme mağazası           | Package registry  |

Paketler projenin tamamı değildir. Projeyi geliştirirken yararlandığımız hazır parçalardır.

`Paketi kullanmak, hazır bir proje kullanmak anlamına gelmez. Paketi kendi projemizin bir parçası olarak kullanırız.`

## Paket İçerisinde Neler Bulunur?
Bir JavaScript paketi yalnızca çalıştırılabilir koddan oluşmayabilir. İçerisinde farklı amaçlara sahip birçok dosya bulunabilir.

Basitleştirilmiş bir paket yapısı şu şekilde olabilir:
```
    ornek-paket/
    ├── package.json
    ├── README.md
    ├── LICENSE
    ├── dist/
    │   ├── index.js
    │   └── index.d.ts
    └── src/
        └── index.ts
```

Bu dosyaların görevleri genel olarak şöyledir:
| Dosya veya klasör | Görevi                                                |
| ----------------- | ----------------------------------------------------- |
| `package.json`    | Paketin adı, sürümü ve çalışma bilgilerini tutar      |
| `README.md`       | Paketin nasıl kullanılacağını açıklar                 |
| `LICENSE`         | Paketin hangi koşullarda kullanılabileceğini belirtir |
| `src`             | Paketin kaynak kodlarını içerebilir                   |
| `dist`            | Dağıtıma veya kullanıma hazır kodları içerebilir      |
| `.js`             | Çalıştırılabilir JavaScript kodlarını içerir          |
| `.d.ts`           | TypeScript tür tanımlarını içerebilir                 |

Her paketin yapısı aynı olmak zorunda değildir. Paketi geliştiren kişi veya ekip farklı bir dosya düzeni kullanabilir.

Ancak yayımlanmış bir JavaScript paketinin paket hakkında bilgi veren bir `package.json` dosyası bulunur.

## Bir Kod Ne Zaman Paket Olur?
Bilgisayarımızda yazdığımız her JavaScript dosyası otomatik olarak paket değildir.
Örneğin:
```
    export function topla(a, b) {
    return a + b;
    }
```
Bu, şu anda yalnızca bir JavaScript modülüdür.

Bu kodun bir paket olarak dağıtılabilmesi için genellikle:
- Bir proje yapısı içine alınması,
- Paket bilgilerini taşıyan bir package.json dosyasının oluşturulması,
- Paketin adı ve sürümünün belirlenmesi,
- Dışarıya sunacağı kodların tanımlanması,
- Dağıtıma hazır hâle getirilmesi
gerekir.

Örneğin paketin `package.json` dosyasının basitleştirilmiş hâli şöyle olabilir:
```
    {
        "name": "hesaplama-araclari",
        "version": "1.0.0",
        "main": "dist/index.js"
    }
```

Bu bilgiler şu anlamlara gelir:
- Paketin adı hesaplama-araclari
- Paketin sürümü 1.0.0
- Kullanılacak ana dosya dist/index.js

## Paket Adı ve Scoped Package
JavaScript paketlerinin kendilerine ait isimleri vardır.

Örneğin:
```
    react
    typescript
    eslint
    swiper
    zod
```

Bir paketi yüklerken bu isim kullanılır:
```
    npm install zod
```

Paket adları genellikle küçük harflerle yazılır.

Bazı paketlerin adının başında @ işareti bulunur:
```
    @testing-library/react
    @types/nodes
    @typescript-eslint/parser
```
Bunlara **scoped package**, yani **kapsamlandırılmış paket** denir.

Yapısı şu şekildedir: `@scope/paket-adi`

Örneğin; `@types/node`ifadesinde:
- `@type` kapsam veya organizasyon adıdır
- `node` paket adıdır

Scoped paketler, ilişkili paketleri aynı kişi, ekip veya organizasyon altında gruplandırmaya yardımcı olur.

## Paket-Kütüphane-Framework-Modül-Plugin Farkı
Bu kavramlar günlük kullanımda birbirinin yerine söylenebildiği için sıkça karıştırılır. Ancak aynı şeyi ifade etmezler.

### Paket ve Kütüphane Farkı
**Paket**, kodun yüklenebilir ve dağıtılabilir biçimidir.

**Kütüphane**, belirli işlemleri gerçekleştirmek için hazırlanmış yeniden kullanılabilir kod koleksiyonudur.

Örneğin React bir kullanıcı arayüzü kütüphanesidir. Aynı zamanda npm üzerinden yüklenebilen bir pakettir:
```
    npm install react
```

Burada iki farklı açıdan konuşuyoruz:
- Teknik kullanım biçimi açısından React bir **pakettir.**
- Yazılım geliştirme amacı açısından React bir **kütüphanedir.**

Bu nedenle bir yazılım hem paket hem de kütüphane olabilir.

### Paket ve Framework Farkı
**Framework** Uygulamanın nasıl yapılandırılacağına ilişkin daha kapsamlı kurallar ve araçlar sunar.

Örneğin Next.js bir framework'tür.
```
    npm install next
```

Ancak Next.js de npm üzerinden next isimli bir paket olarak yüklenir.

Yani:
- Next.js'in projedeki rolü bir **framework** olmaktır.
- Projeye dağıtılma biçimi bir **pakettir.**

Paket ve framework birbirinin alternatifi değildir. Biri **dağıtım biçimini**, diğeri **yazılımın görevini ve kapsamını** açıklar.

### Paket ve Modül Farkı
**Modül** kodün belirli bir sorumlulığa göre ayrılmış, içe veya dışa aktarılabilen parçasıdır.

Örneğin:
```
    export function fiyatHesapla(fiyat, oran) {
        return fiyat - fiyat * oran;
    }
```

Başka bir dosyada bu fonksiyonu içe aktarabiliriz:
```
    import { fiyatHesapla } from "./fiyat-hesapla.js";
```
Buradaki `fiyat-hesapla.js` bir modüldür.

Bir paket ise içerisinde bir veya birden fazla modül barındırabilir:
```
    hesaplama-paketi/
    ├── fiyat-hesapla.js
    ├── vergi-hesapla.js
    ├── kargo-hesapla.js
    └── package.json
```

Kısaca:
`Modül, kodun organizasyon biçimidir. Paket ise kodun dağıtım ve kurulum biçimidir.`

### Paket ve Bağımlılık Farkı
Bir paket, projemizde kullanılmaya başlandığında o projenin **bağımlılığı** olabilir.

Örneğin projemize Zod paketini ekleyelim:
```
    npm install zod
```
Bu durumda:
- `zod` bir pakettir.
- Projemiz çalışırken `zoda` ihtiyaç duyuyorsa `zod`, projemizin bağımlılığıdır.

Dolayısıyla her paket bizim projemizin bağımlılığı değildir. Yalnızca projemizin ihtiyaç duyduğu ve kullandığı paketler bağımlılık hâline gelir.

`Paket, dağıtılan kod birimidir. Bağımlılık ise projenin o pakete ihtiyaç duyduğunu anlatan ilişkidir.`

### Paket ve Eklenti Arasındaki Fark
**Eklenti veya plugin** var olan bir sistemi genişletmek üzere geliştiriken araçtır.

Örneğin ESLint için hazırlanmış bir plugin, ESLint'e yeni kontrol kuralları ekleyebilir:
```
    eslint-plugin-react
```

Bu araç:
- Dağıtım açısından bir pakettir.
- Görev açısından bir eklentidir.
- Kullanıldığı projenin bağımlılığı olabilir.
Bir yazılımın aynı anda birden fazla kavramla tanımlanması normaldir. Kavramlar farklı sorulara cevap verir:

| Soru                                       | Kavram     |
| ------------------------------------------ | ---------- |
| Kod nasıl dağıtılıyor?                     | Paket      |
| Projede buna ihtiyaç var mı?               | Bağımlılık |
| Yeniden kullanılabilir araçlar mı sunuyor? | Kütüphane  |
| Uygulamanın yapısını mı belirliyor?        | Framework  |
| Başka bir sistemi mi genişletiyor?         | Plugin     |
| Kod nasıl parçalara ayrılmış?              | Modül      |

## Açık ve Özel Paketler

### Açık Kaynak Paketler
Kaynak kodu erişilebilir olan ve lisans koşullarına göre kullanılabilen paketlerdir.

Birçok JavaScript paketi açık kaynak olarak geliştirilir. Ancak açık kaynak olması, hiçbir koşul bulunmadan istenildiği gibi kullanılabileceği anlamına gelmez. Paketin lisansının kontrol edilmesi gerekir.

Yaygın lisans örnekleri:
```
    MIT
    Apache-2.0
    GPL
```

### Özel Kaynak Paketler
Bazı paketler yalnızca belirli bir şirketin veya ekibin kullanımına açık olabilir.

Örneğin bir şirket kendi projelerinde ortak olarak kullandığı:
- Buton bileşenlerini,
- Tema sistemini,
- Form araçlarını,
- API istemcisini,
- Kodlama standartlarını
özel bir paket hâline getirebilir.

Bu paketler herkese açık npm Registry yerine şirketin özel registry’sinde saklanabilir veya npm üzerinde private olarak yayımlanabilir.

## Paket Seçerken Nelere Dikkat Edilir?
Bir paketin ihtiyacımız olan özelliği sunması, onu kullanmak için tek başına yeterli değildir. Paketi projeye eklemeden önce güvenilirliği, güncelliği ve projeyle uyumluluğu incelenmelidir.

Paket seçerken temel olarak şunlara dikkat edilmelidir:
- Pakete gerçekten ihtiyaç olup olmadığı,
- Güvenilir bir kişi veya ekip tarafından geliştirilip geliştirilmediği,
- Bakımının ve güncellemelerinin devam edip etmediği,
- Dokümantasyonunun yeterli olup olmadığı,
- Projenin Node.js, React, Next.js ve TypeScript sürümleriyle uyumu,
- Bilinen bir güvenlik açığının bulunup bulunmadığı,
- Paket boyutunun projeyi ve sayfa performansını nasıl etkileyeceği,
- Çalışmak için çok fazla alt bağımlılığa ihtiyaç duyup duymadığı,
- Lisansının projede kullanıma uygun olup olmadığı,
- Kullanıcı arayüzü paketlerinde erişilebilirlik desteğinin bulunup bulunmadığı.

Bir paketin indirilme sayısının yüksek olması, tek başına kaliteli veya güvenli olduğunu göstermez. Güncelleme durumu, dokümantasyonu, güvenliği ve proje ihtiyaçlarına uygunluğu birlikte değerlendirilmelidir.

`Amaç en popüler paketi değil, projenin ihtiyacını güvenli ve sürdürülebilir şekilde karşılayan paketi seçmektir.`

## Avantajlar ve Riskler
### Avantajları
- Daha önce çözülmüş problemleri tekrar çözmemizi önler.
- Geliştirme süresini kısaltır.
- Karmaşık özellikleri daha kolay uygulamamızı sağlar.
- Ortak ve test edilmiş çözümlerden yararlanmamıza yardımcı olur.
- Ekip içinde standart kullanım sağlayabilir.
- Kod tekrarını azaltabilir.
- Projenin yeteneklerini genişletebilir.

### Riskleri
Paket kullanmak avantajlı olsa da bazı riskler taşır:
- Paket artık geliştirilmiyor olabilir.
- Güvenlik açığı içerebilir.
- Yeni sürümü mevcut kodu bozabilir.
- Gereksiz yere proje boyutunu büyütebilir.
- Çok fazla alt bağımlılık yükleyebilir.
- Projeyi belirli bir pakete aşırı bağlı hâle getirebilir.
- Paketin lisansı projeye uygun olmayabilir.

Bu nedenle paket seçimi de yazılım geliştrime sürecinin önemli bir teknik kararıdır.
