# Server ve Client Component Özet Tablo

| Özellik        | Server Component        | Client Component                |
|----------------|-------------------------|---------------------------------|
| Çalışma ortamı | Server                  | Browser                         |
| Varsayılan     | ✔ (Next.js App Router)  | ❌                              |
| JS bundle      | Gönderilmez             | Gönderilir                      |
| State/Hooks    | Kullanılamaz            | Kullanılabilir                  |
| Event handler  | Kullanılamaz            | Kullanılabilir                  |
| Data fetching  | Server’da yapılır       | Client’da yapılır / browser     |
| SEO            | Çok iyi                 | Sınırlı / zayıf olabilir        |
| Performans     | Yüksek                  | Orta                            |
| Interaktivite  | Yok                     | Var                             |
| Kullanım       | Veri + layout           | Etkileşim + UI                  |

## Next.js Kuralı :
Modern Next.js projelerinde şu kural kullanılır:

```
   Mümkün olan her şeyi Server Component yap.
```

Sadece şu durumlarda Client Component kullan:
- state
- event
- interaction