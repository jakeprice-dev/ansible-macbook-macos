# Ansible Playbook for MacOS

## Preparation

### Install Command Line Tools

Open up the default Terminal and install xcode Command Line Developer Tools.

```sh
xcode-select --install
```

Next, change the default shell to Bash (personal preference).

### Change Default Shell to Bash

```sh
chsh -s /bin/bash
```

Restart the terminal, and then proceed with the next steps.

## Install Homebrew

Install Homebrew with the command below.

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Install Ansible

Install Ansible using Homebrew.

```sh
brew install ansible
```

## Install Ansible Galaxy Collections

```sh
ansible-galaxy collection install -r requirements.yml
```

## Optional Tasks

To avoid running certain tasks (such as Homebrew) which may take a while to run, a number of boolean variables are provided in `flags.yml`. 

By default they are all set to `false`.

For an actual intial configuration, or to make sure current software is up to date, the flags can be set to `true`, example below.

```yml
# Download Ansible Galaxy Prerequisites:
download_galaxy: false

# Download applications that need manual installation:
download_apps: false

# Run Homebrew Packages:
run_homebrew_packages: false

# Run Homebrew Casks:
run_homebrew_casks: false

# Run Python pip:
run_pip: true
```

## Add Variables File

Create `vars.yml`, and give the below variables values. 

```sh
firefox_start_page: <url>
healthcheck_unison: <url>
hostname: <hostname>
personal_username: <username>
```

## Run Playbook

```sh
ansible-playbook --ask-become-pass playbook.yml
```

