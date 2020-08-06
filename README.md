# REXPaint-manual

##### an unofficial markdown rewrite of [REXPaint](https://www.gridsagegames.com/rexpaint/)'s manual

[link to the forum thread](https://www.gridsagegames.com/forums/index.php?topic=1455.0)

## Formatting guidelines

1. all keyboard and mouse keys should be formatted as `key`
2. all key names should use the same case used on keyboards:
   * `Alt`, ~~`alt`~~
   * `Esc` ~~`ESC`~~
   * `PrtScr` ~~`Prtscr`~~
3. key combinations are formatted as a single key: `Ctrl-Shift-Alt-p`
4. all UI buttons should be formatted as `button`
5. configuration strings and paths should be formatted: `txtOutputUTF8:`, `../`
6. newlines in indented paragraphs are reproduced literally, with `\` before the newline.
7. file types representations have been unified as `.extension`:
   * ".txt" and "TXT" becomes `.txt`
   * ".csv" and "CSV" becomes `.csv`
   * ".xml" and "XML" becomes `.xml`
   * ".ans" and "ANS" becomes `.ans` ("ANSI" stays that way because it's a [name](https://www.ansi.org/))
8. small changes can be made to remove clarifications made useless by formatting:
   * "by pressing the `Shift` key" becomes "by pressing `Shift`
   * "by pressing the `x` button/key" stays that way, or it wouldn't be clear if it's a UI button or a keyboard key
9. indented paragraphs are represented as paragraphs surrounded by lines
10. some terms have been *italicized* to improve readability, that's up to the reader's discretion, so feel free to suggest additions/removals
11. "--" em dashes have been converted to "—"
12. single chars were quoted with `''` that's a bit of a programmer thing, they should be converted to `""`
13. URLs should be represented as text links when appropriate
14. text links to appendices should be **bold**
15. the manual should be checked with a linter, but warning `MD024` should be ignored.

---
Feel free to suggest changes and improvements
