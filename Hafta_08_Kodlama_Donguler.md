# Hafta 8: Akış Diyagramlarından Kodlamaya: Döngü Yapıları ve Diğer Komutlar

## 1. Giriş ve Ön Hazırlık
Hafta 5 ve 7'deki birikimlerimizde; karar verme işlemlerinin koda dönüştüğünü (`if - else`), kullanıcı ile konuşmanın başladığını (`scanf`) C programlama üzerinden pekiştirdik.
Bu hafta programlamanın en zor ama en fazla zamandan kazandıran temel felsefesine geçişimiz olacak. Kendi algoritmalarımıza taslak olarak atadığımız "Okun başına tekrar yükselen çizgiyi, Sayacı arttırarak sistemi sürekli denemeye fırlatan Döngüleri(Loops)" kodlarda somut kurallar ve kavramlarla yerleştireceğiz.

**Hedeflerimiz:**
- C programlamasındaki tekrar felsefesi olan `while` , `for` yapılarına ısınarak mantığını kavrayabilmek.
- İlgili Karar (Koşul) ve Arttırımı (Sayac) aynı program kodlarının içine uygun süslü paranteze entegre etmek.
- "Kırıcı - Devam Ettirici" özel kelimelerin (`break` ve `continue`) işlevine dair tecrübe edinme.

---

## 2. Döngüler (Loops) Ve Komut Yapılanmaları Nelerdir?
Eğer bir soruna ait belirli komut satırlarının şart sağlandığı sürece sayısız kere (ister 1 milyon, ister sonsuz) çalışmasını kodla istiyorsanız o birim için bir Döngü çemberi programlarsanız! 

Kodlamada, tıpkı "Karar yapıları (if)" gibi "Tekrar/Döngü" fırlatmasının ingilizce türevleri C dillerine kod kelimesi olmuştur: 
*   **While** 
*   **For** 
Bu kavramlar aslında teknik felsefe ve diyagram akışları bakımından yüzde 90 aynı görevi icra ederler ancak kelime kalıbı ve kuralına göre "kullanıcı açısından" pratik seçim farklılığı mevcuttur.

### 2.1.  `while` Döngüsü  (Olan "SÜRECE" Dön!)
While kelime olarak "sırasında/olduğu esnada" şekline bürünür. Şartımız (Aynen IF parantezine konan `Sayi<100` benzeri bir karar parametresi) olduğu müddetçe altındaki süslü yapı parantezi ne var ne yok sürekli ekranda akmaya kodunu devirir!

**Temel C Formülizasyonu (While):**

```c
// Formul Yapisi / Taslak Blok
while ( KOSUL/SART BURADAN DOGRU "EVET" CIKIYORSA ) {
    // BURADAKİ SATİRA GİRECEK!
    // FAKAT "IF"TEN FARKI: BITINCE ALT SATIRA KACAMAZ, PARANTEZ KAPANINCA TEKRAR O "WHILE" IN SORUSUNA ÜSTE GİDER !! (TA KI KOSUL KIRILINCAYA DEK)
    
     // DONGU SONSUZA GITMESIN DIYE (Algoritmayi hatirlayin) Sayaci arttirin: Sayac = Sayac+1 
}

```

*Birinci Örneğimiz (Ekrana 1 den 5 ' e kadar yazı sırasını Sayacıyla yazdırmak):*

```c
#include <stdio.h>
int main() {
    int Sayac = 1; // Dongu nerde baslasin, nerede varsin... Adımı 1 den kuralım

    // İlgili dongu, asagidaki Sayac ogesi "5" E veya Kucukte Esit kaldigi Surece calisip donecek!
    while (Sayac <= 5) {
        printf("Selamlar Bu benim %d 'nci Sayac Donusumimdir.. \n", Sayac);
        
        // Cok hassas yer! Eger sayaci bir artirmiya gitmeseydik.. O "SAYAC" her tur 1 oldugu  icin MİLYARLARCA KERE Ekranda takilip donecekti(Sonsuzluk) ! 
        Sayac = Sayac + 1; //  Alternatifi -> Sayac++; (Kisa kullanimla +1 sayaci demektir!)
    }
    
    printf("Gordugunuz gibi kural yukaridan '6' diye gecemedigi isin Donguden Kirilik Asagi İndik!\n");
    return 0;
}
```
*Bu program saniyeler için de SIFIR hata ile, teker teker 5 haneyi ekranda sıralardı. Asla 6 için iş yürüttürmez alt satır printfine devam eder ve bitirirdi*

### 2.2.  `for` Döngüsü  (Önceden Belli Turlar !)
Dersteki veya sınavdaki algoritma taslağınız eğer ki "Başlangıcı ve Ne zamanı Sayacının Bittiği Şartı" baştan itibaren taslak (1 den başlayıp 2 şer gidecek ve net 100 de fırlayacak!) diyorsa tek tek, farklı defa while parantezlemesi değil tek sıra ile de `for` komutu C dizimine uygulanır. Profesyoneller bunu sever. 
 `For `içine (  *Baslangic Adresini ; Kosul'u  ; ArtisMiktarini* ) aynı anda sıkıştırır.

```c
#include <stdio.h>

int main() {
    int GirenGosterim;
    
    // Yapiyi cozelim:    (BASLANGICI YAP  ;     KOSUL BUYSA BITIR   ;    HER DÖNÜSTE BU KADAR  YUKSELT)
    // C dili sayaci i, j genelde kullanir 
    
    for (int adimGidisi = 0; adimGidisi <= 10; adimGidisi = adimGidisi+2) {
         // Iste simdi adimGidisi degiskenine 0'dan ikişer ikişer kuralina gore: 0..2..4..6..8..10 seklinde bu kisir donguyu kendisi otamatik yapacak !
         printf("Cifter Sayim: %d \n", adimGidisi);
    }
    
    return 0;
}
```

---

## 3. Komutlardan Çıkışlar(Yol Kıranlar):  `break` ve `continue` 
Bir döngümüz var, for veya while 100 bin kere dönecek ama siz "Acil bir Karar if durumunda! Eğer Cıkan numara şifreyse sistem o tura (yani 100 bin e ) varmadan anında parçalansın kopsun!" istersiniz 

1. **`break`  (Kır/Dışı) :** Sistem bunu döngünün tam ortamalarındaki `if (x == durumsuresi)` benzeri kodun icine alır! O kelime "break" i okur okumaz sonsuz dönüm olsa dahi **Aynı çember döngüsünden sonsuzca Dışarı** zıplar ve parantezi terkeder(Yüz bin tur atmayacaktır hemen sonlanıp kapatılcak).

2. **`continue` (Pas Geç/ Atla) :** `break` de ki gibi döngüyü ebediyen parçalamaz. Derki, sadece bu 1 adımlıktaki (Örneğin sıra adımın= "13" ' üncü kısmındasın) turunda print veya işlem uygulama ... 13 ü iptal edip hemen Adım "14" e fırlaması yani bu dönüşü bitirmesidir..
Örn: *13 Cuma rakamıysa Pasla. (Sistem 1.. 12 .. 'yi yazar Continueyi görünce başa çıkar ve 14..  15.. ..' e yazar)* 

---

## 4. Gerçeğe Yansıyan "Kodlu" Kombinasyon / Girdisi Süren Program
Klavyeden kişi  Negatif(- Eksi) sayı Cıkartılana( - girdiği SÜRECE bitirmeyen program) kadar Ekrana sayıyı alıp, eskiye sayıyı ilave edip yazılan  toplamasını yapan bir sistemimiz: *(Bu Geçtiğimiz Diyagramda yapılımıştı işte kodları)*

```c
#include <stdio.h>
int main() {
    int kullanciRakam = 0;
    int depolananTutar = 0;
    
    // Ilk while karar sartina uyup baslamasi icin degiskeni(0) attik yukarida..
    while ( kullanciRakam >= 0 ) {
         
          // Kullanici sisteme rakam atti. Dongu onu kutuya cekip koydu.
          printf("Pozitif ve Toplanacak Tutar verin (Eksi girmek Sistemi Sona Eder):\n");
          scanf("%d", &kullanciRakam);
          
          if(kullanciRakam < 0){ 
                break; // Eksi (-) Girildi anında dongudeki "depolamaya ulasamadam kirmali yapi " ! (Bari son girdiği eksiyi eklemesin)
          }  
         
          // Sistemi kiramadiysa o zaman Depoya eklenebilme onayi(Normaldongu) ! 
          depolananTutar = depolananTutar + kullanciRakam;
    }
  
    // While parcalanip terk elince alt program akisinda devam..
    printf(" Cikan sonuc Toplam Deponuz: %d\n", depolananTutar);
    return 0;
}
```

---

## 5. Hafta Özeti
Bu C Kod parçalarımız ile Kararlar (IF)'in içlerine sayılar (Tekrar- While/For) girerek bilgisayar olgusuna bir donanım harikasından, analatik kod fırtınasına çevirtme aşamalarını en tepe noktada sonlaştırdık. Zira sayılar ve veri tabanları For olmadan sayfanıza dökülmez! Biz de break ler ve For lar sayesinde algoritmamız nereye varacak onun yörüngesini el üstü yazdık.

**Uygulama/Alıştırma Egzersizleri:**
1. C programcılığıyla bir `for` veya (sayacı manuel) `while` kullanarak 0  ile 50 ye kadar ilerlemeli bir sistemle sadece ve sadece (Dönüş if'le Kontrol 11, 22 ,33..) şeklindeki *11 Rakamın Tam Karşılık Katlarını* konsol(Ekrana) çıkmalasın (İpucu: `%` yani mod alın ! ).
2. Sistemsel bir SIFRE oluşturun örneğin `Şifrenin Suresi : 1234` .. Kullanıcı Eğer Giremesse Ekranda While kullanılarak `Kıramadınız Yine Giriş!` denilererek Sonsuz (3-5 kereliş şart değil!)  bir program yazılımı çalışması yapsın! Eğer `1234` girilirse `break` ve ekran yazdır "SİFRE DOGRU SÜRÜM BİTİYOR".
