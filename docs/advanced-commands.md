# Advanced Commands

Only use these if you are comfortable opening Command Prompt as Administrator.

## Check Wi-Fi Driver

```bat
netsh wlan show drivers
```

For the tested MacBook, the Wi-Fi card was:

```text
Broadcom 802.11ac Network Adapter
```

## Check Wi-Fi Interface

```bat
netsh wlan show interfaces
```

If this says Location permission is required, fix Location settings.

## Enable Location Permission for Wi-Fi Scanning

```bat
reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\location /v Value /t REG_SZ /d Allow /f
reg add HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\location /v Value /t REG_SZ /d Allow /f
reg add HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\location\NonPackaged /v Value /t REG_SZ /d Allow /f
```

Restart Windows afterward.

## Reduce Fan Noise

```bat
powercfg /setacvalueindex SCHEME_CURRENT SUB_PROCESSOR PROCTHROTTLEMAX 99
powercfg /setdcvalueindex SCHEME_CURRENT SUB_PROCESSOR PROCTHROTTLEMAX 99
powercfg /setactive SCHEME_CURRENT
```

## Restore Full CPU Turbo

```bat
powercfg /setacvalueindex SCHEME_CURRENT SUB_PROCESSOR PROCTHROTTLEMAX 100
powercfg /setdcvalueindex SCHEME_CURRENT SUB_PROCESSOR PROCTHROTTLEMAX 100
powercfg /setactive SCHEME_CURRENT
```

## Check Active Power Plan

```bat
powercfg /getactivescheme
```

## Check Devices With Problems

PowerShell as Administrator:

```powershell
Get-PnpDevice -PresentOnly | Where-Object { $_.Status -ne 'OK' } | Sort-Object Class,FriendlyName
```

