---
title: "How to Crack Sublime Text 3 with Hex Editor (without license)"
date: 2019-12-31T00:00:00+08:00

categories:
  - "Miscellaneous"
---
Sublime Text is a super fast, feature-rich and versatile text and code editor with an extraordinary features, and amazing performance. I often use it for work,  but have to purchase license. Today, I'll share a 100% workable method to avoid register.
<!--more-->
# Step:
1. Download & Install Sublime Text 3.2.2 Build 3211
2. Visit https://hexed.it/
3. Open file `ublime_text.exe`
4. Search address: `97 94 0D` -> `00 00 00`
5. Offset 0x8545: Original `84` -> `85`
6. Offset 0x08FF19: Original `75` -> `EB`
7. Offset 0x1932C7: Original `75` -> `74` (remove UNREGISTERED in title bar, so no need to use a license)
8. Export File
9. Backup sublime_text.exe file (just rename)
10. Copy sublime_text.exe modified to directory Sublime Text 3

# Easy edit Hex with Powershell
1. Open Powershell as Admin
2. Enter this Line:
Invoke-Expression (New-Object System.Net.WebClient).DownloadString("https://raw.githubusercontent.com/nferrell/PSToolbelt/master/Public/Edit-FileHex.ps1")
Edit-FileHex -FilePath "C:\Program Files\Sublime Text 3\sublime_text.exe" -Offset 0x8545 -Original 84 -Updated 85 -OverwriteOriginal
Edit-FileHex -FilePath "C:\Program Files\Sublime Text 3\sublime_text.exe" -Offset 0x08FF19 -Original 75 -Updated EB -OverwriteOriginal
Edit-FileHex -FilePath "C:\Program Files\Sublime Text 3\sublime_text.exe" -Offset 0x1932C7 -Original 75 -Updated 74 -OverwriteOriginal
3. Done :)

Source: https://gist.github.com/JerryLokjianming/71dac05f27f8c96ad1c8941b88030451/


