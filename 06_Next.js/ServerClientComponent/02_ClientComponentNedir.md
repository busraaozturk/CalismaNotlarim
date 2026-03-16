# Client Component Nedir?

Client Component, Next.js ve modern React mimarisinde bir React component türüdür ve browser'da çalışır.

**`use client`** directive'i yazılır.

### Özellikleri :
- **Browser’da çalışır** (Client Side)
- **State ve interaktivite** sağlar (`useState`, `useEffect`)
- Event handler’lar çalışır (`onClick`, `onChange`, vs.)
- Server component’in aksine, HTML üretmek için **server’a bağlı olmak zorunda değil**
- JS bundle’a dahil edilir, yani browser JS’i indirir ve çalıştırır
- Server API key veya database bağlantısına **direkt erişemez** (fetch veya API route kullanılır) Client Component `interaktif component tipi`, browser’da çalışır ve kullanıcı etkileşimi sağlar.

### Çalışma Ortamı :
- Browser
- Kullanılabilir:
    - window
    - document
    - localStorage
    - event handler

### Kodun Client'a Gönderilmesi : 
- Client'a gönderilir.
    - component JS
    - hooks
    - logic
    - event handlers
    - Yani bundle büyür.

### Avantajları : 
- **Interaktivite**
    - *Button click, modal, dropdown, slider, chart* gibi UI elementleri çalışır.
- **State Yönetimi**
    - React Hooks (`useState`, `useReducer`, `useEffect`) ile dynamic UI oluşturulabilir.
- **Browser API’leri kullanılabilir**
    - window, document, localStorage, sessionStorage, navigator vb.
- **Dinamik İçerik**
    - Kullanıcının input’larına, scroll durumuna veya event’lere tepki verebilir.

### Limitleri : 
- **Server-side veri fetch** avantajını kaybeder → İlk yükleme yavaş olabilir
- SEO’ya katkısı sınırlıdır → HTML hazır gelmez
- Daha büyük JS bundle → performans etkilenebilir
- Bu nedenle **gereksiz yere tüm sayfayı client component yapmak** Next.js performans avantajını öldürür.

### Örnek :

```tsx
// app/components/Counter.tsx
"use client";

import { useState } from "react";

export default function Counter() {
  const [count, setCount] = useState(0);

  return (
    <button onClick={() => setCount(count + 1)}>
      {count} kere tıklandı
    </button>
  );
}
```

**Özellikler :**
- useState kullanıyor → interaktivite var
- onClick event handler → kullanıcı etkileşimi
- Browser’da çalışıyor → server bunu render etmiyor

### Kullanım Senaryoları :
- Form ve input yönetimi
- Modal açma/kapatma
- Button click & dynamic action
- Tab, carousel, slider
- Chart ve grafikler
- Kullanıcı filtreleri, pagination