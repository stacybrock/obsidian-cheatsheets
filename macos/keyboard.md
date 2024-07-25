# macOS Keyboard
## Disable Keyboard Long Press Accented Characters Popup

```
$ defaults write -g ApplePressAndHoldEnabled -bool false
```
## Swapping Escape and Caps Lock keys with hidutil
Post macOS 10.12 Sierra releases include a utility for custom keyboard remapping called `hidutil`.

To swap the Escape and Caps Lock keys:
```
$ hidutil property --set '{"UserKeyMapping":[ {"HIDKeyboardModifierMappingSrc":0x700000039,"HIDKeyboardModifierMappingDst":0x700000029}, {"HIDKeyboardModifierMappingSrc":0x700000029,"HIDKeyboardModifierMappingDst":0x700000039}]}'
```
Changes persist until reboot. A LaunchAgent can be used to apply changes on login.
- https://www.nanoant.com/mac/macos-function-key-remapping-with-hidutil
- https://www.freebsddiary.org/APC/usb_hid_usages.php

## Disable Emoji Autosuggestions
```
$ sudo defaults write /Library/Preferences/FeatureFlags/Domain/UIKit.plist emoji_enhancements -dict-add Enabled -bool NO
```