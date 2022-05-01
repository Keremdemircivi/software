# software
My goal is to make parking sensors for cars
u Projede Neler Öğrenilecek?
Projenin detaylarına inmeden önce bu arduino uygulamasıyla buzzer kontrolü, led kontrolü, ultrasonik sensör kullanımı ve arduino ile if else() kullanımını öğrenmiş olacaksınız.
Kablo Arduino ile Park Sensörü Yapımı için Gerekli Malzemeler Nelerdir?
Arduino Uno R3 Kartı
HC-SR04 Ultrasonik Mesafe Sensörü
5mm LED
Orta Boy Breadboard
220oHm Direnç
Erkek-Erkek Jumper
Arduino ile Park Sensörü Kodu Nasıl Yazılır?
Park sensörü uygulamasında if döngüsü kullanacağız. Hc-sr04 ultrasonik mesafe sensöründen gelen veriyi cm cinsine çevireceğiz. Sonrasında if döngüsü içerisinde ölçülen uzaklıklara göre belirli aralıklarla buzzerden uyarı sesi verip ledi yakıp söndüreceğiz. Projemizi kodlamaya geçmeden önce if-else () kullanımı nasıldır bunu aşağıdan inceleyebilirsiniz.
If Else Yapısı Nedir? 
ingilizcede eğer anlamında kullanılmakta olup else ise değil anlamındadır. If else yapısında bir koşul  veya koşullar doğruysa yapılacak işlemler, koşul doğru değilse yapılacak işlemlerin yazıldığı bir çeşit sorgudur.
f( koşul1)

{

Koşul1 Doğruysa Yapılacak işlemler

}

else if( koşul2)

{

Koşul2 doğruysa yapılacak işlemler

}

else 

{

Hiçbir koşul doğru değilse yapılacak işlemler

}

Yukarıdaki örnekte çalışma mantığını daha kolay anlayabilirsiniz. Koşulları oluştururken karşılatırma operatörlerini kullanırız. Projemizin yazılım aşamasında pekiştireceğinizi düşünüyorum.
Arduino ile Park Sensörü Kodları
const int trigger_pin = 12; //12. pini trigger pin olarak tanımlandı.
const int echo_pin = 13; //13. pini echo pin olarak tanımlandı.
int uyariLed = 2; //2. pini uyariLed olarak tanımlandı.
int buzzer = 6; //6. pini buzzer olarak tanımlandı.

int sure ; //sure adlı bir değişken tanımlandı.
int mesafe ; //mesafe adlı bir değişken tanımlandı.

void setup() {

pinMode(uyariLed , OUTPUT); //aled'i çıkış olarak tanımladık.
pinMode(buzzer , OUTPUT); //buzzer'i çıkış olarak tanımladık.

pinMode(trigger_pin , OUTPUT); //trigger pin'i çıkış olarak tanımladık.

pinMode(echo_pin , INPUT); //echo pin'i giriş olarak tanımladık.

}
void loop()

{

digitalWrite(trigger_pin , HIGH);

delayMicroseconds(1000);

digitalWrite(trigger_pin , LOW);

sure = pulseIn(echo_pin , HIGH); //echo_pin verisi sure değişkenine atandı.

mesafe = (sure / 2) / 29.1; //cm cinsine çevrildi.


if (mesafe <= 10) //mesafe 10 cm den kısaysa aşağdaki işlemler gerçekleşir.
{

digitalWrite(uyariLed , HIGH);
digitalWrite(buzzer , HIGH);

}
else if(mesafe>10 && mesafe<=20) //Mesafe 10 cm den uzun 20cm de eşit veya kısaysa aşağdaki işlemler gerçekleşir.
{
digitalWrite(uyariLed , HIGH);
digitalWrite(buzzer , HIGH);
delay(150); // ledin yanık kalma süresiyle buzzerin uyarı süresi standart bir süreye 150ms ye ayarlandı.
digitalWrite(uyariLed , LOW);
digitalWrite(buzzer , LOW);
delay(250);
}
else if(mesafe>20 && mesafe<=30) //Mesafe 20 cm den uzun 30cm de eşit veya kısaysa aşağdaki işlemler gerçekleşir.
{
digitalWrite(uyariLed , HIGH);
digitalWrite(buzzer , HIGH);
delay(150);
digitalWrite(uyariLed , LOW);
digitalWrite(buzzer , LOW);
delay(450);
}
else if(mesafe>30 && mesafe<=40) //Mesafe 30 cm den uzun 40cm de eşit veya kısaysa aşağdaki işlemler gerçekleşir.
{
digitalWrite(uyariLed , HIGH);
digitalWrite(buzzer , HIGH);
delay(150);
digitalWrite(uyariLed , LOW);
digitalWrite(buzzer , LOW);
delay(650);
}
else if(mesafe>40 && mesafe<=50) //Mesafe 40 cm den uzun 50cm de eşit veya kısaysa aşağdaki işlemler gerçekleşir.
{
digitalWrite(uyariLed , HIGH);
digitalWrite(buzzer , HIGH);
delay(150);
digitalWrite(uyariLed , LOW);
digitalWrite(buzzer , LOW);
delay(850);
}
}
Devreyi kurup yazılımı arduinoya ekledikten sonra yükle butonuna basarak arduino kartınıza yazılım yükleyebilirsiniz. 
Uygulama çalışmasında mesafe sensörüne cisim yaklaştıkça verilen uyarının miktarı artacak ve 10cm ve altında led ve buzzer sürekli açık kalacaktır. Mesafe uzadıkça uyarılar azalacaktır. Keyifli uygulamalar dileriz
