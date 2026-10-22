# CSS Arka Planlar (Backgrounds)
CSS'te arka plan özellikleri, HTML elementlerinin arka plan rengini, konumunu, boyutunu ve görüntülenme biçimini kontrol etmemizi sağlar.

Arka planlar yalnızca dekoratif amaçlarla kullanılmaz. Bir web sayfasında bölümleri birbirinden ayırmak, içerikleri vurgulamak, görsel hiyerarşi oluşturmak ve metinlerin okunabilirliğini artırmak için de kullanılır.

Örneğin bir web sitesinin hero alanında büyük bir arka plan görseli, kart bileşenlerinde sade bir arka plan rengi veya bir başlık bölümünde gradient kullanılabilir.

```
    .hero {
        background-color: #26251f;
        background-image: url("hero.jpg");
        background-repeat: no-repeat;
        background-position: center;
        background-size: cover;
    }
```

Bu örnekte arka plan görseli tekrar etmeden, ortalanarak ve elementin alanını kaplayacak şekilde görüntülenir.