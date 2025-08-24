# installing madrase LMS locally on ubuntu 24.04.02 (Python 3.12.2)

I have docker already installed.
To make sure docker is correctly install you should be able to run
(WITHOUT SUDO)

```
docker run hello-world
```
I you are able to run it only with `sudo` this is not enough,
you should follow the instructions here to be able to run withtout sudo:

https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user

1. I first just install tutor:

```
python3 -m venv env
source env/bin/activate
pip install 'tutor[full]'
```

now we can run:
```
(env) 6.8dafna@guri:~$ tutor --version
tutor, version 18.2.2
```


now we run 'tutor local launch'

I got some things starting to run but at the end I got: en error:
```
(env) 6.8dafna@guri:~$ tutor local launch
==================================================
        Interactive platform configuration
==================================================
Are you configuring a production platform? Type 'n' if you are just testing Tutor on your local computer [y/N] n
As you are not running this platform in production, we automatically set the following configuration values:
    LMS_HOST = local.edly.io
    CMS_HOST = studio.local.edly.io
    ENABLE_HTTPS = False
Your platform name/title [My Open edX] 
Your public contact email address [contact@local.edly.io] 
The default language code for the platform [he]   
Configuration saved to /home/dafna/.local/share/tutor/config.yml
Environment generated in /home/dafna/.local/share/tutor/env
======================================
        Building Docker images
======================================
No image to build
==============================================
        Stopping any existing platform
==============================================
docker compose -f /home/dafna/.local/share/tutor/env/local/docker-compose.yml -f /home/dafna/.local/share/tutor/env/local/docker-compose.prod.yml --project-name tutor_local stop
======================================================
        Starting the platform in detached mode
======================================================
docker compose -f /home/dafna/.local/share/tutor/env/local/docker-compose.yml -f /home/dafna/.local/share/tutor/env/dev/docker-compose.yml --project-name tutor_dev stop
docker compose -f /home/dafna/.local/share/tutor/env/local/docker-compose.yml -f /home/dafna/.local/share/tutor/env/local/docker-compose.prod.yml --project-name tutor_local up --remove-orphans -d
[+] Running 96/107
[+] Running 107/107d                                                                            196.8s 
 ✔ cms-worker Pulled                                                                            196.8s 
 ✔ mysql Pulled                                                                                 235.8s 
 ✔ smtp Pulled                                                                                  125.4s 
 ✔ redis Pulled                                                                                 132.8s 
 ✔ lms Pulled                                                                                   196.8s 
 ✔ mongodb Pulled                                                                               237.3s 
 ✔ lms-worker Pulled                                                                            196.8s 
 ✔ cms Pulled                                                                                   196.8s 
 ✔ caddy Pulled                                                                                 124.4s 
 ✔ mfe Pulled                                                                                   249.8s 
 ✔ permissions Pulled                                                                           213.8s 
 ✔ elasticsearch Pulled                                                                         208.3s 
[+] Running 12/13
 ✔ Network tutor_local_default            Created                                                 0.0s 
 ✔ Container tutor_local-smtp-1           Started                                                 0.9s 
 ✔ Container tutor_local-permissions-1    Started                                                 1.0s 
 ⠋ Container tutor_local-caddy-1          Starting                                                1.2s 
 ✔ Container tutor_local-mysql-1          Started                                                 0.9s 
 ✔ Container tutor_local-mongodb-1        Started                                                 0.5s 
 ✔ Container tutor_local-elasticsearch-1  Started                                                 0.5s 
 ✔ Container tutor_local-redis-1          Started                                                 0.5s 
 ✔ Container tutor_local-lms-1            Created                                                 0.0s 
 ✔ Container tutor_local-mfe-1            Created                                                 0.0s 
 ✔ Container tutor_local-lms-worker-1     Created                                                 0.0s 
 ✔ Container tutor_local-cms-1            Created                                                 0.0s 
 ✔ Container tutor_local-cms-worker-1     Created                                                 0.0s 
Error response from daemon: failed to set up container networking: driver failed programming external connectivity on endpoint tutor_local-caddy-1 (026907d7e5a86d974483137e5bf84aab966c5d36e2ea16d0f0a3ed2cb1679ee5): failed to bind host port for 0.0.0.0:80:172.18.0.3:80/tcp: address already in use
Error: Command failed with status 1: docker compose -f /home/dafna/.local/share/tutor/env/local/docker-compose.yml -f /home/dafna/.local/share/tutor/env/local/docker-compose.prod.yml --project-name tutor_local up --remove-orphans -d
```
It says my localhost address on port 80 is already in use. Apprently for some reason I have 
lighthttpd service running on my laptop. So I had to stop it:
```
sudo systemctl stop lighttpd.service
```
then running again:
```
tutor local launch
```


