#  Sürücüsüz Metro Simülasyonu (Rota Optimizasyonu)

Bu proje, bir metro ağındaki iki istasyon arasında en hızlı ve en az aktarmalı rotayı bulmak için hazırlanan bir simülasyon projesidir. Graf veri yapısı kullanılarak metro ağı modellenmiş ve BFS algoritmasıyla en az aktarmalı rota, A* algoritmasıyla da en hızlı rota bulunmuştur.



# Kullanılan Teknolojiler ve Kütüphaneler

- **Proje dili**: Python

- **collections**
  - `defaultdict`: Otomatik olarak varsayılan bir değer oluşturur. Önceden tanımlanmamış bir anahtara veri eklendiğinde hata vermez ve otomatik bir başlangıç değeri oluşturur. Bu projeden Metro hatları ve istasyonların organize edilmesi için kullanılmıştır.
  - `deque`: Başa ve sona hızlıca eleman eklemek veya çıkarmak için kullanılır. BFS algoritmasında kuyruk veri yapısı oluşturmak için kullanılmıştır.

- **heapq**
  - A* algoritmasında öncelik kuyruğu oluşturmak için kullanılmıştır. Min-heap mantığına göre çalışır. Bu sayede en küçük değer her zaman en önde olmuş olur.

- **typing**
  - `List`: Liste tipini
  - `Dict`: Sözlük data yapısını
  - `Tuple`: Sıralı veri grubunu
  - `Set`: Tekrarsız öğeler için küme yapısını
  - `Optional`: Bir değer varken sonucu döndürür ancak fonksiyonun dönme ihtimalinde de hata vermeden çalışır.



## Algoritmaların Çalışma Mantığı


# BFS (Breadth-First Search) Algoritması

BFS algoritması bir grafı katman katman dolaşarak çalışır. Bu projede BFS algoritması ile sırasıyla => Başlangıç istasyonundan itibaren komşular sırayla keşfedilmiştir => İlk hedef istasyona ulaşıldığında, o rota en az aktarmalı rota olmuş olur => `deque` kullanılarak kuyruk oluşturulur, ziyaret edilen istasyonlar bir `set` içinde tutulur => Aktarma sayısını azaltmak için hatlar arası geçiş en aza indirilir.

> Kullanım Amacı: En kısa adım sayısını garantilediği için bu projedeki en az aktarmalı rotayı bulmak için uygun bir algoritmadır.


# A* (A-Star) Algoritması 

A* algoritması bir graf üzerinde en kısa sürede hedefe ulaşmayı amaçlar. Bu projede A* algoritması ile => Her istasyon arası geçiş süresi (ağırlık) kullanılır => `heapq` ile öncelik kuyruğu oluşturulur ve her adımdaki toplam süre izlenir => Hedefe giden en kısa süreli yol seçilir.

> Kullanım Amacı: Öncelik kuyruğu kullandığı için daha az yol deneyerek hedefe ulaşır. A* bu nedenle tercih edilmiştir.



# Örnek Kullanım ve Test Sonuçları

Kod içindeki örnek testler:

### 1. AŞTİ'den OSB'ye:
- En az aktarmalı rota: AŞTİ → Kızılay → Ulus → Demetevler → OSB
- En hızlı rota: Aynı rota, **22 dakika**

### 2. Batıkent'ten Keçiören'e:
- En az aktarmalı rota: Batıkent → Demetevler → Gar → Keçiören
- En hızlı rota: Aynı rota, **21 dakika**

### 3. Keçiören'den AŞTİ'ye:
- En az aktarmalı rota: Keçiören → Gar → Sıhhiye → Kızılay → AŞTİ
- En hızlı rota: Aynı rota, **14 dakika**



# Projeyi Nasıl Geliştirebiliriz?

- `networkx` veya `matplotlib` gibi kütüphaneler kullanılarak proje görselleştirilebilir
-  A* algoritmasına heuristik eklenerek daha hızlı ve daha verimli çalışması sağlanabilir ya da doğrudan Dijkstra algoritması kullanılabilir.
- Daha anlamlı sonuçlar için daha fazla veri kullanılabilir.