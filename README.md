# go2rtc-cameras-arch

This pkgbuild provides linux desktop entries for a list of cameras to directly open a stream using ffplay.

## Installation

- Clone this repo
- Copy `cameras.sample.json` to `cameras.json`
- Modify `cameras.json`
  - include your go2rtc host
  - set the optional suffix of your cameras, e.g. `_sub` for a sub stream if you have them configured
- `makepkg -i`

