MAC Vendor Analiz Sistemi, ağ üzerindeki cihazların MAC adreslerini analiz ederek üreticilerini belirleyen, cihaz türlerini sınıflandıran ve potansiyel güvenlik tehditlerini tespit eden bir sistemdir. Bu proje, ağ yöneticileri ve güvenlik uzmanlarına ağdaki bilinmeyen veya şüpheli cihazları belirleme konusunda yardımcı olmayı amaçlamaktadır.

2. Projenin Amacı ve Kapsamı

Amaç:

Ağdaki cihazların üreticilerini belirleyerek, ağın güvenliğini artırmak.

Bilinmeyen veya sahte MAC adreslerini tespit ederek güvenlik tehditlerini engellemek.

Ağ yöneticilerine detaylı analiz ve raporlama sağlayarak ağ yönetimini kolaylaştırmak.

Kapsam:

Yerel ağdaki cihazların MAC adreslerini toplamak ve analiz etmek.

Güncel IEEE OUI (Organizationally Unique Identifier) veritabanı ile eşleştirerek üretici bilgilerini çıkarmak.

Şüpheli ve sahte MAC adreslerini belirlemek.

Ağ cihazlarını kategorize ederek IoT cihazları, ağ ekipmanları, mobil cihazlar vb. olarak sınıflandırmak.

Kullanıcıya detaylı analiz ve raporlama sunmak.

3. Çözülen Güvenlik Problemi

Ağ güvenliği açısından, sahte veya bilinmeyen cihazların tespit edilmesi oldukça kritiktir. Bu proje:

Sahte MAC adreslerini tespit ederek, kötü niyetli cihazların ağ üzerinde kimlik sahtekarlığı yapmasını engeller.

Yetkisiz cihazları belirleyerek, ağda izinsiz cihazların olup olmadığını kontrol eder.

IoT cihaz güvenliğini artırarak, üretici bazlı güvenlik açıklarını analiz etmeye yardımcı olur.

Ağ envanter yönetimini kolaylaştırarak, bilinmeyen cihazların izlenmesini sağlar.

4. Hedef Kitle ve Kullanım Alanları

Hedef Kitle:

Ağ güvenlik uzmanları

Sistem yöneticileri

IT departmanları

Siber güvenlik analistleri

Ağ yöneticileri

Kullanım Alanları:

Kurumsal Şirketler: Ağlarındaki cihazları analiz ederek güvenlik risklerini azaltabilirler.

Veri Merkezleri: Ağ envanter yönetimi ve güvenlik kontrolü için kullanılabilir.

Üniversiteler ve Eğitim Kurumları: Ağdaki cihazları tespit ederek, yetkisiz erişimleri engelleyebilirler.

Hassas Ağlara Sahip Kurumlar: (Banka, devlet kurumları vb.) Yetkisiz cihazların ağ erişimini kısıtlamak için kullanılabilir.

Bireysel Kullanıcılar: Kendi ev ağlarında şüpheli cihazları kontrol edebilirler.

5. Teknik Gereksinimler

Kullanılan Programlama Dili:

Python 3.8+

Gerekli Kütüphaneler ve Sürümleri:

scapy (>=2.4.5) → Ağ trafiği analiz etmek için

requests (>=2.26.0) → Güncel OUI verilerini çekmek için

pandas (>=1.3.3) → Verileri analiz etmek ve raporlamak için

argparse (>=1.4.0) → Komut satırı parametrelerini almak için

sqlite3 → Verileri saklamak için

Çalışma Ortamı Gereksinimleri:

İşletim Sistemi: Windows, macOS veya Linux

Bağlantı Gereksinimi: OUI veritabanını güncellemek için internet erişimi

Gerekli Yetkiler: Ağ taraması için yönetici (root) yetkileri gerekebilir

Ek Araçlar:

nmap (opsiyonel, daha derinlemesine ağ taraması için)

arp-scan (opsiyonel, ARP tabanlı taramalar için)

Bu sistem, ağ güvenliğini sağlamak ve bilinmeyen cihazları tespit etmek için etkili bir analiz aracı sunmaktadır.

6. Kurulum Talimatları

1. Python Kurulumu

Python'un en az 3.8 sürümünün yüklü olduğundan emin olun. Eğer yüklü değilse, Python Resmi Sitesi üzerinden yükleyebilirsiniz.

2. Gerekli Kütüphanelerin Yüklenmesi

Aşağıdaki komutları kullanarak gerekli kütüphaneleri yükleyin:

pip install scapy requests pandas argparse sqlite3

3. Ek Araçların Kurulumu (Opsiyonel)

Eğer nmap veya arp-scan kullanmak istiyorsanız, aşağıdaki komutları çalıştırarak yükleyebilirsiniz:

Linux İçin:

sudo apt update && sudo apt install nmap arp-scan

macOS İçin:

brew install nmap arp-scan

Windows İçin:

Nmap Download adresinden indirip kurabilirsiniz.

arp-scan doğrudan Windows için mevcut değildir, ancak bir Linux alt sistemi (WSL) kullanarak çalıştırabilirsiniz.

4. Uygulamanın Çalıştırılması

python mac_vendor_analiz.py --mac_adresi 44:38:39:ff:ef:57 --detayli_analiz True

Bu komut, belirtilen MAC adresi için analiz yapacak ve detaylı analiz seçeneği aktif hale gelecektir.

API Endpoint: GET /api/vendor/{mac_address}
Açıklama: Bu endpoint, kullanıcıdan bir MAC adresi alır ve bu adresin hangi cihaza ait olduğunu ve üreticisini döndürür.

Örnek JSON Yanıtı:
json
{
  "mac_address": "00:14:22:01:23:45",
  "vendor": {
    "name": "Cisco Systems, Inc.",
    "address": "170 West Tasman Dr., San Jose, CA 95134-1706",
    "country": "US",
    "phone": "+1-800-553-6387",
    "website": "https://www.cisco.com"
  },
  "device": {
    "type": "Router",
    "model": "Cisco ISR 4000",
    "serial_number": "1234567890ABC",
    "release_date": "2016-05-15"
  },
  "mac_details": {
    "assigned": "Yes",
    "block_start": "00:14:22",
    "block_end": "00:14:22",
    "organization": "Cisco"
  }
}
Diğer Olası Yanıtlar:
1. Geçersiz MAC Adresi:
Eğer geçerli bir MAC adresi verilmezse, API bir hata mesajı döndürebilir.

Örnek Yanıt:

json
Kopyala
Düzenle
{
  "error": "Invalid MAC address format",
  "message": "Please provide a valid MAC address"
}
2. Bilinmeyen Üretici:
Eğer MAC adresi veritabanında bulunmazsa, API şu şekilde bir yanıt verebilir:

Örnek Yanıt:

json
{
  "mac_address": "00:00:00:00:00:00",
  "error": "Vendor not found",
  "message": "No vendor information found for the provided MAC address"
}
API Kullanım Senaryoları:
MAC Adresi ile Cihaz Tanımlama: Kullanıcılar, bir cihazın MAC adresini vererek üretici bilgisini öğrenebilirler.
Cihaz Türü Bilgisi: Kullanıcılar, cihazın türünü (örneğin router, laptop) öğrenebilirler.
Vendor Veritabanı: Bu API, bir cihazın üretici bilgilerini sağlayarak donanım envanteri yönetimi veya güvenlik analizleri gibi uygulamalarda kullanılabilir.

2320191060-BERKAN ADAR
