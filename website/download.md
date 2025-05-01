@def title = "JuliaMono font - Download"

# Download and installation

## Download

You can find the font files at [https://github.com/cormullion/juliamono/releases](https://github.com/cormullion/juliamono/releases).

On that Releases page, you can download:

- `JuliaMono-ttf .zip|.tar.gz` - just the TTF font files, in either Zip (.zip) or Tarball (.gz)

- `JuliaMono-webfonts .zip|.tar.gz` - just the webfonts (WOFF2), in either Zip (.zip) or Tarball (.gz)

- `JuliaMono .zip|.tar.gz` - both fonts and webfonts (TTF and WOFF), in either Zip (.zip) or Tarball (.gz)

I wouldn't recommend cloning the git repo, unless you want to download over 1 GB of outdated files and git diffs...

The raw source files (in Glyphs.app format) are at [https://github.com/cormullion/juliamonomaster](https://github.com/cormullion/juliamonomaster). You'll need a licensed copy of Glyphs to build the font from these files.

## Installation

### MacOS

To install and activate a font, launch Font Book from your Applications folder, and drag the font files into the middle pane labelled Font. If you're using a different font manager, you already know what to do. :)

#### MacOS Homebrew

On the latest version of Homebrew, you can install the fonts with:

```
brew install font-juliamono
```

### Windows

You can install a font for a single user or for all users. (Some applications (such as Java) don't see fonts unless they have been installed for all users.)

To install and activate a font on Windows, go to Computer |> Local Disk (C:) |> Windows |> Fonts. Locate the expanded .zip file folder, and drag the font files from there into the Fonts folder.

To install for all users, just right-click the font file(s) and choose Install for All Users. Administrator privileges are required.

### Linux - using Font Manager

You might want to install Font Manager:

```
sudo apt install font-manager
```

Then double-click on the font files and click Install on each one.

### Linux - on the command line

For Arch Linux, there is also a [package in the AUR](https://aur.archlinux.org/packages/ttf-juliamono/).

Locate your font folder. Might be one of:

```
~/.fonts
/usr/share/fonts/truetype/newfonts/
~/.local/fonts/
~/.local/share/fonts/
```

and copy the files there. You might want to (or have to) regenerate the font cache:

```
$ fc-cache -f -v
```

And verify installation:

```
$ fc-list | grep "JuliaMono"
```
