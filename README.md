# wsl-speedup

```sh
Write-Output "Launching Windows Terminal"
Start-Process wt

# Disable LSO on WSL network adapter (will launch an admin powershell and disable it there)
Write-Output "Disabling LSO in admin powershell"

$DisableLSOCommand = @"
& {
  Write-Output 'Disabling LFO on vEthernet (WSL)'
  Disable-NetAdapterLso -Name 'vEthernet (WSL)'
}
"@

Start-Process powershell -Verb runAs -ArgumentList @("-Command", $DisableLSOCommand)
```
