# patch-desktop-file-name

This is a Python script that patches the desktop file name in an Electron application's package.json file, such that when the electron application is
packaged in a snap, the desktop file name is correctly set to the snap name.

## Usage

To use this script, you should modify your snapcraft.yaml file to include the following lines:

```yaml
# ...
parts:
  patch-desktop-file-name:
    after: [<app_part>]
    source: https://github.com/snapcrafters/patch-desktop-file-name.git
    source-subdir: electron
    plugin: nil
    build-snaps: [astral-uv]
    override-build: |
      ./patch_desktop_file_name.py "${CRAFT_STAGE}/usr/share/discord/resources/app.asar"
```
