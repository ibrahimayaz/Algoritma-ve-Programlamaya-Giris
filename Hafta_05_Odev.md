# Hafta 5 Ödevi - Algoritma Tasarımı ve Temel Kodlama

**Teslim Kuralları ve Önemli Uyarılar:**
* Bu ödevin cevaplarını içeren dosyanızı (PDF veya Word formatında), belirtilen son teslim tarihine kadar **Öğrenme Yönetim Sistemine (ÖYS/LMS)** yüklemeniz gerekmektedir. Zamanında sisteme yüklenmeyen ödevler sistem tarafından otomatik olarak kapatılacak ve değerlendirmeye alınmayacaktır.
* Yapay zeka kullanımını doğrudan engellemek ve analitik düşünceyi ölçmek amacıyla; aşağıdaki **tüm sorular kişiye (Öğrenci Numaranıza) özeldir**. Başkasının verileriyle veya standart anonim verilerle yapılan yapay zeka kopyası ödevler sıfır (0) olarak değerlendirilecektir.

---

### Soru 1: Sözde Kod (Pseudocode) Tasarımı (35 Puan)
Öğrenci numaralarının her bir hanesi sizin veritabanınızdır. Göreviniz şu:
Kendi **kendi öğrenci numaranızın** rakamlarını tek tek inceleyen (örneğin 2100456 ise sırayla 2, 1, 0, 0, 4, 5, 6), bu rakamların içerisinden **sadece TEK sayı olanları (1, 3, 5, 7, 9)** tespit edip toplayan, çift sayıları ise es geçen ve kodun sonunda bu toplam değeri ekrana basan algoritmanın **SÖZDE KODUNU (Adım 1. Başla, Adım 2.. şeklinde)** yazınız. 

**Kontrol Adımı (Önemli):** Sözde kodu yazdıktan sonra ödev kağıdınızın altına Öğrenci Numaranızı yazıp, tasarladığınız algoritmanın sizin numaranız girdiğinde **tam olarak hangi sonucu** bulacağını adım adım manuel (elle) hesaplayarak algoritmanın doğruluğunu teyit ediniz.

### Soru 2: Akış Diyagramı (Flowchart) Tasarımı (35 Puan)
Bu soruda **"Kendi Öğrenci Numaranızın EN SON HANESİ"** sizin algoritma **"Zıplama/Artış Miktarınız"** olacaktır. *(Uyarı: Eğer numaranızın son hanesi "0" (Sıfır) ise, sonsuz döngüye girmemesi için artış miktarını mecburen 5 (beş) olarak kabul ederek çözünüz).*
    
Sıfırdan başlayarak, döngü her döndüğünde sayının üzerine kendi **artış miktarınız kadar** değer eklendiği ve bu toplam sayının **60'ı geçtiği anda durduğu** bir problemin **Akış Diyagramını** tasarlayınız.
*Örneğin, öğrenci numaranızın sonu 4 ise; 0, 4, 8, 12.. şeklinde sayılar üretilip toplanmalı, koşul 60'ı aşınca diyagram sonlandırılmalıdır.*

* **Çözüm Yönetimi:** Akış diyagramınızı elinizle bir kağıda standart algoritma sembollerini (Paralelkenar, Eşkenar dörtgen, Dikdörtgen vb.) kullanarak çiziniz ve bu çizimin net okunabilir bir fotoğrafını ödev dosyanızın (Word/PDF) içine yerleştiriniz. Bilgisayar çizim araçlarını da (Draw.io, Lucidchart, Mermaid vb.) kullanabilirsiniz.

### Soru 3: Kişiye Özel Döngü ve Sayı Sınıflandırma (30 Puan)
Bu soruda kullanacağınız değerleri kendi öğrenci numaranızdan türetiniz:

- **Artış miktarı (A):** Numaranızın son hanesi. Son hane `0` ise `A = 5` alın.
- **Bölen (B):** Numaranızın sondan ikinci hanesi. Bu hane `0` ise `B = 2` alın.

Algoritmanız `x = 0` değerinden başlamalı ve her turda önce `x` değerine `A` eklemelidir. Yeni `x` değeri **60'ı aşarsa**, bu değeri sınıflandırmadan döngüyü bitirmelidir. `x` değeri 60'ı aşmıyorsa aşağıdaki kurallara göre yalnızca bir gruba ekleyiniz:

1. `x` tek ise **Teklerin Toplamı** değişkenine ekleyiniz.
2. `x` çift ve `B` değerine tam bölünüyorsa **B'ye Bölünen Çiftlerin Toplamı** değişkenine ekleyiniz.
3. `x` çift ve `B` değerine tam bölünmüyorsa **B'ye Bölünmeyen Çiftlerin Toplamı** değişkenine ekleyiniz.

Döngü bittiğinde bu üç toplamı ekrana yazdırınız. Çözümünüzde:

1. Kendi numaranızdan `A` ve `B` değerlerini nasıl elde ettiğinizi gösteriniz.
2. Algoritmanın sözde kodunu adım adım yazınız.
3. Aynı algoritmanın akış diyagramını standart sembollerle çiziniz. Sözde kod ile diyagramın kararları ve işlem sırası birbiriyle aynı olmalıdır.
4. Her turdaki `x` değerini, hangi gruba girdiğini ve üç toplamın güncel değerlerini gösteren bir iz sürme tablosu hazırlayınız. 60'ı aşan ilk `x` değerini de tabloda gösteriniz; bu değer hiçbir toplama eklenmemelidir.

**Puanlama:** Sözde kod 10, akış diyagramı 12, kişisel değerlere göre doğru iz sürme ve sonuçlar 8 puandır.

**Bireysel kontrol:** Değerlendirme sırasında öğretmen, iz sürme tablonuzdan seçeceği bir turda `x` değerinin hangi gruba girdiğini ve toplamların nasıl güncellendiğini açıklamanızı isteyebilir.

---
*Başarılar dileriz. Doğrudan hazır çözüm aramak yerine algoritmik düşünceyi kullanarak zihninizi yormanız, mesleki hayatınız için en değerli kazancınız olacaktır.*
