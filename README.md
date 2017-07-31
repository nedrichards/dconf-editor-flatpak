# dconf-editor-flatpak

Resources to build [dconf-editor](https://github.com/GNOME/dconf-editor) as a flatpak.

Instructions:
-------------

(1) Install the flatpak repository for GNOME nightly:
```
  wget http://sdk.gnome.org/nightly/keys/nightly.gpg
  flatpak --user remote-add --gpg-import=nightly.gpg gnome-nightly http://sdk.gnome.org/nightly/repo
```
(2) Install the required runtimes
```
  flatpak --user install gnome-nightly org.gnome.Platform
  flatpak --user install gnome-nightly org.gnome.Sdk
```
(3) Build dconf-editor from this directory:
```
  flatpak-builder --force-clean --ccache --require-changes \
      --repo=repo app \
      ca.desrt.dconf-editor.json
```
(4) Add a remote to your local repo and install it:
```
  flatpak --user remote-add --no-gpg-verify dconf-editor-repo /path/to/your/flatpak/repo
  flatpak --user install dconf-editor-repo ca.desrt.dconf-editor
```
(5) Run thunderbird as an flatpak:
```
  flatpak run ca.desrt.dconf-editor
```