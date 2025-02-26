# Test

git clone --depth 1 https://github.com/Homebrew/brew ~/.brew

export PATH="$HOME/.brew/bin:$PATH"

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/uninstall.sh)"

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

// 
git clone https://github.com/Homebrew/brew homebrew

eval "$(homebrew/bin/brew shellenv)"
brew update --force --quiet
chmod -R go-w "$(brew --prefix)/share/zsh"

// new

export HOMEBREW_FORCE_BREWED_CURL =1

Since you're using LibreSSL, try re-installing curl with OpenSSL instead of Secure Transport.

Latest Brew
All options have been removed from the curl formula, so now you need to install via:

brew install curl-openssl
Older Brew
Install curl with --with-openssl:

brew reinstall curl --with-openssl

Sau đây là một số gợi ý khác:

Đảm bảo bạn không sử dụng http_proxy/https_proxy.
Sử dụng -v để curl để có đầu ra chi tiết hơn.
Hãy thử sử dụng BSD curl tại /usr/bin/curl, chạy which -a curl để liệt kê tất cả.
Đảm bảo bạn không vô tình chặn curl trong tường lửa của mình (chẳng hạn như Little Snitch).
Hoặc sử dụng wget.


