# PICO-8 Programming Fonts

Herein lies a collection of fonts I've modified for PICO-8 programming.  Why?  I can't say, really, other than it was a small challenge I was tempted to solve.  I can't say I use them... not until, _maybe_, I write a patcher for Consolas anyhow.

### Encoding

It came up elsewhere what the p8 encoding might be.  It is clearly a custom form of Extended ASCII... or, as I think of it, `P8SCII`.  But that's just my opinion.  Ask the author what he calls it, if anything.  Regardless, it's an 8-bit character set right now and -- judging by where the current extended characters sit (on top of Windows 125x, ISO 8859-x, and Unicode control characters) -- forever.

If working on P8 code in an external editor, open and save with a DOS encoding if you can, such as Code Page 437.  This works well in Sublime Text (as "DOS (CP 437)") and in Notepad++ (as either "ANSI" or "Western European -> OEM-US") and probably most others.

Saving as Windows 1252 can _appear_ to preserve the embedded extended characters when using these fonts... but don't be fooled, you may find differently when you reload the file in PICO-8.  To fix, reload as Windows 1252 and save as CP 437.  ISO 8859-1 won't work unless you get really lucky with your editor ("No, your _text_ editor!").  Feeling lucky?  Saving as UTF-8 will destroy the encoding, for sure, with multibyte replacements.

In my opinion, however, it is safer to escape the extended P8SCII characters than embed them:

♥ = `\135` or `\x87` (or `‡` in a PICO-8 OEM font)

### Editor Specifics

#### Sublime Text

Here are some useful preferences to set in "Setting - Syntax Specific" for your *.p8 files:
```
"font_face": "PICO-8 Raize",
"fallback_encoding": "DOS (CP 437)",
"default_encoding": "DOS (CP 437)",
"rulers": [32]
```

Sublime won't load OEM fonts (which may just as well since some editors don't display them completely anyway) so use the non-OEM variants, mono or variable-width, your choice.

Sublime has an odd limitation when working with bitmap FON fonts that a few of you may run into.  That is, if you change the text zoom in Windows to, say, 150% (if you're on a high-DPI display and losing your youth vision like me), Sublime will not let you zoom all the way out with many FON fonts.  The furthest I can zoom out in Sublime with my current Windows display setting is 2x the actual bitmap size for all FON files I have here thus far (I think Windows text zoom is the cause--not sure yet).  The really bizarre thing is that Sublime will let you zoom all the way out on all but the smallest font in a FON file if the file has more than one font in it.  (Thus, the workaround might be to put a tiny font in all files [such as the 4x6 ROM font] but I don't care to go down that hacky road, so good luck getting Sublime to care enough to fix it.)

If working with TrueType or OpenType fonts in Windows with Sublime, the secret to turning off antialiasing is to set GDI mode as well:
```
"font_options": [ "gdi", "no_antialias" ]
```

#### Notepad++

Notepad++ works well with any of these fonts.  If loading and saving as "ANSI" use the OEM variants.  If loading and saving as "OEM-US" use the non-OEM variants.  Sounds a little backwards, eh?  But it makes some sense if you understand how code pages get translated by OSs.

#### Notepad

You don't want to use Windows' Notepad because it doesn't support the Unix line terminators that PICO-8 uses.  I thought I would mention it, however, because it is one of those programs that will only display correctly with the OEM variants of these fonts.
