# Mauro's Keyboard Shortcuts
<center>
  <img src="img/diagram.drawio.svg" />
</center>

## What is this used for?

This is a configuration guide to setup my keyboard shortcuts on MAC, Windows and Linux.
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
	/::\
#If
  ```
If using v2, use this script instead:
  ```
#Requires AutoHotkey v2.0

; Remap RAlt to RControl
RAlt::RControl

; Toggle CapsLock with double press
CapsLock::
{
    KeyWait "CapsLock"
    if (A_PriorKey == "CapsLock") {
        SetCapsLockState GetKeyState("CapsLock", "T") ? "Off" : "On"
    }
}

; Only active when CapsLock is on
#HotIf GetKeyState("CapsLock", "P")

h::Send("{Left}")
j::Send("{Down}")
k::Send("{Up}")
l::Send("{Right}")
`;::Send("{`}")
'::Send("{~}")
/::Send("{\\}")

#HotIf

  ```
3. Double click on `script.ahk` script;
4. Make sure script is running (look for an AutoHotkey icon on windows status bar);
5. Click Win+R, type `shell:startup`, paste a shortcut to AutoHotKey script here;
6. Or, save script as "C:\Users\mauro\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\script.ahk";

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
                                        "key_code": "caps_lock",
                                        "hold_down_milliseconds": 100
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
                                    "key_code": "slash",
                                    "modifiers": {
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "backslash"
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

## Linux Setup (Ubuntu 24.04+)

This setup uses [keyd](https://github.com/rvaiya/keyd), a lightweight key remapping daemon that operates at the kernel level (evdev/uinput). It works on **X11, Wayland, and even TTY**.

1. Install keyd and enable the service:
   ```bash
   sudo apt install keyd
   sudo systemctl enable --now keyd
   ```

2. Create the configuration file `/etc/keyd/default.conf`:
   ```ini
   [ids]
   *

   [main]
   capslock = overload(nav, capslock)
   rightalt = rightcontrol

   [nav]
   h = left
   j = down
   k = up
   l = right
   semicolon = grave
   apostrophe = S-grave
   slash = backslash
   ```

3. Reload the configuration:
   ```bash
   sudo keyd reload
   ```

4. Useful commands for debugging:
   - `keyd list` — list detected keyboards
   - `sudo keyd monitor` — monitor key events in real time
   - `sudo keyd reload` — reload configuration after changes

## Troubleshooting

### CAPS LOCK Quick Tap Not Working on macOS Sequoia

**Symptoms:**
- CAPS LOCK works as a modifier when held down (CAPS + H/J/K/L for arrow navigation works)
- Quick tap on CAPS LOCK does not toggle caps lock state
- Issue occurs after updating to macOS Sequoia on M1 MacBook with Karabiner-Elements 15.1.0+

**Cause:**
macOS Sequoia introduced "accidental keystroke prevention" for CAPS LOCK that requires a minimum 100ms press duration. The configuration needs to specify this timing parameter.

**Solution:**
Verify that the `to_if_alone` block includes the `hold_down_milliseconds` parameter:

```json
"to_if_alone": [
    {
        "key_code": "caps_lock",
        "hold_down_milliseconds": 100
    }
],
```

**Steps to Apply Fix:**
1. Update your karabiner.json file with the corrected configuration above
2. Fully quit Karabiner-Elements (don't just close the window - quit from menu bar)
3. Reopen Karabiner-Elements
4. Test quick tap: Quickly tap CAPS LOCK - it should toggle caps lock state
5. Test hold behavior: Hold CAPS LOCK + H/J/K/L - arrow navigation should work

**Reference:** [Karabiner-Elements Issue #3949](https://github.com/pqrs-org/Karabiner-Elements/issues/3949)
