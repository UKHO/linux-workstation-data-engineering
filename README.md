# linux-workstation-data-engineering

This is to be run on-top of the linux-workstation provided through `UKHO/linux-workstation`

To run the playbook, run the following in the base of the repository:

```
$ sudo ansible-playbook ansible/playbook.yml -i ansible/inventories/laptop-vm/hosts --extra-vars="user_home=$HOME"
$ cat ~/.bash_profile # You should see the following near the end of the file:
...
export PYENV_ROOT=/home/<your username>/.pyenv
export PATH=/home/<your username>/.pyenv/bin:$PATH
if command -v pyenv 1>/dev/null 2>&1; then eval "$(pyenv init -)";fi
```

## Ansible Roles

* Docker
* Docker Compose
* Pyenv

## Pyenv

[Pyenv](https://github.com/pyenv/pyenv) 'lets you easily switch between multiple versions of Python'.

It allows for multiple Python versions to be installed with ease, allowing for development across different requirements.

Alongside this, pyenv-virtualenv is also installed, this allows for virtual environments based upon the pyenv versions.

Usages:

#### Install Python version
```
$ export TMPDIR=. # This is required as /tmp has no-exec, change this back to /tmp when you've installed your version
$ pyenv install <version> 
```

#### Check installed Python versions
```
$ pyenv versions
```

#### Switch Python version
```
$ pyenv global <version> # Either a installed version or `system`
$ python --version # Check to see if the version has changed
Python <version>
$ which python # Ensure that we're pointing to the pyenv Python install
~/.pyenv/shims/python 
```

#### Create a pyenv virtual environment
```
$ pyenv virtualenv <version> <virtual env name> # Try to keep the name short, it will appear when you activate the venv
```

#### Activate a pyenv virtual environment
```
$ pyenv activate <virtual env name>
```

#### Deactivate a pyenv virtual environment
```
$ pyenv deactivate
```