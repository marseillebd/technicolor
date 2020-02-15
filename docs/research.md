[Wiki](https://en.wikipedia.org/wiki/Terminal_capabilities) seems to be a good
starting place for termcap, terminfo, tput, and the POSIX terminal interface.

[ArchWiki](https://wiki.archlinux.org/index.php/Color_output_in_console) also is
an unsurprisingly good place for some details: specific file locations in
particular.

[XVilka's gist](https://gist.github.com/XVilka/8346728#detection) has a lot of
good info, but has no definitive answer for detecting true color support.
Annoyingly, it is explicit about this and revised versions are fairly common.
Listed is a way to query the terminal, but doing this in a script seems fraught.
If you do try it, note that it actually expects you to run the command in a
subshell, then type the string after the blank line (using `ctrl+[` for `^[`),
then hit enter for xxd to print the line.

This [SO answer](https://unix.stackexchange.com/a/269085) has a bunch of working
code, but little in the way of standards.

The bash-ui repository has [these docs](https://github.com/chadj2/bash-ui/blob/master/COLORS.md#xterm-colorspaces)
on the math for terminal colorspaces. After the preliminaroes introducing
xterm256, it focuses on HSV.
Honestly, I think I might end up liking [hue/chroma/lightness](https://en.wikipedia.org/wiki/HSL_and_HSV)
for picking colors.

The [nosh package](http://jdebp.eu./Softwares/nosh/guide/TERM.html) has some
details of starting up a terminal or enumlator, with emphasis on getting it
right.
So does [this SO answer](https://unix.stackexchange.com/a/198949).
The big takeaway is that `.bashrc` should draw info from `tput`, not from
the `TERM` env var.

A good entry-level [guide](http://linuxcommand.org/lc3_adv_tput.php) to what
`tput` can do.
