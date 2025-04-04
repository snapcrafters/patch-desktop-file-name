# patch-desktop-file-name

This is a Python script that patches the desktop file name in an Electron application's package.json file, such that when the electron application is
packaged in a snap, the desktop file name is correctly set to the snap name.

## Usage

To use this script, you should modify your snapcraft.yaml file to include the following lines:

```yaml
# ...
parts:
  # Needed for setting the proper desktop file name in the electron apps
  patch-desktop-file-name:
    after: [discord]
    plugin: nil
    build-snaps: [astral-uv]
    override-build: |
      uv run \
        https://raw.githubusercontent.com/snapcrafters/patch-desktop-file-name/refs/heads/main/electron/patch-desktop-filename.py \
        "${CRAFT_STAGE}/usr/share/discord/resources/app.asar"
```
