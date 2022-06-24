# Mauro's Keyboard Shortcuts
<center>
  <img src="img/diagram.drawio.svg" />
</center>

## What is this used for?

This is a configuration guide to setup my keyboard shortcuts on MAC and Windows.  
I am using 60% keyboards with no QMK firmware support.

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
