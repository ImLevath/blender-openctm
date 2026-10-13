OpenCTM (.ctm) Blender
====================

This Blender plugin (add-on) allows you to import/export files in OpenCTM file format.

Supported versions: **4.2 LTS**, **3.6 LTS** (**Windows**, **macOS**)

## What it imports:
- Meshdata
- UV Coordinates
- Color Data (attributemap with name 'Color' with data RGBA)

## What it exports:
- Meshdata
- UV Coordinates
- Normals
- Color Data (attributemap with name 'Color' with data RGBA)

## Download

- Get the latest installable package from [GitHub Releases](https://github.com/RealIndrit/blender-openctm/releases/latest).
- For Blender **4.2+** use `openctm_ctm-extension-...zip`.
- For Blender **3.6 LTS** use `openctm_ctm-addon-...zip`.

## Installation tutorial

### Blender 4.2+ (Extensions system)
1. Open Blender.
2. Go to **Edit > Preferences > Get Extensions**.
3. Open the menu in the top-right and click **Install from Disk...**.
4. Select `openctm_ctm-extension-...zip`.
5. Enable **OpenCTM (.ctm)** if it is not enabled automatically.

### Blender 3.6 LTS (legacy add-on system)
1. Open Blender.
2. Go to **Edit > Preferences > Add-ons**.
3. Click **Install...** and select `openctm_ctm-addon-...zip`.
4. Enable **OpenCTM (.ctm)** in the add-on list.

### macOS OpenCTM library setup
This add-on needs the OpenCTM dynamic library (`libopenctm.dylib`) at runtime.

1. Install OpenCTM (example with Homebrew):
   ```bash
   brew install openctm
   ```
2. If Blender still cannot find the library, set `OPENCTM_LIB_PATH` to the installed file path (for example `/opt/homebrew/lib/libopenctm.dylib`) before launching Blender.

## Usage

- To import: **File > Import > OpenCTM (.ctm)**
- To export: **File > Export > OpenCTM (.ctm)**


## Showcase
![Example of imported model view](assets/big_workspace.png)
![Example of UV view](assets/workview_uv.png)
![Old Man model with color data](assets/old_man_big.png)

**Note** Some probles that might occur
- Normals might be flipped, fix it by force a recalculate normals in Blender.


## Dev notes

Blender 4.2.0 uses python 3.11 specifically, so use that to install bpy and create a virtualenv for if you want to have IDE autocompletions and such:
```
python3.11 -m venv venv
venv/bin/pip install bpy blender-stubs
```

Build the addon .zip file:
```
build-script.bat
```

It will give 2 zip files, one for addon (3.6), the other is the extensions system (4.2)

Automated release builds:
- Pushing a `v*` tag triggers `.github/workflows/release.yml`.
- The workflow publishes both installable zip files to the GitHub Release assets.

Install dev build:
* Blender > Edit > Preferences > Add-Ons > Install from disk > .zip file (4.2 extension zip file)
* Blender > Edit > Preferences > Add-ons > Install > .zip file ( 3.6 addon zipfile)

# Disclaimer

Plugin prepackages OpenCTM.dll (df04ff1b749e0c66ad72882cc9bccf01 MD5) lib. If you do not trust this file (it is unmodified).
You are free to get your own at [sourceforge](https://sourceforge.net/projects/openctm/)
or compile [source](https://github.com/Danny02/OpenCTM) yourself

On macOS, provide a compatible OpenCTM dynamic library (`libopenctm.dylib`) either:
- in `src/openctm/libs/`, or
- through `OPENCTM_LIB_PATH`, or
- as a system library (Homebrew/MacPorts paths are auto-detected when available).

# Credits

Some credits to the repos/developer that gave me inspiration/head-start by doing most heavy lifting for me.
- [lejafar](https://github.com/lejafar/Python-OpenCTM)
- [Danny02](https://github.com/Danny02/OpenCTM/)
- [Marcus Geelnard](https://sourceforge.net/u/marcus256/)