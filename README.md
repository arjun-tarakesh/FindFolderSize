# FindFolderSize
A powershell command to find folders size and export it to a .csv file



```
Get-ChildItem -Path C:\Example -Directory | ForEach-Object {
    $sizeGB = ((Get-ChildItem $_.FullName -Recurse | Measure-Object -Property Length -Sum).Sum / 1GB)
    [PSCustomObject]@{
        Directory = $_.FullName
        Size_GB = [Math]::Round($sizeGB, 2)  # Rounding to 2 decimal places
    }
} | Export-Csv -Path "C:\Example.csv" -NoTypeInformation

```
