# Arduino ADXL345 İvmeölçer Projesi

<div align="center">

![Arduino](https://img.shields.io/badge/Arduino-Compatible-blue.svg)
![License](https://img.shields.io/badge/license-MIT-orange.svg)
![GitHub](https://img.shields.io/github/stars/serialprint/Arduino-ADXL345?style=social)

**ADXL345 İvmeölçer Modülü ile Üç Eksenli İvme Ölçümü**

Arduino ile ADXL345 ivmeölçer modülünü kullanarak X, Y, Z eksenlerindeki ivme verilerini okuyan ve seri port üzerinden görüntüleyen proje.

</div>

---

## 📋 İçindekiler

- [Özellikler](#-özellikler)
- [Donanım Gereksinimleri](#-donanım-gereksinimleri)
- [Kurulum](#-kurulum)
- [Kullanım](#-kullanım)
- [Pin Bağlantıları](#-pin-bağlantıları)
- [Kod Açıklaması](#-kod-açıklaması)
- [Sorun Giderme](#-sorun-giderme)

---

## ✨ Özellikler

- ✅ **Üç Eksenli İvme Ölçümü**: X, Y, Z eksenlerinde ivme verileri
- ✅ **I2C İletişimi**: Kolay bağlantı ve kullanım
- ✅ **Seri Port Çıktısı**: Gerçek zamanlı veri görüntüleme
- ✅ **Adafruit Kütüphanesi**: Güvenilir ve kolay kullanım

---

## 🔧 Donanım Gereksinimleri

| Bileşen | Miktar | Açıklama |
|---------|--------|----------|
| Arduino (Uno/Nano) | 1 | Mikrodenetleyici |
| ADXL345 Modülü | 1 | İvmeölçer sensörü |
| Jumper Kablolar | 4 | Bağlantı için |
| Breadboard | 1 | Prototipleme için (opsiyonel) |

---

## 📦 Kurulum

### 1. Kütüphane Kurulumu

Arduino IDE'de **Library Manager**'dan şu kütüphaneleri yükleyin:

1. **Adafruit Unified Sensor** (Adafruit_Sensor)
2. **Adafruit ADXL345** (Adafruit_ADXL345_U)

**Kurulum Adımları:**
- Arduino IDE → Sketch → Include Library → Manage Libraries
- "Adafruit ADXL345" araması yapın
- "Adafruit ADXL345" kütüphanesini yükleyin (Adafruit Unified Sensor otomatik yüklenecektir)

### 2. Kodu Yükleme

1. `Arduino ADXL345.txt` dosyasını Arduino IDE'de açın
2. Arduino kartınızı seçin (Tools → Board)
3. Port'u seçin (Tools → Port)
4. Kodu yükleyin (Upload)

---

## 🚀 Kullanım

1. Donanım bağlantılarını yapın (Pin Bağlantıları bölümüne bakın)
2. Kodu Arduino'ya yükleyin
3. Serial Monitor'ü açın (Tools → Serial Monitor, 9600 baud)
4. X, Y, Z ivme değerlerini gözlemleyin

**Örnek Çıktı:**
```
X: 0.12  Y: -0.45  Z: 9.81  m/s^2
X: 0.15  Y: -0.42  Z: 9.80  m/s^2
```

---

## 🔌 Pin Bağlantıları

| ADXL345 Modülü | Arduino Pin | Açıklama |
|----------------|-------------|----------|
| VCC | 5V veya 3.3V | Güç Beslemesi |
| GND | GND | Toprak (Ground) |
| SDA | A4 (Analog 4) | I2C Veri Hattı |
| SCL | A5 (Analog 5) | I2C Saat Hattı |

**Not:** 
- Arduino Uno/Nano için SDA = A4, SCL = A5
- Arduino Mega için SDA = 20, SCL = 21
- 3.3V veya 5V besleme kullanılabilir (modüle göre)

### Bağlantı Şeması

```
ADXL345          Arduino
─────────         ───────
VCC      ──────── 5V/3.3V
GND      ──────── GND
SDA      ──────── A4
SCL      ──────── A5
```

---

## 💻 Kod Açıklaması

### Kütüphaneler

```cpp
#include <Wire.h>                    // I2C iletişimi için
#include <Adafruit_Sensor.h>         // Adafruit sensör kütüphanesi
#include <Adafruit_ADXL345_U.h>      // ADXL345 kütüphanesi
```

### Setup Fonksiyonu

- Seri iletişimi başlatır (9600 baud)
- ADXL345 modülünü başlatır
- Hata kontrolü yapar

### Loop Fonksiyonu

- Her 500ms'de bir ivme verilerini okur
- X, Y, Z eksenlerindeki ivme değerlerini seri porta yazdırır
- Birim: m/s² (metre/saniye²)

---

## 🐛 Sorun Giderme

### ADXL345 Bulunamadı Hatası

**Sorun:** "ADXL345 bulunamadı!" mesajı görünüyor

**Çözümler:**
- I2C bağlantılarını kontrol edin (SDA, SCL)
- Güç bağlantısını kontrol edin (VCC, GND)
- Pull-up dirençlerinin olduğundan emin olun (genellikle modülde mevcuttur)
- I2C adresini kontrol edin (varsayılan: 0x53)

### Veri Okunmuyor

**Sorun:** Seri portta veri görünmüyor

**Çözümler:**
- Serial Monitor baud hızını 9600 olarak ayarlayın
- Arduino'nun doğru portta olduğundan emin olun
- Kodu tekrar yükleyin

### Yanlış Değerler

**Sorun:** İvme değerleri beklenen aralıkta değil

**Çözümler:**
- Sensörün düz bir yüzeyde olduğundan emin olun
- Kalibrasyon gerekebilir
- Sensör aralığını kontrol edin (±2g, ±4g, ±8g, ±16g)

---

## 📚 Ek Kaynaklar

- [ADXL345 Datasheet](https://www.analog.com/media/en/technical-documentation/data-sheets/ADXL345.pdf)
- [Adafruit ADXL345 Kütüphanesi](https://github.com/adafruit/Adafruit_ADXL345)
- [Arduino I2C Kılavuzu](https://www.arduino.cc/en/Reference/Wire)

---

## 🤝 Katkıda Bulunma

Katkılarınızı bekliyoruz! Lütfen:

1. Fork yapın
2. Feature branch oluşturun (`git checkout -b feature/AmazingFeature`)
3. Değişikliklerinizi commit edin (`git commit -m 'Add some AmazingFeature'`)
4. Branch'inizi push edin (`git push origin feature/AmazingFeature`)
5. Pull Request açın

---

## 📝 Versiyon Geçmişi

### v1.0.0
- İlk sürüm
- Temel ivme ölçümü
- Seri port çıktısı

---

## 📄 Lisans

Bu proje MIT lisansı altında lisanslanmıştır.

---

## 👤 Yazar

**serialprint**
- GitHub: [@serialprint](https://github.com/serialprint)

---

<div align="center">

**⭐ Beğendiyseniz yıldız vermeyi unutmayın! ⭐**

Made with ❤️ by serialprint

</div>
