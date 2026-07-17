# Hafta 11: Algoritma Tasarımı ve Uygulamalar - I

## 1. Giriş ve Ön Hazırlık
Geride bıraktığımız 10 hafta boyunca programlamanın temellerini (değişkenler, operatörler), algoritmik düşüncenin görselleştirilmesini (akış diyagramları) ve bunların C dili üzerindeki pratik yansımalarını (karar yapıları, döngüler, diziler ve fonksiyonlar) etraflıca inceledik.

Peki gerçek dünyada bir mühendis veya yazılımcı olarak karşılaştığımız problemleri nasıl çözeriz? Sadece "for döngüsü nasıl yazılır" bilmek yeterli midir? Hayır. Önemli olan, karşıdaki karmaşık problemi küçük paçalara ayırmak ve eldeki araçları (döngü, dizi, fonksiyon) kullanarak adım adım o çözümü inşa etmektir. 

Bu ve takip eden iki haftada (Algoritma Tasarımı I-II-III), öğrendiğimiz tüm bu soyut ve somut araçları harmanlayarak, temel seviyeden karmaşık seviyeye doğru **Gerçek Problem Çözme (Problem Solving)** ve **Uygulama Senaryoları** üzerine çalışacağız. 

**Hedeflerimiz:**
- Basit matematiksel problemleri "Fonksiyon + C Dili + Algoritma" mantığıyla mimarileştirmek.
- Temel algoritmik problemleri (Faktöriyel, Asal Sayı Bulma, Girilen Sayının Rakamlarını Ayırma) kod düzeyinde pratik etmek.

---

## 2. Temel Matematiksel Algoritmalar: Faktöriyel Hesaplaması
Faktöriyel, sayının kendisinden 1'e kadar olan tüm tam sayıların çarpımıdır (Örn: 5! = 5 * 4 * 3 * 2 * 1 = 120). Döngülerin toplayıcı (çarpan) mekanizmalarını anlamak için en meşhur örnektir.

**Sözel Algoritma Mantığı:**
1. Dışarıdan hesabı yapılacak X sayısını iste.
2. Sonuç için bir `Carpim = 1` değişkeni aç (Çarpmada 0 yutandır, o yüzden 1'den başlar).
3. 1'den X'e kadar giden bir Döngü kur (veya X'ten 1'e gerileyen).
4. Her adımda `Carpim = Carpim * Sayac`.
5. Döngü bittiğinde `Carpim`'ı ekrana bas.

**Fonksiyonel C Kodu Tasarımı:**
Ana işlemleri bir fonksiyona atarak profesyonel tasarım yapıyoruz.

```c
#include <stdio.h>

// MATEMATIK FONKSIYONUMUZ 
int faktoriyelHesapla(int GelenSayi) {
    int sonuc = 1;
    // For ile 1'den Gelen Sayiya dogru bir yuruyus
    for(int i = 1; i <= GelenSayi; i++) {
        sonuc = sonuc * i; // Her adimda onceki sonucu yeni i ile carp, uzerine yaz.
    }
    return sonuc; 
}

int main() {
    int girilenSayi;
    printf("Faktoriyeli hesaplanacak sayiyi giriniz (Orn: 5): ");
    scanf("%d", &girilenSayi);
    
    // Eger 0'dan kucuk bir negatif degeri girerse algoritma kirilip hata vermeli (If Kontrolu)
    if(girilenSayi < 0) {
        printf("Hata! Negatif sayilarin faktoriyeli olmaz.\n");
    } else {
        // Fonksiyon cagirilir, direkt printf "icinden" fonskyion calistirip firlatilabir.
        printf("%d sayisinin faktoriyeli = %d dir.\n", girilenSayi, faktoriyelHesapla(girilenSayi));
    }
    
    return 0;
}
```

---

## 3. Matematiksel Analiz Algoritması: Asal Sayı Bulma 
Asal sayı, sadece 1'e ve kendisine tam bölünebilen 1'den büyük tam sayılardır (2, 3, 5, 7, 11...). 
Bunu algoritma ile tespit etmenin mantığı nedir? Bir sayının asal olup olmadığını anlamak için, o sayıyı 2'den başlayarak kendisine kadar (veya yarısına kadar) tüm sayılara tek tek **Mod (%)** mantığıyla bölmeye çalışırız. Eğer "bölümünden kalan 0" olan (yani tam bölen) BİR TANE BİLE sayı çıkarsa o sayı asal değildir. Hiç bölen çıkmazsa Asaldır!

**Bu felsefenin C Kodu Tasarımı (Bayrak Mekanizması):**
*(Algoritmalarda Bayrak (Flag) yöntemi sıkça kullanılır. Önceden Bayrağı havaya kaldırırız "Evet bu Asal (Flag=1) deriz." Döngü dönerken kural bozan tek bir an olursa Bayrağı indirir (Flag=0) yaparız)*

```c
#include <stdio.h>

void AsalMiKontrolEt(int TestEdilecekNumara) {
    int bayrak = 1; // Basta 1(Asal) Kabul edip basliyoruz 
    
    // Eger 0, 1 gibi sayilar verilirse kurali bastan keseriz:
    if(TestEdilecekNumara <= 1){
         bayrak = 0; 
    } 
    else {
         // Dongu 2 den baslar, sayiya varmadan kendi icinde biter
         for (int i = 2; i < TestEdilecekNumara; i++) {
             // Mod isareti kalana bakar (% == 0 tam bolundu demektir!)
             if (TestEdilecekNumara % i == 0) { 
                 bayrak = 0; // Bayrak Dustu (Kural Bozuldu. Asal degil)
                 break; // Tek bir tane bilene yakaladiysa milyonlara varmaya gerek yok! Donguyu HEMEN KIR !! 
             }
         }
    }
    
    // Bayrak durumu 1 kalabildiyse demek ki IF lere hic Dusmedik..
    if (bayrak == 1) {
        printf("BILGI : >> %d Sayisi Muazzam Bir ASAL SAYIDIR! \n", TestEdilecekNumara);
    } else {
        printf("BILGI : >> Olamaz.. %d Sayisi malesef  ASAL DEGIL! \n", TestEdilecekNumara);
    }
}

int main() {
    int klavyeGiris;
    printf("Asal Mı Sorusuna Sokulacak Deger: ");
    scanf("%d", &klavyeGiris);
    
    // Sadece Void e gonderir isini bekleriz!
    AsalMiKontrolEt(klavyeGiris);
    
    return 0;
}
```
*Bu örneği okurken (özellikle sayının kendisine gelene kadarki süreci kontrol etmek için Mod (%) almak ve Break ile performansı artırmak) tam bir programcı analitiği kokar.*

---

## 4. Rakamları Parçalama (Basamak/Haneli Ayırma Algoritması)
Algoritma ve C sınavlarının, problem sorularının favori başlığıdır. Diyelim ki 456 sayısının "Rakamları Toplamı (4+5+6 = 15) nedir?" sorusunu bilgisayara veriyoruz. Sistem kelime kelime 4, 5, 6 olarak okumaz tek bir yapı olarak görür. Peki biz bu bütünü nasıl tek tek kopartacağız?

**Algoritmik Matematik Çözümü:**
- Bir sayının On'a (10) bölümünden KALAN (%) herzaman sayının SON RAKAMINI (Birler basamağını) ele verir ! (Örn: 456 % 10 = **6**'dır.)
- Aynı sayıyı TAM SAYI (int) formatıyla doğrudan On'a (10) BÖLERSENİZ (/) sistem küsüratı `float` yapamayacağı atacağı için sayının ilk kalan kısmı uçar. (Örenğin 456 / 10 = **45** yapar . 45.6 yapmaz çünkü INTEGER.)
- Şartımız: Sayı sıfıra ulaşana kadar bu döngüyü sürdür.

```c
#include <stdio.h>

int RakamToplamiAyirici(int sayimiz) {
    int basamak;
    int toplam = 0;
    
    // Sayi "0" kalana kadar parcalanacagi Surece WHILE döner;
    while( sayimiz > 0 ) {
         
         basamak = sayimiz % 10;   // Ornegin basinda 456' nin 6' sini (% Mod'la) yakaladi!
         toplam = toplam + basamak; // 6'yı birikim Depoyasa Koydu (Toplam=6).
         
         sayimiz = sayimiz / 10;   // Mod(%) almadan, tam sayi integer de 10 a böldü ve (sayi=45) haline  indiridi ! 
         // Dongu Uste cikar. Bu defa 45 'in mod10 'unualir = (5)' i Yakalar!! Toplama ekler vs..
    }
    
    return toplam;
}

int main() {
    int veriler = 981; // Basit ornek = 18 Etmeli...
    printf("Girilen 981 in Parcanlarak Toplam Olgusu = %d\n ", RakamToplamiAyirici(veriler) );
    return 0;
}
```

---

## 5. Hafta Özeti ve Çıkarımlar
Bu haftayla birlikte; soyut olarak işlediğimiz C komutlarınızın, "Zeka küpü" şeklindeki problemlerin parçalanmasında nasıl işlediğine çok sağlam üç örnek (Faktöriyel / Toplama, Bayrak-Asal tespit, Rakam Koparma Döngüsü) verdik. Mühendislik ve yazılımcılıkta bu iskelet (özellikle bölüp modunu alarak parça tespit etmek vb) mantıkları binlerce projenin kalbinde aynen tekrarlanır.

**Laboratuvar / Alıştırma Görevleri:**
1. C editörüne veya defterinize, "Armstrong / Mükemmel Sayı" bulan algoritma programı kurgulayın. (Mükemmel Sayı Algoritması Şudur: Kendisi hariç "tam bölenlerinin" toplamı, yine kendisine eşit olan sayıdır.. Örn 6 sayısının bölenleri 1, 2 ve 3 tür. Toplamı da = 6 Ettiği için Mükemmeldir.) Bu hesabı yukarıdaki Mod ( % == 0) mantığını kullanarak, Toplama for una döktürün!
