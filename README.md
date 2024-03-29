<div align="center">

# Catmoji
[![Latest Release](https://img.shields.io/github/v/release/catmoji/catmoji-colr?color=green&label=Release)](https://github.com/catmoji/catmoji-colr/releases/latest)
[![Discord](https://img.shields.io/discord/752858039337615452?color=blue&label=Discord)](https://discord.gg/32X67EB)
</div>

![preview](https://nekopon.pl/syf/catmojipreview.png)

Catmoji is a project to create a COLR/CPAL-based color OpenType font from the [Twemoji](https://twitter.github.io/twemoji/) collection of emoji images while overriding default face emojis with cat edits.

Note that the resulting font will **only** be useful on systems that support
layered color TrueType fonts; this includes Windows 8.1 and later,
as well as Mozilla Firefox and other Gecko-based applications running on
any platform.

Systems that do not support such color fonts will show blank glyphs
if they try to use this font.

## Getting started

This project makes use of [grunt-webfont](https://github.com/catmoji/grunt-webfont)
and an additional [node.js](https://nodejs.org/en/) script.
Therefore, installation of Node.js (Node.js 17 is recommended) (and its package manager [npm](https://www.npmjs.com/)) is a prerequisite.
Grunt will be installed as a package dependency — no need to install it globally.

The necessary tools can be installed via npm:

    # install dependencies from packages.json, including `grunt-webfont`.
    npm install

The build process also requires [fontforge](https://fontforge.github.io/)
and the TTX script from the [font-tools](https://github.com/behdad/fonttools/) package to be installed, and assumes standard Perl and Python are available.

Both FontForge and font-tools can be installed via package managers on Linux:

    # Ubuntu, for example
    sudo apt-get install fonttools fontforge python3-fontforge python3-distutils

## Building the font

Once the necessary build tools are all in place, simply running:

    make

should build the color-emoji font `build/Catmoji.ttf` from the source SVG files found in `twe-svg.zip` file and `extras`, `overrides` directories.

## Example of usage in Mozilla Firefox
Copy `Catmoji.ttf` from build directory to `~/.local/share/fonts/`

In your terminal emulator run: 

    fc-cache -f -v

Restart Mozilla Firefox if you had it open during fc-cache.

Visit `about:config` and find `"font.name-list.emoji"`

Replace its value with "Catmoji".

## Example of usage in Android (root access required)
(Systemless, recommended) Download Magisk module from releases and install it with Magisk Manager.

(/system method, not recommended) Download .ttf file from releases and replace `/system/fonts/NotoColorEmoji.ttf` or `/system/fonts/SamsungColorEmoji.ttf` with Catmoji depending what ROM you have.

After replacing font file or installing Magisk module, reboot and Catmoji will be seen instead of regular emojis.


## Installing Catmoji systemwide on Debian based distributions
Download Noto font release and put Catmoji .ttf file into `/usr/share/fonts/`.

Open `/etc/fonts/conf.d/45-generic.conf` file with your preferred text editor and above list of emoji fonts add

```
<alias binding="same">
        <family>Twemoji</family> <!-- Catmoji -->
        <default><family>emoji</family></default>
</alias>
```

Now open `/etc/fonts/conf.d/60-generic.conf` file with your preferred text editor and above list of emoji fonts add

```
<family>Twemoji</family>
```
