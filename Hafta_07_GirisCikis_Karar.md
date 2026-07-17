# Hafta 7: Akış Diyagramlarından Kodlamaya: Giriş-Çıkış Komutları ve Karar Yapıları

## 1. Giriş ve Ön Hazırlık
Geçen dersimizde, C dilinin çatısını tanımış ve programlama evrenindeki belleklere uygun verilerin kutuya nasıl (int, float, vb) atanacağını, ve bunları ekrana `printf` yardımıyla yüzde işaretleriyle nasıl yansıtacağımızı aktardık.
Fakat sadece ekrana yazı yazdırmak statik, cansız ve tek düze bir yapı sunar. Programlar "Kullanıcı"lara ihtiyaç duyar. İnsanlarla iletişim kurmaları için "Sorular Sorabilmeli ve Veri Alabilmeleri (Input)" gerekir. Ayrıca geçen haftalarda defalarca "Akış Diyagramlarına" işlediğimiz "Eşkenar Karar" kutularını bugün gerçek kelimelerle, hakiki "Karar (If - Else)" şart cümlelerine oturtacağız. Akış Diyagramı serüveni kodlu hayata vücut bularak giriş yapacaktır!

**Hedeflerimiz:**
- C programlama dilindeki veri alma-okuma (`scanf`) komutunun mantığını oturtmak.
- `if`, `else if` ve `else` komutlarıyla şartlı dallanma yapabilmek.
- Tasarlanan bir Karar Akış Diyagramı şemasını kendi kod satırlarına hatasız işlemek.

---

## 2. Kullanıcı Girişi Almak (Girdi - `scanf`)
Karşı tarafta klavyede olan kullanıcıdan değer almak ve bunu kutunun (değişkenin) içine koymak C programında **`scanf()`** anahtar kelimesiyle başarılır. `Scanf`, aynen `Printf` gibi kütüphanesi hazır (stdio.h) olarak tarafımızdan gelmektedir!

Farketmişsinizdir ki, çıktıda yaptığımız, int veya karakter için olan özel `%` formatlarını, bu defada "Hangi stilde bir değeri kutuya koyacağız" manasıyla klavyeye uyarlıyoruz.

**Sözdizimi Yapısı:** `scanf("Format Kodu Türü", & Değişkeninizin Adı);`

**Not:** C dilindeki veri okuma sisteminde "Adres/Yerbelirtme ampersand işareti" olan **`&`** kesinlikle kullanılmak zorundadır (Yoksa kullanıcı giriş yapsa dahi hata yaratır, bilgisayara veriyi fırlatmayı engeller). Anlamı şudur: "Klavyeden okunan değeri, bellekte isimlendirdiğimiz Değişkeninizin **ADRESİNE** götür yapıştır". 

```c
#include <stdio.h>
int main() {
    int OgrenciNo;
    
    // Oncelikle biz kullaciya aciklayici yazi ciktisi veriyoruz ki kullanici napacagini bilsin:
    printf("Lutfen sistem icin Ogrenci Numaranizi (Tam sayi) giriniz:\n");
    
    // Klavyeden girise ve o girisi adres ( & ) yardimiyla kutuya hapsetmeye haziriz: 
    scanf("%d", &OgrenciNo);
    
    printf("Harika! Sisteme Girdiginiz Ogradiginiz Numarasi ==> %d <-- dir..\n", OgrenciNo);
    
    return 0;
}
```

---

## 3. Karar Yapılarının C Dili Karşılıkları (Eşkenar Çokgenin Kodlanması)
Program kodlarken, Akış Diagramlarında karar vermek için "Eğer durum böyleyse sağdaki kola (Evet) git, Değilse soldaki (Hayır) kola geç" diyoruz. 
C dünyasındaki o eşkenar çokgenin adı aynen algoritmada dilleştirdiğimiz haliyle **`if`** bloğu, hayır kolu ise **`else`** bloğudur.

### 3.1. Temel Bir `if` ve `else` Çatısı

Eğer sorgulanacak blok **DOGRU/TRUE/EVET** dönerse çalışmasını fırlatacağı yer `if`'in parantezleridir. 
Aynı eşkenar döngü sorgulanıp **HATA/YANLIS/HAYIR** olarak dönüş fırlatılırsa otomatik bir sonraki `else` in parantezlerine gider.

```c
// Formul Yapisi 
if ( SART VEYA KOSULLARI MATEMATIKSEL OPERATORLERLE YAZDIGIN YER) {
    // SART SAGLANIYORSA BURADAKI SATIRLARA GIR, KODU BURADAN ÇALIŞTIR !
} else {
    // SART SAGLANMIYORSA, C PROGRAMI DIREKT BURAYA SIÇRAYACAKTIR..
}
```

*Küçük bir vize uygulamasını gerçek koda çeviriyoruz; Geçme Notu 60 olmak zorundaydı.*

```c
#include <stdio.h>

int main() {
    int  OrtalamaNot;
    
    printf("Dersten aldiginiz Notu Giriniz: ");
    scanf("%d", &OrtalamaNot);
    
    // Karsilastirma / İliski Operatorlerinin Hatirlanilamasi (> ,  <,  == ,  >=)
    if (OrtalamaNot >= 60) {
        // Eger giren notu gercekten karsilastirmayi sagliyorsa, tebrik eder:
        printf("Tebrikler. C dilinden Gectiniz!\n");
    } else {
         // Ya esit veya buyuk DEGILDI.. Cihaz bunu algiladigi an uste girmez..
         printf("Uzgunuz.. Siniftan Kaldiniz..\n");
    }
    
    return 0; 
}
```

### 3.2. İç İçe Geçmiş Seçenekler ve `else if` Merdiveni
Diyagram derslerinde, iki sayıyı veya sistemi ayırırken "0 mı ? Yoksa Sıfırdan Büyük mü ? O Zaman ikisi de tutmadıysa Negatiftir (Sıfırdan Küçüktür)" deriz. Sadece EVET/HAYIR 2 tane kapıdan oluşmaz. Birden çok ifli soruyu birbirinin ardına ekranda bağlamaya yarayan sisteme **else if (Değilse Ama Yeni Bir Soru Sor/Eğer..) merdiveni** denilir.

*(Not: Sayı 2'ye bölününce kalanı SIFIR ediyorsa Eşittir manasında  "==" işleçleriyle yapılır)*
```c
int main() {
    int girilenX;
    
    printf("Karsilastirmalik Bir Deger: ");
    scanf("%d", &girilenX);
    
    if (girilenX > 0) {
        printf("Bilgi: Sayi POZİTIF karakterli!");
    } 
    else if (girilenX < 0) { 
        // 2. KAPI - Ilki Eger degilse, bir de suna sorsun!
        printf("Bilgi: Sayi NEGATIF karakterli!");
    } 
    else { 
        // Ustteki iki kapi da kirildi/yanlis. Ihtimal artik YOK (Geride sadece 0 olabilir.. Sonuc olarak sadece ELSE kalmistir.)
        printf("Bilgi: Sistem SIFIR(0)'dir..");
    }

    return 0;
}
```
***Ek Detay:** Algoritmalarda Mantıksal operatörler işledik; VE (`&&`) VEYA (`||`). İşte `if( Not>=0 && Not<=100)` yazarak (C programında VE `&&` ile VEYA `||` ile belirtilir) her iki kuralı da aynı `if` satırına hapsedebileceğimizi unutmayınız.*

---

## 4. Akış Diyagramını Koda Dönüştürme Taslağının "Canlandırılması" 
Derste ilk öğrendiğiniz "Maaş Artışı Kararı", bu örneğini bir Algoritmasından Kurguya ve C Diline adım adım bağlaması: 
**A.** *"Kullanıcı dışardan bir Maaş tutarı girecek, Eğer tutar eski ve düşük olan 17000'dan azsa veya ona "==" Eşitse Zammı ( %20 ) olarak maaşına eklesin Ekrana Bastırsın. Aksi taktirde büyükse %10 eklensin ve bassın"*

```c
#include <stdio.h>
int main() {
   float alinanMaas; 
   printf("Elemaninizin Massini Tl cinsinden kaba girin:\n");
   scanf("%f", &alinanMaas);
   
   if(alinanMaas <= 17000.0) { 
        //  0.20 carpmak = %20 demektir.. Eski massı guncelle.. 
        alinanMaas = alinanMaas + (alinanMaas * 0.20); 
        printf("Cikan Yeni Maas= %f", alinanMaas);
   } else {
        // Yoksa  >17000 durumunda  zaten ust asilacagindan:
        alinanMaas = alinanMaas + (alinanMaas * 0.10); 
        printf("Artis Kismenn de olsa uyarlandi : %f", alinanMaas);
   }
   return 0;
}
```

---

## 5. Haftalık Özet
Beş ve altıncı haftada, ekrana çıktı vermek ("Merhaba C") ile kapattığımız sürecimiz; bu yedinci eğitim dilimi ile interaktif ve konuşkan (Soru cevap – `Scanf`) duruma çıkmıştır. Karar, eşkenar ve Algoritmik Süzgeç yapısını oluşturan "EVET-HAYIR" döngüsü; `if  - else`  sayesinde gerçeğe, derleyici mekanizmasına intikal etmiş olup bir sonraki adım "döngü algoritma yansımalarıdır". 
    
**Uygulama/Alıştırma Egzersizleri:**
1. C editörünü açarak, sistem ekranına `Vize 1`, `Vize 2`, ve `Final` şeklinde 3 ayrı int girişi oluşturan öğrenci sistemi yazın (Üçünde de `scanf` istemesi yapılsın). Formüle bu 3 sayıyı hesaplayarak yansıtsın ve 50 den büyükse if kararından tebriği okutsun..
2. Klavyeden aldığı "1" girişine "Pazartesi", "2" girişine "Salı"... yapacak C karar programını (`if`, `else if`, `else if` ...şeklinde ardı ardına sıralayıp) sonuna kadar oluşturunuz ("else" için geçersiz numara diyebilirsiniz).
