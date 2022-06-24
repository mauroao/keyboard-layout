# Mauro's Keyboard Layout
<center>
  <img src="img/diagram.drawio.svg" />
</center>
A configuration guide setup to my keyboard shortcuts on MAC and Windows.

## Windows setup

1. Install AutoHotkey from https://www.autohotkey.com/;
2. Create a file `script.ahk` and fill with above code:
  ```
RAlt::RControl

CapsLock::
	KeyWait, CapsLock
	If (A_PriorKey="CapsLock")
		SetCapsLockState, % GetKeyState("CapsLock","T") ? "Off" : "On"
Return

#If, GetKeyState("CapsLock", "P") 
	h::Left
	j::Down
	k::Up
	l::Right
	`;::`
	'::~
#If
  ```
3. Start this script;
