# Hafta 11 Ödevi - Diziler (Arrays) ve Fonksiyonlar (Functions)

**Teslim Kuralları ve Önemli Uyarılar:**
* Bu ödevi (PDF veya Word formatında), belirtilen son teslim tarihine kadar **Öğrenme Yönetim Sistemine (ÖYS/LMS)** yüklemeniz gerekmektedir. 
* Tıpkı önceki ödevlerinizde olduğu gibi, **tüm sorular tamamen Öğrenci Numaranıza ve Kişisel Bilgilerinize göre** çözülmek zorundadır. Yapay zekanın tek tip üreteceği standart anonim (örnek) verilerle teslim edilen ödevler kesinlikle değerlendirilmeyecek ve sıfır (0) notu verilecektir. Soruların amacı kopyala-yapıştır kod yazmanız değil, ilgili kodu kendi verinizle elle analiz (Trace) etmenizdir.

---

### Soru 1: Dizi (Array) Manipülasyonu (50 Puan)
Kendi **Öğrenci Numaranızın** rakamlarını, tam sayı dizisinin (array) elemanları olarak tutan bir `int` dizisi oluşturduğunuzu varsayalım. *(Örneğin numaranız 220556 ise diziniz `int numaram[6] = {2, 2, 0, 5, 5, 6};` olmalıdır).*

1. Öğrenci numaranızın uzunluğu kadar kapasitesi olan bu diziyi C dilinde tanımlayınız.
2. Bir `for` döngüsü kullanarak dizinin içindeki elemanları (rakamları) baştan sona tarayınız.
3. Dizinin içinde gezinen bu döngüde bir `if` şartı kurgulayınız: Eğer dizinin o anki index'inde bulunan rakam **ÇİFT BİR SAYI ise**, o rakamın değerini **Kendi İsminizin harf sayısı** kadar artırınız. Rakam **TEK SAYI ise** hiçbir işlem yapmayıp dizide aynen bırakınız.
4. Bu işlemi yapan C kod parçasını (sadece dizi, for ve if kısmı yeterlidir) ödev kağıdınıza yazınız.
5. **Kritik Adım:** Yazdığınız bu koda kendi numaranızı girdiğinizde; algoritma çalıştığı an itibariyle RAM'de dizinizin **EN SON DURUMUNUN (dizinin son halindeki rakamların)** ne olacağını manuel (elle) hesaplayarak kodun altına açıkça yazınız.

### Soru 2: Kurye (Return) Fonksiyon Tasarımı ve Main'den Çağrı (50 Puan)
Bu soruda `main()` ana mekanizmasından tamamen bağımsız, özel bir matematiksel Alt-Program (Function) tasarlayacaksınız.

1. **Fonksiyon Tanımlama:** Geriye `int` (Tamsayı) döndüren ve adı **Kendi İsminiz** olan (Örneğin: `int islemAhmet(...)` veya `int ayseHesapla(...)` şeklinde) bir C fonksiyonu oluşturunuz.
2. Bu fonksiyon dışarıdan (parametre olarak) 2 adet tam sayı (`int sayi1, int sayi2`) almalıdır.
3. **Fonksiyonun Görevi:** Dışarıdan gelen bu iki sayıyı birbiriyle toplasın. Çıkan sonucu, **Öğrenci Numaranızın Son İki Hanesine** bölerek **kalanını (Mod %) hesaplasın** ve bu değeri `main`'e `return` etsin. *(Not: Eğer numaranızın son iki hanesi "00" ise programın çökmemesi için bölen sayıyı "10" olarak kurgulayınız).*
4. **Main() Çağrısı:** Alt satırlara geçerek standart `int main()` bloğunuzu açınız. Main içerisinde kendi adınızı verdiğiniz bu fonksiyonu çağırınız. Çağırırken 1. Parametre olarak bugünkü **Yaşınızı**, 2. Parametre olarak ise **Doğum Yılınızı (Örn: 2004)** parantez içerisine yazarak gönderiniz.
5. **Kritik Adım:** Bu programı C dilinde yazdığınız (Fonksiyon ve Main kodları) kısmı ödeve ekleyiniz. Kodun tam altına; "Gönderdiğim parametreler ışığında, benim ismimi taşıyan fonksiyonum bana tam olarak **[..ŞU SAYIYI..]** sonucunu return edecektir. Çünkü işlemi şu şekilde yapmıştır..." diyerek **kendi verilerinize ait** matematiksel sonucu kanıtlayınız.

---
*Başarılar dileriz. Soruları kendi kişisel şablonunuza dökerek adım adım çalıştırmanız (Kodu kafanızda derlemeniz), bu konulardaki "akış ve adresleme" mantığını yapay zeka araçlarından çok daha iyi pekiştirmenizi sağlayacaktır.*