# Hafta 1: Genel Programlama Bilgisi, Programlamanın Temelleri ve Bilgisayarın Temelleri

## 1. Giriş ve Ön Hazırlık
Bu haftaki dersimiz, yazılım geliştirme dünyasına ilk adımınızı atmanızı sağlayacaktır. Programlamayı öğrenmeden önce, kodlarımızı çalıştıracak olan temel aracımız "bilgisayarı" ve "çalışma mantığını" anlamamız son derece önemlidir. Önlisans seviyesine uygun olarak hazırlanmış bu dökümanda adım adım ve hiyerarşik bir dil kullanılmaktadır.

**Hedefler:**
- Bilgisayarın temel bileşenlerini (donanım ve yazılım) tanımak.
- Bilgisayarların nasıl çalıştığı ve veriyi nasıl işlediği hakkında temel bilgiye sahip olmak.
- Programlama, yazılım, kodlama kelimelerinin teknik karşılıklarını öğrenmek.
- Bilgisayar dillerinin seviyeleri hakkında fikir sahibi olmak.

---

## 2. Bilgisayarın Temelleri

Bilgisayar; kendisine verilen verileri (girdileri) alan, kendi içindeki kurallara ve programlara göre işleyip anlamlı sonuçlar (çıktılar) üreten ve bu verileri depolayabilen elektronik bir cihazdır. Bir bilgisayarın çalışma prensibini insan beynine benzetebiliriz. Çevreden gelen uyarıları alırız, beyinde işleriz ve bir eylemle tepki veririz.

Bilgisayar temelde iki ana unsurdan oluşur: **Donanım (Hardware)** ve **Yazılım (Software)**.

### 2.1. Donanım (Hardware)
Donanım, bilgisayarın elle tutulup gözle görülebilen fiziksel parçalarıdır. 
- **İşlemci (CPU):** Bilgisayarın beynidir. Tüm matematiksel ve mantıksal işlemler burada yapılır.
- **Bellek (RAM - Random Access Memory):** İşlemcinin anlık olarak ihtiyaç duyduğu verilerin geçici olarak tutulduğu yerdir. Elektrik kesildiğinde buradaki veriler silinir.
- **Sabit Disk / SSD:** Bilgilerimizin kalıcı olarak depolandığı yerdir. Cihaz kapansa dahi verileriniz uçar gitmez.
- **Giriş Birimleri:** Fare, klavye, mikrofon, kamera. (Bilgi almak için kullanılır.)
- **Çıkış Birimleri:** Monitör (Ekran), hoparlör, yazıcı. (İşlenen bilgiyi kullanıcıya sunmak için kullanılır.)

### 2.2. Yazılım (Software)
Yazılım, bilgisayarın donanımlarını kontrol eden ve belirli bir amaca yönelik çalışan yönnergeler bütünü veya kodlar kümesidir. Donanım sadece cihazın ruhsuz bir iskeletiyken, yazılım ona can veren zekadır.
- **Sistem Yazılımları:** Windows, macOS, Linux, Android gibi İşletim Sistemleri. 
- **Uygulama Yazılımları:** Word, Excel, Chrome Tarayıcı, Video oyunları.

---

## 3. Programlamanın Temelleri

Gelelim ana konumuz olan programlamaya. 

### 3.1. Programlama Nedir?
Programlama (veya kodlama), bir problemi çözmek için bilgisayara ne yapması gerektiğini anlatan komutlar dizisi yazma işidir. İnsanın başka bir insanla anlaşması için doğal dilleri (Türkçe, İngilizce vb.) kullanması gibi, insanların da bilgisayarlarla iletişim kurması için **Programlama Dilleri** geliştirmesi gerekmiştir.

**Neden Programlamaya İhtiyacımız Var?**
- Tekrar eden rutin işleri saniyeler içinde otomatik olarak yaptırmak.
- İnsan gücü ile yıllar sürecek matematiksel veya istatistiksel hesaplamaları saniyeler içinde yapmak.
- Hayatımızı kolaylaştıran modern uygulamalar (e-devlet, bankacılık uygulamaları, hastane otomasyonları) oluşturmak.

### 3.2. Bilgisayar Veriyi Nasıl Anlar? (0 ve 1 Kavramı)
Bilgisayarların içinde sadece elektronik devreler ve elektrik sinyalleri vardır. Bu nedenle bir bilgisayar, Türkçe veya İngilizce bilmez. Yalnızca makine dili dediğimiz **0 ve 1 (Binary - İkili sistem)** mantığıyla çalışır. 
- **1:** Elektrik var (True / Doğru)
- **0:** Elektrik yok (False / Yanlış)

Siz klavyeden "A" harfine bastığınızda arka planda işlemciye (örneğin 01000001) şeklinde bir ikili kod gider, bu işlemden geçer ve ekranda A olarak görünüz.

### 3.3. Programlama Dillerinin Seviyeleri
Her defasında 0 ve 1'leri kullanarak yazılım üretmek bir insan için işkencedir. Bu engeli aşmak için çeşitli seviyelerde diller oluşturulmuştur:

1. **Makine Dili (Düşük Seviye):** Sadece 0 ve 1'ler. Bilgisayar doğrudan anlar ancak insanın yazması neredeyse imkansızdır.
2. **Assembly Dili:** Makine dilinin biraz daha insancıllaştırılmış halidir, `ADD`, `MOV` gibi kısa kısaltmalar içerir. Ancak yine de yazması zordur.
3. **Orta Seviye Diller:** Hem makineden anlayan hem de insan diline yakın olan dillerdir. Özellikle donanım kontrolü yaparken işimize yarar. (Örn: C dili)
4. **Yüksek Seviye Diller:** İnsan diline, öğrenmesine oldukça yakın olan dillerdir. Okunabilirliği yüksektir. (Örn: Python, Java, C#)

Bizim bu dönemin ilerleyen haftalarında öğreneceğimiz **C Dili**, daha çok orta-yüksek seviye arasında konumlandırılır ve temel kodlama mantığını öğrenmek için dünya üzerinde en çok tercih edilen mühendislik ve önlisans başlangıç dilidir.

---

## 4. Derleyiciler (Compiler) ve Yorumlayıcılar (Interpreter)
Siz insan diline yakın bir C kodu yazdığınızda ("ekrana şunu yaz", "iki sayıyı topla"), bilgisayar bunu doğrudan çalıştıramaz. Bunu 0 ve 1'e çevirecek bir çevirmene ihtiyaç duyar.
- **Derleyici (Compiler):** Yazılan binlerce satır kodun tamamını bir kerede okur, hatalar yoksa tamamını "Makine Diline" (.exe gibi dosyalara) çevirir. C dili bir derleyici kullanır.
- **Yorumlayıcı (Interpreter):** Kodları okurken tek seferde dosyaya çevirmez, satır satır okur ve anında uygular. Python böyle çalışır.

---

## 5. Algoritmaya Hazırlık (Bir Sonraki Haftanın Habercisi)
Programlama, rastgele bilgisayara cümleler yazmak değildir, bir "Problem Çözme" sistematiğidir. Bir probleme çözüm bulmak için o çözümü adım adım formüle etmeliyiz. Önce düşünmeli, planlamalı sonra koda dökmeliyiz. İşte problemi çözmek için kurduğumuz bu adım adım yol haritasına ileride **"Algoritma"** diyeceğiz.

Örneğin, "Kek Yapma Algoritması":
1. Adım: Malzemeleri hazırla.
2. Adım: Yumurta ve şekeri çırp.
3. Adım: Un, yağ, süt ekle ve karıştır.
4. Adım: Önceden ısıtılmış kalıba dök.
5. Adım: 180 derece fırında pişir.
6. Adım: Çıkar ve soğut, dilimleyerek servis yap.

Bilgisayarlar da tıpkı bu adımlardaki gibi sırayla iş yapan aptal ama çok hızlı asistanlardır. 

---

## 6. Ders Özeti ve Uygulama Alıştırmaları
Bu haftalık metnimizde, temel elektronik parçalar, işletim sistemi ile uygulama donanımı farkları, makine dili neden vardır ve neden programlama diline ihtiyaç duyuyoruz gibi başlıklara değindik.

**Uygulama/Araştırma Soruları:**
1. Şu an kullandığınız laboratuvar bilgisayarı veya şahsi bilgisayarınızın işlemcisi (CPU) ve RAM miktarı nedir? 
2. İşletim sistemi olmadan bir bilgisayar çalışabilir mi? Tartışınız.
3. Derleyici ile yorumlayıcı arasındaki en büyük farkı bir benzetme yaparak açıklayınız. 
4. Hayatınızda çok sık tekrarladığınız rutin bir sabah uyanma işlemini, adım adım yazarak kaba bir program planı (ön algoritma) hazırlayınız.

Bu içeriği en kısa sürede tekrar okuyarak, teknik kelimelerin sözlük anlamlarını not atmanız ileriki derslerimizde büyük kolaylık sağlayacaktır. Başarılar dileriz.
