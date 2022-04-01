# Windows 10
## Bootable ISO
[microsoft website](https://www.microsoft.com/en-us/software-download/windows10)

## Setup
### Control Panel setup
- windows key `ris:Windows`
- type control panel
- change to small icons (top right)
- UAC (install confirmation dialogue)
	- `control panel` > `User Accounts` > `Change User Account Control settings`
	- drag slider all the way down
	- hit okay and confirm
- Power Options
	- Set to `High performance` because it's a desktop
		- display turn off
		- hibernation settings
		- sleep
- Sound
	- Playback (output)
		- set default device/communication device
		- right click > `properties` > `levels`
			- set to `100`
	- Recording (input/mic)
		- set default device/communication device
		- right click > `properties` > `levels`
			- set to `100`
---
## Activation
[domain activation video](https://youtu.be/lNxI4aERw5Q)
### edit version registry
- press `win + r` to open run dialog
	- type `regedit` to open the windows registry
		- `HKEY_CURRENT_USER` > `Control Panel` > `Desktop`
		- search in `Desktop` for `PaintDesktopVersion`
		- right click and select `Modify`
		- change `Value data:` to `4`
- close the registery
### update policy
- type `cmd` into the window search
	- right click on Command Prompt
	- run as administrator
		- In the command prompt type `gpupdate /force` and hit enter
		- you should see "User Policy update has completed successfully."
- close cmd
### enable domain activation
- re-open `regedit`
	- `HKEY_LOCAL_MACHINE` > `SYSTEM` > `CurrentControlSet` > `Services`
	- locate `svsvc`
	- right click on `Start` and select `Modify`
	- change `Value data:` to `4`
	- right click in the blank area in the `svsvc` key
		- `New` > `Key`
		- Make the name `KMS`
		- edit (Default) key and set value to `kms_4`
- close the registery
### activation status
- open windows 10 settings
	- select `Update & Security`
	- select `Activation` on the left menu
	- write down/remember the windows Edition name from the top
- use the [[keys.png|Key]] that matches your edition for the next steps
### update domain information
- open the Command Prompt as administrator again
	- run `gpupdate /force`
	- in the command prompt enter `slmgr /ipk your-key-here`
	- wait for Windows Script Host popup to tell you it was successful
		- click okay
	- enter `slmgr /skms kms8.msguides.com`
		- click okay
	- enter `/ato`
		- wait for another Windows Script Host popup and click okay
### validate success
- right click refresh on desktop to make sure "activate windows" watermark is gone
### revert domain changes
- repeat the [[Windows 10#edit version registry|first steps]] to change the `PaintDesktopVersion`'s value data into a `0`
- repeat the [[Windows 10#update policy|policy update]] instructions
### you should be all done :)