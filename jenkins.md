# Jenkins Cheatsheet
## Job Wrangling
### Identify Jobs That Use a Particular Python Virtualenv
```
$ cd $JENKINS_HOME
$ find . -type f -name 'config.xml' | xargs grep '.virtualenvs/somevirtualenv'
```
