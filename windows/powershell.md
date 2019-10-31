### PS1
```powershell
## set profile (like ~/.bashrc) for current user current host
notepad $profile.CurrentUserCurrentHost
## for all user all hosts etc. tab to get suggestions
notepad $profile.AllUsersAllHosts

function Prompt
{
  return "$($env:COMPUTERNAME) | $(Get-UserName) | $($(date).ToString("MMM yyyy | HH:mm:ss")) | $((get-item -Path .\).BaseName)`n>> ";
}
```
