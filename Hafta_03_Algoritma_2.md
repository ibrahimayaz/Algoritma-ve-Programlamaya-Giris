# Hafta 3: Algoritma: Operatörler, Terimler, Algoritma Tasarımı - II

## 1. Giriş ve Ön Hazırlık
Bir önceki haftada algoritmaya giriş yaptık, temel operatörler ile değişkenleri tanımladık ve basit, sıralı, karar gerektiren problemler üzerine bir temel oluşturduk. 

Bu haftanın konusu olan **Algoritma Tasarımı - II**'de, geçen dersteki Karar (If-Else) yapılarını biraz daha karmaşıklaştıracak, ilk kez "Döngü" (Tekrar - Loop) mantığının matematiksel temellerini kağıt üstünde kurgulayacağız. Bilgisayarların insanlardan asıl fark yarattığı özellikleri; sıkılmadan ve yorulmadan milyarlarca işlemi çok kısa bir sürede tekrarlayabilmeleridir. Bu hafta "Tekrar eden iş yapılarını" algoritmalara nasıl yedireceğimizi konuşacağız.

**Hedefler:**
- İç-içe geçmiş karar (şart) yapılarını ayırt edebilmek.
- Döngü/Tekrar algoritma bloğunun amacını kavramak.
- Adım sayaçları (Sayac) mantığını algoritmaya uyarlamak.
- Günlük ve matematiksel algoritma tasarımlarıyla analitik düşünme yeteneğimizi artırmak.

---

## 2. İç İçe Geçmiş Karar Yapıları
Bazı problemlerde algoritmanın sizi yalnızca iki yola (Evet veya Hayır) ayırması yetmez. O koşulun içerisinde, ikinci bir soru (şart) sormanız gerekir. 

Örneğin bir kullanıcınin ehliyet alıp alamayacağı üzerinden algoritma tasarladığımızı düşünelim:
Şart 1: Birey 18 Yaşından Büyük veya Eşit mi? (Yaş >= 18)
- Hayır ise: "Ehliyet Alamazsın"
- Evet ise, o zaman durup ikinci soruya (Şart 2) geçmeliyiz: Sağlık Raporu aldı mı?
    - Hayır ise: "Yaşın tutmasına rağmen sağlık muayenesi eksik."
    - Evet ise: "Sürücü Kursuna Kayıt Olabilir."

Burada Karar içinde Karar yatmaktadır. Eğer 1. şarta zaten Hayır çıksaydı, program sağlık raporu sorusuna hiç uğramadan kapatıp gidecekti.

---

## 3. Sayıcılar (Counters) ve Toplayıcı Yapısı
Sıklıkla göreceğiniz terimlerden olan **Sayaç (Counter)**, algoritma içerisinde 1, 2, 3.. diye veya ikişer, üçer sistemli bir şekilde değeri artan (ya da azalan) bir değişkendir. Özellikle Döngülerde ne kadar tekrar edeceğimizi bulmak için sayaç kurarız.
- Sayacı artırmak: `Sayac = Sayac + 1` (Matematikte bu formül yanlış görünse de, programlamada anlamı şudur: Sayaç kutusunun eski değerinin üstüne 1 ekle ve kendi içine geri kayıt et.)

Aynı durum hesaplamalarda **Toplayıcılar** için geçerlidir: 
- `Toplam = Toplam + Fiyat` (Kasadan her okutulan fiyatta, ana tutarın üstüne eklene eklene yeni bakiye oluşur.)

---

## 4. Döngü (Tekrar - Loop) Mantığına Giriş
Bir işlemin belirli bir amaca veya koşula ulaşana kadar tekrar edilmesine **Döngü (Loop)** denir.

**Örnek Senaryo:** Bilgisayara "Afiş 1" yazan, sonra "Afiş 2", sonrasında da "Afiş 100" yazan bir algoritma kuracağımızı düşünelim. Klasik sıradan algoritma yazarsak, oturup 100 ayrı satır kod/adim yazmamız gerekir (Adım 1. "Afiş 1" yaz, Adım 2. "Afiş 2" yaz... Adım 100. "Afiş 100" yaz).

Halbuki bunu döngü mantığı ile şöyle çözeriz:

Adım 1. Başla.
Adım 2. Sayaç isminde değişken oluştur ve başlangıç değeri olarak 1 ver `(Sayac=1)`.
Adım 3. Ekrana "Afiş " değişken yanına Sayac değerini yazdır.
Adım 4. Sayacın değerine 1 Ekle `(Sayac = Sayac + 1)`.
Adım 5. Eğer Sayac <= 100 ise Adım 3'e **Geri Dön (İşte döngü burada başlıyor)**.
Adım 6. Eğer Sayı 100'ü geçtiyse işlemi bırak, bitti, Adım 7'ye ilerle.
Adım 7. Bitir.

İşte 3 ile 5 adımları arasında bilgisayar kendi kendine sürekli geri gidip dönerek, insanoğlunun haftalarca sıkılıp yapacağı işi yüz mili-saniyede tamamladı.

---

## 5. Algoritma Tasarımı - II : Örnek Senaryolar

Aşağıda hem iç içe şart hem de sayaç/döngü algoritma tasarımlarına yer verilmiştir. Metin olarak tasarım yapmaya iyice adapte olunuz, zira haftaya bu metinleri sembollerle "Akış Diyagramlarına" dökeceğiz.

### Örnek 1: Sayının İşaretini Bulma
Soru: Dışarıdan girilen bir sayının Pozitif mi, Negatif mi yoksa Sıfır (0) mı olduğunu bulan algoritmayı kurun.
*(Burada 3 ihtimal var, tek soru (Evet/Hayır) yetmez, İç İçe sorulmalıdır.)*

1. Başla.
2. "Lütfen Bir Sayı Girin:" mesajını göster.
3. Kullanıcının bilgisini alıp `Sayi` değişkenine koy.
4. **Eğer** `Sayi == 0` ise;
   - Doğru ise ekrana "Sayınız Sıfırdır." yazıp Adım 6'ya git.
   - Yanlış ise Adım 5'e devam et.
5. **Eğer** `Sayi > 0` ise;
   - Doğru ise ekrana "Sayınız Pozitiftir." yaz.
   - Yanlış ise (Yani Ne 0, ne de Büyük değilse zaten Negatiftir) "Sayınız Negatiftir" yaz.
6. Bitir.

### Örnek 2: Döngü ve Toplayıcı Mantığı. (1'den N'ye Kadar Olan Sayıları Toplamak)
Soru: Kullanıcı sistem bir tavan sayı girecek (Diyelim ki 5 girdi). Sistemin görevi: (1+2+3+4+5) bu işlemi otomatik hesaplayıp sonucu bulacak. 

1. Başla.
2. Dışarıdan `LimitSayı` değişkenini al. (Örn 5 olsun).
3. Hafızada `Sayac = 1` ve `Toplam = 0` adında iki tane başlangıç değişkeni kutusu ata.
4. `Toplam = Toplam + Sayac` işlemini yap (Sıfırın üstüne 1 eklendi, artık toplam 1).
5. `Sayac = Sayac + 1` işlemini yap (Sayac'ı bir arttırdık. 2 oldu).
6. **Eğer (ŞART SOR) :** `Sayac <= LimitSayı` ise
   - Şart Doğruysa: Demekki daha bitmemiş işimiz, **Adım 4'e Geri Dön**. (Döngü).
   - Şart Yanlışsa: Demek ki üst limite ulaştık döngü koptu, Adım 7'ye ilerle.
7. Ekrana nihai hesabı bulduğunuz `Toplam` değişkenini yazdır.
8. Bitir.

---

## 6. Haftalık Özet
Bu hafta algoritmalarımıza yön verirken hem sayaç mekanizmalarını öğrendik hem de "tekrar işlemlerine" bilgisayarları nasıl mecbur bıraktığımızın (Adım X'e geri dön taktiğinin) taslağını oluşturduuk. Bu yapıları mantıksal olarak kavradığınız an, herhangi bir yazılıme kodunu okuduğunuzda (Aaa burada koşul açmış kodları geri fırlatıyor) şeklindeki sistematiği çok rahat göreceğinizi hissedebilirsiniz.

**Alıştırma Soruları:**
1. Bilgisayardan çarpım tablosunda sadece 5'leri (5x1=5, 5x2=10, 5x9=45.. gibi) bir döngü kullanarak tasarlayıp ekrana yazdırmak isterseniz nasıl bir Sözel Algoritma adımı tasarlar, hangi adımlara döngüyü fırlatırdınız? Kendi kağıdınıza, yukarıdaki örneklere benzer yazınız.
2. "Mantıksal Operatörler" başlığında geçen VEYA (OR) kullanılarak, "Ürün iadesi için ürünün ya fişinin olması VEYA kullanıcı kartıyla alınmış olması"na bakan iki durumlu bir sözel Karar Algoritması tasarlayınız.
