# `<kbd>` HTML Etiketi

## `<kbd>` – Klavye Giriş Öğesi

`<kbd>` HTML öğesi; **klavye, ses girişi veya başka bir metin giriş cihazından gelen kullanıcı girdisini** temsil eder.

Genellikle:
- Klavye tuşları
- Klavye kısayolları
- Terminal / komut girdileri  
metin içinde **görsel olarak ayırt edilmesi** için kullanılır.

## `<kbd>` Nedir? Ne Amaçla Kullanılır?
- Kullanıcının klavyeden basması gereken **tuşu veya tuşları** ifade eder
- **Semantik** bir HTML etiketidir (anlam taşır)
- Dokümantasyon, yardım sayfaları ve eğitim içerikleri için idealdir
- Ekran okuyucular tarafından **“klavye girdisi”** olarak algılanır  
  (erişilebilirlik açısından önemlidir)

## Temel Kullanım

### Örnek
    
    <p>Kaydetmek için <kbd>Ctrl</kbd> + <kbd>S</kbd> tuşlarına basın.</p> 

- Varsayılan Görünüm (Tarayıcıya Göre Değişebilir)
    - Monospace font
    - Açık gri arka plan
    - İnce kenarlık
    - Hafif padding

## `<kbd>` İç İçe Kullanım

HTML standardı, bir tuş kombinasyonunu temsil etmek için
`<kbd>` etiketi içinde tekrar `<kbd>` kullanılmasına izin verir.

### Örnek

    <kbd>
    <kbd>Ctrl</kbd> + <kbd>S</kbd>
    </kbd>

### Yapı Açıklaması
- Dış `<kbd>` → Kısayolun tamamı
- İç `<kbd>` → Tek tek tuşlar

## Komut Satırı Girdileri İçin Kullanım
### Örnek : 

    <p>Terminalde şu komutu yazın:</p>
    <kbd>npm install</kbd>

- Komut çıktıları için `<code>`
- Kullanıcıdan yazması istenen komutlar için `<kbd>` kullanmak daha doğrudur

## `<kbd>` vs `<code>` vs `<samp>`
### Örnek : 

    <p>
      <kbd>Enter</kbd> tuşuna bastığınızda ekranda
        <samp>Success</samp> yazar.
    </p>

| Etiket | Anlamı |
|------|------|
| `<kbd>` | Kullanıcının girdiği şey |
| `<code>` | Kod |
| `<samp>` | Program çıktısı |

# `<kbd>` Hangi Attribute’ları Alır?

- `<kbd>` global HTML attribute’larını alır. 

- Sık kullanılanlar :
    - id
    - class
    - title
    - style
    - data-*
    - aria-*
    - Kendine özel attribute'u yoktur.

# `<kbd>` Kullanırken Dikkat Edilecekler 

- Kullanıcıdan gerçekten bir tuş basması bekleniyorsa kullan
- Kod göstermek için kullanma
- Erişilebilirlik için açıklayıcı metinle birlikte kullan
- Tek başına uzun metinlerde abartma
