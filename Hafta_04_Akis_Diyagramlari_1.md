# Hafta 4: Akış Diyagramları: Semboller, Analiz ve Tasarım - I

## 1. Giriş ve Ön Hazırlık
Daha önceki haftalarımızda operatörleri, algoritma kavramını ve bir problemi sözel (metin) olarak nasıl adım adım çözeceğimizi (sözde kod tasarımlarını) öğrendik. Ancak sadece yazıyla ifade edilen uzun algoritmaları takip etmek, özellikle karmaşık problemlerde kafa karıştırıcı olabilir.

İşte tam bu noktada, yazıyla anlattığımız algoritma çözümlerimizi **görsel şekiller** vasıtasıyla geometrik sembollere aktarırız. Bu görsel şablonlara **"Akış Diyagramı" (Flowchart)** adını veriyoruz. 

Önlisans programımızda temel hedefimiz, kod yazma işlemine geçmeden önce algoritmik düşünce becerinizi görsel olarak zihninize kazımaktır.

---

## 2. Neden Akış Diyagramı Kullanılır?
- **Görsellik:** İnsan beyni, karmaşık metinlerden ziyade diagram ve şekilleri saniyeler içinde anlayıp yorumlayabilir. 
- **Hatayı Çabuk Görme:** Sürecin hangi yöne aktığı, şartların nerede ikiye ayrıldığı oklara bakarak saniyesinde tespit edilebilir. Mantık hatası (Logic Error) ihtimali çok azalır.
- **Standart Dil:** Siz Türkiye'de bir akış diyagramı çizerseniz, bunu İngilizce bile bilmeyen Çin'deki bir yazılımcı dahi sembollerin evrensel olması sayesinde kolaylıkla okuyup kodlayabilir.

---

## 3. Akış Diyagramı Temel Sembolleri
Diyagramlarımız kafamıza göre çizdiğimiz şekiller değildir; uluslararası standartları vardır. İşte en temel basit seviye sembollerimiz:

1. **Elips (Oval):** Programın başladığı ve bittiği noktaları gösterir. Algoritma her zaman bir *"Başla"* elipsi ile başlar, işler bitince *"Bitir"* elipsi ile sonlanır.
2. **Paralelkenar:** Dışarıdan bilgi okumak (klavyeden giriş yapmak) veya sadece basit ekrana yansıtma (çıkış) durumlarında kullanılır (Genel giriş / çıkış birimidir).
3. **Dikdörtgen:** İşlem, atama veya hesaplama kutusudur. Tüm matematiksel işlemler (toplama, çıkarma) burada yapılır. 
4. **Eşkenar Dörtgen (Karar / Şart):** Mantıksal karşılaştırmalar içerir. (Eğer sayı sıfırdan büyükse sağa git, küçükse aşağı git gibi). İçinden "Evet" ve "Hayır" olmak üzere iki ok çıkar.
5. **Yön Okları:** Sürecin / programın hangi yöne doğru akması gerektiğini temsil eder.
  
![Akış Diyagramı](images/image5.png)
---

## 4. Akış Diyagramı Tasarım Örnekleri

Aşağıda, 3 farklı seviyede algoritma problemi ve bunların Meramid yardımıyla oluşturulmuş standart akış diyagramlarını bulacaksınız. 

### ÖRNEK 1: İki Sayının Toplamını Bulan Program
**Sözel Algoritma:**
1. Başla
2. Bellekten birinci sayıyı iste (Sayı1).
3. Bellekten ikinci sayıyı iste (Sayı2).
4. İkisini Topla ve "Toplam" olarak sakla (Toplam = Sayı1 + Sayı2).
5. "Toplam" değerini ekranda göster.
6. Bitir.

**Akış Diyagramı Şeması:**
```mermaid
graph TD
    A([Başla]) --> B[/1. Sayıyı Giriniz: Sayi1/]
    B --> C[/2. Sayıyı Giriniz: Sayi2/]
    C --> D[Toplam = Sayi1 + Sayi2]
    D --> E@{ shape: doc, label: "Toplam" }
    E --> F([Bitir])
```
*Açıklama:* Başla ve Bitir elipslerle belirtildi. Dışarıdan Sayi1 ve Sayi2 alınırken Giriş/Çıkış sembolü (burada paralelogram niyetine /.../ kullanıldı) uygulandı. İşlem (toplama işlemi) standart dikdörtgen olarak tasarlandı.

---

### ÖRNEK 2: Girilen Sayının Tek mi, Çift mi Olduğunu Bulan Program
Bu örnekte işin içine bir "KARAR (ŞART)" işlemi, yani *Eşkenar Dörtgen* giriyoruz. Sisteme bir sayı verilecek, bu sayı 2'ye tam bölünüyorsa "Çift", bölünmüyorsa "Tek" denilecek.

**Sözel Algoritma:**
1. Başla.
2. Kullanıcıdan bir sayı girilmesini iste.
3. Eğer (Sayı % 2 == 0) ise "Sayınız Çifttir" yaz.
4. Değilse ekrana "Sayınız Tektir" yaz.
5. Bitir.

**Akış Diyagramı Şeması:**
```mermaid
graph TD
    A([Başla]) --> B[/Bir Sayı Giriniz/]
    B --> C{Sayı%2==0}
    
    C -- EVET --> D@{ shape: doc, label: "Sayı Çifttir" }
    C -- HAYIR --> E@{ shape: doc, label: "Sayı tektir" }
    
    D --> F([Bitir])
    E --> F([Bitir])
```
*Açıklama:* Algoritmamız ilk defa dallanma işlemi ("branching") yaptı. Karar kutucuğumuz soruyu sordu, sağa veya sola doğru EVET/HAYIR yanıtlarına göre gidişat şekillendi, ama sonuçta iki ok da programın kapanışı olan Bitir'de buluştu.

---

### ÖRNEK 3: Vize ve Final Notu İle Geçme Durumu Hesaplama
Üniversitelerde yaygın kullanılan dersten geçme sisteminin algoritmasıdır. Vizenin %40'ı ile finalin %60'ı alınır, toplamı (ortalama) eğer 60 ve üzerinde ise Geçti, 60'tan küçükse Kaldı yazılır.

**Sözel Algoritma:**
1. Başla.
2. Vize notunu gir.
3. Final notunu gir.
4. Ortalama = (Vize * 0.4) + (Final * 0.6)
5. Eğer Ortalama >= 60 ise "Dersten Geçtin" yaz.
7. Değilse "Dersten Kaldın" yaz.
8. Bitir.

**Akış Diyagramı Şeması:**
```mermaid
graph TD
    A([Başla]) --> B[/Vize Notunu Gir/]
    B --> C[/Final Notunu Gir/]
    C --> D[Ortalama = Vize*0.4 + Final*0.6]
    D --> E{Ortalama >= 60 mı?}
    
    E -- EVET --> F@{ shape: doc, label: "Dersten geçtiniz" }
    E -- HAYIR --> G@{ shape: doc, label: "Dersten kaldınız" }
    
    F --> H([Bitir])
    G --> H([Bitir])
```



*Açıklama:* Burada hem bir hesaplama (Dikdörtgen İşlem Alanı) kullandık hem de bir algoritmik şart (Karar - Eşkenar Dörtgen) kullandık. Üçüncü örneğimiz, günlük hayattaki otomasyonların bilgisayarın mantığında nasıl işlediğine en güzel yatkınlığı sağlar.

---

### ÖRNEK 4: Klavyeden Girilen Üç Sayının En Büyüğünü Bulan Program
Bu örnekte klavyeden alınan üç sayı karşılaştırılır ve en büyük olan sayı bulunur. Önce ilk sayı en büyük kabul edilir; ardından ikinci ve üçüncü sayılar sırayla bu değerle karşılaştırılır.

**Akış Diyagramı Şeması:**

![Klavyeden girilen üç sayının en büyüğünü bulan akış diyagramı](images/en_buyuk_akis_diyagrami.jpg)

*Açıklama:* `a`, `b` ve `c` değerleri alındıktan sonra `enbuyuk` değişkenine önce `a` atanır. `b` ve ardından `c`, o anki en büyük değerle karşılaştırılır; daha büyük olan varsa `enbuyuk` güncellenir ve sonuç gösterilir.

### ÖRNEK 5: Dikdörtgenin Alanını ve Çevresini Hesaplayan Program
Bu akış diyagramında kullanıcıdan dikdörtgenin kısa ve uzun kenar uzunlukları alınır. Alan `kısa kenar × uzun kenar`, çevre ise `2 × (kısa kenar + uzun kenar)` formülüyle hesaplanıp ekranda gösterilir.

**Akış Diyagramı Şeması:**
```mermaid
graph TD
    A([Başla]) --> B[/Kısa kenarı gir/]
    B --> C[/Uzun kenarı gir/]
    C --> D[Alan = kısaKenar * uzunKenar]
    D --> E[Çevre = 2 * (kısaKenar + uzunKenar)]
    E --> F@{ shape: doc, label: "Alan ve çevreyi göster" }
    F --> G([Bitir])
```

### ÖRNEK 6: Dairenin Alanını ve Çevresini Hesaplayan Program
Bu örnekte kullanıcıdan dairenin yarıçapı alınır. Alan `π × yarıçap × yarıçap`, çevre ise `2 × π × yarıçap` formülleriyle hesaplanır. Hesaplamalarda `π` yaklaşık `3,14` olarak kullanılır.

**Akış Diyagramı Şeması:**
```mermaid
graph TD
    A([Başla]) --> B[/Yarıçapı gir/]
    B --> C[Alan = 3.14 * yarıçap * yarıçap]
    C --> D[Çevre = 2 * 3.14 * yarıçap]
    D --> E@{ shape: doc, label: "Alan ve çevreyi göster" }
    E --> F([Bitir])
```

### ÖRNEK 7: Sayının Pozitif, Negatif veya Sıfır Olduğunu Bulan Program
Bu örnekte kullanıcıdan bir sayı alınır. Önce sayının sıfırdan büyük olup olmadığı kontrol edilir; değilse sıfırdan küçük olup olmadığına bakılır. İki koşul da sağlanmıyorsa sayı sıfırdır.

**Akış Diyagramı Şeması:**
```mermaid
graph TD
    A([Başla]) --> B[/Bir sayı gir/]
    B --> C{Sayı > 0 mı?}
    C -- Evet --> D@{ shape: doc, label: "Sayı pozitiftir" }
    C -- Hayır --> E{Sayı < 0 mı?}
    E -- Evet --> F@{ shape: doc, label: "Sayı negatiftir" }
    E -- Hayır --> G@{ shape: doc, label: "Sayı sıfırdır" }
    D --> H([Bitir])
    F --> H
    G --> H
```

### ÖRNEK 8: Yaşa Göre Reşitlik Durumunu Bulan Program
Kullanıcıdan yaşı alınır ve 18 yaşını doldurup doldurmadığı karar yapısıyla kontrol edilir.

**Akış Diyagramı Şeması:**
```mermaid
graph TD
    A([Başla]) --> B[/Yaşı gir/]
    B --> C{Yaş >= 18 mi?}
    C -- Evet --> D@{ shape: doc, label: "Reşitsiniz" }
    C -- Hayır --> E@{ shape: doc, label: "Reşit değilsiniz" }
    D --> F([Bitir])
    E --> F
```

### ÖRNEK 9: Üç Kenarla Üçgen Oluşup Oluşmadığını Bulan Program
Kullanıcıdan üç kenar uzunluğu alınır. Kenarlar pozitifse üçgen eşitsizliği kontrol edilir: Herhangi iki kenarın toplamı, üçüncü kenardan büyük olmalıdır.

**Akış Diyagramı Şeması:**
```mermaid
graph TD
    A([Başla]) --> B[/a, b ve c kenar uzunluklarını gir/]
    B --> C{a > 0 ve b > 0 ve c > 0 mı?}
    C -- Hayır --> D@{ shape: doc, label: "Kenar uzunlukları pozitif olmalı" }
    C -- Evet --> E{a+b > c ve a+c > b ve b+c > a mı?}
    E -- Evet --> F@{ shape: doc, label: "Üçgen oluşur" }
    E -- Hayır --> G@{ shape: doc, label: "Üçgen oluşmaz" }
    D --> H([Bitir])
    F --> H
    G --> H
```

### ÖRNEK 10: 1'den 5'e Kadar Sayıları Yazdırma
**Soru:** 1'den başlayarak 5'e kadar olan sayıları ekrana yazdıran akış diyagramını oluşturunuz. Karar yapısı, sayacın 5'e ulaşıp ulaşmadığını kontrol ederek döngüyü sürdürür veya bitirir.

**Akış Diyagramı Şeması:**
```mermaid
graph TD
    A([Başla]) --> B[i = 1]
    B --> C{i <= 5 mi?}
    C -- Evet --> D@{ shape: doc, label: "i değerini yazdır" }
    D --> E[i = i + 1]
    E --> C
    C -- Hayır --> F([Bitir])
```

### ÖRNEK 11: 1'den 10'a Kadar Sayıların Toplamını Bulma
**Soru:** 1'den 10'a kadar olan tam sayıların toplamını bulan akış diyagramını oluşturunuz. Her turda sayaç toplama eklenir ve sayaç artırılır; sayaç 10'u geçince toplam ekranda gösterilir.

**Akış Diyagramı Şeması:**
```mermaid
graph TD
    A([Başla]) --> B[i = 1, toplam = 0]
    B --> C{i <= 10 mu?}
    C -- Evet --> D[toplam = toplam + i]
    D --> E[i = i + 1]
    E --> C
    C -- Hayır --> F@{ shape: doc, label: "toplamı göster" }
    F --> G([Bitir])
```

---

## 5. Haftalık Özet ve Alıştırma
Programlama yolculuğunuzda, problemleri algoritmaya çevirmeyi kolaylaştırmak amacıyla akış diyagramı modelleme dilini öğrendik. Doğru çizilmiş bir akış şeması, **C dili** başta olmak üzere her türlü programlama diline %99 doğrulukta bir çeviri demektir. O şema elinizdeyse, sadece çevirmek kalır.

**Laboratuvar / Bireysel Çalışma Soruları:**
1. Klavyeden kullanıcının girdiği bir doğum tarihine göre kullanıcının "Yaşını" hesaplayan (Günümüz Yılı - Doğum Yılı) formülü yazan ve akış diyagramını kendi defterinize semboller ile çizen bir algoritma tasarlayınız.
2. Akış sembolleri içindeki "İşlem / Atama (Dikdörtgen)" ile "Karar / Seçim (Eşkenar Dörtgen)" amaç olarak birbirinden neden ayrılmıştır? 

Önümüzdeki hafta, bu diagramlarda birden çok durum (iç içe kontroller) kısmını daha karmaşık senaryolarla (Akış Diyagramları II) işleyecek ve zihinsel hazırlığımızı tamamlayacağız. 
