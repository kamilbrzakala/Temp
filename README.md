function StartF {
    param (
        [int]$TargetHour = 15,
        [int]$TargetMinute = 30
    )

    # Calculate remaining minutes (rounded)
    $iterations = [math]::Round(((
        Get-Date -Hour $TargetHour -Minute $TargetMinute -Second 0
    ) - (Get-Date)).TotalMinutes)

    # Prevent negative iterations
    if ($iterations -le 0) {
        Write-Host "Target time already passed."
        return
    }

    $shell = New-Object -ComObject "Wscript.shell"

    for ($i = 0; $i -lt $iterations; $i++) {
        $shell.SendKeys("{SCROLLLOCK}")
        cls
        Write-Host "..." $i
        Start-Sleep -Seconds 60
    }
}
