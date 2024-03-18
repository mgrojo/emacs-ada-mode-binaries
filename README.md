# emacs-ada-mode-binaries
AppImages of the [Emacs ada-mode](https://www.nongnu.org/ada-mode/) executables can be found in the releases section.

The AppImage acts as `ada_mode_wisi_lalr_parse`, but all the executables are inside and can be extracted and directly used, since they are mostly statically linked. 

```
chmod +x emacs_ada_mode-8.1.0-x86_64.AppImage
 ./emacs_ada_mode-8.1.0-x86_64.AppImage --appimage-extract
 mv squashfs-root/usr/bin ~/.local/bin
```

Make sure that ~/.local/bin is on the PATH or use any other directory already on it.

Due to the version requirement on re2c, it was not possible to use the oldest supported Ubuntu LTS release, as recommended by the AppImage project. Consequently, older systems could have incompatiblities with the linked libc version.

You can take a look at how they are built in [.github/workflows/main.yml](.github/workflows/main.yml).
