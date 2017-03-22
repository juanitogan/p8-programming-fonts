# PICO-8 Programming Fonts

Herein lies a collection of fonts I've modified for PICO-8 programming.  Why?  I can't say, really, other than it was a small curiosity I was tempted to solve.  I can't say I use them... but for those who want them, here they are.

![Screenshot of Sublime Text, Notepad++, and PICO-8](https://github.com/juanitogan/p8-programming-fonts/blob/master/github-images/screenshot-st3-npp-p8.png)
<br>_Screenshot of Sublime Text, Notepad++, and PICO-8, all displaying the same p8 file._

### Encoding

It came up elsewhere what the p8 encoding might be.  It is clearly a custom form of Extended ASCII... or, as I think of it, `P8SCII` (first! :grin:).  But that's just my opinion.  Ask the author what he calls it, if anything.  Regardless, it's an 8-bit character set right now and -- judging by where the current extended characters sit (on top of Windows 125x, ISO 8859-x, and Unicode control characters) -- forever.

![P8SCII Character Set and P8SCII mapped to Windows 1252](https://github.com/juanitogan/p8-programming-fonts/blob/master/github-images/p8-charmap.png)
<br>_P8SCII mapped to Windows 1252 (also the same mapping as ISO 8859-1, etc)._

If working on P8 code in an external editor, open and save with a DOS encoding if you can, such as Code Page 437.  This works well in Sublime Text (as "DOS (CP 437)") and in Notepad++ (as either "ANSI" or "Western European -> OEM-US") and probably most others.

Saving as Windows 1252 can _appear_ to preserve the embedded extended characters when using these fonts... but don't be fooled, you may find differently when you reload the file in PICO-8.  To fix, reload in your editor as Windows 1252 and save as CP 437.  ISO 8859-1 won't work unless you get really lucky with your editor ("No, your _text_ editor!").  Feeling lucky?  Saving as UTF-8 will destroy the encoding, for sure, with multibyte replacements.

In my opinion, however, it is safer to escape the extended P8SCII characters than embed them:

♥ = `\135` or `\x87`

## Editor Specifics

The comments here will, hopefully, tell you how to use the fonts in most editors, regardless of whether or not it is listed here.

### Sublime Text

Here are some useful preferences to set in "Settings - Syntax Specific" for your \*.p8 files:
```json
"font_face": "PICO-8 Raize",
"fallback_encoding": "DOS (CP 437)",
"default_encoding": "DOS (CP 437)",
"rulers": [32]
```

Sublime won't load OEM fonts (which may be just as well since some editors don't display them completely anyway) so use the non-OEM variants, mono or variable-width, your choice.

> Sublime has an odd limitation when working with bitmap FON fonts that a few of you may run into.  That is, if you change the text zoom in Windows to, say, 150% (if you're on a high-DPI display and losing your youth vision like me), Sublime will not let you zoom all the way out with many FON fonts.  The furthest I can zoom out in Sublime with my current Windows display settings is 2x the actual bitmap size for all FON files I have here thus far (I believe the Windows settings are part of the cause--not sure yet).  The really bizarre thing is that Sublime will let you zoom all the way out on all but the smallest font in a FON file [if the file has more than one font in it].  Thus, the workaround might be to put a tiny font in all files (such as the 4x6 ROM font) but I don't care to go down that hacky road, so good luck getting Sublime to care enough to fix this.

If working with TrueType or OpenType fonts in Windows with Sublime, the secret to turning off antialiasing is to set GDI mode as well:
```json
"font_options": [ "gdi", "no_antialias" ]
```

Another useful feature to enable is to install the Auto Fold package and modify it for \*.p8 files to hide the non-code parts of the file.  [See this wiki for details on this](https://github.com/juanitogan/p8-programming-fonts/wiki/Using-Sublime-Text-and-Auto-Fold-with-PICO-8-files).

### Notepad++

Notepad++ works well with any of these fonts.  If loading and saving as "ANSI" use the OEM variants.  If loading and saving as "OEM-US" use the non-OEM variants.  Sounds a little backwards, eh?  But it makes some sense if you understand how code pages get translated by OSs.

Note: If using TrueType fonts that contain the double-wide extended characters, Notepad++ doesn't always get the spacing right at some sizes between the single- and double-wide characters because, for some wacky reason, Notepad++ sets its own character spacing.

### Notepad

You don't want to use Windows' Notepad because it doesn't support the Unix line terminators that PICO-8 uses.  I thought I would mention it, however, because it is one of those programs that will only display correctly with the OEM variants of these fonts.

# The Fonts

Thus far, only one TrueType font (DejaVu) and Windows FON bitmap fonts are available here.  I could convert the bitmap fonts to Unix/Linux types but I am not set up for testing those conversions so I'll wait for others to do that work, if anyone chooses to, and include them via pull request.  Creating patch files for various vector fonts is also a possibility (such as for Consolas, what I currently use) but I have no plans to engage in such things at the moment because licensing would likely require that I patch them instead of mod them (which would then require maintaining patches for all the various versions scattered across the world).

### PICO-8 ROM
![PICO-8 ROM font preview](https://github.com/juanitogan/p8-programming-fonts/blob/master/github-images/p8-rom-oem.png)
<br>![PICO-8 ROM font preview](https://github.com/juanitogan/p8-programming-fonts/blob/master/github-images/p8-rom-mono-oem.png)

I really didn't want to take the time creating this set -- because I don't see the point in punishing yourself with it -- I did enough of that with bad fonts ***and*** displays way back somewhere in the last century.  But I knew I would be pestered for these if I didn't create them, so here they are in all their "dune" glory (you might be able to figure out what that means if you find this 4x6 font to be worse than all other 4x6 fonts like I do).  I even created these as multi-font FON files (same font in multiple bitmap resolutions) so that your editor should let you zoom in pretty big before Windows decides you're totally insane and replaces it with a default vector font.
* Windows FON fonts:
  * [**PICO-8 ROM**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-rom.fon)
  * [**PICO-8 ROM OEM**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-rom-oem.fon)
  * [**PICO-8 ROM Mono**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-rom-mono.fon)
  * [**PICO-8 ROM Mono OEM**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-rom-mono-oem.fon)
* TrueType fonts:
  * [PICO-8 forum discussion: PICO-8.ttf + variants](http://www.lexaloffle.com/bbs/?tid=3760)
    * Hopefully, these will be updated soon to the Windows-1252/ISO-8859-1 mapping (so that I don't feel tempted to build my own).  I'm not sure if the OEM mapping (Symbol encoding, really, in TrueType) is possible with the FontStruct tool these were created in.

### PICO-8 Tektite
![PICO-8 Tektite font preview](https://github.com/juanitogan/p8-programming-fonts/blob/master/github-images/p8-tektite-oem.png)
<br>![PICO-8 Tektite font preview](https://github.com/juanitogan/p8-programming-fonts/blob/master/github-images/p8-tektite-mono-oem.png)

This is the first font I worked on... because, well, it was just sitting there, begging to be tweaked, when poking around various tools.  I call this one a semi-sane choice for programming.  It is a very VGA-ish 9x16 (plus I added an extra line of "external leading" because it looks better with more line space, but few editors pay attention to that attribute--_HxD_ being the only one I tested that does--so you may want to tell your editor to space it more).  If you like it, you can get the matching set of non-P8 versions (that I also modified a bit from the original Tektite font) by visiting their home here: https://github.com/juanitogan/mkwinfont (also direct-linked below).
* Windows FON fonts:
  * [**PICO-8 Tektite**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-tektite.fon)
  * [**PICO-8 Tektite OEM**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-tektite-oem.fon)
  * [**PICO-8 Tektite Mono**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-tektite-mono.fon)
  * [**PICO-8 Tektite OEM Mono**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-tektite-mono-oem.fon)
  * Matching fonts:
    * [**Tektite**](https://github.com/juanitogan/mkwinfont/raw/master/fonts/tektite16x9.fon) (Windows 1252, ISO-8859-1, "Font has XWindows encoding" option in PuTTY)
    * [**Tektite OEM**](https://github.com/juanitogan/mkwinfont/raw/master/fonts/tektite16x9oem.fon) (CP 437, OEM-US, PC-8)

### PICO-8 MSTester
![PICO-8 MSTester font preview](https://github.com/juanitogan/p8-programming-fonts/blob/master/github-images/p8-tester-oem.png)
<br>![PICO-8 MSTester font preview](https://github.com/juanitogan/p8-programming-fonts/blob/master/github-images/p8-tester-mono-oem.png)

This one is a formerly-sane choice for programming.  It is a squished VGA-ish of 8x12.  This is a sample font that was included with some Microsoft sample code for building a FNT editor, ages ago.  Thus, it sounds like public domain to me even though it looks suspiciuosly like an old version of **Fixedsys**.  I did descend the brackets a bit -- the curly brackets were hardly recognizable.  Otherwise unchanged in the 7-bit region.
* Windows FON fonts:
  * [**PICO-8 MSTester**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-tester.fon)
  * [**PICO-8 MSTester OEM**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-tester-oem.fon)
  * [**PICO-8 MSTester Mono**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-tester-mono.fon)
  * [**PICO-8 MSTester OEM Mono**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-tester-mono-oem.fon)

### PICO-8 Raize
![PICO-8 Raize font preview](https://github.com/juanitogan/p8-programming-fonts/blob/master/github-images/p8-raize-oem.png)
<br>![PICO-8 Raize font preview](https://github.com/juanitogan/p8-programming-fonts/blob/master/github-images/p8-raize-mono-oem.png)

This one is a fairly-sane choice for programming.  It comes in many sizes so I chose the fairly large 11x22 regular for some variety here (maybe I should include the 11x22 bold as well... but I'm bored with this P8 font stuff already and anxious to get back to game building).  I looked at ProFont, Proggy, Terminus, and a few others, and decided I liked Raize the best even though I'm not a huge fan of some of the squarish characters and dislike the high placement of `+` and `-`.  So, now you have to live with it or make your own mod of your favorite.  I'm not entirely sure it is licensed for modding like most of the others I looked at are; it is copyrighted by Raize Software and given out as free software with no license details.
* Windows FON fonts:
  * [**PICO-8 Raize**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-raize.fon)
  * [**PICO-8 Raize OEM**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-raize-oem.fon)
  * [**PICO-8 Raize Mono**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-raize-mono.fon)
  * [**PICO-8 Raize OEM Mono**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-raize-mono-oem.fon)
* Matching fonts:
  * [Raize Software](http://www.raize.com/DevTools/Tools/RzFont.asp) - Three sizes in regular and bold, plus Unix/Linux versions

### PICO-8 DejaVu
![PICO-8 DejaVu font preview](https://github.com/juanitogan/p8-programming-fonts/blob/master/github-images/P8DejaVuOEM.png)
<br>![PICO-8 DejaVu font preview](https://github.com/juanitogan/p8-programming-fonts/blob/master/github-images/P8DejaVuMonoOEM.png)

DejaVu Sans Mono is a pretty nice programming font.  Maybe not the greatest... but its [open-source-ity-ness](https://dejavu-fonts.github.io/License.html) (new word) made it a good candidate for inclusion in this collection.  (The FontForge source files are also found in this repo.)

* TrueType fonts:
  * **PICO-8 DejaVu**
    * [PICO-8 DejaVu](https://github.com/juanitogan/p8-programming-fonts/raw/master/vector-fonts/DejaVu/P8DejaVu.ttf)
    * [PICO-8 DejaVu Bold](https://github.com/juanitogan/p8-programming-fonts/raw/master/vector-fonts/DejaVu/P8DejaVu-Bold.ttf)
    * [PICO-8 DejaVu Oblique](https://github.com/juanitogan/p8-programming-fonts/raw/master/vector-fonts/DejaVu/P8DejaVu-Oblique.ttf)
    * [PICO-8 DejaVu Bold Oblique](https://github.com/juanitogan/p8-programming-fonts/raw/master/vector-fonts/DejaVu/P8DejaVu-BoldOblique.ttf)
  * **PICO-8 DejaVu OEM**
    * [PICO-8 DejaVu OEM](https://github.com/juanitogan/p8-programming-fonts/raw/master/vector-fonts/DejaVu/P8DejaVuOEM.ttf)
    * [PICO-8 DejaVu OEM Bold](https://github.com/juanitogan/p8-programming-fonts/raw/master/vector-fonts/DejaVu/P8DejaVuOEM-Bold.ttf)
    * [PICO-8 DejaVu OEM Oblique](https://github.com/juanitogan/p8-programming-fonts/raw/master/vector-fonts/DejaVu/P8DejaVuOEM-Oblique.ttf)
    * [PICO-8 DejaVu OEM Bold Oblique](https://github.com/juanitogan/p8-programming-fonts/raw/master/vector-fonts/DejaVu/P8DejaVuOEM-BoldOblique.ttf)
  * **PICO-8 DejaVu Mono**
    * [PICO-8 DejaVu Mono](https://github.com/juanitogan/p8-programming-fonts/raw/master/vector-fonts/DejaVu/P8DejaVuMono.ttf)
    * [PICO-8 DejaVu Mono Bold](https://github.com/juanitogan/p8-programming-fonts/raw/master/vector-fonts/DejaVu/P8DejaVuMono-Bold.ttf)
    * [PICO-8 DejaVu Mono Oblique](https://github.com/juanitogan/p8-programming-fonts/raw/master/vector-fonts/DejaVu/P8DejaVuMono-Oblique.ttf)
    * [PICO-8 DejaVu Mono Bold Oblique](https://github.com/juanitogan/p8-programming-fonts/raw/master/vector-fonts/DejaVu/P8DejaVuMono-BoldOblique.ttf)
  * **PICO-8 DejaVu Mono OEM**
    * [PICO-8 DejaVu Mono OEM](https://github.com/juanitogan/p8-programming-fonts/raw/master/vector-fonts/DejaVu/P8DejaVuMonoOEM.ttf)
    * [PICO-8 DejaVu Mono OEM Bold](https://github.com/juanitogan/p8-programming-fonts/raw/master/vector-fonts/DejaVu/P8DejaVuMonoOEM-Bold.ttf)
    * [PICO-8 DejaVu Mono OEM Oblique](https://github.com/juanitogan/p8-programming-fonts/raw/master/vector-fonts/DejaVu/P8DejaVuMonoOEM-Oblique.ttf)
    * [PICO-8 DejaVu Mono OEM Bold Oblique](https://github.com/juanitogan/p8-programming-fonts/raw/master/vector-fonts/DejaVu/P8DejaVuMonoOEM-BoldOblique.ttf)
* Matching fonts:
  * [DejaVu Fonts](https://dejavu-fonts.github.io/)
