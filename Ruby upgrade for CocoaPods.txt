Your error indicates that you are using an outdated Ruby version (2.6.10), but `securerandom` requires Ruby 3.1.0 or higher. To fix this issue, follow these steps:

### 1. **Check Your Ruby Version**
Run:
```sh
ruby -v
```
If it shows `2.6.10`, you need to upgrade Ruby.

---

### 2. **Upgrade Ruby**
#### **For macOS (Recommended)**
If you're using macOS, install a newer version of Ruby using Homebrew:
```sh
brew install ruby
```
Then, add the new Ruby path to your shell:
```sh
echo 'export PATH="/opt/homebrew/opt/ruby/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```
Check the version again:
```sh
ruby -v
```

---

#### **For Linux**
If you're using Ubuntu/Debian:
```sh
sudo apt update
sudo apt install ruby-full
```

For RVM users:
```sh
curl -sSL https://get.rvm.io | bash -s stable
source ~/.rvm/scripts/rvm
rvm install 3.1
rvm use 3.1 --default
```

---

### 3. **Reinstall CocoaPods**
Once Ruby is upgraded, install CocoaPods again:
```sh
sudo gem install cocoapods
```
Then, verify installation:
```sh
pod --version
```

---

Let me know if you need more help! 🚀
