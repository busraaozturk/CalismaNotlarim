# Server Component Nedir?

Next.js App Router'da her component varsayılan olarak **Server Component**'tir.  
Bu şu anlama gelir:

- Kod sunucuda çalışır
- Tarayıcıya JS yükü daha az gider
- SEO ve performans artar
- Ama her şey Server Component olamaz

Server Component, **sunucuda çalışan React componentidir.**  
Next.js ve modern React mimarisinde bir React component türüdür ve **sunucuda (server) çalışır**.

### Özellikleri
- **Server’da çalışır**, browser’da çalışmaz
- HTML üretir ve client’a sadece HTML + minimal React payload gönderir.
- Data fetching ve API çağrılarını doğrudan server’da yapabilir.
- Browser API’lerini (`window`, `document`, `localStorage`) kullanamaz.
- Default olarak Next.js App Router’da her component Server Component’tır.
- Server Component 'component tipi', server tarafında render edilen React component’tır.

### Çalışma Ortamı
- Server (Node.js)
- Browser API yoktur

### Kodun  Client'a Gönderilmesi
- Client'a JavaScript göndermez.
- HTML + küçük React payload gönderilir

### Avantajları :
- **Performans :**
    - HTML server’da üretilir → client’a hızlı gelir → First Paint çok hızlıdır.
    - JavaScript bundle küçülür, çünkü interaktif olmayan componentler client’a gönderilmez.
- **SEO :**
    - HTML hazır gelir → arama motorları içeriği rahat indeksler.
- **Güvenlik :**
    - API key’ler ve database bağlantıları server’da kalır. Browser’a gitmez.
- **Data Fetching :**
    - API veya database sorguları server’da yapılır, client tarafında ekstra fetch gerekmez.
    - Kod basitleşir, loading state minimal olur.

### Limitleri
- **Hooks sınırlamaları:** `useState`, `useEffect` gibi browser hooks’ları kullanamaz
- **Browser API'leri yok:** `window`, `document`, `localStorage` gibi şeyler çalışmaz
- **Interaktivite yok:** Button click, modal açma gibi etkileşimler server component'te yapılamaz.  
  **Interaktif şeyler için Client Component kullanmak gerekir.**


### Örnek :

```tsx
// app/products/page.tsx
export default async function ProductsPage() {
  // Server-side fetch
  const res = await fetch("https://api.example.com/products");
  const products = await res.json();

  return (
    <div>
      <h1>Ürünler</h1>
      <ul>
        {products.map((p) => (
          <li key={p.id}>{p.name}</li>
        ))}
      </ul>
    </div>
  );
}
```

**Özellikler :**
- Fetch server'da çalışıyor
- HTML server'dan client'a gidiyor
- Browser JS bundle'ında bu kod yok

### Kullanım Senaryoları
- Blog sayfası
- Ürün listesi
- Dashboard veri çekme
- Layout
- Seo içerik