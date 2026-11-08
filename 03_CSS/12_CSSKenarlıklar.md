# CSS Kenarlıklar, Outline ve Gölgeler (Borders, Outline & Shadows)

CSS'te bir elementin görünümünü yalnızca arka plan rengi veya boyutları belirlemez. Elementin çevresindeki kenarlıklar, köşelerin şekli, odak göstergeleri ve gölgeler de tasarımın önemli parçalarıdır.

Örneğin bir ürün kartında ince bir kenarlık, bir butonda yuvarlatılmış köşeler veya bir form alanında klavye odağını gösteren bir outline kullanılabilir.

Bu bölümde CSS'in border, outline ve box-shadow özelliklerini, aralarındaki farkları ve gerçek projelerde nasıl kullanıldıklarını inceleyeceğiz.

```
    .card {
        padding: 24px;
        background-color: #ffffff;

        border: 1px solid #e5e2da;
        border-radius: 12px;

        box-shadow: 0 4px 16px rgba(0, 0, 0, 0.08);
    }
```

Bu örnekte:
- border kartın kenarlığını oluşturur.
- border-radius köşeleri yuvarlatır.
- box-shadow kartın çevresine gölge ekler.

## CSS Kenarlıklar Nedir?
**CSS'te border** bir elementin padding alanı ile margin alanı arasında bulunan kenarlık bölgesini kontrol eder. 

Bu alanı 05_CSSBoxModel konusunda incelemiştik.
```
    ┌────────────────────────────────┐
    │             MARGIN             │
    │  ┌──────────────────────────┐  │
    │  │          BORDER          │  │
    │  │  ┌────────────────────┐  │  │
    │  │  │      PADDING       │  │  │
    │  │  │   ┌────────────┐   │  │  │
    │  │  │   │  CONTENT   │   │  │  │
    │  │  │   └────────────┘   │  │  │
    │  │  └────────────────────┘  │  │
    │  └──────────────────────────┘  │
    └────────────────────────────────┘
```

Kenarlıklar üç temel özellik üzerinden tanımlanır.

|Özellik                               |Görevi                                |
|--------------------------------------|--------------------------------------|
|border-width                          |Kenarlığın kalınlığını belirler       |
|border-style                          |Kenarlığın çizgi stilini belirler     |
|border-color                          |Kenarlığın rengini belirler           |

Bu özellikler ayrı ayrı kullanılabildiği gibi border shorthand ile tek satırda da yazılabilir.

### Temel Kullanım
```
    .box{
        border-width: 2px;
        border-style: solid;
        border-color: #7d8570;
    }
```

Aynı tanımın kısa hali: 
```
    .box{
        border: 2px solid #7d8570;
    }
```

**Önemli:** Kenarlığın görünmesi için genellikle *border-style* özelliğinin none dışında bir değer alması gerekir. Çünkü varsayılan değeri *none*'dır.

