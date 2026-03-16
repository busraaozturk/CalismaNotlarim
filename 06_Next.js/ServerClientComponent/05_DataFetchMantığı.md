# Server ve Client Component'in Veri Çekme (fetch) Mantığı

| Özellik           | Server Component                      | Client Component                                   |
|------------------|----------------------------------------|---------------------------------------------------|
| Fetch yeri       | Server’da                              | Browser’da                                        |
| Fetch zamanlaması| Render sırasında → HTML ile birlikte   | Component mount olduktan sonra (`useEffect`)      |
| SEO              | ✔ HTML hazır                           | ❌ HTML boş, SEO zayıf                             |
| First Load       | Hızlı                                  | İlk yükleme yavaş                                  |
| Caching          | Server caching kullanılabilir          | Tarayıcı cache veya client cache                  |

## Server Component ile Data Fetch
Server Component’te fetch yapmak çok basittir çünkü **async/await kullanabilirsin** ve direkt HTML ile render edebilirsin.

**Özellikleri:**
- Fetch **server’da yapılır**, client bunu görmez.
- HTML **hazır gelir** → SEO çok iyi, First Paint hızlı.
- API key veya database bağlantıları **güvenli** server tarafında kalır.
- Yani Server Component fetch = **veri direkt server’da alınır ve render edilir**.

### Server Component Fetch Mantığı
- Client sayfayı ister → server request alır
- Server fetch yapar (API, DB)
- Server HTML üretir + client’a gönderir
- Browser HTML’i gösterir (hydration yapılabilir)

```
    Browser → Request
    Server → fetch + HTML
    Browser → gösterim
```

## Client Component ile Data Fetch
- Client Component’te fetch **browser’da yapılır**, genellikle `useEffect` veya `useSWR` gibi hook’lar ile.
- **Özellikleri**
    - Fetch browser’da yapılır → ilk render boş olabilir.
    - Loading state gerekir.
    - SEO’ya katkısı sınırlıdır.
    - Client Component fetch = **veri browser’da alınıp UI interaktif şekilde güncellenir**.

### Client Component Fetch Mantığı
- Server HTML gönderir (genellikle boş veya skeleton UI)
- Browser component mount - useEffect çalışır
- Fetch browser'dan API'ye gider
- State güncellenir - UI render edilir

```
    Server → boş HTML
    Browser → useEffect → fetch
    Browser → UI güncellenir
```