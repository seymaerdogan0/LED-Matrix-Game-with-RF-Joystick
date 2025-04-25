# LED-Matrix-Game-with-RF-Joystick
Bu projede, iki adet PIC16F887 mikrodenetleyicisi kullanılarak joystick'ten alınan verilerin RF modülleri üzerinden kablosuz şekilde aktarılması ve bu veriye göre 8x8 LED Matrix üzerindeki bir karakteri hareket ettirmesi sağlanmıştır.

## 📦 Proje Bileşenleri

- **PIC16F887 (2 adet)**: Verici ve alıcı birimlerde kullanılmıştır.
- **RF Modülleri (433 MHz TX-RX)**: Kablosuz haberleşme için.
- **Joystick Kullanıcıdan yön verisi alınır.
- **MAX7219 + 8x8 LED Matrix**: Görsel çıkış birimi.
- **Proteus (ISIS)**: Devre tasarımı ve simülasyonu için.
- **CCS C**: Mikrodenetleyici programlaması için.

---

## 📁 Dosyalar

- `rf_transmitter.c` : Joystick verisini okuyarak RF ile gönderen verici kodu.
- `rf_receiver.c` : Gelen RF sinyale göre LED Matrix'i güncelleyen alıcı kodu.
- `proje_devre.png` : Proteus devre şeması ekran görüntüsü.(görseldeki potansiyometre yerine gerçek joystick kullanıldı elektronik devrede)

---

## 🔧 Sistem Çalışma Mantığı

### Verici (Transmitter)

1. AN0 ve AN1 pinlerinden joystick’in yatay ve dikey yön bilgisi alınır.
2. ADC ile okunan bu değerler 10-bit çözünürlükle dijitalleştirilir.
3. Belirli eşiklere göre `pot1` ve `pot2` değerleri hesaplanır.
4. Bu değerlere karşılık gelen 32-bit NEC RF kodları, RF modülü üzerinden gönderilir.

### Alıcı (Receiver)

1. Harici kesme ile RF verisi alınır ve NEC protokolüne göre ayrıştırılır.
2. Gelen koda göre `pot1` ve `pot2` değerleri set edilir.
3. MAX7219 sürücüsü kullanılarak LED Matrix’e A, B, C, D karakterleri çizdirilir veya temizlenir.
4. Belirli kombinasyonlarla animasyon veya sabit karakter gösterimleri yapılır.

---

## 🚀 Kullanım

1. Her iki PIC16F887 için ayrı ayrı `rf_transmitter.c` ve `rf_receiver.c` kodları derlenip yüklenmelidir.
2. Proteus simülasyonunda RF modüller arasında doğru bağlantı kurulduğundan emin olun.
3. Simülasyon başlatıldığında joystick’in yönüne göre LED Matrix’te görseller değişecektir.

---

## 🧠 Öğrenilenler

- NEC protokolü ile RF haberleşme
- Analog okuma ve dijital karşılık üretme
- MAX7219 ile SPI benzeri protokolde LED Matrix kontrolü
- PIC16F887 ile kesme yönetimi ve zamanlayıcı kullanımı

---

## 📸 Ekran Görüntüsü

![Devre Şeması](proje_devre.png)

---

## ✍️ Yazar

Bu proje, [Mikroişlemciler Dersi] kapsamında gerçekleştirilmiştir.

---

