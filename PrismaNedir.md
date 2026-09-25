Prisma Nedir?
Prisma, TypeScript/Node.js projelerinde veritabanıyla konuşmayı kolaylaştıran bir ORM (Object-Relational Mapping) aracı. Normalde veritabanına SQL sorguları elle yazarsın (SELECT * FROM posts WHERE...); Prisma bunun yerine sana tip güvenli bir JavaScript/TypeScript API'si verir — prisma.post.create(...), prisma.post.findMany(...) gibi. Üç ana parçası var:

schema.prisma — veritabanı tablolarını (model) tek bir dosyada, insan-okunur bir DSL ile tanımladığın yer
Prisma Client — o şemadan otomatik üretilen (generate edilen), tam tip güvenli sorgu kütüphanesi
Migrate — şema değişikliklerini gerçek veritabanına güvenli şekilde uygulayan araç


Custom cursor