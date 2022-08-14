# talon-gaze-ocr

[Talon](https://talonvoice.com/) scripts to enable advanced cursor control using
eye tracking and text recognition (OCR). This is alpha functionality which uses
experimental/unsupported APIs, so it could break at any time.

To install, `git clone` this repo into your user directory. Requires
[knausj_talon](https://github.com/knausj85/knausj_talon) to be installed as a
sibling in the same directory. On Mac, all Python package dependencies are
present in the `.subtrees` directory so that no pip installations are needed. On
Windows, the Talon OCR API is not yet available, so you will need to run
`%APPDATA%\talon\.venv\Scripts\pip.bat install winrt pillow`. On all platforms,
if packages are available through standard pip installation, these will be
preferred (e.g. so that faster binary installations can be used.)

Features:

- Click, select, or position caret adjacent to any text visible onscreen.
- Tracks eye position as you speak to filter matches.
- Offers disambiguation if multiple matches are present.
- Works with or without an eye tracker (just expect slower processing and more
  disambiguation).
- Matches homophones of recognized words (based on CSV in knausj). Also matches
  numbers and punctuation in either their spoken form (e.g. "two" and "period")
  or their symbolic form (e.g. "2" and ".").
- Briefly displays debugging overlay if no matches are present.

Known issues:

- Only operates on the main screen, as defined by Talon.
- Some settings changes require Talon restart.
- Numbers must be referred to by their individual digits.
- Modifications to punctuation and digit names in knausj not leveraged.
- Depends on OS-provided text recognition (OCR), which is not perfectly accurate.
- Cursor positioning often imprecise around text with underline, strikethrough,
  or squiggly.
- Text caret can interfere with text recognition.
- Command subtitles may cause disambiguation when selecting a range of text.

To contribute, changes can be pushed and pulled to all repositories using
`push_all.sh` and `pull_all.sh`, provided that `origin`, `screen-ocr`,
`gaze-ocr`, `rapidfuzz`, and `jarowinkler` are all configured as git remotes,
and `git subtree` is available.
