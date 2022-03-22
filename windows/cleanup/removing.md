# Removing apps guide

## Packages

`Get-AppxPackage -AllUsers *phone*`

## Wmi Object

`Get-WmiObject -Class Win32_Product`

## Pipes

`CMD | Select-Object -Property Name | Select-String -Pattern name`
