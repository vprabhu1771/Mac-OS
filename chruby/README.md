```bash
https://github.com/postmodern/chruby
```

`nano ~/.zshrc`

```bash
source /opt/homebrew/opt/chruby/share/chruby/chruby.sh

source /opt/homebrew/opt/chruby/share/chruby/auto.sh

chruby ruby-3.3.4

export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
export PATH="/opt/homebrew/lib/ruby/gems/4.0.0/bin:$PATH"
```

Ah, there it is! Looking at the bottom of your ~/.zshrc file, chruby is explicitly configured to force your system to use ruby-3.3.4 on every single terminal launch:

```bash
source /opt/homebrew/opt/chruby/share/chruby/chruby.sh
source /opt/homebrew/opt/chruby/share/chruby/auto.sh
chruby ruby-3.3.4
```

Because chruby ruby-3.3.4 runs after your global setup, it completely overrides your GEM_HOME variables and forces gem install to target the 3.3.4 directory, breaking your CocoaPods setup.
## The Direct Fix
If you want your Mac to fully switch over to Ruby 4.0.7 and Homebrew's CocoaPods, you need to comment out or remove those chruby lines so they stop hijacking your terminal.

   1. Open your configuration file:
   ```bash
   nano ~/.zshrc
   ```
   2. Clean up and restructure your file:
   Delete the messy gem resets and comment out the chruby lines. Your clean, finalized .zshrc file should look exactly like this:
   ```bash
   export PYENV_ROOT="$HOME/.pyenv"
   export PATH="$PYENV_ROOT/bin:$PATH"if command -v pyenv 1>/dev/null 2>&1; then
     eval "$(pyenv init --path)"
     eval "$(pyenv init -)"fi
   export PATH=~/Downloads/flutter/bin:$PATH
   
   export LANG=en_US.UTF-8
   export LANGUAGE=en_US.UTF-8
   export LC_ALL=en_US.UTF-8
   
   export ANDROID_HOME=$HOME/Library/Android/sdk
   export PATH=$PATH:$ANDROID_HOME/emulator
   export PATH=$PATH:$ANDROID_HOME/tools
   export PATH=$PATH:$ANDROID_HOME/tools/bin
   export PATH=$PATH:$ANDROID_HOME/platform-tools
   
   export PATH="$PATH:$HOME/.composer/vendor/bin"
   # --- HOMEBREW RUBY 4.0.7 & COCOAPODS CONFIG (KEEP AT THE VERY BOTTOM) ---
   unset GEM_HOME
   unset GEM_PATH
   export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
   export PATH="/opt/homebrew/lib/ruby/gems/4.0.0/bin:$PATH"
   ```
   3. Save and Exit:
   Press Ctrl + O, hit Enter, and press Ctrl + X.
   4. Apply and Reinstall CocoaPods:
   Open a brand new terminal tab or window to completely dump the cached variables, then run:
   ```bash
   gem install cocoapods
   hash -r
   which pod
   ```
   
Once you run which pod in the new window, what file path does the terminal print out?

