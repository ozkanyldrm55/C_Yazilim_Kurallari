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

**Örnek:**
```c
static void process_data_buffer(void);
static int calculate_checksum(const uint8_t* data, size_t length);
```

## 3. Sihirli Sayılar (Magic Numbers) Kullanılmamalı

- Anlam ifade etmeyen sabit sayılar yerine `#define` veya `const` kullanılarak açıklayıcı isimler verilmelidir.
  ```c
  #define MAX_RETRY_COUNT 3
  ```

## 4. Açıklayıcı Yorumlar ve Fonksiyon Başlıkları

- Her fonksiyon, ne yaptığı, parametreleri ve dönüş değeri ile birlikte kısa bir açıklama içermelidir.
  ```c
  /**
   * @brief  Sensörden veri okur.
   * @param  sensorID: Okunacak sensörün ID'si
   * @retval Okunan veri
   */
  int read_sensor_data(uint8_t sensorId);
  ```
  
## 5. `const` Kullanımı

- Değişmeyecek parametreler ve göstericiler için `const` kullanılmalıdır.
  ```c
  void set_speed(const int maxSpeed, int currentSpeed) {
    // maxSpeed = 100;  // ❌ Hatalı kullanım: const değişken değiştirilemez
    currentSpeed = 50;  // ✅ Geçerli: currentSpeed değiştirilebilir

    printf("Max: %d, Current: %d\n", maxSpeed, currentSpeed);
}
  ```

> 📌 Bu kurallar sürekli olarak güncellenebilir.

