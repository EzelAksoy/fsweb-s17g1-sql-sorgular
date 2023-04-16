# SQL Sorgu Alıştırmaları

Bu hafta SQL sorguları üzerine çalışıyorsunuz. Bugünkü alıştırmada sizin için hazırladığımız veritabanında aşağıda istediğimiz sonuçları elde etmenize yarayan SQL sorgularını oluşturacaksınız.

# Proje Kurulumu

Projeyi forklayın ve clonlayın. Tamamladığınızda da pushlayın.

## Kütüphane Bilgi Sistemi

Bu veritabanı, bir okulun kütüphanesinden öğrencilerin aldıkları kitapların bilgisini barındırmaktadır.

#Tablolar
`ogrenci` tablosu öğrencilerin listesini tutar.
`islem` tablosu öğrencilerin kütüphaneden aldıkları kitapların bilgilerini tutar
`kitap` tablosu kütüphanedeki kitapların bilgisini tutar
`yazar` tablosu kitapların yazarları bilgisini tutar
`tur` tablosu kitapların türlerini tutar.

Tablo ilişiklerini görmek için [ktphn.png] dosyasına göz atın.

Yazdığınız sorguları buradan test edebilirsiniz: [https://ergineer.com/assets/materials/fkg36so5-kutuphanebilgisistemi-sql/] (update, delete, drop sorguları iptal edilmiştir).

### Görevler

Aşağıda istenilen sonuçlara ulaşabilmek için gerekli SQL sorgularını altlarına yazın.

    1) ÖRNEK SORU: Öğrenci tablosundaki tüm kayıtları listeleyin.

    	CEVAP: select * from ogrenci


    2) Öğrenci tablosundaki öğrencinin adını ve soyadını ve sınıfını listeleyin.

    	CEVAP:  Select ograd,ogrsoyad,sinif from ogrenci

    3) Öğrenci tablosundaki kız öğrencileri listeleyin.

    	CEVAP:  Select ograd,ogrsoyad,cinsiyet from ogrenci
                Where cinsiyet = "K"


    4) Öğrenci tablosunda kaydı bulunan sınıfların adını her sınıf bir kez görüntülenecek şekilde listeleyiniz.

    	CEVAP:  Select sinif from ogrenci
    			Group By sinif

    5) Öğrenci tablosunda, 10A sınıfında olan kız öğrencileri listeleyiniz.

    	CEVAP:  Select ogrno,ograd,ogrsoyad from ogrenci
    			Where cinsiyet= "K" and sinif="10A"

    6) Öğrenci tablosundaki 10A veya 10B sınıfındaki öğrencilerin adını, soyadını ve sınıfını listeleyiniz.
    	CEVAP:  Select ogrno,ograd,ogrsoyad from ogrenci
    			Where sinif="10B" or sinif="10A"

    7) Öğrenci tablosundaki öğrencinin adını, soyadını ve numarasını okul numarası olarak listeleyiniz. (as kullanım örneği)
    	CEVAP:	Select o.ograd,o.ogrsoyad,o.ogrno from ogrenci as o


    8) Öğrenci tablosundaki öğrencinin adını ve soyadını birleştirip, adsoyad olarak listeleyiniz. (concat, as kullanım örneği)

    	CEVAP: Select Concat(o.ograd,o.ogrsoyad) as adsoyad from ogrenci as o


    9) Öğrenci tablosundaki Adı ‘A’ harfi ile başlayan öğrencileri listeleyiniz.

    	CEVAP: Select o.ograd from ogrenci as o
    		   WHERE ograd LIKE 'a%'


    10) Kitaplar tablosundaki sayfa sayısı 50 ile 200 arasında olan kitapların adını ve sayfa sayısını listeleyiniz.

    	CEVAP: Select k.kitapadi,k.sayfasayisi from kitap as k
    		   Where k.sayfasayisi Between 50 and 200


    11) Öğrenci tablosunda adı Fidan, İsmail ve Leyla olan öğrencileri listeleyiniz.

    	CEVAP: Select * from ogrenci as o
    		   Where ograd="Fidan" or ograd="İsmail" or ograd="Leyla"


    12) Öğrenci tablosundaki öğrencilerden adı A, D ve K ile başlayan öğrencileri listeleyiniz.

    	CEVAP: Select * from ogrenci as o
    		   Where ograd LIKE "a%" or ograd LIKE "d%" or ograd LIKE "k%"


    13) Öğrenci tablosundaki sınıfı 9A olan Erkekleri veya sınıfı 9B olan kızların adını, soyadını, sınıfını ve cinsiyetini listeleyiniz.

    	CEVAP: Select o.ograd,o.ogrsoyad,o.sinif,o.cinsiyet from ogrenci as o
    		   Where (sinif="9A" and cinsiyet="E") or (sinif="9B" and cinsiyet="K")


    14) Sınıfı 10A veya 10B olan erkekleri listeleyiniz.

    	CEVAP: Select * from ogrenci as o
    		   Where (sinif="10A" or sinif="10B") and cinsiyet="E"


    15) Öğrenci tablosunda doğum yılı 1989 olan öğrencileri listeleyiniz.

    	CEVAP: Select * from ogrenci as o
               Where dtarih Like "%1989%"


    16) Öğrenci numarası 30 ile 50 arasında olan Kız öğrencileri listeleyiniz.

    	CEVAP: Select * from ogrenci as o
    		   Where cinsiyet="K" and ogrno Between 30 and 50


    17) Öğrencileri adına göre sıralayınız (alfabetik).

    	CEVAP: Select * from ogrenci as o
    		   Order By ograd


    18) Öğrencileri adına, adı aynı olanlarıda soyadlarına göre sıralayınız.

    	CEVAP: Select * from ogrenci as o
    	       Order By ograd,ogrsoyad


    19) 10A sınıfındaki öğrencileri okul numarasına göre azalan olarak sıralayınız.

    	CEVAP: Select * from ogrenci as o
    	       Where sinif="10A"
    		   Order By ogrno DESC


    20) Öğrenciler tablosundaki ilk 10 kaydı listeleyiniz.
    [İPUCU: `Select top tüm mysql versiyonlarında düzgün çalışmaz. LİMİT kullanmak daha faydalıdır`]

    	CEVAP: Select * from ogrenci as o
    		   Limit 10

    21) Öğrenciler tablosundaki ilk 10 kaydın ad, soyad ve doğum tarihi bilgilerini listeleyiniz.

    	CEVAP: Select ogrno,ograd,ogrsoyad,dtarih from ogrenci as o
    		   Limit 10


    22) Sayfa sayısı en fazla olan kitabı listeleyiniz.

    	CEVAP: Select * from kitap as k
    		   Order By sayfasayisi DESC
    		   Limit 1



    23) Öğrenciler tablosundaki en genç öğrenciyi listeleyiniz.

    	CEVAP: Select * from ogrenci as o
    		   Order by dtarih DESC
    		   Limit 1


    24) 10A sınıfındaki en yaşlı öğrenciyi listeyin.

    	CEVAP: Select * from ogrenci as o
    		   Where sinif="10A"
    		   Order By dtarih ASC
    		   Limit 1


    25) İkinci harfi N olan kitapları listeleyiniz.

    	CEVAP: Select * from kitap as k
    		   Where kitapadi Like "_n%


    26) Öğrencileri sınıflarına göre gruplayarak listeleyin.

    	CEVAP: Select * from ogrenci as o
    		   Order by sinif


    27) Öğrencileri her sorgulamada sıralaması farklı olacak şekilde rastgele listeleyin.
    [İPUCU: rand() fonksiyonu]

    	CEVAP: Select * from ogrenci as o
    		   Order By rand()


    28) Öğrenci tablosundan Rastgele bir öğrenci seçiniz.

    	CEVAP: Select * from ogrenci as o
    		   Order By rand()
    		   Limit 1


    29) 10A sınıfından rastgele bir öğrencinin adını, soyadını, numarasını ve sınıfını getirin.

    	CEVAP: Select * from ogrenci as o
    		   Where sinif="10A"
    		   Order By rand()
    		   Limit 1

    # Esnek
    30) Öğrenci tablosunda aynı isimde kaçar öğrenci olduğunu bulmak istiyoruz.
    Öğrenci isimlerinin sayısını "adet" olarak öğrencilerin isimleri "isim" olarak listeleyin.
    [İPUCU: count() ve group by]

    	CEVAP: Select COUNT(ograd) as adet,ograd as isim from ogrenci
    		   Group by ograd
