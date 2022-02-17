# Windows installation guide

- [Windows installation guide](#windows-installation-guide)
  - [Bypass OEM preinstalled key](#bypass-oem-preinstalled-key)
  - [Uninstall Cortana app](#uninstall-cortana-app)
  - [Uninstall Microsoft Edge](#uninstall-microsoft-edge)

## Bypass OEM preinstalled key

On install USB open /Sources\
create new file PID.txt\
with contents of:

[PID.txt](PID.txt)

```toml
[PID]
Value=VK7JG-NPHTM-C97JM-9MPGT-3V66T
```

(replace VK...6T with actual key if present)

Priority of keys:

1. Finding a product key in the PID.txt file
2. Finding a product key in UEFI/BIOS
3. The user manually enters a product key when asked for one
4. No product key is found or entered - then the user is asked for Home or Pro

## Uninstall Cortana app

Open PowerShell in Administrator mode

`Get-AppxPackage -allusers Microsoft.549981C3F5F10 | Remove-AppxPackage`

## Uninstall Microsoft Edge

In cmd go to `cd C:\Program Files (x86)\Microsoft\Edge\Application\xxx\Installer`
where `xxx` is the current version

`setup.exe --uninstall --system-level --verbose-logging --force-uninstall`

**It could go back!**

To fix this open `regedit` in Administator mode\
go to `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft`\

Create new key named `EdgeUpdate`\
RMC > new DWORD 32-bit\

```txt
Value name = DoNotUpdateToEdgeWithChromium
Value date = 1
```
