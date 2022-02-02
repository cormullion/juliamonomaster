@def title = "JuliaMono font - Download"

# Download and install

#### Download

You can find the font files at [https://github.com/cormullion/juliamono](https://github.com/cormullion/juliamono).

I'd suggest downloading the ZIP file, or downloading the individual files (click, then "Download") just the ones you want. I wouldn't recommend cloning the git repo, unless you want over 1GB of old outdated font files on your disk.

### Installation

#### MacOS

To install and activate a font, launch Font Book from your Applications folder, and drag the font files into the middle pane labelled Font. If you're using a different font manager, you already know what to do. :)

##### MacOS Homebrew

On the latest version of Homebrew, you can install the fonts with:

```
brew tap homebrew/cask-fonts
brew install --cask font-juliamono
```

#### Windows

You can install a font for a single user or for all users. (Some applications (such as Java) don't see fonts unless they have been installed for all users.)

To install and activate a font on Windows, go to Computer |> Local Disk (C:) |> Windows |> Fonts. Locate the expanded .zip file folder, and drag the font files from there into the Fonts folder.

To install for all users, just right-click the font file(s) and choose Install for All Users. Administrator privileges are required.

#### Linux - using Font Manager

You might want to install Font Manager:

```
sudo apt install font-manager
```

Then double-click on the font files and click Install on each one.

#### Linux - on the command line

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
