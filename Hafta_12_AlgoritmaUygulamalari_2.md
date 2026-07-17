# Hafta 12: Algoritma Tasarımı ve Uygulamalar - II

## 1. Giriş ve Ön Hazırlık
Algoritma Tasarımı konusundaki ikinci haftamızda, önceki haftanın matematiksel ve mantıksal problem süzgecini (faktöriyel, asal sayılar) geride bırakıp yapısal veri kümeleri üzerinde problemler çözeceğiz.

Bu haftanın odaklandığı tasarım teması "Dizi (Array) Algoritmaları" olacak. Gerçek dünya programlamalarında tekil veriden ziyade yüzlerce veri bloğu üzerinden ayıklama, bulma, listeleme veya yer değiştirme gibi kurgular revaçtadır. Liste içinden bir veriyi bulma sistematiği veya en küçüğünü hesaplama vizyonu tüm veritabanı kurgularının temelini atar. 

**Hedeflerimiz:**
- Array(Dizi) içerisinde dolaşıp sayıların en büyüğünü(Max) ve en küçüğünü(Min) tespit etme algoritmalarını kurmak.
- Liste içindeki bir veriyi Arama (Linear Search / Doğrusal Arama) algoritması ile tespitini yapabilmek.
- İki farklı dizi bloklarını birbirleri içinde harmanlayarak işlemlere aktarmak.

---

## 2. Dizilerde "En Büyük (Max)" veya "En Küçük (Min)" Bulma Algoritması
Bir sınıfın öğrencilerinden "En yüksek notu kapan kişiyi", 100 kişilik bir liste (Array) formatından algoritmik olarak nasıl buluruz?

**Sözel Algoritma Çözüm Stratejisi:**
1. Bilgisayarlar listedeki her şeyi tek seferde göremez. Cihaz sırayla teker teker bakmak zorundadır (Döngü ile).
2. Sistemde (hafızada) en başa geldiğinde, dizinin 0. index'indeki (İlk Öğrenci) Puanına: "Bizim Şimdilik Bulduğumuz EN YÜKSEK (Maksimum) SKORUMUZ BUDUR!" (`max = Liste[0]`) diyelim ve kral tahtına ilk notu oturtalım.  
3. For döngüsü ile Dizi[1]'den (ikinci sıradan) itibaren listenin sonuna kadar diziyi taramaya başla.
4. Karar Kapısı (`if`): "Acaba şu an okuduğumuz Sıradaki Puan, bizim tahttaki `max` sayısından BÜYÜK (>) MÜ?"
5. Eğer karşımıza o anki "max" tan daha ulu bir sayı çıkarsa, tahtı ona devrederiz (`max = Yeni Okunan Dizi Puanı`).
6. Liste sona (100. kişi vs.) indiğinde döngü zaten kopacağından, elimizde mutlak "En Büyük Not (max)" sapasağlam duruyor olacaktır.

**C Dili Çıkarım Kodu:**

```c
#include <stdio.h>

int main() {
    int i;
    // Okuldaki Not Dizisi: Rastgele karmasik rakamlar. (Boyut=6 eleman)
    int okuldakiNotlar[6] = { 45, 12, 85, 33, 98, 7 }; 
    
    // Efsane Taslak !! Dizinin basindaki "Ilk eleman[0] 'ı = MAX " Kabul Ettik. Kralliga O Oturdu! (Max degeri anlik 45).
    int maxSayi = okuldakiNotlar[0]; 
    int minSayi = okuldakiNotlar[0]; // Kucuk icinde ayar cektik.

    // 1(ikinci okumadan) basla.. 6'ya kadar Say (Tarama) !.
    for(i = 1; i < 6; i++) {
        
        // EGER LISTE OKUNURKEN, KRALTAN BUYUGU VARSA TAHTI DEVRET! 
        if( okuldakiNotlar[i] > maxSayi ) {
            maxSayi = okuldakiNotlar[i];
        }
        
         // AYNI VIZYONU; KRALTAN KUCUGUNU BULARAK (MIN) DEGERINE ATIN! 
        if ( okuldakiNotlar[i] < minSayi){
             minSayi =  okuldakiNotlar[i];
        }
    }
    
    printf("Listede Arastiriilan En YUKSEK (Max) Skor : %d \n", maxSayi);
    printf("Listede Arastiriilan En BASARISIZ (Min) Skor : %d \n", minSayi);
    
    return 0;
}
```

---

## 3. Dizilerde "Arama / Bulma (Search)" Algoritmaları
E-ticaret sitelerinde bir ürün arattığınızda veritabanında liste nasıl sorgulanıyor? İşte bu uygulamanın mimarisine Doğrusal Arama (Linear Search) Algoritması denir. Mantığı şudur, Array baştan sonra listelenirken `if` koşuluyla sadece ve sadece Senin Klavyeden Yazdığın rakam / bilgi Listede tutmuşmu diye For döngüsü taramaktır.

**(Ufak Bir Bayrak "Flag" Katılımı daha yapacağız. Sistemin listede var olup olmadığı tespitinde Bayrakları kaldıracağız !)**


```c
#include <stdio.h>

void dizide_AramaSistemi_Gerceklestir(int arananKullaniciKodu) {
    
    // Elimizde Bankaya Kayitli Listesel 5 Uye Numarasi var: 
    int uyeVeriListemiz[7] = { 101, 552, 908, 14, 255, 303 , 661 };
    
    int bulundu_Bayragi = 0; // "Sifir(0)'i Henuz Bulunamadi" varsayiyoruz ! 
    int indexNoKactaCikti = -1;  // Kacta ciktigi yerini bilelim ..
    
    // Linear Arama - listede Gezinis
    for( int siraAtla = 0 ; siraAtla < 7 ; siraAtla++){
        
        // KARAR SORGUSU!: Aranan Kelime/Sayi = Listenin o an taradigi Sirasina Eslesiyor "==" Mu!? 
        if ( arananKullaniciKodu == uyeVeriListemiz[siraAtla] ){
            
              bulundu_Bayragi = 1;  // Bayragi (1 - EVET E Cekiyoruz !! Listedeydin Cıktın ! )
              indexNoKactaCikti = siraAtla; //  Burda cıktıgını hapaslayalim.
              
              break; // Geri kalan yuzlerceyi taramanin lüzmu yok Eger tek listeyse HEMEN KIR FOR DÖNGUSUNU !
        }
    }
    
     // Sonuc Felsefesİ! Sadece bayraga bakariz!  (If degeri bayraginin dogrulugu demek "bayrak==1 "dir.)
     if ( bulundu_Bayragi == 1) { 
         printf("Ayarli Sorgu => %d || %d Numarali (Sira) Uyesinde BASARIYLA TESPiIT EDİLDİ!", arananKullaniciKodu, indexNoKactaCikti );
     } else {
         printf("ERROR : %d Aramasi Listede YOK! 404 Cıktı Alindi.. ", arananKullaniciKodu);
     }
}

int main(){
     // 908 i cagiralim, Listede vardi ve bulacaktir ..
     dizide_AramaSistemi_Gerceklestir(908);
     
     printf("\n\n");
     
     // 100 U yollayali; YOKTUR YOK CIKACAKTIR!
      dizide_AramaSistemi_Gerceklestir(100);
     
    return 0;
}
```

---

## 4. İki Ayrı Dizinin Paralel (Senkron) Çalıştırıldığı Algoritma 
Olaylar her zaman sadece "PuanDizisi" (101,90,50) formatında basit gitmez. 
Diyelim ki programda 5 elemanlık `FiyatDizisi`miz ve 5 Elemanlık (Paralel endeskine uyan) Alınan `SiparisAdeti` Dizimiz bulunuyor. Sipariş edilen Adet sayısına Fiyatı carpiştirip, bu müşterinin  Banka Fiş Toplam Kart Tutarlını hesaplantan For sitemi kurgulayacapız!

Buradaki Mimetik Algoritmatik puf nokta: HER IKI  Arrayı sadece 1 For döngüsünün 'i' değerinden bir kerede çağırmaktır !! ( Ayrı ayrı For açılmaz ).

```c
#include <stdio.h>

int main() {
    
    // Indeks kesisimleri bir biriyle aynidir. ( Indeks 0'in Fiyati = 10,  Siparisi= 2' dir)
    float urunFiyatlari[4] = { 10.50 , 5.0 , 20.25 , 100.0   };
    int alinanSiparisSayilari[4]   = { 2 ,     4   ,    1  ,    0      };
    
    float KasaBakiyeToplamGirdi = 0.0;
    
    printf(" --- Musteri Fatura Kesim Fis Dokumu --- \n");
    
    // For Döngüsünde Tektipleme isleyi
    for(int indeks = 0 ; indeks < 4 ; indeks++) {
         
         // Fiyati aliniyor x Adet sayisiyna CARPILARAK; ara fiyat bulunuyor.. 
         float anlikCarpimliTutar = ( urunFiyatlari[indeks] * alinanSiparisSayilari[indeks] ) ;
         
         printf(" > %d ' nci Urunden => ( Fiyat : %0.2f  x %d Adet ) = Cikan Faturasi : %0.2f TL ..\n", (indeks+1), urunFiyatlari[indeks], alinanSiparisSayilari[indeks], anlikCarpimliTutar);
         
         // Kasaya Devirli Toplayici Sistem (Toplam = Toplam + Eklenen)
         KasaBakiyeToplamGirdi = KasaBakiyeToplamGirdi + anlikCarpimliTutar;
    }
    
    printf("\n MUSTERI NIHAI CIKIS HESABI FISININ TOPLAMI === >> %0.2f TL ", KasaBakiyeToplamGirdi);
    return 0; 
}
```

---

## 5. Hafta Özeti
Veritabanları mantığına geçişteki en ciddi C Dili algoritması olan Arrays(Listelere) olan analitik hükmedileşi gördürk! Max min i bulmak için dizinin başını lider alarak hepsini For (donguyle) taranması gerekti ve if kararı ile tek tek sorgulandı!.  Bir ürün arama bulma (Google aramalarınin ilkel yapisi ) için ise ; bayraklar(flag=0) indirlisiyle ve if icinde varmi yaklandısiyla süzülüşleri izledik. !

**Alıştırma Test Egzersizi:**
1. İçerisinde 8 adet sıcaklık rakamları olan (-5 , -10 ,  0 , 20 , 35 ) vs.. formatındaki `Sicaklik[8] Array`inden faydalarak, Sisteme **C dilinde** Programlama Yaratısı olarak ( İcindeki Sadece 0  'dan KUCUKLERIN / yani eksilerin ) , FOR la gezip de KAC ADET EKSİ bulunduğunu ( Sayaç ını yapnınızi "Toplamayacaksınız, Adet sayacaksınız." ). Yani sonuç  "`Sistemde Su kadar Eksi/Kış Sicaklık tespit edildi`" i bulan kurguyu yazınız.. 
