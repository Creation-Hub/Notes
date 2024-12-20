The Creation Kit can take a long time to load.
There are some Windows tweaks that can be applied to speed things up.

It's slow because Windows Defender (Windows Security) will scan every file as it unpacks the BA2 archives into RAM.
Adding an exclusion for the Creation Kit process will greatly speed things up.

**Environment**
- Windows 10
- 64gb ram
- Installed to `C:\Program Files (x86)\Steam\steamapps\common\Starfield`
- Creation Kit is run as administrator.
- Virus & Threat Protection : Exclusion added for *Process* `C:\Program Files (x86)\Steam\steamapps\common\Starfield\CreationKit.exe`. Use a full path so that this exclusion is *less* likely to be exploited by malware.

**See**
- <https://support.microsoft.com/en-us/windows/add-an-exclusion-to-windows-security-811816c0-4dfd-af4a-47e4-c301afe13b26>
- <https://support.microsoft.com/en-us/topic/how-to-add-a-file-type-or-process-exclusion-to-windows-security-e524cbc2-3975-63c2-f9d1-7c2eb5331e53>

My first test was untimed *Without* a Virus & Threat Protection exclusion.
After noticing the time difference I removed the exclusion and began the first timed test.

By "to launch" I mean from the time I double click the icon to the time the app is launched and responsive.

**With Exclusions**
- Total 40s to launch
- Total 1m 50s to plugin loaded (1m, 10s)

**Without Exclusions**
- Total 3m 2s to launch
- Total 4m 19s to plugin loaded (1m, 17s)

**With Exclusions**
- Total 38s to launch
- Total 1m 48s to plugin loaded (1m, 10s)

Adding an exclusion for real time virus protection really does reduce Creation Kit launch time by a few minutes, but plugin load times see little influence.
