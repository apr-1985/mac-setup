# mac-setup
Ansible Code to setup Mac environment

## Prerequisites

### HomeBrew

```bash
xcode-select --install
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Pyenv & Python

[pyenv guide](https://opensource.com/article/19/6/python-virtual-environments-mac)

```bash
brew update
brew install openssl readline sqlite3 xz zlib
brew install pyenv

pyenv install 3.9.5
pyenv global 3.9.5
```

Add to `.bash_profile`

```bash
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"
export WORKON_HOME=~/.virtualenvs
mkdir -p $WORKON_HOME
. ~/.pyenv/versions/3.9.5/bin/virtualenvwrapper.sh
```
## Ansbile 

```bash
mkvirtualenv ansible
pip install ansible
ansible-galaxy collection install community.general
```