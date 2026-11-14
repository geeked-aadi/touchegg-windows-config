# Touchegg Windows Gestures for KDE
Touchégg configuration that brings Windows-style touchpad gestures to KDE Plasma. Swipe to open the overview, show the desktop, switch apps and switch virtual desktops, just like on a Windows precision touchpad.

## Requirements
- KDE Plasma running an **X11 session** (Touchégg does not work on Wayland). At the login screen, choose **Plasma (X11)**.
- [Touchégg](https://github.com/JoseExposito/touchegg) installed and its service running.

## Installation
[Install Touchégg first if you haven't already](https://github.com/JoseExposito/touchegg)
```shell
# Download touchegg.conf from this repo, then:
mkdir -p ~/.config/touchegg
cp touchegg.conf ~/.config/touchegg/touchegg.conf
sudo systemctl restart touchegg
```
**That's it!**

If Touchégg isn't running yet:
```shell
sudo systemctl enable touchegg
sudo systemctl start touchegg
```

## Usage
### Swipe Gestures
  - 3 Fingers UP: **Overview** (all open windows)
  - 3 Fingers DOWN: **Show Desktop** (swipe again to restore)
  - 3 Fingers LEFT/RIGHT: **Switch Apps** (Alt+Tab)
  - 4 Fingers UP: **Overview**
  - 4 Fingers DOWN: **Show Desktop**
  - 4 Fingers LEFT/RIGHT: **Switch Virtual Desktops**

### Pinch Gestures
  - 3 Fingers PINCH IN: **Close Window**
  - [Browsers] 2 Fingers PINCH IN/OUT: **Zoom Out/In**

### Handled by Plasma, not Touchégg
  - Tap: left click
  - 2 Fingers TAP: right click
  - 2 Fingers SLIDE: scroll

Enable and tune these in **System Settings > Input Devices > Touchpad**.

## Differences from Windows
- Touchégg only supports swipes with 3+ fingers on touchpads, and taps only on touchscreens. Windows' 3-finger tap (Search) and 4-finger tap (Notifications) are not possible.
- The Plasma Overview looks different from Windows Task View, but does the same job.
- The Alt+Tab swipe moves one app at a time instead of showing a smooth switcher.
- 3-finger pinch to close a window has no Windows equivalent.

## Customization
Edit `~/.config/touchegg/touchegg.conf` and restart the service:
```shell
sudo systemctl restart touchegg
```
To add per-app gestures, get an app's name by running this and clicking its window:
```shell
xprop | grep WM_CLASS
```
Then use it in `<application name="...">`. See the [Touchégg docs](https://github.com/JoseExposito/touchegg#configuration) for all gestures and actions.

## Troubleshoot
- **Nothing happens:** check you're on an X11 session (`echo $XDG_SESSION_TYPE` should print `x11`) and that the service is running (`systemctl status touchegg`).
- **Overview doesn't open:** check that **Overview** is bound to `Meta+W` in System Settings > Keyboard > Shortcuts, or change the `<keys>` in the config to match your binding.
- **Gestures conflict with Plasma's built-in touchpad gestures:** disable one of them.
- **Alt+Tab swipe does nothing:** make sure Alt+Tab is enabled in System Settings > Window Management > Task Switcher.


## Keywords
kde, kde plasma, touchegg, touchpad gestures, linux touchpad gestures, windows gestures linux, windows touchpad gestures on linux, precision touchpad linux, multitouch gestures, linux multitouch gestures, trackpad gestures linux, linux gestures, swipe gestures, three finger swipe linux, four finger swipe linux, show desktop gesture, switch virtual desktops gesture, plasma x11, kde plasma customization, linux touchpad config
