# C Yazılım Kuralları

Bu doküman, projede kullanılan C diline özel yazılım geliştirme kurallarını tanımlar. Kodun okunabilirliğini, sürdürülebilirliğini ve ekip içinde tutarlılığı artırmak amacıyla hazırlanmıştır.

---

## 1. İsimlendirme Kuralları

- **Global değişkenler** büyük harfle başlamalıdır ve `camelCase` biçiminde yazılmalıdır.  
  **Örnek:**  
  ```c
  int SystemStatus;
  bool DeviceMode;
  ```

- **Lokal değişkenler** küçük harfle başlamalıdır ve yine `camelCase` stilinde yazılmalıdır.  
  **Örnek:**  
  ```c
  int tempValue;
  uint8_t loopIndex;
  ```

- **Fonksiyon isimleri**, işlemi belirten fiillerle başlamalı ve `snake_case` stilinde yazılmalıdır.  
  **Örnek:**  
  ```c
  void read_sensor_data(void);
  bool init_uart_driver(void);
  ```

---

## 2. Fonksiyon Tanımlama – `static` Kullanımı

- Aynı dosya içinde kullanılacak yardımcı fonksiyonlar tanımlanırken `static` anahtar kelimesi eklenmelidir.
- Bu yaklaşım:
  - Erişim kapsamını kısıtlar,
  - Kodun modülerliğini artırır,
  - Sembol çakışmalarını önler.

**Örnek:**
```c
static void process_data_buffer(void);
static int calculate_checksum(const uint8_t* data, size_t length);
```

---

## 3. Dosya Yapısı ve Bölümleme

- Her `.c` dosyasının ilişkili bir `.h` başlık dosyası olmalıdır.
- Başlık dosyaları **çift tırnak ("") ile**, sistem kütüphaneleri **açılı parantez (<>) ile** include edilmelidir.
- Include sırası: kendi header → bağımlı local header'lar → sistem kütüphaneleri.

## 4. Header Guard Kullanımı

- Her `.h` dosyasında **include guard** veya `#pragma once` kullanılmalıdır:
  ```c
  #ifndef MY_MODULE_H
  #define MY_MODULE_H

  // Declarations

  #endif // MY_MODULE_H
  ```

## 5. Sihirli Sayılar (Magic Numbers) Kullanılmamalı

- Anlam ifade etmeyen sabit sayılar yerine `#define` veya `const` kullanılarak açıklayıcı isimler verilmelidir.
  ```c
  #define MAX_RETRY_COUNT 3
  ```

## 6. Açıklayıcı Yorumlar ve Fonksiyon Başlıkları

- Her fonksiyon, ne yaptığı, parametreleri ve dönüş değeri ile birlikte kısa bir açıklama içermelidir.
  ```c
  /**
   * @brief  Sensörden veri okur.
   * @param  sensorID: Okunacak sensörün ID'si
   * @retval Okunan veri
   */
  int read_sensor_data(uint8_t sensorID);
  ```

## 7. `typedef` ile Struct Kullanımı

- `typedef struct` ile tanımlanan yapılar kısa ve anlamlı adlarla kullanılmalıdır.
  ```c
  typedef struct {
      uint8_t id;
      float temperature;
  } SensorData_t;
  ```

## 8. `const` Kullanımı

- Değişmeyecek parametreler ve göstericiler için `const` kullanılmalıdır.
  ```c
  void send_data(const uint8_t* buffer, size_t length);
  ```

## 9. Boşluk ve Girinti Standartları

- Kod girintisi **4 boşluk** veya proje standardı neyse o şekilde olmalıdır (tab yerine boşluk tercih edilir).
- Her `if`, `while`, `for`, `else` bloğu süslü parantez `{}` ile yazılmalıdır, tek satır olsa bile.

---

> 📌 Bu kurallar sürekli olarak güncellenebilir. Lütfen yeni bir kural öneriniz varsa proje yöneticisine bildirin veya bir Pull Request oluşturun.

