# st
Yet another [suckless st terminal](https://st.suckless.org/) custom version

## What this is

This is a custom build of the suckless st terminal with patches applied and custom configuration. This repo consists of the vanilla st-0.8.4 and the patches to apply to the source code.
One advantage over other repos with the patches applied is that here you _can_ apply more patches. You will, most likely, need to change the patch order and/or resolve conflicts.


## What patches are in this repo?
The following patches are available:
* [Alpha](https://st.suckless.org/patches/alpha/) (controlled in .Xresources)
* [Scrollback](https://st.suckless.org/patches/scrollback/) (shift+arrows)
* [Scrollback mouse](https://st.suckless.org/patches/scrollback/) (no MOD key required)
* [Boxdraw](https://st.suckless.org/patches/boxdraw/) (can be disabled in config)
* [Xresources](https://st.suckless.org/patches/xresources/)
* [Ligatures](https://st.suckless.org/patches/ligatures/)
* [SelectionColors](https://st.suckless.org/patches/selectioncolors/) (can be disabled in config)

In order for ligatures to show in the terminal, you will need a font that supports those. A good example is [Monoid](https://github.com/larsenwork/monoid)

\*Note: I am not the author of any of the patches. Credit is for these amazing authors. The work of this repo is to resolve conflicts when applying multiple patches that touch the same files. Because of this, patches *need* to be applied in order.\
\*\*Note: In order for Alpha patch to work, you need an X compositor, such as `compton` or `picom`

Patch `9-config.diff` contains some configs, feel free to change them to your liking. More options are available. See below


## Installation for dummies
```
git clone https://github.com/DasHammett/st.git
cd st
for i in patches/*.diff; do patch < $i; done
make
sudo make install
```
## How can I personalize fonts, colors and alpha?
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
Absolutely! Take a look at the `config.def.h` file and make the adjustments you would like, specially on the bindings. Changes need to be done AFTER applying the patches, otherwise will fail. If you already compiled st, then please edit `config.h` file instead. Remember you will need to compile and install again st.\
Changes in the `.Xresource` file just require the good ol' `xrdb -merge ~/.Xresources` and re-open st

