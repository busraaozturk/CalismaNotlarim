# npm, Yarn ve pnpm Karşılaştırması
npm, Yarn ve pnpm aynı temel görevi yerine getirir: JavaScript projelerindeki paketleri ve bağımlılıkları yönetir. Aralarındaki temel fark; komutları, paketleri saklama yöntemleri ve sundukları ek özelliklerdir.

| Özellik               | npm                            | Yarn                                | pnpm                          |
| --------------------- | ------------------------------ | ----------------------------------- | ----------------------------- |
| Node.js ile gelir mi? | Genellikle evet                | Hayır                               | Hayır                         |
| Lock dosyası          | `package-lock.json`            | `yarn.lock`                         | `pnpm-lock.yaml`              |
| Paket ekleme          | `npm install zod`              | `yarn add zod`                      | `pnpm add zod`                |
| Paket kaldırma        | `npm uninstall zod`            | `yarn remove zod`                   | `pnpm remove zod`             |
| Script çalıştırma     | `npm run dev`                  | `yarn dev`                          | `pnpm dev`                    |
| Paket depolama        | Her projede kurulum            | Sürüme ve ayara göre değişir        | Ortak store kullanır          |
| Öne çıkan yönü        | Yaygın ve başlangıç için kolay | Esnek yapı ve workspace özellikleri | Disk alanını verimli kullanır |

## Hangisi Tercih Edilmelidir?
- **npm:** Yeni başlayanlar ve standart projeler için yeterli ve yaygındır.
- **Yarn:** Özellikle Yarn kullanan ekip projelerinde ve gelişmiş workspace yapılarında tercih edilebilir.
- **pnpm:** Çok sayıda proje veya paket içeren yapılarda disk kullanımı ve bağımlılık düzeni açısından avantaj sağlar.

Ancak mevcut bir pojede kişisel tercihe göre package manager değiştirilmemelidir. Öncelikle lock dosyasına bakılmalıdır:
```
package-lock.json → npm
yarn.lock         → Yarn
pnpm-lock.yaml    → pnpm
```

En doğru package manager her zaman 'en hızlı' olan değil, projenin ve ekibin belirlediği araçtır. Aynı projede npm, Yarn ve pnpm karıştırılmamalıdır.
