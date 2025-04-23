## PowerShell 101

#### Windows PowerShell
```
C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
```

#### Windows PowerShell ISE
```
C:\Windows\System32\WindowsPowerShell\v1.0\powershell_ise.exe
```

## Clear | Write | Variables
```powershell
Clear-Host

Write-Host "Hello World"

Write-Host "Hello $env:username `n"

# store username in variable 
$username = $env:username
Write-Host "`$username = $username `n"

# store string in variable
$var = "This Is Easy"
Write-Host $username $var
```

## Test | Create | Remove

#### Test-Path
```powershell
Test-Path "C:\Temp" -PathType Container
```

#### New-Item
```powershell
New-Item "C:\Temp" -ItemType Directory
New-Item "C:\Temp" -ItemType Directory -Force
New-Item "C:\Temp" -ItemType Directory -Force | Out-Null
```

#### Remove-Item
```powershell
Remove-Item "C:\Temp"
```

#### Conditions
```powershell
if(<<this is $TRUE>>){
    <<when $true do this>>
}
# optional
else{
    <<when $false do this>>
}
```

#### Logic
```powershell
Clear-Host

# if Temp doesn't exist create it
if(Test-Path "C:\Temp" -PathType Container){
    Write-Host "[Directory] C:\Temp Exists"
}
else{
    New-Item "C:\Temp" -ItemType Directory -Force | Out-Null
    Write-Host "[Directory] C:\Temp Created"
}

# create bad.txt
New-Item "C:\Temp\bad.txt" -ItemType File -Force | Out-Null
Write-Host "[Created] C:\Temp\bad.txt"

# if bad.txt exists remove it
if(Test-Path "C:\Temp\bad.txt" -PathType Leaf){
    Remove-Item "C:\Temp\bad.txt" -Force
    Write-Host "[Removed] C:\Temp\bad.txt"
}
```

## Website Requests

#### Invoke-Webrequest
```powershell
Invoke-WebRequest "https://api.ipify.org"
(Invoke-WebRequest "https://api.ipify.org").content
```