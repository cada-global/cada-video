# CADA Video — downloads

CADA Video automatically switches NDI PTZ cameras to whoever is speaking in a meeting room. It follows the microphones: ceiling and table mic arrays from Shure, Sennheiser and Yamaha, and conference systems from Televic, Bosch, Shure, Vissonic and Audio-Technica.

This repository holds the **Windows installers only**. Get the latest version here:

**➜ [Latest release](https://github.com/cada-global/cada-video/releases/latest)**

## Which file do I need?

| File | What it is |
|------|------------|
| `CADA.Installer.msi` | The installer. This is the one you need. |
| `CADA.Installer.msi.sha256` | Its SHA-256 checksum, to check the download. |
| Source code (zip / tar.gz) | Added by GitHub to every release automatically. It contains only this README; you don't need it. |

Direct link to the newest installer:
`https://github.com/cada-global/cada-video/releases/latest/download/CADA.Installer.msi`

## Check the download

In PowerShell, in the download folder:

```powershell
(Get-FileHash .\CADA.Installer.msi -Algorithm SHA256).Hash.ToLower()
Get-Content .\CADA.Installer.msi.sha256
```

The two hashes must match. If they don't, don't run the installer: download it again.

## Install

You need local administrator rights on the CADA PC.

1. Run `CADA.Installer.msi`. The installer is not yet code-signed, so Windows shows warnings it doesn't show for signed software:
   - **Windows protected your PC**: click **More info**, then **Run anyway**.
   - **Publisher: Unknown** (administrator prompt): click **Yes**.
   - If nothing happens, right-click the MSI → **Properties** → tick **Unblock** → **OK**, and run it again.
2. CADA installs as the Windows service `CADAService`. When the installer closes, your browser opens `http://localhost:8080/setup`, where the setup wizard takes you through devices, cameras and zones.

Silent install for scripts and deployment tools:

```powershell
Unblock-File .\CADA.Installer.msi
msiexec /i CADA.Installer.msi /qn
```

To uninstall: **Settings → Apps → Installed apps**, search for *CADA Video*, **Uninstall**.

Full installation steps, troubleshooting and configuration are in the CADA user manual.
