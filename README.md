# Welcome

### Vagrantfile

This is a single file that makes sure that we all have the same development environments regardless of the OS or system configuration we have

**note: you need to have vagrant installed and ubuntu/trusty64 added to your vagrant box**

### Steps

1. clone the repo in a desired folder of your choice, this will not be your development folder but will be the portal where you can share files between your VM and host machine directly
  ```git
git clone https://www.github.com/strawHatRobby/vagrantInit
  ```

2. cd into the downloaded directory and run

  ```bash
    vagrant up
  ```

***note: This is a long process and will take quite a long amount of time. In, programmers terminology its called seeing the paint dry***

- once everything is completed and you are back to your normal prompt, type the following to log in to your VM

  ```bash
    vagrant ssh
  ```

- now we are going to install a bunch of things to speed your workflow which unfortunately I couldn't add via the script itself, due to restricted access and to make sure nothing gets broken. Therefore, keeping the integrity of the dev environment

**note: One or more steps might ask you to enter your password, at the moment its just 'vagrant'**

  ```bash
  sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
  sed -i 's/ZSH_THEME="robbyrussell"/ZSH_THEME="gnzh"/g' ~/.zshrc
  echo "export DISPLAY=:10" >> ~/.zshrc
  cd ~/
    git clone https://github.com/rupa/z.git ~/z
    echo ". ~/z/z.sh" >> ~/.zshrc
    source ~/.zshrc
  ```

- Time to editing your /etc/host

now this is different in both windows and unix based machines

So depending on what you have

## o Windows

1. open file C:\Windows\System32\Drivers\etc\hosts
2. and add the following line

```
  10.10.5.5 dev.django.com
```
## o Unix

1. open /etc/hosts in your favourite text editor
2. and paste the following line

```
  10.10.5.5 dev.django.com
```  

- now in the terminal, make sure you are in your vagrant machine ,i.e, you have typed in vagrant ssh from your host machine/terminal

- cd to  ~/djangoTemplate

- Run the following command

```
  sudo python ./manage.py runserver
```

- Now go to your browser and go to the site
  dev.django.com

# Feel the awesomeness

## Passing the tests in the djangoTemplate

1. Make firefox work head-lessly

- Run the following command on your terminal

```bash
    sudo Xvfb :10 -ac &
```

- after the prompt pauses, press the following

  Windows: Ctrl + C
  Unix: cmd + C

- check to see if firefox gives any error, if nothing happens and the prompt doesn't show up

![firefox working fine as a headless browser](https://github.com/strawHatRobby/vagrantInit/blob/master/documentAssets/firefox.jpg  "Firefox.jpg")

**It means everything is working fine**

2. making sure the tests pass

- got to the djangoTemplate directory

- run

  ```bash
    sudo behave features
  ```
- if all teh tests pass ( all green ), then everything is set up properly and you are ready to start working on your first django project

#### => If you encounter any problems anywhere, contact me on slack
