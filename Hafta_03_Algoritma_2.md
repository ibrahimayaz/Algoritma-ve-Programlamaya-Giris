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
Karar yapısı, bir koşulun doğru ya da yanlış olmasına göre algoritmanın farklı adımları izlemesini sağlar. Önce tek koşullu basit kararları, ardından bir kararın içinde yeni bir kararın bulunduğu **iç içe geçmiş kararları** inceleyelim.

### 2.1. Basit Karar Yapısı
Bir koşulun sonucuna göre iki farklı işlemden birini seçmek, basit karar yapısıdır. Örneğin sınavdan geçme durumunu bulan algoritmada yalnızca notun 50 veya üzerinde olup olmadığına bakarız.

**Örnek: Sınavdan Geçti mi?**

1. Başla.
2. Öğrencinin sınav notunu alıp `Not` değişkenine koy.
3. **Eğer** `Not >= 50` ise ekrana "Sınavı Geçtiniz." yaz. **Değilse** ekrana "Sınavdan Kaldınız." yaz.
4. Bitir.

Bu örnekte tek bir soru sorulur. Koşul doğruysa bir mesaj, yanlışsa diğer mesaj gösterilir; ikinci bir koşul kontrol edilmez.

### 2.2. İç İçe Geçmiş Karar Yapısı
Bazı problemlerde ilk koşulun sonucu, başka bir koşulun kontrol edilip edilmeyeceğini belirler. İlk koşul sağlanıyorsa ikinci bir soru sorarız; sağlanmıyorsa bu soruya hiç geçmeyiz. Kararın içinde başka bir karar bulunduğu için bu yapıya **iç içe geçmiş karar yapısı** denir.

**Örnek: Sınav Sonucuna Göre Başarı Durumu**

Bu kez yalnızca geçme-kalma durumunu değil, sınavı geçen öğrencinin başarı düzeyini de bulalım. Önce geçme koşulunu kontrol eder, yalnızca geçen öğrenciler için ikinci koşula bakarız.

1. Başla.
2. Öğrencinin sınav notunu alıp `Not` değişkenine koy.
3. **Eğer** `Not >= 50` ise;
   - **Eğer** `Not >= 85` ise ekrana "Sınavı geçtiniz, başarı düzeyiniz yüksek." yaz.
   - **Değilse** ekrana "Sınavı geçtiniz." yaz.
4. **Değilse** ekrana "Sınavdan kaldınız." yaz.
5. Bitir.

İkinci koşul (`Not >= 85`), yalnızca ilk koşul (`Not >= 50`) doğru olduğunda kontrol edilir. Örneğin notu 40 olan bir öğrenci için algoritma doğrudan "Sınavdan kaldınız." mesajını verir; yüksek başarı koşulunu değerlendirmez.

**Örnek: Ehliyet Başvurusu İçin Uygunluk**

Ehliyet başvurusu için önce yaş koşulunu, yaş koşulu sağlanıyorsa sağlık raporunun bulunup bulunmadığını kontrol edelim.

1. Başla.
2. Kullanıcının yaşını alıp `Yas` değişkenine koy.
3. **Eğer** `Yas >= 18` ise;
   - Sağlık raporu olup olmadığını alıp `SaglikRaporuVarMi` değişkenine koy.
   - **Eğer** `SaglikRaporuVarMi` doğru ise ekrana "Sürücü kursuna kayıt olabilirsiniz." yaz.
   - **Değilse** ekrana "Yaş koşulunu sağlıyorsunuz ancak sağlık raporunuz eksik." yaz.  
4. **Değilse** ekrana "18 yaşından küçük olduğunuz için başvuru yapamazsınız." yaz.
5. Bitir.

Burada ilk koşul yaşla ilgilidir. Kullanıcı 18 yaşından küçükse algoritma sağlık raporunu sormadan sonuç verir. Yaş koşulu sağlanırsa ikinci karar devreye girer. Böylece bir kararın sonucuna bağlı olarak başka bir kararın çalışmasını sağlamış oluruz.

**Örnek: Sipariş Tutarına Göre Kargo Ücreti**

Bir alışveriş sitesinde, sipariş tutarı belirli bir limite ulaşınca kargo ücretsiz olsun. Limitin altındaki siparişlerde ise standart veya hızlı kargo seçimine göre ücret belirlensin.

1. Başla.
2. Sipariş tutarını `SiparisTutari` değişkenine, kargo tercihini `HizliKargoMu` değişkenine al.
3. **Eğer** `SiparisTutari >= 1000` ise ekrana "Kargo ücretsiz." yaz.
4. **Değilse**;
   - **Eğer** `HizliKargoMu` doğru ise ekrana "Kargo ücreti 100 TL." yaz.
   - **Değilse** ekrana "Kargo ücreti 50 TL." yaz.
5. Bitir.

Bu örnekte kargo tercihi, yalnızca sipariş tutarı 1000 TL'nin altındaysa kontrol edilir. Böylece bir koşulun başka bir koşulun içinde yer aldığı üçüncü bir iç içe karar örneği görmüş olduk.

---

## 3. Sayıcılar (Counters) ve Toplayıcı Yapısı
Sıklıkla göreceğiniz terimlerden olan **Sayaç (Counter)**, algoritma içerisinde 1, 2, 3.. diye veya ikişer, üçer sistemli bir şekilde değeri artan (ya da azalan) bir değişkendir. Özellikle Döngülerde ne kadar tekrar edeceğimizi bulmak için sayaç kurarız.
- Sayacı artırmak: `Sayac = Sayac + 1` (Matematikte bu formül yanlış görünse de, programlamada anlamı şudur: Sayaç kutusunun eski değerinin üstüne 1 ekle ve kendi içine geri kayıt et.)

Aynı durum hesaplamalarda **Toplayıcılar** için geçerlidir: 
- `Toplam = Toplam + Fiyat` (Kasadan her okutulan fiyatta, ana tutarın üstüne eklene eklene yeni bakiye oluşur.)

---

## 4. Döngü (Tekrar - Loop) Mantığına Giriş
Bir işlemin belirli bir amaca veya koşula ulaşana kadar tekrar edilmesine **Döngü (Loop)** denir.

Bir döngünün temelinde üç adım vardır: başlangıç değerini belirlemek, tekrarlanacak işlemi yapmak ve her turda değeri güncelleyip devam koşulunu kontrol etmek. Koşul sağlandığı sürece işlem tekrarlanır; sağlanmadığında döngü biter.

### Örnek 1: Afişleri Numaralandırma
Bilgisayarın ekrana "Afiş 1", "Afiş 2" ve bu şekilde "Afiş 100" yazmasını isteyelim. Döngü kullanmazsak her afiş için ayrı bir adım yazmamız gerekir. Sayaç kullanarak bu tekrarları kısa bir algoritmayla yapabiliriz.

1. Başla.
2. `Sayac = 1` olarak başlangıç değerini ata.
3. Ekrana "Afiş " metnini ve `Sayac` değerini yaz.
4. `Sayac = Sayac + 1` işlemini yap.
5. **Eğer** `Sayac <= 100` ise Adım 3'e geri dön.
6. **Değilse** Bitir.

Sayaç her turda bir arttığı için algoritma afişleri 1'den 100'e kadar sırasıyla yazar ve 100'ü geçince durur.

### Örnek 2: 1'den 3'e Kadar Sayma
Sayaç kullanarak ekrana 1, 2 ve 3 sayılarını yazdıralım.

1. Başla.
2. `Sayac = 1` olarak başlangıç değerini ata.
3. `Sayac` değerini ekrana yaz.
4. `Sayac = Sayac + 1` işlemini yap.
5. **Eğer** `Sayac <= 3` ise Adım 3'e geri dön.
6. **Değilse** Bitir.

### Örnek 3: Geri Sayım
Bir başlangıç sayısından 1'e kadar geriye doğru sayıp ekrana yazdıralım. Bu örnekte sayaç artmak yerine her turda bir azalır.

1. Başla.
2. `Sayac = 5` olarak başlangıç değerini ata.
3. `Sayac` değerini ekrana yaz.
4. `Sayac = Sayac - 1` işlemini yap.
5. **Eğer** `Sayac >= 1` ise Adım 3'e geri dön.
6. **Değilse** Bitir.

Ekrana sırasıyla 5, 4, 3, 2 ve 1 yazılır. Sayaç 0 olduğunda koşul yanlış olur ve döngü sona erer.

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
