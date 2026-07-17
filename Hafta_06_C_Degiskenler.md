# Hafta 6: C Programlama Dili: Değişkenler ve Veri Tipleri

## 1. Giriş ve C Diline Merhaba
Geçtiğimiz 5 hafta boyunca, programlama disiplininin arka planını hazırladık. Makinaların donanım/yazılım bağıntılarını, algoritmik düşünceyi ve süreç şablonlarını (Akış Diyagramlarını) irdeleyerek zihnimizi bir "yazılımcı analitiği" kıvamına soktuk. Bugünden itibaren bu dökümandan somut bir Programlama Dili olan **"C" Dili** dünyasına geçiş yapıyoruz. Artık yazdıklarımızı, ekrandaki programlara ve kod satırlarına dönüştüreceğiz.

**Hedefler:**
- C dilinin çıkış amacı ve donanıma olan yakınlığını kavramak.
- Temel bir C kod dosyasının mimarisini, ana şablonunu anlamak.
- Ram'de yer alan veri tiplerinin (Tam Sayılar, Ondalık Sayılar, Karakterler) C dilindeki karşılıklarını detaylandırmak.

---

## 2. Neden C Programlama Dili Öğreniyoruz?
Önlisans ya da mühendislik seviyesindeki bir bilgisayar bilimi öğrencisinin temel yapı taşlarının başında C programlama dili öğretilir. 
Python gibi modern ve kısa komutlu diller çok popüler olsa da, programlama etiğini ve "arka planda bilgisayar bunu süzgecinden nasıl geçiriyor, belleği (RAM'i) nasıl harcıyor" sorusunu öğreten tek dil C dilleridir.

Pek çok modern dilin (Java, C#, C++) dedesi C'dir. C'de söz dizimini anlayan biri birkaç ay içerisinde dünyadaki çoğu teknik dili rahatlıkla idrak edecektir. 
Linux, Windows çekirdekleri, oyun motorları donanımın tam kalbine dokunabilme ve maksimum hızla çalışabilme kabiliyeti yüzünden çoğunlukla C & C++ tercihinde bulunmuştur.

---

## 3. C Derleyicisi (Compiler) ve İlk Programımızın İskeleti

### 3.1. C Derleyicisi (Compiler) Nedir?
Bizler programlarımızı insanların okuyup anlayabileceği İngilizce benzeri C komutlarıyla (örneğin `printf`, `int main`) yazarız. Ancak hatırlayacağınız üzere bilgisayar donanımı (işlemci) sadece `0` ve `1` adı verilen makine dilinden anlar. 
İşte yazdığımız bu C kaynak kodlarını (örneğin sonu `.c` uzantılı dosyaları) bilgisayarın anlayacağı makine diline çeviren, kodda kural hatası (syntax error) yoksa bunu çalıştırılabilir bir uygulamaya (Windows için `.exe` dosyasına) dönüştüren aracı yazılımlara **Derleyici (Compiler)** denir. GCC, Dev-C++ derleyici motoru veya Visual Studio bunlara örnektir. İşlem sırası basittir: Kod yazılır, derleyiciye verilir (compile işlemi) ve oluşan program çalıştırılır (run).

### 3.2. Kod İskeletimiz

C dilinde geliştirilmiş en temel, her "yeni başlayan"ın (Newbie) yazdığı ilk program ekrana merhaba yazdırmakla başlar. İncelemek üzere o kodu sunalım:

```c
#include <stdio.h> // Birinci kisim: Kutuphaneler dahil ediliyor.

// Ikinci kisim: Ana (Merkez) Fonksiyon. Program calismaya buradan baslar.
int main() {
    
    // Ucuncu kisim: Kodlarin - Gozle Gorulen Komutlarin Basladigi Alan!
    printf("Merhaba, Programa Hazirim!\n");
    
    return 0; // Komut satiri duzgun calisti bilgisini sisteme ilet ve fonksiyonu kapat.
}
```

Bu iskelet parçalarındaki temel bilgiler şöyledir:
- `#include`: Standart "Ekrandan Veri Almak ve Ekrana Veri Yazdırmak (Input/Output)" için `stdio.h` isimli kütüphaneyi çekmemizi sağlar. Bu çekilmezse, ekrana kelime yazma komutu olan `printf` kendi görevini tanımazdı!
- `int main()`: Tüm C dillerindeki uygulamalarda, bilgisayar derlemeye / kurgulamaya direkt olarak main kelimesini arayarak başlar. Bu bloğun içine de işlem akışınızı eklersiniz.
- `{` ve `} ` *(Süslü Parantezler)*: Türkçe düşünürsek "Birleşik bir cümlelik (Kapsam)" demektir, yazılan satırlar parantezin sınırını terk etmez!
- Noktalı virgül `;`: Her komutun yan yana bittiğini anlatan, Türkçe gramerlerdeki "Nokta(.)" yapısıdır. Bunlar unutulursa sistem kodu derlemeden kırmızı hata basar (SyntaX - Gramer Hatası).

---

## 4. Değişkenler ve Bellek (RAM) Yönetimi
Akış diyagramları kısmında `Sayı 1`, `Sayı 2` şeklinde kafamızdan metinle isimlendirerek kullandığımız değişkenler kısmına döndük. 
Fakat C dili çok katı bir dildir. Sisteme "Selam ben `Sayi` diye değişken tanımladım" diyip geçemezseniz! O verinin **"NE TİPTE/BOYUTTA"** olacağını da (bu bir kelime mi, harf mi, bin küsürlü atamalı bir sayı mı vs.) ona önceden haber vermelisiniz.  Haber vermelisiniz ki bilgisayar, geçici RAM belleğinde ihtiyaçtan büyük yerleri rezerve edip bilgisayarı çökertmesin. 

İşte bu sürece C dilinde **Değişken Belirleme ve Veri Tipleri (Data Types)** deniyor.

### 4.1. Temel Veri Tipleri
Önlisans aşamasında 3-4 kilit yapıyı en çok kullanacağız:

1. **`int` (Integer - Tamsayılar):** Kesir / Bölünmeyen kaba sayılardır. (-5, 10, 0, 1000). Ram’de (genellikle) 4 Byte yer kaplarlar -2 Milyar ila +2 Milyar arasındaki sayılara kucak açabilir.
   Tanımlama örneği: `int Sayi = 5;`,  `int Yas = 21;`
   
2. **`float` (Ondalık/Kesirli Sayılar):** Küçük virgüllü ve noktalı rakamlarda kullanılan sayılardır.
   Tanımlama örneği: `float Maliyet = 15.5;`  (Not: Türkiye'deki gibi virgül (,) KULLANILMAZ sistemde nokta (.) basılır).
   
3. **`double` (Kapasiteli Ondalık Sayılar):** Float’ın ağabeyidir. Bilimsel bir hesaplama vs yapıyorsanız küsürat hatası vermemesi için daha ağır bu tıpı çağırırsınız (15 haneli).
   Tanımlama örneği: `double pDizisi = 3.14159265;`

4. **`char` (Character - Sadece Tek Bir Karakter):** Klavyedeki harf ('A', 'B') sembol veya sayı değerlerini ancak "Teker teker" saklamak için yaratılmış tek byte alan tiplerdir. En belirgin özelliği karakterler içeri atanırken değer Tırnak (`'...'`) içinde verilmelidir. 
   Tanımlama Örneği: `char KanGrubu = 'A';`

*(Ayrıca metin yazabilmek için de birden fazla karakter dizisini bir araya getiren string dizileri vardır ki haftalarca sonra "Diziler-Arrays" konusunda yoğunlaşacağız)*.

### 4.2. Değişken Tanımlama Süreç Formülü
C dilinde bir değişkeni oluştururken soldan sağa bir formül vardır:
`Veri_Tipi_Adı` + `Kullanıcının Verdiği Metinsel Değişken Adı` + `=` + `Değeri` + `;`

**Ayrı Ayrı Kod Parçalarına Yansımaları:**
```c
int main() {
    // 1- İsterseniz kutuyu önceden açıp, değerini sonra yerleştirebilirsiniz.
    int ogrenciYasi; 
    ogrenciYasi = 23; 
    
    // 2- İsterseniz "Kutunu ismini verirken peşinen değer takabilmek de yasal!"
    float biskivuFiyati = 9.99;
    char okulKodHarfi = 'M';

    // Ayni turden birden cok cift kutucuk acilabilir..
    int Vize, Final, Ortalama;
    
    return 0;
}
```
*Burada en hassas kural:* C "Büyük ile Küçük" Harfe Duyarlıdır! (Case Sensitive). Eğer programda `int a` derseniz ve aşağıda `A` değerini kullanmaya çalışırsanız program o değişkeni bulamaz. C'ye göre (a) ve (A) aynı anlamlara gelmez! 

---

## 5. Değişkenleri Ekrana Bastırmak Üzerine Küçük Bir Başlangıç (`%` Parametreleri)
Biz `printf("Merhaba\n")` diyerek tırnak içini normal basarız. Peki demin oluşturduğumuz yaşı (ogrenciYasi= 23) ekranda "Kişinin yaşı: 23" yazmak istersek ne yapacağız? `printf("Yas: ogrenciYasi")` dersek ekranda literal o metni yazar 23 basmaz. 

İşte değişkenin içeriğini C'de ekranda oynatmak istiyorsanız "Biçim Niteleyicileri (Format Specifiers)" gerekir (Bunlara format damgası denir): 
- `%d` veya `%i` : Tamsayıları (int) temsil eder.
- `%f` : Ondalık yapıları (float) simgeler.
- `%c` : Harfleri / karakterleri (char) çeker.

```c
#include <stdio.h>

int main() {
    int Yil = 2026;
    float Bakiye = 120.50;
    
    // Yili virgüllü yapı ile C'ye çektirdik..
    printf("Bulundugumuz yil: %d dir.\n", Yil); 
    
    // Küsüratlı verimizi bir de çektirelim...
    printf("Elimizdeki Paramiz (Bakiye) : %f Turk Lirasidir.\n", Bakiye);
    return 0;
}
```

---

## 6. Haftalık Özet
Bu hafta diyagramların hayal aleminden çıkıp, gerçek kod kütüphanesi olan `stdio.h` 'ı bağlamayı, `printf()` kelimesiyle komuta dökmeyi kavramaya başladık. Operatörler, algoritma derslerinde gördüğünüz ve formüle ettiğiniz Matematiksel işaretlerin birebirleri olduğundan o adımları aynı harflerle koda koyabilirsiniz (`int toplam = x + c; `gibi).
Bizim asıl eforumuz; C dilindeki en hayati iskelet olan "RAM'in limitlerini gözetmek adına Veri Tipinin İllaki (Zorunlu Olarak) Belirtilmesi (`int`, `float`, `char`)" sürecidir. İleride sistemden veri girerken bile (Kullanıcı yaşını söyle demeden evvel) daima programın başında bu kutucukları önceden ayırmayı adımız kadar iyi bilmeliyiz!

**Alıştırma Testleri:**
1. Kişisel bilgisayarına, programlamaya uygun C kodu derleyen bir Ide program kur (Visual Studio Code, Dev-C++, veya CodeBlocks) ve ilk koddaki "Merhaba, Programa Hazirim!" metnini bastırarak konsol ortamını (Siyah Ekran) gözlemle. 
2. Ondalıklı (`float` yapısını) kullanan bir veri ile `printf` metodu birleştirildiğinde, değer olarak virgülden sonra istemediğimiz kadar 0 rakamı ortaya çıkabilir! Format basamağını `%0.2f` yaptığınızda ekranda ne değişmektedir, araştırıp uygulayınız. 
