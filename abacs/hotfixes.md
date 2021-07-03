# HotFixes

PowerShell command to extract this information

Dependencies: PSScriptTools

`$hotfixes = Get-HotFix | Select-Object HotFixID,InstalledOn,Description` `$hotfixes | ConvertTo-Markdown -title HotFixes -AsTable | Out-File -Encoding utf8 -FilePath .\hotfixes.md`

## HotFixes

| HotFixID | InstalledOn | Description |
| :--- | :--- | :--- |
| KB4601050 | 05/02/2021 00:00:00 | Update |
| KB4561600 | 05/02/2021 00:00:00 | Security Update |
| KB4562830 | 05/02/2021 00:00:00 | Update |
| KB4570334 | 05/02/2021 00:00:00 | Security Update |
| KB4577266 | 05/02/2021 00:00:00 | Security Update |
| KB4577586 | 05/02/2021 00:00:00 | Update |
| KB4580325 | 05/02/2021 00:00:00 | Security Update |
| KB4586864 | 05/02/2021 00:00:00 | Security Update |
| KB4589212 | 05/02/2021 00:00:00 | Update |
| KB4593175 | 05/02/2021 00:00:00 | Security Update |
| KB4598481 | 05/02/2021 00:00:00 | Security Update |
| KB5000736 | 05/18/2021 00:00:00 | Update |
| KB5003173 | 05/14/2021 00:00:00 | Security Update |
| KB5003242 | 05/14/2021 00:00:00 | Security Update |

