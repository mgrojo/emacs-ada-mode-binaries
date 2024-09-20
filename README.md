[![Build](https://github.com/mgrojo/emacs-ada-mode-binaries/actions/workflows/main.yml/badge.svg)](https://github.com/mgrojo/alr2appimage/actions/workflows/main.yml)
[![Alire](https://img.shields.io/endpoint?url=https://alire.ada.dev/badges/emacs_ada_mode.json)](https://alire.ada.dev/crates/emacs_ada_mode.html)
[![Alire CI/CD](https://img.shields.io/endpoint?url=https://alire-crate-ci.ada.dev/badges/emacs_ada_mode.json)](https://alire-crate-ci.ada.dev/crates/emacs_ada_mode.html)
[![Download][download-img]][download]
[![Gitter chat](https://badges.gitter.im/gitterHQ/gitter.png)](https://gitter.im/ada-lang/Lobby)

  [download-img]: https://img.shields.io/github/downloads/mgrojo/emacs-ada-mode-binaries/total.svg
  [download]: https://github.com/mgrojo/emacs-ada-mode-binaries/releases
  
# emacs-ada-mode-binaries
> [!NOTE]  
> The official site of Emacs ada-mode is https://savannah.nongnu.org/projects/ada-mode/, where their sources can be found. This "unofficial" GitHub repository has been set up only for having a GitHub action that gets the latest Alire release and builds the binaries with a setup that  should work for most of the Linux users. Maybe someone can contribute similar actions for MacOS or other OSes, so it serves more users. 

AppImages of the [Emacs ada-mode](https://www.nongnu.org/ada-mode/) executables can be found in the [releases](https://github.com/mgrojo/emacs-ada-mode-binaries/releases) section.

The AppImage acts as `ada_mode_wisi_lalr_parse`, but all the executables are inside and can be extracted and directly used, since they are mostly statically linked. 

```
chmod +x emacs_ada_mode-8.1.0-x86_64.AppImage
./emacs_ada_mode-8.1.0-x86_64.AppImage --appimage-extract
 mv squashfs-root/usr/bin/* ~/.local/bin
```
Make sure that `~/.local/bin` is on the `PATH` or use any other directory already on it.

The executables are dynamically linked with GNAT 12. Thus, unless you have GNAT 12 libraries already installed, you have to move also the libraries to an appropriate place (e.g. present in `LD_LIBRARY_PATH`).
```
mv squashfs-root/usr/lib/* ~/.local/lib
```

Due to the version requirement on re2c, it was not possible to use the oldest supported Ubuntu LTS release, as recommended by the AppImage project. In order to fix that, I've patched ada-mode in this [fork and branch](https://github.com/mgrojo/ada-mode/tree/mgrojo-ada-mode-binaries). That repository is cloned by the GitHub action in order to build on Ubuntu 20.04. You can take a look at how the binaries are built and then pushed directly to Releases in [.github/workflows/main.yml](.github/workflows/main.yml).
