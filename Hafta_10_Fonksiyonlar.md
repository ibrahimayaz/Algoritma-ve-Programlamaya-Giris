# Hafta 10: Fonksiyonlar (Functions)

## 1. Giriş ve Ön Hazırlık
Haftalarca kodlarımızı ve döngülerimizi C dilindeki ana merkez bloğu olan `int main() { ... }` isimli süslü paranteze doldurmaya çalıştık.
Ama programımız profesyonelleştiğinde, 5000 hatta 100 binler seviyesinde satır kod okuduğunuzu varsayın! Aynı hesaplama kodlarını (örneğin %18 KDV ekleme veya Ortalama alma algoritması), Main'in içerisinde farklı zamanlarla "sürekli alt alta (Copy-Paste gibi)" yazarak programı mahvedemeyiz! 

İşte bu evrede **"Fonksiyonlar (Functions - Alt Programcıklar)"** dediğimiz modüler kod mimarisine gireceğiz. 

**Hedeflerimiz:**
- Modüler C Kod parşömen mantığını ve neden Fonksiyona mecbur kaldığımızı öğrenmek.
- Main (Gövde) ortamından kopuk kendi işinizi yaptırdığınız alt metotlar kurabilmek. 
- Fonksiyonlardan çağrıların ve geri sonuç döndürmenin(Kuryelik) matematiğini koda yansıtmak..

---

## 2. Fonksiyon Nedir? Faydaları Neler?
Belirli ve sadece "TEK BİR İŞLEMİ" yapmak üzere süslenmiş / yaratılmış bir kod blokaj parçasına (mini-program) denir.. 

*Örnek Felsefesi*: Müzik Çalar Kodunuz var; "Sesi Artır Fonksiyonu var, Parça Değiş Fonks , Parçayı Başlat Fonksiyonları var". Hepsini Ana Main'de birleştirseydiniz bulamzdınız kodunu.. Halbuki sadece yeri geldiğinde "SesiArtir();" isimli çağırdınız  koda (Main oraya gidip o görevi ifra edip) geri döner... 

1. **Tekrarlardan (Kod Kalabalığnan) Uzaklaşma :** Kodunuzu bir kere fonksiyonda tasarlarsınız. Main() bloklarından istediğiniz zaman adıyla cagirıp çalıştırtabilirsiniz.
2. **Sorun Tespiti Kolaylığı:** Program bozuldu, KDV hesaplamada mı arıza çıktı? Maini taramaz; Sadece ismini "kdvHesaplama" yapan o ufak mini fonskiona girer 2 satırlı sorunu cozersiniz!
3. **Ekip Çalışmasına Elveriştir:** Projede Ayşe login(giriş) fonksiyonunu yazar Ali (Veritabanı Okuma ) fonksiyonu , Mehmet Gorsel yazarsa hepsini en son Main() 'da toplarlar! Birbirlerine girmeden.. 

---

## 3. C'de Kendi Fonksiyonlarımızı (Metot/AltPrg) Tasarlamak 
Kendi fonksiyonlarımızı, her daim ana fonskyionun üst kısmına (Ya `main()` den önce , ki C makinalarınca onu Main görebilsin - okusun) yerleştiririzi.

C dillerinde İki Ana Tip Görev felsefesiz vardır: 
1. **Veri Döndürmeyen ("Ben Ekrana Basarım, Sana Kuryelik Etmem" Görevlisi =  `void`)**
2. **Veri Döndüren ("İşlemi Alır Yapar , Sonucu Sisteme/Main'e Gerçek Ürün Götürür",  = `int`, `float`, vs...)**

### 3.1. Void Fonksyionu (Dönemsiz - Boş Metotlar) Kurulumları
Void "Boşluk" demektir, Görevi işlemi yapıp fonskyionda durmak veya ekrana `printf` çekip kapatmaktır. Sistemin matematiksel hesabı Ana Main'e atıp kaydetme yapısı (Return) barındırmaz. 

**Tasarım Semasi:** `void FonskYaratilmisAdi () {   // Kodlariniz   } `

```c
#include <stdio.h>

// ISTE PROGRAMCIGIMIZ! MAIN DEN ONCELİKI UST SIRASINDA !! 
void selamYazdirBana() { 
     // Gorselligini Veya İşleyisi sadece Ekrana (Sana) Donuk.. Matematigi yok .
     printf("\n >>> Hos Geldiniz Sayin Uye Sistemimiz Acildi !! <<<\n");
}  // Ve mini islemci kendi basina da kapandı ! 


int main() {
    
    printf("Su An Ben Main (Programin Ana Kalbindeyim) Fonksiyondayim..\n");
    
    // YUKARDAN KENDI GOREVI OLAN FONKSIYONU ISMIYLE CAGIRIYORUMM !! 
    selamYazdirBana();
    // Iki kere de tekrarlayabilirisiz (Dongu yazmadna !!)
    selamYazdirBana(); 

    printf("Hepsine gidip gorevlerini taptiklarinda Bende Main'e asagi kactim..\n");
    return 0;
}
```

---

## 4. Matematiki Fonskiyonlara Parametre(BİLGİSİ) Atanması ve Geri Dön(Return) İsteme..
C programlamasında görevci Fonksiyona, "Al Sana Ben Main'im Su rakam malzemeleri veriyorum. Banada Bu Malzemenden Kek Ver!" felsefesinin en sık koduna "Return() fonskyonlar " diyoruz. 

Bu defa `void` değilde o fonskiyonun Kuryelik görevi (`int`, `float`) ne göndericekse tipi baştan verilir !
Ayrıca dışarıdan parametreleri "Parantezlera (`int numaraAl `)" alır..

*Basit Örneklem: Iki Rakam Gönderilecek Toplam Sonucu Ana Kalba Düsecektir :*

```c
#include <stdio.h>

// Fonksıyon Void Degil INT Dondurucek Cunku MAıne Bıze Toplam Tamsayi( INT ) getırecegını bildirmistir :
// ( .. ) Parantez kismina İki Tane "PARAMETRE (Degisken Havuzu)" kurmustur!
int ikiRakamTopla(int RakamA, int RakamB) { 
     
     int ToplamCikan = RakamA + RakamB;
    
     // GOREV BELIRTIYORUZ: "Return(GeriDon)".. Nereye Cagrildiginsa o Cikan "Sayiyi" Oranın Icınde ver!
     return ToplamCikan; 
} 

int main() {
    
    int GelenKuryeninVerisi; // Ben  Maine bu gelecek int (Toplamcikani ) kendi kapima taslarim:
    
    // GelenVeriye Eşitledik... Aynen ismiyle 10 ve 20 yi (Rakam A ve Rakam B ye) sirayla attik!
    // Fonskyion uctu ! RakamA (10) ;  Rakam bB (20 ) ile hesabi yapti ve iceriye Return ( Toplami 30 olan ) atti !! 
    GelenKuryeninVerisi = ikiRakamTopla(10 , 20);
    
    // Gorduunuz gibi Main Ekrana rahatlıkla kurye getirisini ekrana kucakladi.. 
    printf("Ustaki Ozel Islemcinin Fiyatisal Sonuc Ciktisi: %d \n", GelenKuryeninVerisi);
  
    return 0;
}
```
*Artık ben 1 Milyar Kere de Ana sistemden 1 Topla çağrısı fonskiyonuna istedeğim (70,80) , (90,10) lar atıp yüzlerce değişkeni o bir sistem bloğundan çıkartabiliyorum demektir !*

---

## 5. Haftalık Özet Fırtınasının Finali..
C ve genel geçerli yazılımları öğrenmede Fonksion (Methods - Alt görevciler) bir mühendisin olmazlarsa olmaz iskeletleridir. Eger Kodlar Tek parantez yığılımı (Sadece Main) yaparsak bu Spagetti (Karmaşa ) programcılığı olur.. Her fonksıyon "Tek isleme" odaklandırmalıdır.. Yazılan fonskiyonlara ( Parametre Parantazı içine Malzmelerini ) verir; sonucunda Void lerle boş işlemle yansıtmamayı; ama eger İşlem bir formül ve Veritabanı aktarımcılığıysa (Return int/ float) kurgusundan geriye çağrılandırıldığı yerdeki ana değişkene geri bırakırız!

**Uygulama/Alıştırma Egzersizler :**
1. Geri Sayı Dönümlü(`float`) olan; kendisine yollalınan, Çember Yarı Çarpını (R: `int` Parametresi olarak C den alınıp) içeride alanının (Pi  `3.14 * r * r ` ) algoritma matematiğine uyup, C'nin ana maininde Çıkan formülü (`printf` le Gösteren ) Fonksiyonel yazılımlı program parçasını kurgulayıp işletiniz..
2. Kullanıcının Şifresine ve Kullancını adını stringle(`%s` ) girdi olarak dışardan verditen.. Veriyi  `char` ve Şifreyi alarak  "`KullaniciDogrumuHesapla`" fonksiyonun void siz yollayın... Hesapla altfonksiyonunu `if (1234)` kontrolunu  ayrı satırlarında yapıp ekrana sadece Basarili -Basarisiz! Printlerini Void kullanarak dökmesini kurgulayın!  
