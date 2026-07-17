# Hafta 13: Algoritma Tasarımı ve Uygulamalar - III

## 1. Giriş ve Ön Hazırlık
Algoritma ve programlama üzerine geçirdiğimiz koca bir dönemin şüphesiz en "Algoritmik Yetenek" ve "Beyin Fırtınası" barındıran haftasına ulaştık. 
Bu son uygulama dersi, Array'ler içinde dolaşma (dizi tarama) yetkinliğini daha zor ve karmaşık mekanizmalar üzerine inşa eder: "Sıralama (Sorting)" algoritmaları ve iki boyutlu matris/tablo (Matris-İki Boyutlu Diziler) yapıları...

E-ticaret veya bankacılık verilerinde "Fiyata Göre Sırala, A'dan Z'ye Sırala" butonuna her gün basıyorsunuz. Peki o buton arkasında sisteme C programcılığında nasıl bir mekanizma gönderiyor? Veya bir Excel sayfasındaki "Satır-Sütun" şeklindeki veri dizilimi kodda nasıl yaşar? 

**Hedeflerimiz:**
- Basit takas (Swap) algoritması mekanizmasını hafıza boşluklarıyla kurgulamak.
- Dünyanın en meşhur ama en kaba sıralama mantığı "Bubble Sort (Kabarcık Sıralaması)" ile liste düzenlemek.
- Çift (İki) boyutlu Dizilerdeki Matris (Satır / Sütun) kavrayışına ve döngülerine giriş...

---

## 2. Takas / Yer Değiştirme (Swap) Algoritmasının Mantığı
Sıralama dünyasının veya verileri değiştirmenin kalbi "Kutuların içeriğini takas etmeye" bağlıdır. İki elinizde iki ayrı bardak su ve meyve suyu olsun. Suyu ötekine, meyve suyunu da suyunkine boşaltmanın tek kuralı nedir? Dışarıdan yeni bir "Boş Bardak" almak!
Aynı şey C kodlarında Variable (Kutu Değişkenlerinde) yer alır.

```c
// Basit Takas Eylemi
int Kutu_A = 10;
int Kutu_B = 25;
int Gecici_BosKutu; // Temiz Bardak (Temp) !! 

// 1. Islem: Kutu_A nin icindekini Bos Kap'a emanet kopyala
Gecici_BosKutu = Kutu_A;   // Gecicikutu= 10 oldu, A serbestlesti.

// 2. Islem: Artik bosa dusun Kutu_A nin yerine Kutub unkini (25 i) cek
Kutu_A = Kutu_B ; // A = 25 basildi.. Kural isler.

// 3. İSLEM: B nin bosalan yerine basidani Emanet bardakdaki  eski a yi ustu.. 
Kutu_B = Gecici_BosKutu;

// Sonuc ! : A : 25  B: 10 ..  Takaslar Mukemmel
```
*Bu swap (takas) mantığını tüm sıralama metotlarında ana felsefe işleviyle kullanacağız!*

---

## 3. Kabarcık Sıralaması Algoritması (Bubble Sort Algorithm)

Listede gelişigüzel dağılmış dizileri(Array) **Küçükten Büyüğe (veya Büyükten Küçüğe)** doğru sıralatmak istediğimiz programın "İki Adet İç İçe For" kullanmış muazzam şeklidir Bubble Sort!
Suyun yüzeyine önce ufak ve ağır baloncukların büyük baloncukların ittirerek sıralanması mantığını yansıtır:

**Sirkülasyon Şeması (Sözlü):** 
1. `[ 5 , 1 , 4 , 2 ]` adlı bir listemiz var diyelim.. Program yan yana (Yandaki ikisine) iki komşuyu inceler *( 5 ve 1 )*
2. Kendine sorar `if (İlk Eleman > İkinci Yandakinden )` - Baktık Ki 5, 1'den Büyük , "O zaman Kaba tabirle yerlerini takas et (Yukarıdaki Swapla) "... Liste `[ 1, 5 , 4,  2 ]` Olur.
3. Sonra sıra 5 ve 4e gelir. Yine takaslar.. Liste `[ 1, 4 , 5, 2 ]` Olur.. Bu işlemi listende taaaa ilk turlar bitene kadar yapar.
4. Bu for turları, sayac boyutları aşılamayacak şekilde tekrar  bastan tararlar.. Ta ki hiçbir değişim yapılana dek..  

**C Dilindeki Profesyonellere Uygun Çalışma Kodlanması**

```c
#include <stdio.h>

int main() {
    int KarmaListe[6] = { 88, 12, 110, 4, 39, 1 }; 
    int elemanKap = 6; 
    int tempGecici; 
    
    // Iki tane Ic-Ice (Ust uste olan ) For gereklidir! 
    // Usteki Dongu , Tur(Asama) Dongusudur.. Alta taramasi bittikce Yeni bastan Tur firlatir.
    for (int disTur = 0; disTur < elemanKap - 1; disTur++) {
        
        // Ic For; sadece Yandaki ile karsilasip en uca varma isidir
        for (int icTarama = 0; icTarama < elemanKap - disTur - 1; icTarama++) {
            
            // KARAR KAPISI IF = Siradaki(icTarama) , Kendi Bir SAG (Yandaki Komsusu) + 1  Elemanindan BUYUK MU?
             if ( KarmaListe[icTarama] > KarmaListe[icTarama + 1] ) {
                 
                  // EVET BUYUK !! DEMEK KI BOZUKLUK VAR O YANDAKI KUCUK SAYIYI  BU TARAFA AL.. (SWAP/ TAKAS ET) 
                  tempGecici = KarmaListe[icTarama];
                  KarmaListe[icTarama] = KarmaListe[icTarama + 1];
                  KarmaListe[icTarama + 1] = tempGecici;
             }
        }
    }
    
    // Ekrana Ciktiliyalim Bakalim Cihaz Cidden (Min- Max i dogru kurmusmu )? 
    printf(" --- Algoritma Bubble Sort Tarafindan Siralanmis Yeni Dizilis---\n\n");
    for (int i= 0 ; i < 6 ; i++){
        printf(" List[%d]:%d -- ",  i , KarmaListe[i] );
    }
    
    return 0;
}
```
*Bu yapı programcılık bilimlerine ait üniversite sınavları haricinde pek nadiren elinizle yazılır lakin kod bloklarını tasarlarken, zihninizde o sıralı listelere ait vizyonun geliştiği muazzam kancadır.*

---

## 4. İki Boyutlu (Satır - Sütunlu) Dizilere / Matris'e Giriş ! 

Sınıftaki çocukların Notunu ` [ 10,  20,  50 ] ` tuttuk. 
Fakat "Vizesini, Finalini ve Bütünlemesini AYNI TREN VAGONUNA" koyup alt alta ve yan yana olan bir Excel Çizelgesine koymamız gerekirse ne olur ? İşte buna `İki Boyutlu Diziler ( Matrisler )` kurgusu  diyoruz.. Arrayin içerisince Array listesi.. 

Tanımlanma Esasları `ArrayAdi[ SATIR_LIMTI_SAYISI ] [ SUTUN_LIMITSAYİSİ_YAN YANA ]` olmak şekliyledir! 

```c
#include <stdio.h>

int main() {
    
    // 2 Satır (Alt Alta İki Satir) ve  3 Sutunluk  (3 Yanyana Kumesel Eleman ) lik MATRIS Cizer !! 
    // Yani "NotExcelTablosu [2 Satir] [3 Sutun_Verisi]"
    int NorExcelTablosu[2][3] = {  
        {70, 80, 90},    // 0' İncı  SatıraAit   3 Tane Sutun Ogrencileri !
        {40, 50, 60}     // 1 'İncı  Satıra Ait Sutunsal Yapıdakİ Dıger 3 Lusu .. 
    };

    // İcinde Erismek Istıyorsan "Kombine Yapi Girersin" ( Orn:  0.Satir ,  2.nci Sutun Elemeni Getirt )
    // Array Mantigina Gore => 0. Satir "70 80 90",    Icınerisindeki 2 nci Sutun Indexİ !:  (0.=70 , 1=80, 2.=90'i Getirt )!
    
    printf("\n Secili Tablo Odacigindaan Matrise Ulasma Bilgisi Puan=  %d \n\n", NorExcelTablosu[0][2]);

    // MATRISI TUMUYLE EKRAN  OKUYUB YAZDIRMA ( 2 Adet Ic Ice For la yapilir! 1 for yanyanasini  digeri satıri ezer..! )
    for(int satirIndex = 0 ; satirIndex < 2 ; satirIndex++){
        
        for( int sutunindeks =0 ; sutunindeks < 3 ; sutunindeks ++){ 
             printf(" Veri : %d\t", NorExcelTablosu[satirIndex][sutunindeks] );
        }
        printf("\n"); // Alt Satira gecis enter bas 
    }
  
    return 0;
}
```

---

## 5. Hafta Özeti ..
Bu uygulama partında (Bölüm III); C programlaması diline özgü, yerinden oklara/döngülere ve matematikele evrilen Array mantığının uç noktalarına, Bubble Sortlama sırasıyla nasıl oynandığını gördünüz. Değişenler havuzundan  çıkıp geçici kaplarla (Takas/Temp) kurgulanmanın güvenceselliği hissettiniz.. Ve çoklu listeleme metotlarıyla EXCELL vari İki Yönlü Boyutların C diline oturtulduğundaki o for for sarmallarını aplettik.
Sizler tüm bu metotlarla algoritmaları koda sokabilen ve ne istediğini bilgisayarlar mantığıyla "Söz Dizimi " hatası bırakmadan veren bir temel programlama evrelerine erdiniz !

**Uygulama/Alıştırma Egzersizler :**
Satır 3 Sütun Cizen bir Array tanımlayına ( 3x3 luk Matrix `MatrisDiz[3][3]`   ve  Buaradaki tüm 9 Rakamıda icersinde rastgele kendiniz kodda kurgulayıp yazın ( {10,1,5..} )...  İç ice  (Sütun -  Satır foru fonsksyonunu ) kullanarak, Ekrandakı " SADECE İcerigi Cift( 2 Ye MOD(%) ) lari 0" ları Süzme yontemı arayarak Sactan Ekrana Çıkarip Cıft Dizesini print ediniz !!
