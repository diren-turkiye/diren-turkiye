# SANSÜRLE MÜCADELE REHBERİ

## VPN nedir? Ne işe yarar?

Normalde bir internet servis sağlayıcı (İSS), internet trafiğinizi. HTTPS gibi şifreleme protokolleri internette yaygın olarak kullanıldığı için ne yazdığınız veya okuduğunuzu tam olarak göremeseler de eriştiğiniz siteler hakkında bir fikir edinebilirler. Bu şekilde, devletler sansür uygulamaktadır.

VPN kullanarak, ilk olarak başka bir ülkedeki bir sunucuya, ardından bağlanmak istediğiniz yere bağlanabilirsiniz. Bu şekilde İSS'niz yalnızca bir VPN'e bağlı olduğunuzu görür ve içeriği hakkında bilgi edinemez. Bu şekilde devletler inernete erişiminizi sansürleyemez.

## Önerilen VPNler listesi

1) **ProtonVPN (ücretsiz:)** [Android: Google Play Store](https://play.google.com/store/apps/details?id=ch.protonvpn.android&hl=tr), [iOS: App Store](https://apps.apple.com/tr/app/proton-vpn-fast-secure/id1437005085), [macOS](https://github.com/ProtonVPN/ios-mac-app/releases), [Windows](https://github.com/ProtonVPN/win-app/releases)

- Eğer uygulama Google Play Store'dan kaldırılırsa Proton VPN'in [GitHub reposundan](https://github.com/ProtonVPN/android-app/releases) da indirilebilir. 
- Proton VPN'i kullanırken, ilk olarak "Connect" tuşuna basarak bağlanmayı deneyin. Eğer bu başarısız olursa, Settings -> Protocol -> Stealth seçeneğini seçtikten sonra bağlanmayı deneyin. Bu özellik, VPN bağlantınızı gizlemeye çalışacaktır.

- Eğer bu da çalışmaz ise, Settings -> Advanced Settings -> Alternative routing'i açıp deneyin.

2) **Mullvad (ücretli):** [Android: Google Play Store](https://play.google.com/store/apps/details?id=net.mullvad.mullvadvpn), [Android: F-Droid](https://f-droid.org/tr/packages/net.mullvad.mullvadvpn/), [iOS: App Store](https://apps.apple.com/tr/app/mullvad-vpn/id1488466513), [macOS](https://github.com/mullvad/mullvadvpn-app/releases/download/2025.4/MullvadVPN-2025.4.exe),  [Windows](https://github.com/mullvad/mullvadvpn-app/releases/download/2025.4/MullvadVPN-2025.4.exe)

- Eğer bağlantı kuramazsanız, sağ üstteki dişli çark ikonuna tıklayıp ayarlara girin ve "VPN Settings" -> "WireGuard obfuscation" altından "UDP-over-TCP" seçeneğini seçin. Bu da başarısız olursa aynı menü altındaki "Shadowsocks" seçeneğini kullanmayı deneyebilirsiniz.

## DNS over HTTPS / DNS over TLS

### DNS nedir?

DNS servisleri, bir web sitesini ziyaret etmek istediğinizde, o alan adını IP adresine dönüştüren servislerdir. Örneğin `wikipedia.org`'u ziyaret etmek istediğinizde size `185.15.58.224` IP adresini verecektir.

DNS servisleri, genelde sisteminizin varsayılan ayarlarında şifresiz olarak çalışacaktır. Bu demektir ki, İSS'niz sizin erişmek istediğiniz siteler için yaptğınız DNS isteklerini görebilecek ve bu şekilde sansür veya gözetim uygulayabilecektir.

DNS over HTTP veya DNS over TLS gibi Şifrelenmiş DNS protokolleri kullanarak bu problem çözülebilir ve sansür ile gözetim daha zor bir hale getirilebilir.

**Not: Şifreli DNS servisleri kullanmak, VPNlerin aksine eriştiğiniz IP adresini İSS'nizden saklamayacaktır. Girilen sitelerin gizli kalması için VPNlerin yerine KULLANILMAMALIDIR. Sansür ve gözetimi zorlaştırmak için tek başına veya VPN'e ek olarak kullanımını tavsiye ediyoruz.**

#### Android

Eğer telefoununuz Android 9 ve üzeri ise aşağıdaki adımları izleyerek DNS over TLS'i aktif hale getirebilirsiniz:

1. Ayarlar -> Ağ ve İnternet -> Gelişmiş -> Gizli DNS'e tıklayın.
1. "Gizli DNS sağlayıcının ana makine adı" seçeneğini etkin hale getirin ve aşağıdaki alan adlarından birini girin:
    - `dns.quad9.net`
    - `dns.mullvad.net`
    - `one.one.one.one`

#### iOS

1. [Quad9 web sitesinden](https://docs.quad9.net/Setup_Guides/iOS/iOS_14_and_later_%28Encrypted%29/) DNS profilini indirin. Bunu "Download Profile" bölümü altındaki "Recommended: HTTPS (.9)" tuşuna basarak yapabilirsiniz.
1. Telefonunuzdaki Dosyalar uygulamasına gidin, ekranın en alt kısmındaki "Göz At" tuşuna tıklayın ve İndirilenler klasörüne girin. Bu klasörde, indirdiğiniz "Quad9...mobileconfig" dosyasına tıklayın.
1. Ayarlar -> Profil İndirildi seçeneğine tıklayın -> Sağ üst köşedeki yükle tuşuna basın.


#### Windows 11

1. Başlat düğmesine sağ tıklayın ve Ayarlar butonunu seçin -> Soldaki menüden "Ağ ve internet"'i seçin -> Eğer kablosuz internet ile bağlıysanız "Wi-Fi" seçeneğine, kablolu internet ile bağlıysanız "Ethernet" seçeneğine tıklayın.
1. “DNS sunucusu ataması”nın yanındaki ”Düzenle” tuşuna tıklayın -> Menüden "El ile girilen" seçeneğini seçin -> IPv4'ü açın ve aşağıdaki değişiklikleri yapın.

    - Tercih edilen DNS: 9.9.9.9 (Eğer olmazsa: 194.242.2.2)
    - HTTPS üzerinden DNS: Açık (otomatik şablon)
    - Altetnatif DNS: 149.112.112.112 (Eğer olmazsa: 1.1.1.1)
    - HTTP üzerinden DNS: Açık (otomatik şablo)


#### macOS (Big Sur ve sonrası)

1. [Quad9 web sitesinden](https://docs.quad9.net/Setup_Guides/MacOS/Big_Sur_and_later_%28Encrypted%29/) DNS profilini indirin. Bunu "Download Profile" bölümü altındaki "Recommended: HTTPS (.9)" tuşuna basarak yapabilirsiniz.
1. İndirilenler klasörüne gidin, ve indirdiğiniz "Quad9...mobileconfig" dosyasına tıklayın.
1. Sistem Tercihleri -> Profiller'e tıklayın > Sağ üst köşedeki yükle tuşuna basın.

## Tor

**Uyarı: Eğer Tor kullanacaksanız köprüleri etkinleştirdiğinizden emin olun. Aksi takdirde İSS'niz, Tor kullandığınızı kolayca tespit edebilir. Köprü kullansanız dahi, İSS'niz çeşitli trafik analizi teknikleriyle Tor kullandığınızı tespit edebilir ve bu ekstra dikkat çekebilir.**

Köprüleri etkinleştirmek için aşağıdaki adımları takip edin:

Tor Browser: Tor Browser'ı açtıktan sonra Bağlantıyı yapılandır tuşuna basın ve "Köprüler kullanılsın" seçeneğini etkinleştirin. Eğer varsayılan köprüler çalışmıyorsa "Köprüler isteyin" tuşu ile veya [Tor'un Telegram botuyla](https://t.me/GetBridgesBot) yeni köprü adresleri alabilirsiniz.

Orbot: Orbot'u açtıktan sonra "Nasil bağlanılacağını seç" tuşuna basın ve "Tor'dan köprü (Obfs4)" seçeneğini seçip "Sonraki" tuşuna girin ve ekrandaki karakterleri girdikten sonra Bağlan tuşuna basın.

- Tor Browser:  [Android: Google Play Store](https://play.google.com/store/apps/details?id=org.torproject.torbrowser&hl=tr), [Windows, macOS, Linux, Android: Tor web sitesi](https://www.torproject.org/tr/download/)
- Orbot: [Android: Google Play Store](https://play.google.com/store/apps/details?id=org.torproject.android&hl=tr), [iOS, macOS: App Store](https://apps.apple.com/us/app/orbot/id1609461599?platform=iphone)

Tor Browser, trafiğinizi Tor ağından geçiren bir tarayıcıyken Orbot, cihazınızın tüm trafiğini Tor üzerinden geçirir. Bu demektir ki Orbot kullandığınızda Twitter, WhatsApp vb. gibi uygulamaları yasaklı olsa dahi kullanabilirsiniz.

Eğer VPN servislerine erişmekte zorluk çekiyorsanız Tor ağı aracılığıyla sansürü aşabilirsiniz. 

Tor üzerinden internet bağlantısı kurduğunuzda trafiğiniz, konumunuzu ve etkinliğinizi sizi izlemeye çalışanlardan gizleyen ve dünya çapındaki gönüllüler tarafından işletilen bir aktarıcı ağı üzerinden geçirilir.

**Bir sonraki rehberlerimiz için adresimizi takipte kalın!**
