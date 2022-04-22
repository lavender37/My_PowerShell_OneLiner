# PowerShell_OneLiner
My collection of PowerShell One-Liners for data processing on Windows.


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
[System.Reflection.Assembly]::LoadWithPartialName("System.Windows.Forms") | Out-Null;$p = New-Object System.Windows.Forms.OpenFileDialog -Property @{Filter = "All|*.*"}; if($p.ShowDialog() -eq $true){$filename = $p.FileNames}; certutil -hashfile $filename MD5

```

#### Check a file for SHA1

This Script will open a file dialog then you can select a file for getting SHA1 in the terminal

```PowerShell

[System.Reflection.Assembly]::LoadWithPartialName("System.Windows.Forms") | Out-Null;$p = New-Object System.Windows.Forms.OpenFileDialog -Property @{Filter = "All|*.*"}; if($p.ShowDialog() -eq $true){$filename = $p.FileNames}; certutil -hashfile $filename SHA1

```

#### Check a file for SHA256

This Script will open a file dialog then you can select a file for getting SHA256 in the terminal

```PowerShell

[System.Reflection.Assembly]::LoadWithPartialName("System.Windows.Forms") | Out-Null;$p = New-Object System.Windows.Forms.OpenFileDialog -Property @{Filter = "All|*.*"}; if($p.ShowDialog() -eq $true){$filename = $p.FileNames}; certutil -hashfile $filename SHA256

```
