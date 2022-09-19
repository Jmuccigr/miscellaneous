---
title: Changing sounds in Outlook for MacOS
date: 14 September 2022
---

## Outlook Sounds

The sounds for Outlook live in `/Applications/Microsoft Outlook.app/Contents/Frameworks/OutlookCore.framework/Versions/A/Resources/` which is an alias for `/Applications/Microsoft\ Outlook.app/Contents/Frameworks/OutlookCore.framework/Versions/A/Resources/`.

The solution is to copy new .wav format files with the appropriate names to this folder, fixing their permissions just to be sure. For example:

```
> sudo cp Dmailsent.wav /Applications/Microsoft\ Outlook.app/Contents/Frameworks/OutlookCore.framework/Resources/mailsent.wav
> sudo chmod 664 /Applications/Microsoft\ Outlook.app/Contents/Frameworks/OutlookCore.framework/Resources/mailsent.wav
```

I like to use the Mail.app sounds, which can be found in `/System/Library/PrivateFrameworks/ToneLibrary.framework/Versions/A/Resources/AlertTones/` as .caf files. Convert to wav with `> ffmpeg -i input.cav /path/output.wav`

List of wav files:

- mailerror.wav
- nomail.wav
- goodbye.wav
- mailsent2.wav
- reminder.wav
- welcome.wav
- mailsent.wav
- newmail.wav
