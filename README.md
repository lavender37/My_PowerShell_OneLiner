# PowerShell_OneLiner
My collection of PowerShell One-Liners for data processing on Windows.

我发现当需要做一些复杂操作时，限定命令只有一行是困难的，因此在下次或者某个时间，我会添加一些脚本用于辅助。当然，执行时仍然是一行的

Default - Work on Powershel

⭐ - CMD Compatibility

⚠️ - Not sure the compatibility for Powershell with other version


### check Powershell version

```PowerShell
$PSVersionTable
```

### my powershell version

```powershell
Name                           Value
----                           -----
PSVersion                      5.1.19041.1645
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.19041.1645
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

## Local Policy for Powershell Scrpit

#### allow local machine Script

```PowerShell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
```

## Install a module

#### install module with proxy
For unknown reasons, I can't install the Powershell module directly, but it works fine with Proxy, so the command line added
```
Install-Module -Name ModuleName -Proxy 'ProxyAddress'
```

## Find in a Directory

#### Find all empty direcory in a Directory

```PowerShell
Get-ChildItem /path/to/directory -Recurse -Directory | Where-Object {!$_.GetFileSystemInfos().Count}
```
Format the result
```Powershell
Get-ChildItem ./ -Recurse -Directory | Where-Object {!$_.GetFileSystemInfos().Count} | Format-Table -Property FullName, LastWriteTime
```
Find the file with extension $.tlog$
```Powershell
Get-ChildItem ./ -Recurse -Directory | Where-Object {$_.Name -match ".*\.tlog$"} | Format-Table -Property FullName, LastWriteTime
```
## Verify a file

#### Check a file for MD5

This Script will open a file dialog then you can select a file for getting MD5 in the terminal

```PowerShell
[System.Reflection.Assembly]::LoadWithPartialName("System.Windows.Forms") | Out-Null;$p = New-Object System.Windows.Forms.OpenFileDialog -Property @{Filter = "All|*.*"}; if($p.ShowDialog() -eq $true){$filename = $p.FileNames; certutil -hashfile $filename MD5}
```

#### Check a file for SHA1

This Script will open a file dialog then you can select a file for getting SHA1 in the terminal

```PowerShell
[System.Reflection.Assembly]::LoadWithPartialName("System.Windows.Forms") | Out-Null;$p = New-Object System.Windows.Forms.OpenFileDialog -Property @{Filter = "All|*.*"}; if($p.ShowDialog() -eq $true){$filename = $p.FileNames; certutil -hashfile $filename SHA1}
```

#### Check a file for SHA256

This Script will open a file dialog then you can select a file for getting SHA256 in the terminal

```PowerShell
[System.Reflection.Assembly]::LoadWithPartialName("System.Windows.Forms") | Out-Null;$p = New-Object System.Windows.Forms.OpenFileDialog -Property @{Filter = "All|*.*"}; if($p.ShowDialog() -eq $true){$filename = $p.FileNames; certutil -hashfile $filename SHA256}
```

## Registry Operation

#### copy file path from Right-Click menu

```
not ready
```
## Firewall Operation[administrator privilege]

#### Find all enabled rules

```
not ready
```

## Module Installation

#### Install module for current user

```
Install-Module module_name -Scope CurrentUser
```
## Restart Option[administrator privilege]

#### restart right now ⭐
```
shutdown -r -t 0
```

#### restart for setting bios right now ⭐
```
shutdown -r -t 1 /fw
```

#### restart for choosing the advance restart option right now ⭐
```
shutdown -o -r -t 0
```

# PowerShell_OneLiner based on the command line mode of other software

## Find the handle for file or folder ⭐

setting handle.exe in $env:PATH before using the command. [downlaoad from here https://download.sysinternals.com/files/Handle.zip]

```Powershell
handle /path/to/directoryorfile
```

## Create SFX rar for file or folder ⭐

setting winrar.exe in $env:PATH before using the command. 

for folder
```
WinRAR.exe a -sfx'Default.SFX' -p'password;,' -r des.rar ./
```

for file
```
WinRAR.exe a -sfx'Default.SFX' -p'password;,' des.rar ./filename
```
