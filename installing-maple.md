# setp by step to install Maple version of openedx locally with the madras staf.

I have ubuntu 24.04 with python 3.12.3
I will follow Shai Berger's tutorial in order to install Maple version of the madrasa framework.
here is his tutorial that I will follow:

https://github.com/madrasafree/openedx_devops/wiki/Getting-started

note that his tutorial is for installing Redwood, I'll follow the instructions while changing
them to fit to Maple version.

First I use venv for local enviroment:
```
python3 -m venv maple
source maple/bin/activate
```
now, instead of installing tutor<19 , we want to install the tutor version that corresponds to Maple which  ‘tutor[full]>=13.0.0,<14.0.0’ (according to https://docs.tutor.edly.io/install.html#running-older-releases-of-open-edx):
```
pip install 'tutor[full]>=13.0.0,<14.0.0'
```
This failed. I opened a question about it:
https://discuss.openedx.org/t/failed-to-install-tutor-version-for-maple-on-ubuntu-24-04-python-3-12-3/17001

I guess Maple is not supported for my python3 verison.
I install python 3.10.12 using pyenv.
after installing pyenv according to chatGPT instructions, I ran:
```
rm maple
pyenv local 3.10.12
python3 -m venv maple
source ~/maple/bin/activate
pip install 'tutor[full]>=13.0.0,<14.0.0'
```
and now it works! Now `tutor --version` shows 13.3.2
(Another suggestion from chatgpt of how to solve is with docker (which I didn't try): `docker run -it --rm python:3.10 bash`

now let's export the tutor root to be for our maple version so it does not clash with the
redwood version we already installed in another python env:
```
mkdir -p ~/madrasa/maple-env
export TUTOR_ROOT=~/madrasa/maple-env
```
We of course do not want to add this export to .bashrc as suggested by Shai, since we
have multiple tutor installations, so we want to set this manually according to the 
installation we want to work with.
Shai also suggest setting TUTOR_PLUGINS_ROOT. Not sure what is is
running
```
tutor plugins printroot
```
shows
```
/home/dafna/.local/share/tutor-plugins
```
oh, this is not good, we want a Maple specific. Let's set it as well:
```
mkdir -p ~/madrasa/maple-plugins
export TUTOR_PLUGINS_ROOT=~/madrasa/maple-plugins
```
now we have:
```
$ tutor plugins printroot
/home/dafna/madrasa/maple-plugins
```
And now as of Shai's tutorial:
```
(maple) 6.8dafna@guri:~$ tutor config save --interactive
Are you configuring a production platform? Type 'n' if you are just testing Tutor on your local computer [Y/n] n
As you are not running this platform in production, we automatically set the following configuration values:
    LMS_HOST = local.overhang.io
    CMS_HOST = studio.local.overhang.io
    ENABLE_HTTPS = False
Your platform name/title [My Open edX] 'My Maple edX'
Your public contact email address [contact@local.overhang.io] dafna@fastmail.com
The default language code for the platform [en] he
Configuration saved to /home/dafna/madrasa/maple-env/config.yml
Environment generated in /home/dafna/madrasa/maple-env/env
```
Shai wrote a requirements.txt file:
https://github.com/madrasafree/openedx_devops/wiki/Getting-started#requirementstxt

For Maple it will have to change 










