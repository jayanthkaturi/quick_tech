### PS1
```powershell
function Prompt
{
  return "$($env:COMPUTERNAME) | $(Get-UserName) | $($(date).ToString("MMM yyyy | HH:mm:ss")) | $((get-item -Path .\).BaseName)`n>> ";
}
```
