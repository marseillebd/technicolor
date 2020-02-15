# Technicolor

Handy functions for colorizing terminal output.

## Installation

Put [`technicolor`](technicolor) on your path.

It's a Bourne Shell script, so it should require nothing special on Unixen and Unix-alikes.

## Usage

Technicolor can be used as an executable:

  * `technicolor test` Print number of colors supported.
    If there are few enough colors, each code will be printed in the corresponding color.
  * `technicolor code <RGB>` Print the terminal color code nearest the given rgb-space hex code.
    The leading hash is optional (but why would you ever actually use it?).
  * `technicolor` (with no arguments) does nothing.
  * `technicolor <RGB> <TEXT> [FLAGS…]` acts as `withaf`.
  * `technicolor <ARGS> <RGB> <TEXT> [FLAGS…]` acts as `withcol`.
    Note that `<ARGS>` here is mandatory, as otherwise it will act as `withaf`.


Or it can be sourced
    (`source "$(which technicolor)"` or `. "$(which technicolor)"`)
    to provide a number of functions:

  * `withcol <ARGS…> <TEXT> <FLAGS…>`
        Where `ARGS` are any combination of `-f<RGB>`, `-b<RGB>` or `-a<ATTR>`
        for foreground, background, and attribute respectively.
        Recognized attributes are `bold`, `ul`, `rev`, `blink`, `invis`, `so`, and `ul`.
        This sets the colors and attributes (later flags may override earlier ones),
            prints the `TEXT` (passing additional `FLAGS` to `echo`),
            and finally resets all colors and attributes (i.e. `tput sgr0`).
        Note that only one string may be passed to `echo`,
        and that additional arguments to `echo` need to come after the `TEXT`, or after a `--`.
        If `ARGS` includes a `-s` flag, then the reset code is not produced.
        Though it is possible to use `withcol '' -n` to clear attributes, I recommend using `nocol`.
  * `withaf <RGB> <TEXT> <ARGS...>`
    As `withcol`, but only sets the foreground color.
    This is included because it is such a common use case.
  * `nocol` Clear all colors and attributes.
  * `rgb2tput` (WIP) Convert a 6-digit RGB hexcode into the nearest code for `tput`.
