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
$myvar = "This Is Easy"
Write-Host "$username $myvar`n"

# last trick
Write-Host "C:\Users\$($env:username)\Desktop"
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
```
#### Using Content
```powershell
$request = Invoke-WebRequest "https://api.ipify.org" -UseBasicParsing
$ip = $request.Content
Clear-Host
Write-Host "StatusCode = $($request.StatusCode)"
Write-Host "IP = $ip" 
```

#### Downloading Files
```powershell
Invoke-WebRequest "https://api.ipify.org" -OutFile "C:\Users\$env:username\Desktop\ip.txt"
```

## Starting Processes
```powershell
$filepath = "C:\Users\$env:username\Desktop\ip.txt"

Invoke-WebRequest "https://api.ipify.org" -OutFile $filepath
Start-Process notepad.exe -ArgumentList "$filepath" -Wait
```