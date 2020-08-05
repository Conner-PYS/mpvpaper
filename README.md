![Preview](https://github.com/GhostNaN/mpvpaper/blob/assests/preview.png)
# MPVPaper
### MPVPaper is a wallpaper program for wlroots based wayland compositors such as sway that allows you to ~~render glsl shaders~~ play videos with mpv as your wallpaper.
###### Or a fork of glpaper that plays videos using mpv, instead of rendering shaders.

## Dependencies
- mpv
- wlroots

## Building 
### Building Requirements:

- ninja
- meson
- pkg-config
### Instructions:
Clone:
```
git clone --single-branch https://github.com/GhostNaN/mpvpaper
```
Or if you have an older GPU and it doesn't start, use the OpenGL 3.0 version instead:
```
git clone --single-branch --branch opengl-3.0 https://github.com/GhostNaN/mpvpaper
```
Build:
```
cd mpvpaper
meson build --prefix=/usr
ninja -C build
```
Install:
```
ninja -C build install
```
## Installers 
### Arch Based:
AUR package: https://aur.archlinux.org/packages/mpvpaper-git/

## Usage
### Running
Simple example:
```
mpvpaper DP-2 /path/to/video
```
You can also forward mpv options by passing "--mpv-options" or "-o" like so:
```
mpvpaper -o "no-audio --loop-playlist shuffle" HDMI-A-1 www.url/to/playlist
```
### Controlling
If you would like to control MPVPaper while it's running, use a mpv input-ipc-server like this:
```
mpvpaper -o "input-ipc-server=/tmp/mpv-socket" DP-1 /path/to/video
```
Then input commands with socat. For example, toggle pause:
```
echo 'cycle pause' | socat - /tmp/mpv-socket
```
For more commands read: https://mpv.io/manual/master/#command-interface
## Notes
If you are on sway, you can get your display outputs with:
```
swaymsg -t get_outputs
```
And make sure you don't let swaybg stand in your way:
```
killall swaybg
```
## Acknowledgments
- glpaper for the boilerplate code, check em out here:
  - https://hg.sr.ht/~scoopta/glpaper
## License
This project is licensed under the GPLv3 License - see the [LICENSE](/LICENSE) file for details
