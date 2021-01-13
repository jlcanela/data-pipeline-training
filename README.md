# Data Pipeline training

## Install Polynote

First install Polynote following instructions at https://polynote.org/docs/01-installation.html.

The following install have been tested using https://github.com/polynote/polynote/releases/download/0.3.12/polynote-dist-2.12.tar.gz.

```
curl -o polynote-dist-2.12.tar.gz -L https://github.com/polynote/polynote/releases/download/0.3.12/polynote-dist-2.12.tar.gz
tar xzf polynote-dist-2.12.tar.gz -C `pwd`/opt
rm polynote-dist-2.12.tar.gz
```

## Microsoft WSL2

There are some network connectivity issues related to use of WSL2 with polynote. 
Please check [#671](https://github.com/polynote/polynote/issues/671) in [Installation link](https://polynote.org/docs/01-installation.html)

## Using github project to manage notebook versions

Add the following configuration into you polynote config.yml configuration file:
```
storage:
  mounts:
    data-pipeline-training:
      dir: <path to the data-pipeline-training folder where you did checkout the project>
```

## Python support

The setup is using pyenv virtualenv, but if you prefer any other tool, just adapt the instructions accordingly. 

Python jep module is requiring a python shared environment. 
https://github.com/pyenv/pyenv/issues/392

To install a shared python version: 
```
CONFIGURE_OPTS=--enable-shared pyenv install 3.8.5
```

To install the python requirements using pyenv:
```bash
git checkout URL
cd path
pyenv virtualenv 3.8.5 data-pipeline-training
cd ~/opt/polynote
pyenv local data-pipeline-training
pip install -r requirements.txt
```

Don’t forget to export your config, for example witĥ the following:
```bash
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
export SPARK_HOME=`pwd`/opt/spark-3.0.0-bin-hadoop2.7
export PATH="$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin"
```

If necessary check Polynote [github issues](https://github.com/polynote/polynote/issues).