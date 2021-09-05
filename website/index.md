@def title = "The JuliaMono Typeface"
@def hasmath = true
@def hascode = true

### JuliaMono - a monospaced font for scientific and technical computing

~~~<img src="/assets/specimen_1.png" width="100%" alt="specimen image 1"> ~~~

JuliaMono is a monospaced typeface designed for programming and in other text editing environments that require a wide range of specialist and technical Unicode characters. It was intended as an experiment to be presented at the 2020 JuliaCon conference in Lisbon, Portugal.

JuliaMono is:

- free
- distributed with a liberal licence [^licence]
- suitable for scientific and technical programming as well as for general purpose hacking
- full of Unicode goodness
- easy to use, simple, unquirky, friendly, and approachable
- available for MacOS, Unix, and Windows [^windows]

This site uses JuliaMono for all text; if your browser can’t[^ohdear] (or you didn’t allow it to) download and display web fonts, you’ll only see the font in action in the images. You’ll see three large dots here when/if the font has been successfully downloaded:

~~~<span style="text-align: center;font-family: JuliaMono-Regular;font-size:4rem;"> (  ) </span>~~~

To download and install JuliaMono, see the instructions [here](/download/).

### Type anything here. Nobody’s looking.
~~~
<textarea class="tryit" rows="4" cols="50">
</textarea>
~~~

### Screenshots

Editing code in [Juno](https://github.com/JunoLab/Juno.jl).

~~~
<div id="enlargewrap">
    <a class="enlarge">
        <img src="/assets/juno-example.png" width = "300" alt="screenshot of Juno editor">
            <span>
                <img src="assets/juno-example.png" width = "800" alt="screenshot of Juno editor">

            </span>
    </a>
</div>
~~~

And in [VS Code](https://www.julia-vscode.org).

~~~
<div id="enlargewrap">
    <a class="enlarge">
        <img src="/assets/vscode-example.png" width = "300" alt="screenshot of VS code editor">
            <span>
                <img src="assets/vscode-example.png"  width = "800" alt="screenshot of VS code editor">
            </span>
    </a>
</div>
~~~

And in [Vim](https://www.vim.org):

~~~
<div id="enlargewrap">
    <a class="enlarge">
        <img src="/assets/vim-example.png" width = "300" alt="screenshot of VIM editor">
            <span>
                <img src="assets/vim-example.png" width = "800" alt="screenshot of VIM editor">
            </span>
    </a>
</div>
~~~

And in [Emacs](https://www.gnu.org/software/emacs/):

~~~
<div id="enlargewrap">
    <a class="enlarge">
        <img src="/assets/emacs-example.png" width = "300" alt="screenshot of emacs editor">
            <span>
                <img src="assets/emacs-example.png" width = "800" alt="screenshot of emacs editor">
            </span>
    </a>
</div>
~~~

### Examples

~~~<img src="/assets/specimen_2.png" width="100%" alt="specimen image 2"> ~~~

~~~<img src="/assets/specimen_3.png" width="100%" alt="specimen image 3"> ~~~

The following examples will be rendered in JuliaMono by your browser (if it’s successfully downloaded the web font versions), so I hope what you see here is close to what I made.

The CSS markup applied to the following code also uses another weight of the typeface JuliaMono-Medium, which is a smidgeon bolder:

```julia
using Zygote: @adjoint
function ignore(f)
  try return f()
        catch e; return 0; end
end
@adjoint function ignore(f)
  try Zygote._pullback(__context__, f)
  catch e
    0, ȳ -> nothing
  end
end
```

There are different weights of JuliaMono[^masters], so you can control the amount of contrast you have in your highlighted code:

~~~<span style="font-family: JuliaMono-Light;">JuliaMono-Light</span>~~~

~~~<span style="font-family: JuliaMono-Regular;">JuliaMono-Regular</span>~~~

~~~<span style="font-family: JuliaMono-Medium;">JuliaMono-Medium</span>~~~

~~~<span style="font-family: JuliaMono-Bold;">JuliaMono-Bold</span>~~~

~~~<span style="font-family: JuliaMono-ExtraBold;">JuliaMono-ExtraBold</span>~~~

~~~<span style="font-family: JuliaMono-Black;">JuliaMono-Black</span>~~~

They all occupy the same amount of horizontal space, so they can be mixed without losing alignment.

Each of these also has a matching italic variant: so JuliaMono-Light has JuliaMono-LightItalic, and so on.

(There are also versions of two of the fonts with “Latin” in the name: these are stripped down versions supporting just the basic MacRoman/Windows1252 “Latin” character sets. You probably don't want to use these - they're intended for use mainly as place-holders, of interest if you want to have more control over font loading times in web browser-based applications.)

In the hands of a virtuoso (such as Dr Zygmunt Szpak, the author of the following Julia code fragment[^zscode]), the range of available Unicode characters can be quite expressive:

```
function T(𝛉::AbstractArray,
           𝒞::Tuple{AbstractArray,
           Vararg{AbstractArray}},
           𝒟::Tuple{AbstractArray, Vararg{AbstractArray}})
    ⊗ = kron
    l = length(𝛉)
    𝐈ₗ = SMatrix{l,l}(1.0I)
    𝐈ₘ = SMatrix{1,1}(1.0I)
    𝐓 = @SMatrix zeros(l,l)
    N = length(𝒟[1])
    ℳ, ℳʹ = 𝒟
    Λ₁, Λ₂ = 𝒞
    𝚲ₙ = @MMatrix zeros(4,4)
    𝐞₁ = @SMatrix [1.0; 0.0; 0.0]
    𝐞₂ = @SMatrix [0.0; 1.0; 0.0]
    for n = 1:N
        index = SVector(1,2)
        𝚲ₙ[1:2,1:2] .=  Λ₁[n][index,index]
        𝚲ₙ[3:4,3:4] .=  Λ₂[n][index,index]
        𝐦    = hom(ℳ[n])
        𝐦ʹ   = hom(ℳʹ[n])
        𝐔ₙ   = (𝐦 ⊗ 𝐦ʹ)
        ∂ₓ𝐮ₙ = [(𝐞₁ ⊗ 𝐦ʹ) (𝐞₂ ⊗ 𝐦ʹ) (𝐦 ⊗ 𝐞₁) (𝐦 ⊗ 𝐞₂)]
        𝐁ₙ   = ∂ₓ𝐮ₙ * 𝚲ₙ * ∂ₓ𝐮ₙ'
        𝚺ₙ   = 𝛉' * 𝐁ₙ * 𝛉
        𝚺ₙ⁻¹ = inv(𝚺ₙ)
        𝐓₁   = @SMatrix zeros(Float64,l,l)
        for k = 1:l
            𝐞ₖ = 𝐈ₗ[:,k]
            ∂𝐞ₖ𝚺ₙ = (𝐈ₘ ⊗ 𝐞ₖ') * 𝐁ₙ * (𝐈ₘ ⊗ 𝛉) + (𝐈ₘ ⊗ 𝛉') * 𝐁ₙ * (𝐈ₘ ⊗ 𝐞ₖ)
            # Accumulating the result in 𝐓₁ allocates memory,
            # even though the two terms in the
            # summation are both SArrays.
            𝐓₁ = 𝐓₁ + 𝐔ₙ * 𝚺ₙ⁻¹ * (∂𝐞ₖ𝚺ₙ) * 𝚺ₙ⁻¹ * 𝐔ₙ' * 𝛉 * 𝐞ₖ'
        end
        𝐓 = 𝐓 + 𝐓₁
    end
    𝐓
end
```

### Languages

Here are some samples of various languages[^languages] :

~~~
<table class="language">
	<tr>
		<td>Ancient Greek</td>
		<td>Ἄδμηθ’, ὁρᾷς γὰρ τἀμὰ πράγμαθ’ ὡς ἔχει, λέξαι θέλω σοι πρὶν θανεῖν ἃ βούλομαι.</td>
	</tr>
	<tr>
		<td>Bulgarian</td>
		<td>Я, пазачът Вальо уж бди, а скришом хапва кюфтенца зад щайгите.</td>
	</tr>
	<tr>
		<td>Catalan</td>
		<td>«Dóna amor que seràs feliç!». Això, il·lús company geniüt, ja és un lluït rètol blavís d’onze kWh.</td>
	</tr>
	<tr>
		<td>Czech</td>
		<td>Zvlášť zákeřný učeň s ďolíčky běží podél zóny úlů</td>
	</tr>
	<tr>
		<td>Danish</td>
		<td>Quizdeltagerne spiste jordbær med fløde, mens cirkusklovnen Walther spillede på xylofon.</td>
	</tr>
	<tr>
		<td>English</td>
		<td>Sphinx of black quartz, judge my vow.</td>
	</tr>
	<tr>
		<td>Estonian</td>
		<td>Põdur Zagrebi tšellomängija-följetonist Ciqo külmetas kehvas garaažis</td>
	</tr>
	<tr>
		<td>Finnish</td>
		<td>Charles Darwin jammaili Åken hevixylofonilla Qatarin yöpub Zeligissä.</td>
	</tr>
	<tr>
		<td>French</td>
		<td>Voix ambiguë d’un cœur qui au zéphyr préfère les jattes de kiwi.</td>
	</tr>
	<tr>
		<td>Georgian</td>
		<td>სწრაფი ყავისფერი მელა ახტება ზარმაც ძაღლს.</td>
	</tr>
	<tr>
		<td>German</td>
		<td>Victor jagt zwölf Boxkämpfer quer über den großen Sylter Deich.</td>
	</tr>
	<tr>
		<td>Greek</td>
		<td>Ταχίστη αλώπηξ βαφής ψημένη γη, δρασκελίζει υπέρ νωθρού κυνός.</td>
	</tr>
	<tr>
		<td>Guarani</td>
		<td>Hĩlandiagua kuñanguéra oho peteĩ saʼyju ypaʼũme Gavõme omboʼe hag̃ua ingyleñeʼẽ mitãnguérare neʼẽndyʼỹ.</td>
	</tr>
	<tr>
		<td>Hungarian</td>
		<td>Jó foxim és don Quijote húszwattos lámpánál ülve egy pár bűvös cipőt készít.</td>
	</tr>
	<tr>
		<td>IPA</td>
		<td>[ɢʷɯʔ.nas.doːŋ.kʰlja] [ŋan.ȵʑi̯wo.ɕi̯uĕn.ɣwa]</td>
	</tr>
	<tr>
		<td>Icelandic</td>
		<td>Kæmi ný öxi hér, ykist þjófum nú bæði víl og ádrepa.</td>
	</tr>
	<tr>
		<td>Irish</td>
		<td>Ċuaiġ bé ṁórṡáċ le dlúṫspád fíorḟinn trí hata mo ḋea-ṗorcáin ḃig.</td>
	</tr>
	<tr>
		<td>Latvian</td>
		<td>Muļķa hipiji mēģina brīvi nogaršot celofāna žņaudzējčūsku.</td>
	</tr>
	<tr>
		<td>Lithuanian</td>
		<td>Įlinkdama fechtuotojo špaga sublykčiojusi pragręžė apvalų arbūzą.</td>
	</tr>
	<tr>
		<td>Macedonian</td>
		<td>Ѕидарски пејзаж: шугав билмез со чудење џвака ќофте и кељ на туѓ цех.</td>
	</tr>
	<tr>
		<td>Norwegian</td>
		<td>Jeg begynte å fortære en sandwich mens jeg kjørte taxi på vei til quiz</td>
	</tr>
	<tr>
		<td>Polish</td>
		<td>Pchnąć w tę łódź jeża lub ośm skrzyń fig.</td>
	</tr>
	<tr>
		<td>Portuguese</td>
		<td>Luís argüia à Júlia que «brações, fé, chá, óxido, pôr, zângão» eram palavras do português.</td>
	</tr>
	<tr>
		<td>Romanian</td>
		<td>Înjurând pițigăiat, zoofobul comandă vexat whisky și tequila.</td>
	</tr>
	<tr>
		<td>Russian</td>
		<td>Широкая электрификация южных губерний даст мощный толчок подъёму сельского хозяйства.</td>
	</tr>
	<tr>
		<td>Scottish</td>
		<td>Mus d’fhàg Cèit-Ùna ròp Ì le ob.</td>
	</tr>
	<tr>
		<td>Serbian</td>
		<td>Ајшо, лепото и чежњо, за љубав срца мога дођи у Хаџиће на кафу.</td>
	</tr>
	<tr>
		<td>Spanish</td>
		<td>Benjamín pidió una bebida de kiwi y fresa; Noé, sin vergüenza, la más champaña del menú.</td>
	</tr>
	<tr>
		<td>Swedish</td>
		<td>Flygande bäckasiner söka hwila på mjuka tuvor.</td>
	</tr>
	<tr>
		<td>Turkish</td>
		<td>Pijamalı hasta yağız şoföre çabucak güvendi.</td>
	</tr>
	<tr>
		<td>Ukrainian</td>
		<td>Чуєш їх, доцю, га? Кумедна ж ти, прощайся без ґольфів!</td>
	</tr>
</table>

~~~

### Unicode coverage

~~~<img src="/assets/unicode-sample.svg" width="100%" alt="Unicode sampler"> ~~~

One of the goals of JuliaMono is to include most of the characters that a typical programmer or monospaced-font user would reasonably expect to find. (Except for all those emojis - they are best handled by the operating system.) Here's a few less common ones:  

~~~<img src="/assets/specimen_6.png" width="100%" alt="specimen image 6"> ~~~

In JuliaMono, every character is the same width, because this is a [monospaced](https://en.wikipedia.org/wiki/Monospaced_font) typeface. Usually, typefaces with a lot of Unicode mathematical symbols are not monospaced, because they’re intended for use in prose and $ \LaTeX $ applications, rather than in programming code. You probably want ∑s in your code rather than $ \sum $s, because the big ones will upset your formatting.

From a design perspective, forcing every character into the same size box is a problem. It’s like fitting every human being of whatever shape or size into identical airplane seats - some characters are bound to look uncomfortable. There’s never quite enough room for a nice-looking “m” or “w”.

The Julia package [UnicodePlots.jl](https://github.com/Evizero/UnicodePlots.jl) uses various Unicode characters to plot figures directly in a terminal window. [^linespacing]

~~~
<div id="enlargewrap">
    <a class="enlarge">
        <img src="/assets/unicodeplots.png" width = "300" alt="UnicodePlots in action">
            <span>
                <img src="/assets/unicodeplots.png" width = "800" alt="UnicodePlots in action">
            </span>
    </a>
</div>
~~~

and the [ImageInTerminal.jl](https://github.com/JuliaImages/ImageInTerminal.jl) package uses Unicode characters to display images in the terminal:

~~~
<div id="enlargewrap">
    <a class="enlarge">
        <img src="/assets/imageinterminal.png" width = "300" alt="ImageInTerminal">
            <span>
                <img src="/assets/imageinterminal.png" width = "800" alt="ImageInTerminal">
            </span>
    </a>
</div>
~~~

It’s also a good idea to support box-drawing characters, such as the ones used for displaying DataFrames.jl output (terminal permitting):

```
julia> df = DataFrame(A=samples, B=glyphs)
df = 10×2 DataFrame
│ Row │ A              │ B                   │
│     │ String         │ String              │
├─────┼────────────────┼─────────────────────┤
│ 1   │ sample 1       │ ▁▂▁▁▂▄▅▁▄▁▁▅▆▂▇▅▂▇  │
│ 2   │ sample 2       │ ▁▂▄▁▁▃▁▆▂▆▃▁▂▃▂▇▄   │
│ 3   │ sample 3       │ ▁▆▇▁▃▇▇▆▅▅▄▇▇▅▅▇▄▂  │
│ 4   │ sample 4       │ ▅▁▄▁▆▃▁▃▇▂▂▇▅▇▃▆▃▁  │
│ 5   │ sample 5       │ ▆▂▁▂▇▆▃▅▅▄▆▇▄▇▆▁▇   │
│ 6   │ sample 6       │ ▁▁▇▂▂▇▃▅▂▂▆▂▄▄▁▄▂▇▆ │
│ 7   │ sample 7       │ ▂▃▂▁▁▇▁▂▆▂▁▇▁▄▃▂▁▄  │
│ 8   │ sample 8       │ ▄▄▁▂▄▁▅▁▅▁▂▂▇▂▁▃▄▄  │
│ 9   │ sample 9       │ ▁▁▁▂▁▆▃▄▄▁▂▂▃▂▁▅▁▆▃ │
│ 10  │ sample 10      │ ▁▇▄▂▅▃▇▁▇▇▆▄▇▅▄▂▄▅▄ │
```

(Can you spot the little used and sadly mathematically-unsupported “times” (×) character?)

For a comparison of JuliaMono with other math-capable monospaced fonts, visit [mono-math.netlify.app](https://mono-math.netlify.app), which shows how Unicode math symbols look.

JuliaMono is quite greedy[^greedy], and contains quite a few Unicode glyphs.

~~~<img src="/assets/barchart.svg" width="100%" alt="silly barchart"> ~~~

(Of course, size isn’t everything - quality can beat quantity, and other fonts will offer different experiences[^otherfonts]).

If you want to know whether you can use a Unicode character as an identifier in your Julia code, use the undocumented function `Base.isidentifier()`. So, for example, if you have the urge to use a dingbat (one of the classic [Herman Zapf dingbat](https://en.wikipedia.org/wiki/Zapf_Dingbats) designs) as a variable name, you could look for something suitable in the output of this:

```
julia> for n in 0x2700:0x27bf
			Base.isidentifier(string(Char(n))) && print(Char(n))
	   end
✀✁✂✃✄✅✆✇✈✉✊✋✌✍✎✏✐✑✒✓✔✕✖✗✘✙✚✛✜✝✞✟✠✡✢✣✤✥✦✧✨✩✪✫✬✭✮✯✰✱✲✳✴✵✶✷✸✹✺
✻✼✽✾✿❀❁❂❃❄❅❆❇❈❉❊❋❌❍❎❏❐❑❒❓❔❕❖❗❘❙❚❛❜❝❞❟❠❡❢❣❤❥❦❧➔➕➖➗➘➙➚➛➜➝➞➟➠➡
➢➣➤➥➦➧➨➩➪➫➬➭➮➯➰➱➲➳➴➵➶➷➸➹➺➻➼➽➾➿

julia> ❤(s) = println("I ❤ $(s)")
❤ (generic function with 1 method)

julia> ❤("Julia")
I ❤ Julia
```

### Contextual and stylistic alternates

~~~<img src="/assets/specimen_7.png" width="100%" alt="specimen image 7"> ~~~

JuliaMono is an [OpenType](https://en.wikipedia.org/wiki/OpenType) typeface. OpenType technology provides powerful text positioning, pattern matching, and glyph substitution features, which are essential for languages such as Arabic and Urdu. In English, OpenType features are often seen when letter pairs such as ~~~<span style="font-size: 1.5em;font-family: Georgia;font-variant-ligatures: no-common-ligatures; ">fi</span>~~~ in certain fonts are replaced by a single glyph such as ~~~<span style="font-size: 1.5em; font-family: Georgia;">ﬁ</span>~~~. These [ligatures](https://en.wikipedia.org/wiki/Orthographic_ligature) have been used ever since printing with moveable type was invented, replacing the occasional awkward character combination with a better-looking alternative.

To be honest, I’m not a big fan of their use in coding fonts (and I’m not the only one[^nottheonlyone]). I like to see exactly what I’ve typed, rather than what the font has decided to replace it with.

The Julia language is designed to use Unicode characters, and so ligatures aren't usually needed, but there are a few places where the obvious Unicode glyphs are not accepted by the language, where the ASCII-art substitutes can be improved by the judicious use of alternate glyphs. There are also a few places where some subtle tweaks can enhance readability without introducing ambiguity.

#### Contextual alternates

In JuliaMono, the following substitutions are applied when the **contextual alternates** feature is active:

~~~
<table class="sstable">
    <tr>
    <th><p>typed</p></th>
    <th><p>displayed</p></th>
    </tr>
    <tr>
    <td class="code_ss_off">-></td>
    <td class="code_calt_on">-></td>
    </tr>

    <tr>
    <td class="code_ss_off">=></td>
    <td class="code_calt_on">=></td>
    </tr>
    <tr>
    <td class="code_ss_off">|></td>
    <td class="code_calt_on">|></td>
    </tr>
    <tr>
    <td class="code_ss_off"><|</td>
    <td class="code_calt_on"><|</td>
    </tr>
    <tr>
    <td class="code_ss_off">::</td>
    <td class="code_calt_on">::</td>
    </tr>
    <tr>
    <td class="code_ss_off"><--</td>
    <td class="code_calt_on"><--</td>
    </tr>
    <tr>
    <td class="code_ss_off">--></td>
    <td class="code_calt_on">--></td>
    </tr>
    <tr>
    <td class="code_ss_off"><--></td>
    <td class="code_calt_on"><--></td>
    </tr>
</table>
~~~

You can see some of these in action in the following code fragment:[^width]

```
julialang = true # (!= 0)
(x, y) -> (x + y)
f(p::Int) = p * p
@inbounds if f in (Base.:+, Base.:-)
    if any(x -> x <: AbstractArray{<:Number})
         nouns = Dict(
            Base.:+ => "addition",
            Base.:- => "subtraction",
        )
    end
end
df2 = df |>
    @groupby(_.a) |>
    @map({a = key(_), b = mean(_.b)}) |>
    DataFrame # <|
```

#### Stylistic sets

OpenType fonts also offer you the ability to choose different designs for certain characters. These are stored as a ‘stylistic set’.

All the options are stored in the font, and are often referred to by their internal four letter code (not the best user-oriented design, really). For example, the contextual alternates listed above are collectively stored in the **calt** feature.

Sometimes, an application will show the options more visually in a Typography panel[^typographypanel], usually tucked away somewhere on a Font chooser dialog.

Here’s a list of the stylistic sets currently available in JuliaMono.

~~~
<table class="sstable">
    <tr>
    <th><p>feature code</p></th>
    <th><p>off</p></th>
    <th><p>on</p></th>
    <th><p>description</p></th>
    </tr>

    <tr>
    <td>zero</td>
    <td class="code_ss_off">0</td>
    <td class="code_zero_on">0</td>
    <td><p>slashed zero</p></td>
    </tr>

    <tr>
    <td>ss01</td>
    <td class="code_ss_off">g</td>
    <td class="code_ss_on">g</td>
    <td><p>alternate g</p></td>
    </tr>

    <tr>
    <td>ss02</td>
    <td class="code_ss_off">@</td>
    <td class="code_ss_on">@</td>
    <td><p>alternate @</p></td>
    </tr>

    <tr>
    <td>ss03</td>
    <td class="code_ss_off">j</td>
    <td class="code_ss_on">j</td>
    <td><p>alternate j</p></td>
    </tr>

    <tr>
    <td>ss04</td>
    <td class="code_ss_off">0</td>
    <td class="code_alt_zero">0</td>
    <td><p>alternate 0</p></td>
    </tr>

    <tr>
    <td>ss05</td>
    <td class="code_ss_off">*</td>
    <td class="code_ss_on">*</td>
    <td><p>lighter asterisk</p></td>
    </tr>

    <tr>
    <td>ss06</td>
    <td class="code_ss_off">a</td>
    <td class="code_ss_on">a</td>
    <td><p>simple a</p></td>
    </tr>

    <tr>
    <td>ss07</td>
    <td class="code_ss_off">`</td>
    <td class="code_ss_on">`</td>
    <td><p>smaller grave</p></td>
    </tr>
    <tr>
    <td>ss08</td>
    <td class="code_ss_off">-></td>
    <td class="code_ss_on_dl">-></td>
    <td><p>distinct ligatures</p></td>
    </tr>
    <tr>
    <td>ss09</td>
    <td class="code_ss_off">f</td>
    <td class="code_ss_on">f</td>
    <td><p>alternate f</p></td>
    </tr>
    <tr>
    <td>ss10</td>
    <td class="code_ss_off">r</td>
    <td class="code_ss_on">r</td>
    <td><p>alternate r</p></td>
    </tr>
    <tr>
    <td>ss11</td>
    <td class="code_ss_off">`</td>
    <td class="code_ss_thinnergrave">`</td>
    <td><p>thinner grave</p></td>
	</tr>
	<tr>
	<td>ss12</td>
    <td class="code_ss_off">====</td>
    <td class="code_ss_on">====</td>
    <td><p>joining equals</p></td>
    </tr>
	<td>ss13</td>
    <td class="code_ss_off">&lt;!--</td>
    <td class="code_ss_on">&lt;!--</td>
    <td><p>HTML comment</p></td>
    </tr>
	<td>ss14</td>
    <td class="code_ss_off">==</td>
    <td class="code_ss_on">==</td>
    <td><p>double equals</p></td>
    </tr>
	<td>ss20</td>
    <td class="code_ss_off">(_)</td>
    <td class="code_ss_on">(_)</td>
    <td><p>splashtidy</p></td>
    </tr>

</table>
~~~

All this fancy technology is under the control of the application and the operating system you’re using. Ideally, they will provide an easy way for you to switch the various OpenType features on and off.

Browser-based editors such as Juno and VS Code support many OpenType features in their editor windows, but not in the terminal/console windows. They provide a settings area where you can type CSS or JSON selectors to control the appearance of features, and you’ll have to know the feature codes. Some features are opt in, others are opt out; this too can vary from application to application.

Terminal/console applications also vary a lot; on MacOS the **Terminal** and **iTerm** applications try to offer controls for OpenType features, with varying degrees of success. On Linux, some terminal applications such as [Konsole](https://konsole.kde.org) and [Kitty](https://sw.kovidgoyal.net/kitty/#font-control) offer quite good support, but others such as [Alacritty](https://github.com/alacritty/alacritty) offer little or none, as yet. [^terminal]

If the application allows, you should be able to switch the `calt` contextual ligatures off, particularly since quite a few people won’t like any of them in their code. For the following listing, I switch the **calt** set off using CSS (see [here](/faq/#how_do_i_control_features_in_css_in_juno_or_vs_code)), and then enable some of the alternative stylistic sets: compare characters such as the **0**, **g**, **a**, **j**, and **@** with the previous listing:

@@code_calt_off_ss_on
```
julialang = true # (!= 0)
(x, y) -> (x + y)
f(p::Int) = p * p
@inbounds if f in (Base.:+, Base.:-)
    if any(x -> x <: AbstractArray{<:Number})
         nouns = Dict(
            Base.:+ => "addition",
            Base.:- => "subtraction",
        )
    end
end
df2 = df |>
    @groupby(_.a) |>
    @map({a = key(_), b = mean(_.b)}) |>
    DataFrame # <|
```
@@

(I originally liked the idea of a circular ``@`` sign, but in practice it doesn’t work too well at small point sizes, as the details disappear. But I’ve kept it anyway.)

## If you really don't like any ligatures

It's possible that you don't like even the few ligatures and
contextual alternate characters provided in JuliaMono. If
switching them off isn't possible, or not drastic enough,
you can strip them out of the font with the following
terminal magic (courtesy of @fredrikekre):

```
$ cat Dockerfile
FROM python
RUN pip install fonttools
COPY run.sh /scripts/
ENTRYPOINT ["/scripts/run.sh"]

$ cat run.sh
#!/bin/bash
set -euo pipefail

VERSION="${1-}"

mkdir -p /juliamono-source
mkdir -p /juliamono-output
mkdir -p /juliamono

# Download release version
curl -L "https://github.com/cormullion/juliamono/releases/download/v${VERSION}/JuliaMono.tar.gz" | tar -xzvC /juliamono-source

# Strip glyphs
for f in /juliamono-source/*.ttf
do
    pyftsubset "$f" '*' --output-file=/juliamono-output/$(basename "$f")  --layout-features-=calt,liga
done

# Pack it up
tar -C /juliamono-output -czvf /juliamono/JuliaMono-${VERSION}.tar.gz $(ls /juliamono-output)

$ cat Makefile
.PHONY: image strip
VERSION := 0.021
image:
        docker build -t juliamono-strip:latest .

strip:
        docker run --rm -v ${PWD}:/juliamono juliamono-strip:latest "${VERSION}"
```


@@jm_h1
# Private Use Areas (PUAs)
@@

There are a few areas of the Unicode system that have been officially kept empty and are thus available to store characters that are not part of the standard. These are called the **Private Use Areas**, and there are three: `\ue000` to `\uf8ff`, `\UF0000` to `\UFFFFD`, and `U100000` to `U+10FFFD`.

Each typeface can do its own thing in these areas. In JuliaMono you'll find these, among others, and if you ask nicely I might add some more:

~~~
<img src="/assets/specimen_8.png" width="100%" alt="private use area">
~~~

The obvious drawback to using characters in a Private Use Area is that you have to have installed the font wherever you want to see them rendered correctly, unless they’ve been converted to outlines or bitmaps. If the font isn’t installed (eg on github), you have no idea what glyph - if any - will be displayed.

You can define these to be available at the Julia REPL. For example, say you want the Julia circles to be available in the terminal when you type `\julialogo`~~~<span style="font-size: 1.5em;"></span>~~~ in a Julia session with the JuliaMono font active. Run this:

```
using REPL
REPL.REPLCompletions.latex_symbols["\\julialogo"] = "\ue800"
```

Now you can insert the logo in strings by typing `\julialogo`~~~<span style="font-size: 1.5em;"></span>~~~:

```
julia> println("Welcome to ")
Welcome to 
```

It’s usually possible to type Unicode values directly into text. This is a useful skill to have when you’re not using a capable REPL. On MacOS you hold the Option (⌥) key down while typing the four hex digits (make sure you’re using the Unicode Hex Input keyboard). On Windows I think you type the four hex digits followed by `ALT` then `X`. On Linux it might be `ctrl`-`shift`-`u` followed by the hex digits.


### Thanks!

Thanks to: Thibaut Lienart for his [Franklin.jl](https://github.com/tlienart/Franklin.jl) web site builder; to Jérémie Knüsel who provided invaluable suggestions and advice; to Dr Zygmunt Szpak for his cool maths code; to Simeon Schaub for the issues and PRs, and to others in the Julia community for help and suggestions.

### Footnotes
[^licence]:  &nbsp; “licence” Although not MIT-licensed like Julia, JuliaMono is licensed using the [SIL Open Font licence](https://scripts.sil.org/OFL), which allows the fonts to be used, studied, modified, freely redistributed, and even sold, without affecting anything they’re bundled with.

[^windows]:  &nbsp; “Windows” For more information about if and how it works on Windows, read [this](/faq/#does_it_work_on_windows), but I currently don't know enough about Windows font technology and how it differs from MacOS and Unix. Early reports said that the font didn't look good on Windows. This was because the format was CFF/PostScript OTF, which isn't hinted on Windows. A switch to TTF/TrueType OTF, which is hinted, was considered an improvement.

[^ohdear]: &nbsp; “downloading font problems” The problem might be something to do with the web security feature called [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS/Errors/CORSMissingAllowOrigin) which prevents a web page accessing the resources it needs.

[^masters]:  &nbsp; “masters” In fact there are four masters (Light, Regular, Bold, and Black), and the other instances are interpolated between them.

[^zscode]: &nbsp; “maths in code” spotted [here](https://github.com/JuliaArrays/StaticArrays.jl/issues/537#issuecomment-439863841)

[^languages]: &nbsp; “languages” Apologies for errors - I don’t speak most of these languages.

[^linespacing]: &nbsp; “terminals and line spacing” Terminal applications usually provide the option to vary the line spacing.  For perfectly smooth Unicode plots, you can adjust this until the shaded glyphs are in tune. But for coding purposes you might want the line spacing increased (or decreased) from the default, depending on the trade-off between reading speed, font size, and how many lines of code you can cram in.

[^greedy]: &nbsp; “greedy” referencing [this classic Julia blog post](https://julialang.org/blog/2012/02/why-we-created-julia/)

[^otherfonts]: &nbsp; “better fonts...” Operator Mono and Fira are excellent typefaces... Try them! Also try IBM Plex Mono, Iosevka, Recursive, and Victor Mono, to name a few of my favourites. Like programming languages, every typeface has its strengths and weaknesses. Perhaps keep JuliaMono for font fallback purposes... ;)

[^nottheonlyone]: &nbsp; “not the only one” Matthew Butterick says [“hell no”](https://practicaltypography.com/ligatures-in-programming-fonts-hell-no.html) to them. He also uses the phrase “well-intentioned amateur ligaturists” which isn’t a label I want to have. But more seriously, he says: “my main concern is typography that faces other human beings. So if you’re preparing your code for others to read — whether on screen or on paper — skip the ligatures.”

[^width]: &nbsp; “alternate glyphs” Note that the substitute glyphs occupy the same width as the source glyphs they're replacing. While you could in theory use one of the thousands of Unicode arrows, such as →, as a replacement for the ‘stabby lambda’ (~~~<span class="code_ss_off">-></span>~~~), these are the width of a single character, and so you'd be changing the width of your string/line whenever you made the substitution.

[^typographypanel]: &nbsp; “Typography panel” These vary widely in their abilities and functions: the MacOS Terminal app’s Typography panel is comprehensive but I’m not convinced that all the buttons are wired up yet...

[^terminal]: &nbsp; “terminals again” Writers of terminal apps usually have their own ideas about how fonts and type should be managed and displayed. I haven’t yet found one that did everything that I wanted it to and nothing I didn’t expect it to. In the world of fonts, nothing is 100% correct, which can be frustrating. You can track some of the issues and discussions on github and elsewhere: here’s a [VS Code](https://github.com/microsoft/vscode/issues/34103) issue; here are the [Alacritty terminal developers](https://github.com/alacritty/alacritty/issues/50) working on it; here is the [iTerm documentation](https://iterm2.com/documentation-fonts.html) talking about performance.


