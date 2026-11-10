# Windows x64 paketleme

Bu depo Qt/C++ uygulamasının **Windows 10/11 x64** kopyasıdır. PyInstaller kullanılmaz.

GitHub deposu: `ticketgoteknoloji-web/ticketgo-izleme-windows`  
Güncelleme API: `https://api.github.com/repos/ticketgoteknoloji-web/ticketgo-izleme-windows/releases/latest`

macOS deposu (`ticketgoteknoloji-izleme-monit-r-`) ve Release varlıkları bu projeden etkilenmez.

## Gereksinimler

- Visual Studio 2022 Build Tools (MSVC)
- CMake + Ninja
- Qt 6.5+ (`win64_msvc2022_64`)
- Inno Setup 6

## Yerel derleme

```powershell
$env:QT_PREFIX = "C:\Qt\6.8.1\msvc2022_64"
.\packaging\windows\build.ps1
```

Çıktılar:

- `build-windows/TicketGoIzleme-Windows-x64-Setup.exe`
- `build-windows/TicketGoIzleme-Windows-x64-Setup.exe.sha256`
- `build-windows/TicketGoIzleme-update-manifest.json`

Kurulum yönetici gerektirmez (`PrivilegesRequired=lowest`).  
Uygulama: `%LocalAppData%\TicketGoTeknoloji\TicketGo Izleme`  
Kullanıcı verisi: `%AppData%\TicketGoTeknoloji\SistemIzleme` (kaldırmada silinmez)

## Güncelleme

Windows istemcisi yalnızca `TicketGoIzleme-Windows-x64-Setup.exe` paketini seçer.
İndirmeden önce SHA-256 doğrulanır. Yanlış platform, eksik paket veya hatalı checksum kurulumu engeller.
macOS zip paketleri Windows istemcisine sunulmaz.

Kod imzalama sertifikası yoksa paket **imzasız**dır; SmartScreen uyarısı görülebilir.
Sertifika yalnızca GitHub Secrets üzerinden kullanılmalıdır; kaynak koda gömülmez.

CI artifact adı: `TicketGoIzleme-Windows-x64`

Release yayını CI tarafından otomatik yapılmaz; installer ve güncelleme doğrulanmadan yayınlanmamalıdır.
