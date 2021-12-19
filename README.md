# Ansible Playbook for MacOS

## Preparation

Open up the default Terminal, and type `pip3`. This will then prompt you to install `Command Line Developer Tools`.

Next, change the default shell to Bash (from zsh, because I'm a traditional old thing).

```sh
chsh -s /bin/bash
```

Restart the terminal, and then proceed with the next steps.

## Install Homebrew

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Install Ansible

```sh
pip3 install ansible --user
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

