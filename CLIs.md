### Poweroff Computer - PowerShell
`Stop-Computer -Force`

### Or using Command Prompt
`shutdown /s`

### Delete all logs
`for /F "tokens=*" %1 in ('wevtutil.exe el') DO wevtutil.exe cl "%1"`

### Create a Simple Scheduled Task
`schtasks /create /sc minute /tn "Notepad1" /tr notepad.exe`

### Run cmd with SYSTEM
`psexec64.exe -d -s -i cmd.exe`

### Enable Command Line Auditing
```
auditpol /set /subcategory:"Process Creation" /success:enable /failure:enable
reg add "HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System\Audit" /v ProcessCreationIncludeCmdLine_Enabled /t REG_DWORD /d 1 /f
auditpol /get /subcategory:"Process Creation"
reg query "HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System\Audit" /v ProcessCreationIncludeCmdLine_Enabled
Get-WinEvent -LogName Security | Where-Object { $_.Id -eq 4688 } | Select-Object -First 5
```

### Simple Web Server with PHP Support (one-liner)
good reference: https://stackoverflow.com/questions/1678010/php-server-on-local-machine
`php -S 0.0.0.0:80`

### Or using Python (one-liner)
`sudo python3 -m http.server 80`

### Disabling the Windows SmartScreen can be done using the following command:
`reg.exe ADD "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer" /v SmartScreenEnabled /t REG_SZ /d "Off"`





