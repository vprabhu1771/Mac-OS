To make your system use Ruby 4.0.7 (installed via Homebrew) instead of the older Ruby 3.3.4 version, you need to add the Homebrew Ruby path to the very front of your shell's environment path.
Because ruby 3.3.4 is currently loaded earlier in your system's search order, running the ruby command bypasses the Homebrew version entirely.
## How to Switch to Homebrew Ruby 4.0.7
Run the following commands in your terminal to update your configuration file (assuming you are using the default macOS Zsh shell):

   1. Add the Homebrew Ruby binary paths to your .zshrc profile:
   
   echo 'export PATH="/opt/homebrew/opt/ruby/bin:$PATH"' >> ~/.zshrc
   echo 'export PATH="/opt/homebrew/lib/ruby/gems/4.0.0/bin:$PATH"' >> ~/.zshrc
   
   2. Apply the changes to your current terminal session:
   
   source ~/.zshrc
   
   3. Verify the active version:
   
   ruby --version
   
   It should now output ruby 4.0.7....

If the version still shows 3.3.4 after running those commands, please share the output of cat ~/.zshrc so we can see how your version manager (like chruby, rbenv, or rvm) is overriding the path.

