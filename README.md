<img width="1033" height="117" alt="Ekran görüntüsü 2026-11-04 163103" src="https://github.com/user-attachments/assets/802d14e2-8396-4f0b-93ef-69346f476f49" />
<img width="1486" height="626" alt="Ekran görüntüsü 2026-11-04 164600" src="https://github.com/user-attachments/assets/6858f3b9-e903-4583-bd76-a6f28cbe3d0c" />
<img width="940" height="633" alt="Ekran görüntüsü 2026-11-04 163210" src="https://github.com/user-attachments/assets/25ee8163-086c-41c5-a1d1-ba45aa925065" />
<img width="870" height="386" alt="image" src="https://github.com/user-attachments/assets/bc385adb-fb6a-462c-811f-8654700ed1ff" />
<img width="1511" height="599" alt="image" src="https://github.com/user-attachments/assets/968652a2-db1f-4bf7-95af-3661450350a0" />
<img width="518" height="697" alt="image" src="https://github.com/user-attachments/assets/66b9a993-968e-454d-a9ba-df004d65fdc7" />
<img width="570" height="459" alt="image" src="https://github.com/user-attachments/assets/aed4782b-7a36-4faf-8482-826e3c03fe53" />
<img width="750" height="589" alt="image" src="https://github.com/user-attachments/assets/0040a8dc-137c-4187-90ab-0b16a47e0dd9" />
<img width="1436" height="622" alt="image" src="https://github.com/user-attachments/assets/92747f3c-90f8-4f70-bac4-30bda66b8e27" />
<img width="1181" height="690" alt="Ekran görüntüsü 2026-11-04 163252" src="https://github.com/user-attachments/assets/c923f98d-6e4c-4c4c-abb3-6a8268f780fd" />
<img width="1178" height="647" alt="Ekran görüntüsü 2026-11-04 163404" src="https://github.com/user-attachments/assets/e7f0ce0a-f1d6-46ee-855f-592746fce5c4" />
<img width="1151" height="415" alt="Ekran görüntüsü 2026-11-04 163424" src="https://github.com/user-attachments/assets/f1d654d4-3d68-4f11-832c-c8a4ff011996" />



# e-Devlet Simülasyonu ve Yetkilendirme Sistemi (Mockup Projesi)

> **Not:** Bu depo yalnızca proje vitrinidir. Kaynak kodlar paylaşılmamaktadır.

---

## Projenin Amacı ve Çözüm Ürettiği Gerçek Hayat Senaryoları

Günümüzde vatandaşlar; hukuki, mali veya idari işlemleri için avukatlar, muhasebeciler, işverenler veya danışmanlarla resmi evrak paylaşmak durumunda kalmaktadır.

Mevcut sistemde bu işlem genellikle **e-Devlet şifresinin doğrudan karşı tarafla paylaşılması** yoluyla yapılmaktadır. Şifre paylaşımı, ilgili kişiye sadece istenen belgeyi değil; sağlık verilerinden tapu bilgilerine, vergi borçlarından nüfus kayıtlarına kadar kişinin tüm dijital varlığına sınırsız ve kontrolsüz bir erişim hakkı vermektedir. Bu durum, veri mahremiyeti ve kişisel bilgi güvenliği açısından devasa bir güvenlik açığı yaratmaktadır.

Bu proje, tam da bu **somut ve güncel sorunu çözmek** amacıyla geliştirilmiş bir "Kısıtlı Yetkilendirme Mimarisidir". Temel hedef, kullanıcıların **şifrelerini asla kimseyle paylaşmak zorunda kalmadan**, işlemlerini güvenle halledebilmelerini sağlamaktır.

Geliştirilen bu simülasyon, standart bir web uygulamasının ötesine geçerek şu hedefleri gerçekleştirir:

- **Şifresiz e-Veri Paylaşımı:** Ana kullanıcının, kendi profilinden 3. şahıslara sadece gerekli modül için özel bir "Yetki Kodu" üretebilmesi.
- **Kademeli Erişim Yönetimi (Role-Based Access Control):** Şifreyi bilen ana kullanıcı ile yetki kodunu bilen misafir kullanıcı arasındaki sınırların net çizilmesi.
- **Şeffaflık ve İzlenebilirlik:** Hangi belgenin, kim tarafından, ne zaman görüntülendiğinin kayıt altına alınarak sistemde tam bir denetim izi (audit trail) bırakılması.

---

## Kullanılan Teknolojiler (Tech Stack)

- **Backend:** Python, Flask Framework
- **Frontend:** HTML5, CSS3, JavaScript (e-Devlet UI konseptine sadık kalınarak tasarlanmış şablonlar)
- **Veritabanı:** SQLite
- **Güvenlik / Entegrasyonlar:** `qrcode`, `pyotp` (2FA), Algoritmik TCKN Doğrulama, Brute-Force (IP Ban) Koruması
- **Geliştirme Araçları:** Visual Studio Code, DB Browser for SQLite

---

## Temel Özellikler ve Modüller

### 1. Dinamik Yetkilendirme ve Misafir Erişimi (Ana Çözüm Modülü)

- **Yetki Kodu Jeneratörü:** Kullanıcılar şifrelerini vermek yerine, süreli ve hizmet bazlı (belirli bir evraka özel) yetki kodları oluşturabilir.
- **İzole Edilmiş Misafir Paneli:** Misafirler ana portala erişemez; sadece yetkilendirildikleri kısıtlı arayüze yönlendirilir.
- **Temsilci İşlem Onayı (Real-Time İzin):** Misafir belgeyi açmak istediğinde ana kullanıcının ekranına anlık bir onay bildirimi düşer; onay verilmeden veri aktarımı gerçekleşmez.

### 2. İleri Seviye Kimlik Doğrulama ve Güvenlik

- **Algoritmik TCKN Kontrolü:** 11 hane ve tek/çift hane matematiksel formülleriyle backend tabanlı doğrulama.
- **İki Aşamalı Doğrulama (2FA):** Google Authenticator entegrasyonu ile TOTP tabanlı dinamik kod doğrulama.
- **Brute-Force Koruması (IP Ban):** Art arda hatalı girişlerde IP adresinin 15 dakika süreyle sisteme engellenmesi.

### 3. Sistem Loglama ve Denetim İzi (Audit Trail)

- Başarılı/başarısız oturumlar, yetki kodu hareketleri ve evrak görüntüleme eylemleri IP ve zaman damgasıyla loglanır.

---

## 📌 Proje Durumu ve Güvenlik Notu

- Bu deponun amacı, geliştirilen **Kısıtlı Yetkilendirme Mimarisinin** mimari yapısını ve vizyonunu sergilemektir.
- Güvenlik ve veri mahremiyeti ilkeleri gereği **kaynak kodlar ve veritabanı şablonu bu vitrin deposunda yer almamaktadır**; tüm geliştirme süreci ayrı ve gizli (Private) bir depoda yürütülmektedir.

---

## ⚠️ Yasal Uyarı ve Sorumluluk Reddi

> Bu yazılım projesi; veri mahremiyeti, algoritma geliştirme ve sistem güvenliği (PoC - Konsept İspatı) konularında pratik yapmak amacıyla tasarlanmış bağımsız, yerel bir simülasyondur.

- Projenin Türkiye Cumhuriyeti kurumları veya resmi e-Devlet Kapısı ile hiçbir idari, resmi veya teknolojik bağı **bulunmamaktadır**.
- Oltalama (phishing), veri hırsızlığı veya herhangi bir kötü niyetli faaliyet amacıyla kullanılamaz.
