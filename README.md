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

> 📌 Bu kurallar sürekli olarak güncellenebilir. Lütfen yeni bir kural öneriniz varsa proje yöneticisine bildirin veya bir Pull Request oluşturun.

