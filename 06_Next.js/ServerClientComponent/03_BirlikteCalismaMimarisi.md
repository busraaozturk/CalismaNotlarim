# Server ve Client Component Birlikte Çalışma Mimarisi

Next.js mimarisinde en önemli yapı:
```
Server Component
      ↓
Client Component
```

**Server Component**
- veri getirir
- UI oluşturur

**Client Component**
- etkileşim sağlar

### Örnek Server Component : 

```
import AddToCart from "./AddToCart"

export default async function ProductPage(){

const product = await getProduct()

return (
<div>
    <h1>{product.name}</h1>
    <AddToCart productId={product.id}/>
</div>
)
}
```

### Örnek Client Component :

```
"use client"

export default function AddToCart({ productId }){

 return <button>Sepete ekle</button>

}
```