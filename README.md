# Arduino-ADXL345
Merhaba! Bu Arduino kodu, ADXL345 ivmeölçer modülünü kullanarak üç eksenli ivme verilerini okuyup seri port aracılığıyla görüntülemeyi sağlar.

1. İlk olarak, gerekli kütüphaneleri içe aktarıyoruz. Wire kütüphanesi I2C iletişimi için, Adafruit_Sensor ve Adafruit_ADXL345_U kütüphaneleri ise ivmeölçerimizi kullanmak için gereklidir.

2. 'accel' adında bir Adafruit_ADXL345_Unified nesnesi oluşturuyoruz. Bu nesne, ADXL345 modülünü temsil eder. 12345, cihazın I2C adresidir.

3. 'setup' fonksiyonunda seri iletişimi başlatıyoruz (9600 baud). Ardından ADXL345'ü başlatmaya çalışıyoruz. Eğer başlatma işlemi başarısız olursa, seri port aracılığıyla bir hata mesajı gösterip programı sonsuz bir döngüye sokarak durduruyoruz.

4. 'loop' fonksiyonunda ivme verilerini okuyup seri port aracılığıyla görüntülüyoruz. 'sensors_event_t' türünde bir yapı oluşturarak ivme verilerini bu yapıya atıyoruz. Sonra X, Y ve Z ivmelerini seri port üzerinden gösteriyoruz. Her döngüde 0.5 saniye bekliyoruz.

Bu kodu yüklediğinizde, ADXL345 modülünün üç eksenli ivme verilerini seri monitörde gözlemleyebilirsiniz. Eğlenceli projelerde kullanmanızı dileriz! 🚀💡🔌
