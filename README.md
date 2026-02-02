👤 Geliştirici

Volkan Özdemir
Elektrik-Elektronik Mühendisliği Öğrencisi

🔗 GitHub: https://github.com/Wolynx

🔗 LinkedIn: https://www.linkedin.com/in/ozdemirvolkantech

# Arduino + Python Yüz Takipli Servo Kontrol Sistemi

Bu proje, kamera görüntüsünden yüz algılayarak iki eksenli (X–Y)
servo motorları gerçek zamanlı olarak kontrol eden bir sistemdir.
Görüntü işleme Python (OpenCV) tarafında yapılır, hesaplanan açılar
seri haberleşme üzerinden Arduino’ya gönderilir.

Proje; gömülü sistemler, bilgisayarlı görü ve donanım–yazılım
entegrasyonunu birlikte kullanmayı amaçlamaktadır.

---

## 🎯 Proje Özeti
- Gerçek zamanlı yüz algılama (OpenCV)
- Arduino üzerinden servo motor kontrolü
- Seri haberleşme (UART)
- Yumuşak ve titreşimsiz servo hareketi (smoothing)
- İki eksenli pan–tilt kontrol sistemi

---

## 🧩 Sistem Mimarisi

- Python tarafı yüz algılama ve açı hesaplamasını yapar  
- Hesaplanan X,Y açıları seri porttan Arduino’ya gönderilir  
- Arduino servo motorları kontrol eder

---

## 🛠️ Kullanılan Donanımlar
- Arduino (UNO / Nano vb.)
- 2× Servo Motor (X–Y ekseni)
- USB Kamera
- Harici 5V güç kaynağı (servo motorlar için önerilir)

---

## 🔌 Pin Bağlantıları

| Bileşen | Arduino Pin |
|------|-------------|
| X Ekseni Servo | D9 |
| Y Ekseni Servo | D10 |

⚠️ **Önemli:**
- Servo motorların **GND (kahverengi)** ve **VCC (kırmızı)** uçları ortak olmalıdır  
- Servo motorlar için harici besleme kullanılması önerilir

---

## 🧠 Yazılım Yapısı

### Arduino Tarafı
- Seri porttan gelen `X,Y` formatındaki verileri okur
- Servo açılarını 0–180° aralığında sınırlar
- Servo motorları gerçek zamanlı olarak kontrol eder
- Başlangıçta servo motorları orta konuma getirir

### Python Tarafı
- OpenCV ile yüz algılama (Haar Cascade)
- Yüz konumuna göre servo açılarını hesaplama
- Ani hareketleri önlemek için yumuşatma (smoothing)
- Arduino ile seri haberleşme
- Gerçek zamanlı görüntü ve FPS gösterimi

---

## 📚 Kullanılan Kütüphaneler

### Arduino
- Servo.h

### Python
- OpenCV (cv2)
- PySerial
- NumPy

---

## ⚙️ Ayarlar (Python)

```python
SERIAL_PORT = 'COMX'
BAUD_RATE = 115200
CAMERA_ID = 0
RESOLUTION = (640, 480)
SMOOTHING_FACTOR = 0.25
