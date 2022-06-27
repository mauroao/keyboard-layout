# Mauro's Keyboard Shortcuts
<center>
  <img src="img/diagram.drawio.svg?" />
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
3. Double click on `script.ahk` script;
4. Make sure script is running (look for an AutoHotkey icon on windows status bar);

## MAC Setup

1. Install Karabiner Elements from https://karabiner-elements.pqrs.org/ ;
3. Open your karabiner.json file (it will be in `~/.config/karabiner/karabiner.json`).
4. Find `complex_modifications`. It will have a key `rules` that takes a list (`"rules": [...]`).
5. Inside the square brackets, paste this:

  ```json
                    {
                        "description": "Caps Lock + I/J/K/L to Arrow Keys, Caps + ; and ' to ` and ~ ",
                        "manipulators": [
                            {
                                "from": {
                                    "key_code": "caps_lock"
                                },
                                "to": [
                                    {
                                        "set_variable": {
                                            "name": "caps_arrows_mode",
                                            "value": 1
                                        }
                                    }
                                ],
                                "to_after_key_up": [
                                    {
                                        "set_variable": {
                                            "name": "caps_arrows_mode",
                                            "value": 0
                                        }
                                    }
                                ],
                                "to_if_alone": [
                                    {
                                        "key_code": "caps_lock"
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "conditions": [
                                    {
                                        "name": "caps_arrows_mode",
                                        "type": "variable_if",
                                        "value": 1
                                    }
                                ],
                                "from": {
                                    "key_code": "h",
                                    "modifiers": {
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "left_arrow"
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "conditions": [
                                    {
                                        "name": "caps_arrows_mode",
                                        "type": "variable_if",
                                        "value": 1
                                    }
                                ],
                                "from": {
                                    "key_code": "j",
                                    "modifiers": {
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "down_arrow"
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "conditions": [
                                    {
                                        "name": "caps_arrows_mode",
                                        "type": "variable_if",
                                        "value": 1
                                    }
                                ],
                                "from": {
                                    "key_code": "k",
                                    "modifiers": {
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "up_arrow"
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "conditions": [
                                    {
                                        "name": "caps_arrows_mode",
                                        "type": "variable_if",
                                        "value": 1
                                    }
                                ],
                                "from": {
                                    "key_code": "l",
                                    "modifiers": {
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "right_arrow"
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "conditions": [
                                    {
                                        "name": "caps_arrows_mode",
                                        "type": "variable_if",
                                        "value": 1
                                    }
                                ],
                                "from": {
                                    "key_code": "semicolon",
                                    "modifiers": {
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "grave_accent_and_tilde"
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "conditions": [
                                    {
                                        "name": "caps_arrows_mode",
                                        "type": "variable_if",
                                        "value": 1
                                    }
                                ],
                                "from": {
                                    "key_code": "quote",
                                    "modifiers": {
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "grave_accent_and_tilde",
                                        "modifiers": ["left_shift"]
                                    }
                                ],
                                "type": "basic"
                            }

                        ]
                    }

  ```
