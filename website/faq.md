@def title = "JuliaMono font - FAQ"
@def mintoclevel=2
@def hasmath = true
@def hascode = true

# Frequently asked questions

\toc

## ‘Why⁉’

The typeface was introduced at the 2020 Julia Programming Language conference, JuliaCon (which was to be in Lisbon, Portugal, but a certain virus had other ideas) as my contribution to the festivities.

## ‘Where can I see it in action?’

Feel free to compare it with other fonts at [dev fonts](https://devfonts.gafi.dev/) and [www.programmingfonts.org](https://www.programmingfonts.org/#julia-mono).

If you use a lot of mathematics, visit the [mono-math.netlify.app](https://mono-math.netlify.app) site, which shows how Unicode math symbols look in various fonts.

To find out about JuliaMono's Unicode support, you could look at the Glyphs page on this site, or you could visit [glyphy.info](https://glyphy.info) and type a name (eg `interrobang`) or a hexadecimal number (eg `0x203d`), If the glyph is present in JuliaMono, you'll see a checkmark `✓`:

~~~<img src="/assets/glyphydotinfo.png" width="100%" alt="glyphy.info screen"> ~~~

Julia users can also do this without leaving the REPL. Install the Glyphy.jl package in the usual way, and then run it like this:

```julia
julia> using Glyphy

julia> glyphy("interrobang")

0203d   ‽   ✓    interrobang
02e18   ⸘   ✓    inverted interrobang
1f679   🙹   ✓    heavy interrobang ornament
1f67a   🙺   ✓    sans-serif interrobang ornament
1f67b   🙻   ✓    heavy sans-serif interrobang ornament
 found 5 glyphs matching "interrobang"

julia> glyphy(0x203d)

0203d   ‽   ✓    interrobang
```

## ‘I don’t like it as much as ``$(my_favourite_font)``’

**That’s not a question!** But I know what you mean. Choice of work environment (editor, font, colour scheme, background music, preferred beverage, etc.) is very much a personal thing, and over the hours, days, and weeks that you work with your particular setup, you’ll grow accustomed to it, and unfamiliar work environments will look unappealing or even ugly. You’d probably need to try any alternatives for a while before you get more accustomed to them.

## ‘How can I use the web fonts?’

Find the relevant CSS file, and add a link to a WOFF2 file stored on a server.

Option 1 (using the [jsdelivr](https://cdn.jsdelivr.net) content delivery network):

```
@font-face {
	font-family: JuliaMono-Light;
	src: url("https://cdn.jsdelivr.net/gh/cormullion/juliamono/webfonts/JuliaMono-Light.woff2");
}
```

Option 2 (using the [cdnjs](https://cdnjs.com/libraries/juliamono) content delivery network):

```
@font-face {
	font-family: JuliaMono-Light;
	src: url("https://cdnjs.cloudflare.com/ajax/libs/juliamono/0.048/JuliaMono-Light.woff2");
}
```

Then, in the area of the CSS where you control the appearance of monospaced text:

```css
pre {
	font-family: JuliaMono-Light;
}
code {
	font-family: JuliaMono-Light;
	}
```

Notice that the CDNJS version points to a specific version (e.g. v0.048 here), whereas the JSDELIVR version always retrieves the latest release.

You may prefer to serve the WOFF/2 fonts from your own server. One problem you might encounter is related to [Cross-origin resource sharing](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing), which on some browsers prevents one web page from downloading fonts from another.

There are some other options for the `@font-face` directive, which determine things like the behaviour of web pages while the fonts are still downloading, the range of characters you want to download, and so on.

## ‘How do I control features in VS Code or CSS?’

### VS-Code

In VS-Code you’ll find the font settings somewhere in the labyrinthine (but thankfully searchable) Settings department.

![VS Code settings](/assets/vscode-settings-1-800.png)

To control the display of contextual and stylistic alternates, click on the Edit Settings in JSON, and look for `editor.fontLigatures`:

![VS Code settings](/assets/vscode-settings-2-800.png)

This uses the feature codes ([listed here](/#contextual_and_stylistic_alternates)). These should be switched on or off in a single line.

For example, if you like a slashed zero, a single story g, and fancier HTML comments, you want `zero`, `ss01`, and `ss13` to be switched on, so type:

```css
 selector {
	 "editor.fontLigatures": "'zero', 'ss01', 
       'ss13'"
	}
```

If you don’t like contextual alternates, but quite fancy a lighter asterisk, use this:

```css
 selector {
	 "editor.fontLigatures": "'calt' off, 'ss05'",
     }
```

### CSS

In a CSS stylesheet, you can specify the font with the required CSS selectors:

```css
@font-face {
    font-family: JuliaMono-Light;
    src: url("https://cdn.jsdelivr.net/gh/cormullion/juliamono/webfonts/JuliaMono-Light.woff2");
}
```

And apply them to HTML elements using something like:

```css
p {
	font-family: JuliaMono-Light;
	font-size: 1.2em;
	font-style: normal;
}
```

You can switch off the contextual alternates (such as `->` and `=>`) for a given selector with:

```css
selector {
	font-variant-ligatures: no-contextual;
	}
```

Or on (if it’s not enabled by default) with:

```css
selector {
	font-variant-ligatures: contextual;
	}
```

Select any stylistic sets in a single line. For example:

```css
selector {
    font-variant-ligatures: no-contextual;
	font-feature-settings: "zero", "ss02";
	}
```

~~~
<p>switches off contextual alternates and enables the slashed zero (<span class="code_ss_on">0</span>) and the simpler "g" (<span class="code_ss_on">g</span>).</p>
~~~

<!--  force a paragraph  -->

## ‘Can I use this font in a Jupyter notebook? And how do I do it?’

It’s a good question. Some browsers these days are reluctant to give you access to things stored on your own local disks, “for security reasons”. But a local copy of the font may be available and accessible on your particular set-up. If not, you could try using web fonts, as above. For example, if there’s a Jupyter CSS file here:

```
~/.jupyter/custom/custom.css
```

you could add definitions like this:

```css
@font-face {
	font-family: JuliaMono-Light;
	src: url("https://cdn.jsdelivr.net/gh/cormullion/juliamono/webfonts/JuliaMono-Light.woff2");
}

.rendered_html table{
    font-size: 16px !important;
}

div.input_area {
    background: #def !important;
    font-size: 16px !important;
}

div.output_area pre{
    background: #def !important;
    font-size: 16px !important;
    font-family: JuliaMono-Light;
}

.CodeMirror {
    font-size: 16px !important;
    font-family: "JuliaMono-Light" !important;
    font-feature-settings: "zero", "ss01";
    font-variant-ligatures: contextual;
}
```

which downloads the font once and is then available to applications.

~~~
<div id="enlargewrap">
    <a class="enlarge">
        <img src="/assets/jupyter-example.png" width = "300" alt="screenshot of jupyter editor">
            <span>
                <img src="/assets/jupyter-example.png" width = "800" alt="screenshot of jupyter editor">
            </span>
    </a>
</div>
~~~

## ‘Is it just for Julia coding? How does it “work well with” Julia?’

No, that's just the language I use. You can use the font for any purpose, with any language.

```css
# In python3
# By default the encoding is "utf-8"
import sys

# printing the default encoding
print("The default encoding for python3 is:", sys.getdefaultencoding())

# to define string as unicode
# we need to prefix every string with u"...."
p = u"\u2119"
y = u"\u01b4"
t = u"\u2602"
h = u"\u210c"
o = u"\u00f8"
n = u"\u1f24"

# printing Python
print(p+y+t+h+o+n)
The default encoding for python3 is: utf-8
ℙƴ☂ℌøἤ
```

or APL (technically [BQN](https://github.com/mlochbaum/BQN)):

```css
 ⊑+`∘⌽⍟12↕2  # The 12th Fibonacci number
```

For Julia specifically:

* it has all the glyphs used in the Unicode Input chapter of the Julia documentation (except for the emojis)
* a few of the glyphs and ligatures were designed with the Julia programming language in mind
* the font contains special features such as contextual alternates, stylistic sets, and “ligatures” that complement Julia syntax

## ‘How do I use the font in plots, say in Plots.jl?’

Another great question. Are you sure you want a monospaced font on your plot? If you do, it should be easy enough to ask for the font when you plot. But it’s never as simple as you want it to be, as is usual in the world of fonts.

I know very little about plotting in Julia, but some investigations suggest that:

- `pyplot()` works well, mostly, as does Makie.jl
- some backends do their own thing with fonts. For example, I couldn’t persuade the GR backend to use JuliaMono at all.

Here’s some code that uses JuliaMono for a plot. The plot shows the frequency of occurrence of every Unicode character used in the Julia git repository, and uses the characters as plot markers. I went through every text file and totalled all the characters - there are 956044 letter “e”s, and so on. I’m using `pyplot()`; the `freqs` DataFrame holds the characters and the counts. I’ve created a few font objects using `Plots.font()`, which makes it easier to use different text styles in the `plot()` function. I haven’t yet worked out how to use the different weights of a font family.

```
using Plots, Plots.PlotMeasures
pyplot()
theme(:dark)

juliamonofont8 = Plots.font(family="JuliaMono", 8,
    halign=:center, colorant"white")
juliamonofont12 = Plots.font(family="JuliaMono", 12,
    halign=:center, colorant"white")
juliamonofont80 = Plots.font(family="JuliaMono", 80,
    halign=:center, colorant"grey30")

annotation = "counting character frequencies\nin Julia source files "

p = plot(1:100,
    freqs[1:100, 2],
    fontfamily         = "JuliaMono",
    margin             = 20mm,
    yaxis              = :log10,
    annotation         = [
        (50, 1000, Plots.text(annotation, juliamonofont12)),
        (80, 1_000_000, Plots.text("", juliamonofont80))
        ],
    linewidth          = 0.25,
    series_annotations = Plots.text.(freqs[1:100, 1], Ref(juliamonofont8)),
    xlabel             = "← more frequent | less frequent → ",
    ylabel             = "occurrences (log scale) ",
    labelfontsize      = 6,
    titlefontsize      = 14,
    formatter          = :plain,
    size               = (800, 500),
	title              = "Top 100 characters\nin the Julia github repo ",
    legend             = false,
    )

display(p)
```

![frequency counts](/assets/julia-frequencies.svg)

The top 9 characters - “etanirsol” - are a good match for the typical English frequency count e.g. “etarionsh”. It’s to be expected that parentheses make a very good showing, here.

Although over 3600 unique characters occur in the Julia documentation, about 3000 of them appear just once. All of them, except the emojis which aren’t in JuliaMono, could be plotted, but the long tail isn’t very interesting visually.

For plotting emoji characters, you’ll have to dive into the internals of the plots system...

Notice that the y-axis labels are in DejaVu Sans, provided with matplotlib. That’s because the `:log10` scaling code does its own $ \LaTeX $-y business, ignoring the current font. However, at least I was able to insert the Julia logo successfully, since it’s part of the JuliaMono font.

## ‘Can I use it in a $ \LaTeX $ document?’

In a $ \LaTeX $ document, you should be able to define and use local fonts.

Robert Moss put together an excellent package to help negotiate the various font issues that you might encounter when using Unicode and $ \LaTeX $:

[A custom Julia language style for the LaTeX listings package, and Unicode support for the JuliaMono font in a `lstlisting` environment.](https://github.com/mossr/julia-mono-listings).

An earlier approach that worked for me is as follows:

In your $ \LaTeX $ source file, define the mono font and point to the local pathname:

```
\usepackage{fontspec}
\usepackage{unicode-math}
\usepackage[utf8]{inputenc}
\usepackage{minted}

\setmonofont{JuliaMono-Regular.ttf}[
    Path = /Users/me/Library/Fonts/,
    Contextuals = Alternate,
    CharacterVariant=1,
    Scale = MatchLowercase,
	BoldFont = JuliaMono-Bold.ttf,
	%Numbers = OldStyle
]
```

Then you can use something like `minted` to format the code.

~~~
<div id="enlargewrap">
    <a class="enlarge">
        <img src="/assets/latex-example.png" width = "300" alt="screenshot of latex ">
            <span>
                <img src="/assets/latex-example.png" width = "800" alt="screenshot of latex ">
            </span>
    </a>
</div>
~~~

(I used the lualatex engine.)

## ‘Aren’t these font files too big?’

It depends if you mean the web fonts or the ‘desktop’ fonts. Web fonts come in two flavours, `.WOFF` and `.WOFF2`, where the `2` indicates a more recent and slightly more compact format. `JuliaMono-Light.woff2` is 837KB - the size of a PNG image, perhaps?

The `.TTF` versions are getting on for 2.5MB each. (See [Does it work on Windows]([this](/faq/#does_it_work_on_windows)).)

For comparison, the Themes folder of `.CSS` files for the Julia manual (and for every manual built with Documenter.jl since v0.21) is about 700KB. So in that light the WOFF2 fonts aren’t that bad. Of course, the two Google fonts downloaded by every Julia document (Lato and Roboto) are tiny, at 14KB and 11KB, with 221 glyphs in each.

So, if you’re building a website, or designing for mobile applications, the size of the WOFF2 file(s) might be an important factor to weigh against the advantages of having predictable character sets. (This site is a bit of an exception, for obvious reasons.) Note that you can specify font subsets in the CSS using the **unicode-range** feature, which defines a restricted set of characters which you know are going to be used, so that users don’t download any that they won’t need.

You could consider using the ‘-Latin’ variants to obviate the initial loading time. These have a limited number of glyphs (restricted to the basic Latin character set), but will at least be quick to download.

## ‘How is this different from any other Unicode font?’

You’re right, of course, there are many coding fonts, all perfectly adequate for the task of programming in Julia and most other languages. Comparing two different fonts is a matter of how important small similarities and differences are. Perhaps with one font you’ll see the occasional empty box or odd replacement rather than the character you were hoping for. Or perhaps sometimes you won’t like a particular glyph.

More likely, though, the overall ‘feel’ of a new and unfamiliar font - too narrow, too wide, too dense, too light, too quirky, too dull, too consistent, too variable - is a matter of personal taste, immune to objective measurement.

Most people probably can’t tell the difference between Helvetica and Arial, and certainly aren’t going to be bothered about minor differences between JuliaMono and other coding fonts. But that’s fine. Just stick to your current favourites!

## ‘Where are the design notes? Don't typeface designers love talking about how it was designed?’

Oh, yes. Well, the design goals of JuliaMono were to make a programmming font that's readable, easy to use, unquirky, simple, and including most of the characters (glyphs) required for modern scientific and technical programming.

Matthew Carter, the famous typeface designer, talks about how the aim when designing a font is to create “a beautiful set of letters” rather than “a set of beautiful letters”; the idea being that making the characters in the font harmonious and consistent with each other is of primary importance. But I would suggest that most typefaces, such as Matthew Carter’s familiar Georgia typeface, are designed to communicate prose in text languages - English, French, Russian - where the words are familiar recognizable units, and there’s much redundancy, such that predictability assists reading. You want the eye to glide swiftly and easily over the page.

However, programming and coding typefaces have to address different problems:

- code can often consist of sequences of non-language characters

- a single variable name might combine latin and greek letters and various punctuation characters

- often you want to compare areas of text with other areas (such as code laid out in tabular form)

- sometimes the characters are placed so as to form larger patterns, such as bitstrings, or array contents

- punctuation marks are no longer just hints to guide readers, but critical pieces of syntax that might completely alter the meaning of the surrounding text

- the programmer doesn't read code in the same way that they would read prose

- there’s much less redundancy in code: when reading prose you’ll find it easy to overlook misspellings and typos, when working with code you’ll want to find the misspellings and typos - you don’t really want your eye to glide smoothly past these

So I'd argue that making letters easy to distinguish is as important as making them harmoniously consistent. A primary goal is to make characters that tend to be similar different. For example, the digits 3, 8, and 0 have similar curved tops, so the 3 has a flat-top, and the 0 is more distinctive. The letters a, g, p, and q in many fonts often have the same round shape sitting on the baseline; by adopting the two-storey design for a and g there are two fewer letters to be confused. The asymmetries of characters like B and 8 have been enhanced. And so on.

The shapes aren’t compressed or condensed. The glyphs aren’t fashionably thin. It might feel quite “airy” because of the generous spacing. The punctuation is quite solid and possibly larger than you’d expect (my eyesight is probably poorer than yours!). Perhaps it’s not so good for non-code text (do you find this web page difficult to read?).

If you want to find out more about typeface and font legibility, a good place to start would be to see the work of [Sophie Beier](http://sofiebeier.dk).

## ‘Where’s the source? What’s the licence?‘

The font is OFL/SIL-licensed, and you can find the source [here](https://github.com/cormullion/juliamonomaster). The SIL license allows you to do almost anything you want, **except** re-issue it under tha same name or with a different licence.

## ‘Is it finished?’

Some say that projects are never finished, just abandoned. As of December 2023, I’m still making small changes and fixes, and it’s currently at version 0.052. Always download the latest version if you want the typeface to perform at its best. There will probably always be minor releases in the future, particularly if the Unicode Consortium introduce lots of new characters, and so the font will probably never be finished.

## ‘Why don’t these accents/marks work properly?’

Unicode allows you to combine characters. In the Julia REPL, you can type a character and then modify it by adding a mark or diacritic. For example:

```
e\vec
```

displays as

```
e⃗
```

and the arrow mark is displayed above the character. These **combining marks** are listed in the Unicode Input section of the Julia documentation. It’s sometimes possible to add more than one:

```
e\vec\dot
```

which JuliaMono renders like this:

```
e⃗̇
```

However, as usual, each terminal does its own thing, with varying results:

~~~
<div id="enlargewrap">
    <a class="enlarge">
        <img src="/assets/font-terminal-comparison.png" width = "300" alt="screenshots terminal emulators">
            <span>
                <img src="/assets/font-terminal-comparison.png" width = "800" alt="screenshots terminal emulators">
            </span>
    </a>
</div>
~~~

Some terminal applications choose not to implement all OpenType features, possibly for performance reasons.

If it does work for you, this is fun:

```
jul\iota\ddot\dota
```

giving:

```julia
julϊ̇a
```

## ‘Does it work on macOS?’

Yes. JuliaMono works well, with most modern MacOS text editors, such as Visual Studio Code, Sublime Text, the excellent free CotEditor, Panic's new Nova editor, BBEdit, and TextEdit, among others. If these editors support OpenType features such as stylistic alternatives and ligatures (not all do), these features of JuliaMono should work well.

## ‘Does it work on Linux?’

Yes.

Font management in Linux may require you to become familiar with the `fontconfig` program. And it may be necessary to provide an additional configuration file (in `/etc/fonts/local.conf` for example), that contains instructions like the following:

```html
<alias>
    <family>monospace</family>
    <prefer>
	    <family>JuliaMono</family>
	</prefer>
</alias>
```

With some older terminal software, the ligatures and alternate characters may cause problems, or not work at all. Not all terminals choose to display ligatures, others are just confused by fonts that have them.

## ‘Does it work on Windows?’

The font works quite well on a good quality display, but will struggle to maintain quality when displayed on low-resolution displays.

On Windows, the shapes of letters are distorted in order to place the important features of letters on pixels, rather than ‘between’ pixels (which could make features disappear). On high-resolution displays, as found on Apple devices, it isn't necessary to distort letter shapes in this way. The distortion is controlled by a process called ‘hinting’. On Windows displays, you may find that there is unevenness and variations in thickness and alignments, particularly at smaller sizes and on lower resolution screens. This is due to the hinting process generating distorted shapes so as to target pixels.

JuliaMono is an OTF/TTF-flavoured font that contains hinting instructions. Hinted fonts are larger than OTF/CFF (PostScript-flavour) as a consequence.

## ‘What about a nerdfonts version?’

[nerdfonts](https://www.nerdfonts.com) adds about four thousand extra glyphs to a font. It does this by creating a new font that combines an existing font’s glyphs with a bunch of new ones, using a FontForge Python script.

JuliaMono concentrates on the Unicode standard glyphs, whereas Nerdfonts adds many non-standard glyphs such as product and brand logos, trade names, icons for dozens of file extensions, programming languages, commercial applications, and a fair number of other characters such as weather symbols. It’s aimed at a much wider audience. The Nerdfonts glyph set doesn’t overlap too much with JuliaMono's.

You can download a Nerdfonts-enhanced version of JuliaMono [here](https://github.com/mietzen/juliamono-nerd-font/tree/main), thanks to the hard work of [@mietzen](https://github.com/mietzen)!

## ‘What about JuliaSans?’

One day perhaps.


