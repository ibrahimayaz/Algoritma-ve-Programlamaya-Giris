# Hafta 9: Dizi (Array) Uygulamaları

## 1. Giriş ve Ön Hazırlık
Hafta 8 itibarıyla programlamanın iskeletini ve kalbini oluşturan temel elementlerin çoğuna (Değişkenler, If-Else Şartları, For ve While Döngüleri) ulaştık. Ancak fark etmişsinizdir ki, eğer bir laboratuvarda oturan yüzlerce öğrencinin yaşlarını alıp ortalamasını bulmak istesek, bellekte "100 adet" kutucuk yani tek tek `int Yas1, Yas2, ... Yas100;` yazmamız gerekirdi!
Eğer veri girişimiz (veritabanı sayımız) muazzam rakamlara ulaşacaksa değişken yaratmanın felsefesi biter.

Bu hafta tümünü tekleştiren bir kavrama, C dilinde "Kümelerin ve Liste Koleksiyonlarının" yani **Dizilerin (Arrays)** kod mekanizmasına ışık tutacağız ve en çok iş akışı sunan Döngü (for) ile ne kadar verimli bir bağ olduğuna şahit olacağız.

**Bu Haftanın Hedefleri:**
- Dizi felsefesini, mimarisini tanımlama ve C diline uyarlayabilmeyi.
- Hafıza(Bellek) bloklarına Dizi elemanı adresiyle (Indexler) atama/çağırma(Cikti alma) komutunu kurgulamayı..
- Sayac(Dongü/ফর) kurgusunu Dizilere endeksli taramada kullana bilmeyi kavramaktır!

---

## 2. Diziler (Array) Nedir? Amacı Ne İşe Yarar?
Sistem içeresinde benzer şekilde tek bir ismin bünyesinde, art arda gelen depoya, listelemeye dizilişlere Dizi denir (Tek sefer kalıp yaratılarak onlarca veriyi sıralayacak vagon gibidir.)

*Değişken Kıyaslaması:*
*   Sıradan bir kutucuk (Değişken) `int kutu = 5; ` derseniz tek saklarsınız.
*   Halbuki Dizi felsefesi:  *(Tren gibidir. Vagonların Hepsi Öğrenci Sayılarıdır ama Adı 1 tanedir: PuanTren)*..  

**Dizi Tanımlamasının Kuralı  :**  
`[ Veri Tipi(int, float vb) ]   [ Dizinin Adi ]  ( Köşeli Parantez icerisinde Eleman KAPASİTESİ (Orn: 5 veri.. 50 verilik! )  ] ;`

```c
#include <stdio.h>
int main() {
    // 5 ögrenciden oluşan Yaslari tutan bir "Int Dizisi" tanımlamasi.. 
    int ogrenciYaslari[5]; 
  
    // Ya icersine biz elverisine aninda vercekseli: Kümeli Parantezi C ye gondeririz!
    float fiyatListeleri[3] = { 10.50 ,  15.99 ,  6.25  } ; 

    return 0;
}
```

---

## 3. Dizilere / Vagonlara Erişim ("Index"  Kavramlamları )
C Programı, Vagonları bir sayı listesinden sayarken **İNSANLAR GİBİ (1) NUMARALI VAGON'DAN SAYMAZ**.
Yazılımlar dizileri her koşulda 0 (Sıfır.. Index No:0) adresinden sıralar. Buna Array Numaratör Indexleri diyebiliriz!!
Yanı siz bir diziye `5` verielik kapı(kapasite) dediyrseniz C ; { 0 , 1 , 2, 3, 4 } seklındekı rakam kutuları oluşturup bitirir! 

Kutu İçi Ödevi veya Cıkış Çağrısı Nasıl islenmektedir ?  
*   ` Dizinismi [ HANGI KUTUSU ]  ; `

```c
int main() {
    int okulumdakiPuanlar[3];  // Sayilar kapasitesi sadece => (Odan 0 ,Odan 1,  Odan 2 seklinde RAM'i acar !!)
    
    okulumdakiPuanlar[0] = 75; // "Sistem 0 numarali indeks kutusuna gitmeni emretti, icini degistir 75 yap dedi."
    okulumdakiPuanlar[1] = 42; 
    okulumdakiPuanlar[2] = 95; 

     // Eğer cikiisda Yazida Cagirmak isteseydiniz Aynen Degisken gibi!
     printf("Dizideki Ucuncu Sinav Notunuz  =  %d Puan! \n", okulumdakiPuanlar[2]);
    
     return 0;
}
```

---

## 4. For Döngüleriyle Dizilerin Sentezi
Diziler 5 odalıyken manuel teker teker yukarıdaki index[0-1-2] verisi ile elle çağrabilirsiniz ! Gelin görünki Arrayler Genelde {1000 - 50 bin} elemandır ve "For" döngüsündeki Sayac(İndeks) tamda bu numaranın indeks sıralarına kafa kafaya oturmak için yapılmıştır!

Adım Sayaç numarasını, Dizinin içindeki `[*Buraya Sayaç Adimi Girer*]` bağlayarak tek hamle ile listeyi uçurursunuuz!  

*Ornek Kurgulama(5 sayıyı Listede tut- Sırayla Bastırsın) :*

```c
#include <stdio.h>

int main() {
    // Toplancak Notu listeyi kapali sekile icerik doldurduk:
    int siraliCNotum[5] = { 10 , 20 , 30,  80, 100 };
    int i ; // (Kisa Dongu Simgemiz )
    
    // For kuruyoruz ; 0. Indeksten basliyor, Dizimiz[ 5 ] 'ten kucuk olduguna kadar okur cunku zaten son numara 5 degil "4 (Index kuralina gore) " tur . 
    for( i = 0 ; i < 5 ;  i=i+1 ){
       
       // Iste Efsane Kesisim burada olur, Her defasinda siraliCnotun[0] -siraliCnotun[1] .. artan Donguyu  index e cevirdik ! 
       printf(" Vagon Kutusu No[%d] ' de su An Puaniniz := %d  Bulunmakta :) \n", i  ,  siraliCNotum[ i ]);
        
    }

    return 0;
}
```

---

## 5. Dizi Uygulamalarında Metinler ( Karakter/Char ile String  )
Daha önceden tek Karakter (`char harf = 'A';`) biliyorduk . C dilinde Metin ("Kelime/Cumle") kavramınız  aslında tek tek harflerin dizilip listelendiğini gösterdiği, `Char` tiplerine dizilmiş katar Array yapılar olarak görülür. String kelimesi kullanılmakla bilinmesine rağmen C dilinin özünde "C dizilisi / `char diziAd[Harflimit]`" felsefesi verisini besler. 

- Metin (String) Yazdırma formatı `%s` ile Ekranda fırlatılsa basılır!

```c
#include <stdio.h>
int main() {
    // Merhaba kelimesini, harflerini siralicayan (char) formatinla Dizi Listesine Gonderir(Kapasiteyi o hesaplayaabilir de kucuk parantez bos olursa)!: 
    char mesajListemiz[] = "Merhaba Algoritma Dunyasi!"; 
    
    printf("Ekrana Cikti: %s\n", mesajListemiz);

    return 0;
}
```

---

## 6. Haftalık Özet Sistemi
Listeleme işlemleri (Array,Dizeller) hem hafızada gereksiz binlerce farklı ismi yaratmaktan bizi kurtarabildiği gibi veritabanılar arası sokuşturduğumuz sıralamaya çok verimli uyarlamalardır!  Odanın adresi index 0 ilkesinden yürüdüğünü aklımıza mutlak kurallamalıydık.. For mekanizmaların Sayaç sayımı (0' dan List'in Uzunluğuna - 1 kadar ) dizelere tam oturduğuna şahit  oluk ve bu iki ayrılmaz yapıyı tek elden test ettik.. 

**Uygulama/Alıştırma Egzersizler :**
1. İçerisinde 10 verilik (Kendiniz kapalı köşeli olarak atayınız 50,22,60...) Array yapısı kurun ve For ve Bir `if` (Karar) Döngüsü yazarak Dizi İçindeki 50'DEN BÜYÜKLERİ ayıklayıp Ekrana Yazdırtacak kombine C Programı tasarısı geliştirin!
2. Bir Arrayi (5 Hanelik Boş Kutu Açarak  :`int notlar[5];` ) for yardımı ile döngü sırasında klavyeden O kullanıcıya `scanf` formatıyla sora sora o beşlisini sırayla klavyeden çekip doldurtun ! O Liste dolunca "Listenin Toplamını (Dongu yardımlarıyla Toplayici `Toplam` ile) C'de çıktıla !! 
