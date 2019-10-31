# awscli, aws-sam-cli self contained venv
Set up the awscli and aws-sam-cli in a virtual env, ready for use

I didn't want to use homebrew, and had issues when these two were
installed in two different python3 environments:
```
ModuleNotFoundError: No module named 'urllib3.packages.six'
```

### Requirements
Python3.7

### Installation
```
# Clone the repository
git clone https://github.com/ayoung012/awscli-sam-venv.git
cd awscli-sam-venv

# Create and activate a virtual env to contain the aws clis
python3 -m venv aws
source aws/bin/activate

# Upgrade pip
python3 -m pip install --upgrade pip
# Install awscli and aws-sam-cli
python3 -m pip install -r requirements.txt

# Configure the aws-cli
aws configure
```

#### Configuring the aws-cli
https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html

### Usage
```
# Ensure virtual env is active
source awscli-sam-venv/aws/bin/activate

# Verify access to aws-cli and sam-cli
aws --version
sam --version
```

#### Getting started with SAM
https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-getting-started-hello-world.html


#### Sidenote on referencing pip/venv
Various distros have their own favourite ways to make pip/venv accessible
on the command line. This often tripped me up when trying to figure out
whether I was installing dependancies in the python2 or python3 environments.

This [red hat article](https://developers.redhat.com/blog/2019/05/07/what-no-python-in-red-hat-enterprise-linux-8/)
sums up nicely how this generally makes everyones life just a little bit
more interesting (read: difficult).

Expressly using `python3 -m pip install` ensures that you are definitely installing to
python3, regardless of your distro setup.

