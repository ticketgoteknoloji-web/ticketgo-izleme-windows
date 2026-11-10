# TicketGo Teknoloji İzleme ve Takip Sistemi — Windows

Bağımsız Windows 10/11 x64 masaüstü istemcisi (Qt 6 / C++ / CMake / QML).

- Depo: https://github.com/ticketgoteknoloji-web/ticketgo-izleme-windows
- Güncelleme: GitHub Releases/latest (yalnız Windows x64 Setup.exe + SHA-256)
- Paketleme: Inno Setup → `TicketGoIzleme-Windows-x64-Setup.exe`

Bu klasör macOS izleme projesinin Windows kopyasıdır. macOS deposuna push edilmez.

## Geliştirme

```powershell
$env:QT_PREFIX = "C:\Qt\6.8.1\msvc2022_64"
cmake -S . -B build-windows -G Ninja -DCMAKE_BUILD_TYPE=Release "-DCMAKE_PREFIX_PATH=$env:QT_PREFIX"
cmake --build build-windows --config Release --target ops_core_tests update_tests ticketgo-izleme ticketgo-update-helper
.\build-windows\ops_core_tests.exe
.\build-windows\update_tests.exe
.\packaging\windows\build.ps1
```

Ayrıntılar: `packaging/windows/README.md`
