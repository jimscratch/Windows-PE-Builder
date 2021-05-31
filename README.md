# Windows Preboot Environment (WinPE) Builder

This repo contains an powershell scripts to ....

## Create WinPE System:
```cmd
copype.cmd amd64 C:\Temp\WinPE
```

## Add Modules to WinPE:
```powershell
#Mount the image from "" to ""
Dism /Mount-Image /ImageFile:"C:\Temp\WinPE\media\sources\boot.wim" /Index:1 /MountDir:"C:\Temp\WinPE\mount"

#Add Windows capabilities from the local ADK
Dism /Image:"C:\Temp\WinPE\mount" /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-WMI.cab"
Dism /Image:"C:\Temp\WinPE\mount" /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-WMI_en-us.cab"
Dism /Image:"C:\Temp\WinPE\mount" /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-NetFx.cab"
Dism /Image:"C:\Temp\WinPE\mount" /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-NetFx_en-us.cab"
Dism /Image:"C:\Temp\WinPE\mount" /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-FMAPI.cab"
Dism /Image:"C:\Temp\WinPE\mount" /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-SecureStartup.cab"
Dism /Image:"C:\Temp\WinPE\mount" /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-SecureStartup_en-us.cab"
Dism /Image:"C:\Temp\WinPE\mount" /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-EnhancedStorage.cab"
Dism /Image:"C:\Temp\WinPE\mount" /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-EnhancedStorage_en-us.cab"
Dism /Image:"C:\Temp\WinPE\mount" /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-Scripting.cab"
Dism /Image:"C:\Temp\WinPE\mount" /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-Scripting_en-us.cab"
Dism /Image:"C:\Temp\WinPE\mount" /add-package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-PowerShell.cab"
Dism /Image:"C:\Temp\WinPE\mount" /add-package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-PowerShell_en-us.cab"
Dism /Image:"C:\Temp\WinPE\mount" /add-package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-StorageWMI.cab"
Dism /Image:"C:\Temp\WinPE\mount" /add-package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-StorageWMI_en-us.cab"
Dism /Image:"C:\Temp\WinPE\mount" /add-package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-DismCmdlets.cab"
Dism /Image:"C:\Temp\WinPE\mount" /add-package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-DismCmdlets_en-us.cab"
```

After this step you can develop you WinPE Application and embed it on the WinPE Folder "C:\Temp\WinPE".

## Unmount WinPE
```powershell
dism /unmount-wim /mountdir:"C:\Temp\WinPE\MOUNT" /commit
```

## Create WinPE System:
```cmd
MakeWinPEMedia /ISO /f C:\Temp\WinPE C:\Temp\WinPE\CustomisedWinPE.iso
```

You can now use CustomisedWinPE.iso for deployment on WDS, USB-Stick or something else.
 

## Requirements:
- PowerShell 5.0
- Windows 10
- Windows ADK an PE-AddOn

# Feature requests
If you have an idea for a new feature in this repo, send me an issue with the subject Feature request and write your suggestion in the text. I will then check the feature and implement it if necessary.

Created by @niklasrast 