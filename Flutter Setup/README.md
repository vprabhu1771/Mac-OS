Google -> Flutter -> Get Started -> Mac OS -> ios ->  Install the Flutter SDK 


Download and Install -> Select  Intel Processor OR Apple Silicon


The Flutter SDK should download to the macOS default download directory: 

```bash
~/Downloads/
```

Create a folder where you can install Flutter.

Consider creating a directory at `~/development/`

Extract the file into the directory you want to store the Flutter SDK.

```bash
unzip ~/Downloads/flutter_macos_arm64_3.27.3-stable.zip \
       -d ~/development/
```

When finished, the Flutter SDK should be in the `~/development/flutter directory`.


# Add Flutter to your PATH

To run Flutter commands in the Terminal, add Flutter to the PATH environment variable. This guide presumes your Mac runs the latest default shell, `zsh`. Zsh uses the `.zshenv` file for environment variables.

Launch your preferred text editor.

If it exists, open the Zsh environmental variable file `~/.zshenv` in your text editor. If it doesn't, create `~/.zshenv`.

Copy the following line and paste it at the end of your `~/.zshenv` file.

`export PATH=$HOME/development/flutter/bin:$PATH`

Save your `~/.zshenv` file.

To apply this change, restart all open terminal sessions.

If you use another shell, check out this tutorial on setting your PATH.


# CocoaPods

$ gem install cocoapods