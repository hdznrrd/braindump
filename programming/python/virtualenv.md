# virtualenv, virtualenvwrapper
http://docs.python-guide.org/en/latest/dev/virtualenvs/

sudo yum install python-virtualenv python-virtualenvwrapper
echo 'export WORKON_HOME=~/Development/PythonEnvs' >> ~/.zshrc
echo 'source /usr/bin/virtualenvwrapper.sh' >> ~/.zshrc

# autoenv
https://github.com/kennethreitz/autoenv

git clone git://github.com/kennethreitz/autoenv.git ~/.autoenv
echo 'source ~/.autoenv/activate.sh' >> ~/.zshrc

# create a new venv
mkvirtualenv <name>
echo 'workon <name>' >> /path/to/project/.env

# helpful pointers
lsvirtualenv
cdvirtualenv
lssitepackages
cdsitepackages
more: http://virtualenvwrapper.readthedocs.org/en/latest/command_ref.html
