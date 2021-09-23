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

## Fira Code Theme

[Download](https://github.com/tonsky/FiraCode/releases) and extract.
In the TTP folder select all and Open and install

## Vscode

Standard install then turn on Setting sync to Elsevier GitHub.
Check all boxes and then choose merge local

## Ansible

```bash
mkvirtualenv ansible
pip install ansible
ansible-galaxy collection install community.general
```

## Running

```bash
ansible-playbook mac-setup.yml --ask-become-pass
```

Note: Some Roles have a never tag on them as they are not very idempotent so will need to be specified directly e.g.

```bash
ansible-playbook mac-setup.yml --tags golang --ask-become-pass
```
