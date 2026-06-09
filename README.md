# Round the iterations to the nearest integer
$iterations = [math]::Round(($(Get-Date -Hour 15 -Minute 00 -Second 0) - $(Get-Date)).TotalMinutes)

$shell = New-Object -ComObject "Wscript.shell"

for ($i = 0; $i -lt $iterations; $i++) {
    $shell.sendkeys("{SCROLLLOCK}")
    cls
    Write-Host "..." $i
    Start-Sleep -Seconds 60
}
