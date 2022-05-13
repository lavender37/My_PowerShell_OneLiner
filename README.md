# PowerShell_OneLiner
My collection of PowerShell One-Liners for data processing on Windows.

All command is in one line but not single command in one line. 

⭐ - CMD Compatibility

⚠️ - Not sure the compatibility for other version


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

## Find in a Directory

#### Find all empty direcory in a Directory

```PowerShell

Get-ChildItem /path/to/directory -Recurse -Directory | Where-Object {!$_.GetFileSystemInfos().Count}

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

# PowerShell_OneLiner based Outside Program

## Find the handle for file or folder ⭐

setting handle.exe in $env:PATH before using the command. [downlaoad from here https://download.sysinternals.com/files/Handle.zip]

```Powershell

handle /path/to/directoryorfile

```
