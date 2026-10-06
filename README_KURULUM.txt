YDS KELİME PWA v4 — KULLANICI ADI + ŞİFRE
===========================================

Bu sürümde kullanıcı ekranda SADECE kullanıcı adı ve şifre görür.
Ad-soyad, telefon ve e-posta istenmez.

ÖNEMLİ: GitHub Pages tek başına kullanıcı hesabı saklayamaz. Bu nedenle
ücretsiz Firebase Authentication + Firestore kullanılıyor. Uygulama, Firebase'in
e-posta/şifre motorunu teknik olarak kullanır ama kullanıcıdan gerçek e-posta
almaz. Kullanıcı adı arka planda yds_KULLANICIADI@yds-user.invalid biçiminde
teknik bir kimliğe çevrilir; bu adres kullanıcıya gösterilmez ve gerçek e-posta değildir.

5 DAKİKALIK KURULUM
-------------------
1) https://console.firebase.google.com/ adresinde yeni proje oluştur.
2) Build > Authentication > Get started > Sign-in method bölümünde
   "Email/Password" yöntemini etkinleştir. E-posta doğrulaması açmana gerek yok.
3) Build > Firestore Database > Create database.
4) Firestore > Rules ekranına paketteki firestore.rules içeriğini yapıştır ve Publish.
5) Project settings (dişli) > Your apps > Web app (</>) oluştur.
6) Verilen firebaseConfig değerlerini firebase-config.js dosyasına yapıştır.
7) Bu klasördeki TÜM dosyaları GitHub deponun köküne yükle.
8) Settings > Pages > Deploy from a branch > main / root seç.

GİRİŞ
-----
Kullanıcı adı: 3-24 karakter. Türkçe karakter girilirse otomatik sadeleştirilir.
Şifre: en az 6 karakter.

Her kullanıcının şu verileri ayrı tutulur:
- XP ve seviye
- günlük hedef ve seri
- rozetler
- öğrendim / tekrar listesi
- son bölüm ve sayfa
- swipe ilerlemesi

Eski v3 ilerlemesi ilk girişte bulunursa uygulama bunu yeni hesaba aktarmayı sorar.

ŞİFRE UNUTULURSA
----------------
Gerçek e-posta veya telefon alınmadığı için otomatik "şifremi unuttum" yoktur.
Kullanıcı giriş yaptıktan sonra menüden şifresini değiştirebilir. Şifreyi tamamen
unutan kullanıcı için daha sonra yönetici reset sistemi eklenebilir.

GÜVENLİK
--------
Firestore kuralları kullanıcıların sadece kendi /users/{uid}/state kayıtlarını
okuyup yazmasına izin verir. Firebase config dosyası gizli anahtar değildir; güvenlik
Firestore Rules ve Authentication ile sağlanır.
