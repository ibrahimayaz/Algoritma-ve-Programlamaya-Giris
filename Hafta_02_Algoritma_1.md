# Hafta 2: Algoritma: Operatörler, Terimler ve Algoritma Tasarımı - I

## 1. Giriş ve Ön Hazırlık
Geçen hafta bilgisayarın çalışma prensiplerine ve programlamanın ne anlama geldiğine değindik. Bu hafta ise, kod yazmadan hemen önceki en kritik aşama olan "Algoritma" kavramına derinlemesine giriş yapıyoruz. Bilgisayarlar ne kadar hızlı olurlarsa olsunlar, onlara "ne yapacaklarını" adım adım söyleyecek bir mühendise (size) ihtiyaçları vardır.

**Bu Haftanın Hedefleri:**
- Algoritma kavramının tanımını ve günlük hayattaki örneklerini kavrayabilmek.
- Algoritmaların özellikleri ve tasarım prensiplerini anlamak.
- Değişken (Variable) ve Sabit (Constant) gibi en temel yazılım terimlerini kavramak.
- Matematiksel, ilişkisel ve mantıksal operatörlerin kullanım amaçlarını öğrenmek.

---

## 2. Algoritma Nedir?
Algoritma; belirli bir problemi çözmek ya da belirli bir amaca (sonuca) ulaşmak için tasarlanmış, **başlangıcı ve sonu belli olan**, adım adım kurallar (yönergeler) bütünüdür.

Algoritma bir bilgisayar kodu değildir, sadece problemin çözümünün insan dilindeki mantıksal dökümüdür. Doğru yazılmış bir algoritma, İngilizce, Türkçe veya matematikle ifade edilebilir; ardından Python, C, Java gibi diller aracılığıyla kodlanabilir.

### 2.1. Algoritmanın Temel Özellikleri
Geçerli ve işe yarar bir algoritmanın bazı evrensel kuralları olmalıdır:
1. **Giriş ve Çıkış:** Mutlaka bir başlangıcı (girdi) ve bir sonucu (çıktı) olmalıdır. 
2. **Kesinlik (Netlik):** Adımlar çok net olmalı, yorum farkına dayalı kafa karışıklığı (belirsizlik) yaratmamalıdır. (Örn: "Biraz tuz ekle" yerine, "2 çay kaşığı tuz ekle" denilmelidir).
3. **Sonluluk:** Bir algoritma sonsuz döngüye(kısır döngü) girmeden makul bir deneme sonrasında kesinlikle sonlanmalıdır.
4. **Etkinlik:** Sorunu doğru ve gerektiği kadar adımda çözmelidir (ne çok kısa ne lüzumsuz derecede uzun).

---

## 3. Temel Terimler: Değişkenler ve Sabitler
Bilgisayar bir işlem yaparken verilere ihtiyaç duyar ve bu verileri geçici belleğinde (RAM üzerinde) depolar. Tıpkı bir mutfakta baharatların farklı kavanozlara konulması gibi, veriler de RAM'deki adreslerde tutulur.

### 3.1. Değişken (Variable) Nedir?
Çalışma zamanında (program akarken) içerisindeki değeri değişebilen, farklı veriler atanabilen RAM kutucuklarıdır. 
- *Örnek:* Bir oyundaki `oyuncuCan` değeri (100 ile başlar, kurşun yedikçe 80'e, 50'ye düşer). Veya matematiksel bir işlemde dışarıdan okuduğunuz `Sayi1` değişkeni.

**Değişken İsimlendirme Kuralları:**
Programlamaya başlarken verilerimize isimler koyacağız (X, Sayi, Yas, Not).
Bu aşamada değişkenlere isim verirken genel kurallar:
- Sayı ile başlanmaz (5sayi olmaz, fakat sayi5 olur).
- Özel karekter(_ alt tire hariç) ile başlanmaz ve özel karekter(_ alt tire hariç) içeremez.
- Türkçe karakterler (ç, ş, ğ, ü, ö, ı) kullanılmamaya çalışılır. 
- Boşluk bırakılmaz (Ogrenci Notu yerine OgrenciNotu veya Ogrenci_Notu yazılır).
- Değişken adı ilgili programlama diline ait anahtar kelimelerden oluşamaz.

### 3.2. Sabit (Constant) Nedir?
Program çalıştığı andan kapanana kadar içindeki değerinin hiç değişmeyeceği kesin olan verilere ait kutucuklardır.
- *Örnek:* Matematik formülündeki "Pi (π) Sayısı" her zaman 3.14'tür program ortasında 4.2 olmaz. Ya da 1 haftadaki gün sayısı her zaman `7`'dir sabittir. 

---

## 4. Operatörler
Verileri işlemek, karşılaştırmak ve bir sonuca ulaşmak için kullandığımız sembollerdir. Operatörler, algoritmanın hesaplama kalbidir. Bizleri 3 temel gruba ayırıyoruz: Aritmetik, Karşılaştırma, Mantıksal.

### 4.1. Aritmetik (Matematiksel) Operatörler
Günlük hayattan bildiğiniz matematiksel işlemleri yaparlar:
- **+ (Toplama)** 
- **- (Çıkarma)**
- *** (Çarpma)** (Çarpı işareti olarak X değil yıldız kullanırız).
- **/ (Bölme)**
- **% (Mod Alma):** Programlamaya yeni giren bir kavramdır. "Bölümünden kalan" anlamındadır. Örneğin: `10 % 3 = 1`'dir. (10'u 3'e bölseniz kalan 1 olur). Algoritmalarda sayıların "tek mi çift mi" olduğunu anlamak için sıkça kullanılır.

### 4.2. İlişkisel (Karşılaştırma) Operatörleri
İki veriyi ölçüp tartar, sonuç olarak genellikle "Doğru (Evet)" veya "Yanlış (Hayır)" çıkartırlar. "Eğer bir durum varsa bunu yap" derken bu operatörler sorgulanır.
- **> (Büyüktür):** `5 > 3` (Doğru)
- **< (Küçüktür):** `4 < 2` (Yanlış)
- **>= (Büyük Eşittir):** `Not >= 60` 
- **<= (Küçük Eşittir):** `Not <= 100`
- **== (Eşittir):** Matematikteki tek `=`, atama yaparken; eğer iki sayının birebir aynı olup olmadığını "soruyorsak" iki kez eşittir `==` kullanılır. (`Sifre == "1234"` ise giriş yap.)
- **!= (Eşit Değildir):** İki verinin farklı olduğunu ölçer. `Kullanici_Ad != ""` (Kullanıcı adı boş değilse işlemi yap.)

### 4.3. Mantıksal Operatörler
Birden fazla karşılaştırma veya şarta ihtiyacımız olduğunda şartları birbirine bağlar. 
- **VE (AND) Operatörü:** İstenen şartların **tümünün** doğru olmasını ister. Biri bile yanlışsa işlem iptal olur. 
  *(Örn: Burs alma şartı = "Not ortalaması 80'in üzerinde olacak" VE "Disiplin cezası almamış olacak")*
- **VEYA (OR) Operatörü:** İstenen şartlardan **en az birisinin** doğru olması yeterlidir. 
  *(Örn: Kayıt olma şartı = "Kredi Kartı ile ödeyecek" VEYA "Nakit ödeyecek". İkisinden biriyle işlem onaylanır).*
- **DEĞİL (NOT) Operatörü:** Mantığın tersini, tersine çevirmeyi kapsar. "Doğru" olanı "Yanlış", "Yanlış" olanı "Doğru" yapar.

---

## 5. Algoritma Yapıları Nelerdir?
Algoritmalar temelde yukarıdan aşağıya (1, 2, 3.. şeklinde) adım adım sırayla çalışırlar (Sıralı yapı). Ancak sorunlar ilerledikçe bu sıralı dizilişte "Seçim/Karar" yapısına girmek zorundayız.

**Karar (Dallanma) Yapısı Nedir?**
Hayattaki bir yol ayrımı gibidir. Algoritma her yoldan gidemez, yukarıda gördüğümüz "İlişkisel Operatörler" ile sistem bir soru sorar, sonuca göre ya A yolundan ya da B yolundan akış devam eder. 
Örneğin yukarıda yazdığımız Vize-Final geçme algoritması: `Eğer (If) Puan >= 60 -> Geçecek Değilse (Else) -> Kalacak.` 

*(Not: Algoritma Döngü (Tekrar) yapılarını ilerleyen haftalarda kapsamlı şekilde işleyeceğiz).*

---

## 6. Sözel Algoritma Tasarım Örnekleri

**Örnek 1: İki ayrı notu alıp ortalama çıkaran algoritma:**
Adım 1. Başla
Adım 2. Vize (V) notunu gir, Final (F) notunu gir
Adım 3. Ortalama = ( V * 0.4 ) + ( F * 0.6 ) hesabı yap
Adım 4. Bulunan "Ortalama" değerini Ekrana yaz.
Adım 5. Bitir.

**Örnek 2: ATM'den Para Çekme Mantığı:**
Adım 1. Başla
Adım 2. Kullanıcıdan şifreyi girmesini iste.
Adım 3. Şifre `1234` değerine **Eşit (==) mi**?
Adım 4. Eşitse 5'inci adıma geç. Eşit DEĞİLSE 9'uncu adıma (Bitir) git. (Karar yapısı)
Adım 5. Çekilecek tutarı gir.
Adım 6. Girilen tutar BankaHesabı'ndan Küçük Eşit (<=) mi? 
Adım 7. Eşit veya Küçükse Parayı ver, hesabından düş. Tutar Yetersizse "Bakiye Yetersiz" yaz.
Adım 8. Kartı İade et.
Adım 9. Bitir.

---

## 7. Hafta Özeti
Bu hafta algoritmalarda verilerin nasıl tutulacağını (Değişkenler), sabit olan değişmeyen verileri, iki sayı veya veriyi birbiriyle tarttığımız operatörleri ve mantık kapılarını öğrendik. 

**Alıştırmalar:**
1. Günlük hayattan 2 tane Sabit veriye ve 2 tane Değişken veriye örnek veriniz.
2. `Sıcaklık == 100` ifadesi ile `Sıcaklık = 100` ifadesinin programlama mantığında çalışma amacı olarak farkı nedir? Araştırınız.
3. Elinizde 1'den 100'e kadar rakamlar var. Mod (%) operatörünü kullanarak o sayının çift bir sayı olup olmadığını tespit eden matematiksel sorgunuz nasıl olurdu? Kağıda yazınız.

Haftaya, operatörler üzerinden tasarımlar yapmaya (Algoritma Tasarımı - II) devam edeceğiz. Bol antrenman dileriz.
