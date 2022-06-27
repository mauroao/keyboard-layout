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

Space::return

Space Up::
    if (A_PriorKey = "Space")
    {
        Send {Space}
    }
    return

Space & k::Up
Space & h::Left
Space & j::Down
Space & l::Right

Space & `;::`
Space & '::~

Space & c::^c ; copy
Space & x::^x ; cut
Space & v::^v ; paste
Space & z::^z ; undo 
Space & a::^a ; select all
Space & t::^t ; new tab 
Space & m::#m ; minimize all

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
                        "description": "Space FN Mode",
                        "manipulators": [
                            {
                                "from": {
                                    "key_code": "spacebar"
                                },
                                "to": [
                                    {
                                        "set_variable": {
                                            "name": "space_fn_mode",
                                            "value": 1
                                        }
                                    }
                                ],
                                "to_after_key_up": [
                                    {
                                        "set_variable": {
                                            "name": "space_fn_mode",
                                            "value": 0
                                        }
                                    }
                                ],
                                "to_if_alone": [
                                    {
                                        "key_code": "spacebar"
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "conditions": [
                                    {
                                        "name": "space_fn_mode",
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
                                        "name": "space_fn_mode",
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
                                        "name": "space_fn_mode",
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
                                        "name": "space_fn_mode",
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
                                        "name": "space_fn_mode",
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
                                        "name": "space_fn_mode",
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
