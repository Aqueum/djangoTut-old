# djangoTut setup

## Setup vagrant box
- Pick box from [Vagrant](https://app.vagrantup.com/boxes/search?_ga=2.235591302.605526645.1500926823-1879209973.1499723689)
- I chose [ubuntu/xenial64](https://app.vagrantup.com/ubuntu/boxes/xenial64)
  - create new folder, I called mine `djangoTut`
  - I added the path to djangoTut as an alias called djangoTut by:
    - nano .bash_profile
    - add the line: `alias djangoTut='cd "/Users/PATH_TO_YOUR_DJANGOTUT_FOLDER"'
  - navigate to new folder in terminal
  - `vagrant init ubuntu/xenial64`
  - edit vagrant file
    - uncomment `# config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
`
    - change ports `80` and `8080` to `8000` as that's what the django development server uses
    - so you now have `config.vm.network "forwarded_port", guest: 8000, host: 8000, host_ip: "127.0.0.1`
  - `vagrant up`
  - `vagrant ssh` to SSH into your new box
  
## Install Django
- `python3 -m django --version` to confirm no django installed (or check version)
- [install database](https://docs.djangoproject.com/en/1.11/topics/install/#database-installation), if not SQLite, but tutorial uses SQLite
- [remove django](https://docs.djangoproject.com/en/1.11/topics/install/#removing-old-versions-of-django) if you have an out of date version
- install pip
  - `sudo apt-get update --fix-missing` (I did this at pip's instruction but assume I should have done it first)
  - `sudo apt install python3-pip` to install pip
  - `pip3 install --upgrade pip` to upgrade pip
- setup [virtualenv](https://virtualenv.pypa.io/en/stable/)
  - `pip3 install virtualenv` to install virtualenv
  - `cd /vagrant`
  - `virtualenv ENV` to create a new virtual environment in directory ENV
  - `source ENV/bin/activate` to activate virtual env
- `pip install Django` to install Django
- `python -m django --version` to check installed version - I have 1.11.3
  
## Set up Django project
- `django-admin startproject mysite` to create django settings, database configuration & file structure
- check project working
  - `cd /vagrant/mysite`
  - `python manage.py runserver` to run lightweight **non-production** development server
  - 
  




# To launch
- in terminal `djangoTut` or navigate to the folder with your vm
- `vagrant up`
- `vagrant ssh`
- `cd /vagrant/mysite`
- `source ../ENV/bin/activate`
- `python manage.py runserver`


vagrant reload