# Run the scripts
These Linux scripts retrieve excel file from Robert Shiller's web site, convert it to a datapackage and **publish back the datapackage to github**.

In order to run the scripts, you'll need a valid on github with write access on the repository.

## Fork the repository into your github account...
Because you won't have write access to mine.

## Allow ssh access to your repository
If you don't have a public/private ssh key pair, follow this  [github tutorial](https://help.github.com/articles/generating-ssh-keys/) 
and be sure you add your ssh key to your account.

Then you must configure your local ssh access to github in your ``~/.ssh/config`` file. Mine looks like :

    Host github.com
        HostName github.com
        User git
        IdentityFile ~/.ssh/lexman_github_rsa

## Clone the project... With ssh !

    git clone git@github.com:lexman/s-and-p-500.git
    git checkout tuttle	

## Install the dependencies
The scripts work with some python code and are glued together with [tuttle](github.com/lexman/tuttle), a *make for data*.

Install all dependencies :

    pip install jinja2
    pip install -r requirements.txt

You can also work on a [virtualenv](http://docs.python-guide.org/en/latest/dev/virtualenvs/) .

NB : under debian-based distributions you might need to be able to compile and install the messytables dependencies : ``sudo apt-get install libxml2-dev libxslt-dev python-dev lib32z1-dev``

## Change the publication url... Because you can't publish to my github account
Edit file `scripts/tuttlefile` and change `lexman` to your user account in the line : 

    http://raw.githubusercontent.com/lexman/s-and-p-500/tuttle/data/data.csv <- file://../data/data.csv


## Run the scripts

    cd scripts
	tuttle run
	
Now you have updated the datapackage on your github repository !