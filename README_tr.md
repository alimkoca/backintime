[![Build Status](https://app.travis-ci.com/bit-team/backintime.svg?branch=master)](https://app.travis-ci.com/bit-team/backintime)
[![Coverage Status](https://coveralls.io/repos/github/bit-team/backintime/badge.svg?branch=master)](https://coveralls.io/github/bit-team/backintime?branch=master)
[![Source code documentation status](https://readthedocs.org/projects/backintime-dev/badge/?version=latest)](http://backintime.readthedocs.org/projects/backintime-dev/en/latest/?badge=latest)

# Back In Time
<sub>Kullanım hakları (C) 2008-2022 Oprea Dan, Bart de Koning, Richard Bailey,
Germar Reitze, Taylor Raack<sub>
 
Back-In-Time dosyaları ve klasörleri yedeklemek için kullanılan basit bir yedekleme aracıdır.
Back-In-Time GNU/Linux işletim sistemi üzerinde çalışır ve ikisi de Python3 üzerinde çalışan 
`backintime` ve QT5 grafiksel kullanıcı arayüzü kullanan `backintime-qt` komut satırı uygulamalarını 
size sunar.

Uygulama manuel veya planlı yedeklemeler için ve onları yerel veya SSH yoluyla uzaktan
bağlantılı olarak depolamak için `rsync` komut satırı uygulamasını kullanır. Her bir yedekleme
basitçe gerçek uygulamaların kopyasından oluşan bir klasörden oluşur, ama değişmeyen dosyalar
hafızayı verimli kullanmak için yedekleme sistemine bağlanmıştır. Ayrıca uygulamamız [FlyBack](https://en.wikipedia.org/wiki/FlyBack)
uygulamasından esinlenilmiştir.
  
Uygulamamızı rahatça kullanmanız için sadece 3 şeye ihtiyacınız var:

* Hangi dosyalarının yedekleneceğinin bilinmesi gerekir.
* Yedeklemelerin tam olarak nerede kaydedileceğinin bilinmesi gerekir.
* Yedekleme sıklığı (manuel, her saat, her gün, her ay).
  
## Geliştirilme durumu

Açıkçası bu projenin geliştirilme durumu epeyce bir süredir ölü gibiydi. Ama 2022 yazında
az kişiden oluşan bir ekip olarak projeyi yeniden harekete geçirdik. 
Bizimle kalın, çünkü ♥️ Zamanda Geriye Gitmek için doğru olana ihtiyacınız var. 😁

Şu anda yeni özellikler ekleyemesek de [genel sorunları](https://github.com/bit-team/backintime/issues?q=is%3Aissue+is%3Aopen+label%3AHigh)
halletmeye çalışıyoruz. Eğer projemize katkı sağlamak istiyorsanız [CONTRIBUTING](CONTRIBUTING.md) dosyasına bir göz atın :).
  
## Genel

- [Dokümantasyon, SSS, Destek](#documentation-faqs-support)
- [Kurulum](#installation)
- [Görülen sorunlar ve Çözümler](#known-problems-and-workarounds)
- [Projemize katkı sağlayın](CONTRIBUTING.md)

## Dokümantasyon, SSS, Destek

 * [Son kullanıcı dokümantasyonu](https://backintime.readthedocs.org/) (pek güncel değil)
 * [SSS - Sık Sorulan Sorular](FAQ.md)
 * [Geliştiriciler için kaynak kodu dokümantasyonu](https://backintime-dev.readthedocs.org)
 * [Sorunlar](https://github.com/bit-team/backintime/issues) bölümünü soru sormak ve bugları raporlamak için kullanın.
 * [Elektronik posta listesi _bit-dev_](https://mail.python.org/mailman3/lists/bit-dev.python.org/)

## Kurulum

_Back In Time_ bir çok işletim sisteminde mevcuttur ve indirmek için depolarını kullanabilirsiniz. 
Eğer projeye katkı sağlamak istiyorsanız veya _Back In Time_'ın son geliştirici sürümünü kullanıyorsanız lütfen
şuraya bir göz atın [`CONTRIBUTING.tr.md` ile kurulum](CONTRIBUTING.md#build--install). Ayrıca bağımlılıkları da
aynı yerden görebilirsiniz.

Eğer kullandığınız GNU/Linux dağıtımı _Back In Time_ için resmi bir versiyon
seçeneği sunmuyorsa lütfen bir Github üzerinde bir sorun başlığı açın ve bunu
bilmemizi sağlayın. Biz bunu yapana kadar ise aşağıda yer alan seçenekleri
kullanabilirsiniz.

### Alternatif Kurulum Seçenekleri

**Ubuntu ve Debian tabanlı dağıtımlar için PPA**

Halihazırda mevcut stabil versiyonla bir PPA (Gizli Paket Arşivi)
(`ppa:bit-team/stable`) ve test amaçlı bir PPA versiyonumuz mevcut (`ppa:bit-team/testing`).

    # "Warning: apt-key is deprecated..." uyarısını şimdilik görmezden gelebilirsiniz (#1338 numaralı konu başlığına göz atın)
    sudo add-apt-repository ppa:bit-team/stable
    sudo apt-get update
    sudo apt-get install backintime-qt

veya

    sudo add-apt-repository ppa:bit-team/testing
    sudo apt-get update
    sudo apt-get install backintime-qt

**ArchLinux**

Arch Linux için ise paketten ayrı olarak grafiksel kullanıcı arayüzünü dahil eden 
AUR [`backintime`](https://aur.archlinux.org/packages/backintime) paketimiz mevcut.

    # Ama kurulumdan önce genel anahtarı kuruluma dahil etmeniz gerekiyor.
    gpg --keyserver pgp.mit.edu --recv-keys 615F366D944B4826
    # Fingerprint: 3E70 692E E3DB 8BDD A599  1C90 615F 366D 944B 4826

    wget https://aur.archlinux.org/cgit/aur.git/snapshot/backintime.tar.gz
    tar xvzf backintime.tar.gz
    cd backintime
    makepkg -srci
