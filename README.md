> **Note**
> 
> This is the `gtk4` branch. You are reading the README for the work-in-progress, unreleased GTK 4 version.
> 
> To learn about the last stable, GTK 3 version, see [README.md in the `master` branch](https://github.com/johnfactotum/foliate/blob/master/README.md).

<img src="data/com.github.johnfactotum.Foliate.svg" align="left">

# Foliate

Read books in style.

## Installation

### Run Time Dependencies

- `gjs` (>= 1.72)
- `gtk4` (>= 4.10)
- `libadwaita` (`gir1.2-adw-1` in Debian-based distros)
- `webkitgtk-6.0` (`gir1.2-webkit-6.0` in Debian-based distros)

#### Optional Dependencies

To enable auto-hyphenation, you will need to install hyphenation rules, e.g., `hyphen-en` for English, `hyphen-fr` for French, etc. (which strictly speaking are optional dependencies for WebkitGTK, not Foliate itself).

### Obtaining the Source

The repo uses git submodules. Before running or installing, make sure you clone the whole thing with `--recurse-submodules`.

### Run without Building or Installing

It's possible to run directly from the source tree without building or installing. Simply run

```
gjs -m src/main.js
```

This can be useful if you just want to quickly try out Foliate or test a change.

But note that this will run it without using GSettings, so settings will not be saved. To solve this, you can compile the schema by running

```
glib-compile-schemas data
```

Then you can set the schema directory when running the app:

```
GSETTINGS_SCHEMA_DIR=data gjs -m src/main.js
```

### Building and Installing from Source

The following dependencies are required for building:

- `meson` (>= 0.59)
- `gettext`

To install, run the following commands:

```
meson setup build
sudo ninja -C build install
```

To uninstall, run

```
sudo ninja -C build uninstall
```

#### Installing to a Local Directory

By default Meson installs to `/usr/local`. You can install without root permissions by choosing a local prefix, such as `$PWD/run`:

```
meson setup build --prefix $PWD/run
ninja -C build install
```

You can then run it with

```
GSETTINGS_SCHEMA_DIR=run/share/glib-2.0/schemas ./run/bin/foliate
```

## License

This program is free software: you can redistribute it and/or modify it under the terms of the [GNU General Public License](https://www.gnu.org/licenses/gpl.html) as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

The following JavaScript libraries are bundled in this software:

* [foliate-js](https://github.com/johnfactotum/foliate-js), which is MIT licensed.
* [zip.js](https://github.com/gildas-lormeau/zip.js), which is licensed under the BSD-3-Clause license.
* [fflate](https://github.com/101arrowz/fflate), which is MIT licensed.

---

<a href="https://www.buymeacoffee.com/johnfactotum" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>
