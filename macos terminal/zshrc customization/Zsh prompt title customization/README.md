Customizing your Zsh prompt and terminal title on macOS is a straightforward process that can significantly improve your workflow. You can modify the `~/.zshrc` file to change both how your prompt looks and what information is displayed in the terminal window title.

### ✏️ Customizing the Zsh Prompt (PS1)

The primary way to change your prompt is by editing the `PROMPT` or `PS1` variable in your `~/.zshrc` file.

**1. Open your configuration file:**
You can use any text editor. For a simple approach, use `nano` in the Terminal:
```bash
nano ~/.zshrc
```

**2. Basic Prompt Customization:**
You can set your prompt to display specific information using **prompt escapes**. For example, to show only the current folder and a `>` symbol, you would add this line to the bottom of the file :
```bash
export PS1="%1~ > "
```
Save the file (in `nano`, press `Ctrl+X`, then `Y`, then `Enter`) and either restart Terminal or run `source ~/.zshrc` to see the change.

Here are some common prompt escapes you can use to build your own prompt :

| Escape | Description |
| :--- | :--- |
| `%n` | Username |
| `%m` | Hostname (up to the first dot) |
| `%~` | Current working directory (with `~` for home) |
| `%1~` | Current directory only (not the full path) |
| `%#` | `#` if root, otherwise `%` |
| `%T` | Current time (24-hour) |
| `%D` | Current date |

**3. Adding Colors:**
You can add color using the `%F{color}` and `%f` escape sequences . For instance, a green username and a yellow directory would look like this:
```bash
PROMPT="%F{green}%n@%m %F{yellow}%~ %F{blue}%# %f"
```

### 🏷️ Customizing the Terminal Title

You can also change the text in the window or tab title bar to help identify different sessions.

**Method 1: Manual Setting via Terminal Preferences**
The most persistent way to set a title is through the Terminal app itself. Go to **Terminal > Settings > Profiles**, select your profile, and click the **Window** or **Tab** pane to enter a custom title or choose which information to display (like the working directory or active process) .

**Method 2: Setting Title with a Zsh Function**
For a more dynamic approach, you can add a shell function to your `~/.zshrc` file that changes the title on command .
Add this function:
```bash
tabt () {
    echo -ne "\033]1;$*\007"
}
```
After saving and reloading, you can change the tab title by running `tabt My Project Title`.

This method works by sending an **OSC (Operating System Command) escape sequence** to the terminal, which is a standard way for programs to communicate title changes .

I hope this helps you get your terminal set up just the way you like it. If you have a specific prompt design in mind, feel free to share more details.
