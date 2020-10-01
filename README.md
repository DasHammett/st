# st
Yet another [suckless st terminal](https://st.suckless.org/) st terminal custom version

## What this is

This is a custom build of the suckless st terminal with patches applied and custom configuration. This repo consists of the vanilla st-0.8.4 and the patches to apply to the source code.


## What patches are in this repo?
The following patches are available:
* Alpha (controlled in .Xresources)
* Scrollback (shift+arrows)
* Scrollback mouse (no MOD key required)
* Boxdraw
* Xresources
* Ligatures

In order for ligatures to show in the terminal, you will need a font that supports those. A good example is [Monoid](https://github.com/larsenwork/monoid)

## Installation for dummies
```
git clone https://github.com/DasHammett/st.git
cd st
for i in patches/*.diff; do patch < $i; done
make
sudo make install
```
## How can I personalize colors and alpha?
Edit your ```.Xresources``` file and add the relevant colors you would like, as well as the alpha and font to use wit the following format
```
*font: Monoid:style=Regular:pixelsize=12:antialias=true:autohint=false
*boldFont: Monoid:style=Bold:pixelsize=12:antialias=true:autohint=false
*italicFont: Monoid:style=Italic:pixelsize=12:antialias=true:autohint=false
*alpha: 0.4
*color0:           #3f3f3f
*color1:           #ff0f0f
*color2:           #00b45a
*color3:           #dfcf8f
*color4:           #3030ff
*color5:           #dc8cc3
*color6:           #8cd0d3
*color7:           #dcdccc
*color8:           #709080
*color9:           #cc5454
*color10:          #5EBDAB
*color11:          #E8E86C
*COLOR12:          #4186be
*color13:          #ec93d3
*color14:          #93e0e3
*color15:          #ffffff
```
These are global settings, it is also possible to configure them for just st by replacing `*` for `st.`\
(```st.font: Input:style=Regular:pixelsize=13:antialias=true:autohint=false``` for example)

## Can I futher customize st?
Absolutely! Take a look at the config.def.h file and make the adjustments you would like, specially on the bindings. Remember you will need to compile and install again st.\
Changes in the `.Xresource` file just require the good ol' `xrdb -merge ~/.Xresources` and re-open st

