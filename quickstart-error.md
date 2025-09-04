```
(maple) 6.8dafna@guri:~$ tutor local quickstart
==================================================
        Interactive platform configuration
==================================================
Are you configuring a production platform? Type 'n' if you are just testing Tutor on your local computer [y/N] n
As you are not running this platform in production, we automatically set the following configuration values:
    LMS_HOST = local.overhang.io
    CMS_HOST = studio.local.overhang.io
    ENABLE_HTTPS = False
Your platform name/title [My Maple edX]  
Your public contact email address [dafna@fastmail.com] 
The default language code for the platform [he] 
Configuration saved to /home/dafna/madrasa/maple-env/config.yml
Environment generated in /home/dafna/madrasa/maple-env/env
==============================================
        Stopping any existing platform
==============================================
docker-compose -f /home/dafna/madrasa/maple-env/env/local/docker-compose.yml -f /home/dafna/madrasa/maple-env/env/local/docker-compose.prod.yml -f /home/dafna/madrasa/maple-env/env/local/docker-compose.tmp.yml --project-name tutor_local stop
Stopping tutor_local-cms-worker-1    ... done
Stopping tutor_local-cms-1           ... done
Stopping tutor_local-lms-worker-1    ... done
Stopping tutor_local-mfe-1           ... done
Stopping tutor_local-lms-1           ... done
Stopping tutor_local-redis-1         ... done
Stopping tutor_local-elasticsearch-1 ... done
Stopping tutor_local-mongodb-1       ... done
Stopping tutor_local-caddy-1         ... done
Stopping tutor_local-mysql-1         ... done
Stopping tutor_local-smtp-1          ... done
======================================================
        Starting the platform in detached mode
======================================================
docker-compose -f /home/dafna/madrasa/maple-env/env/local/docker-compose.yml -f /home/dafna/madrasa/maple-env/env/dev/docker-compose.yml -f /home/dafna/madrasa/maple-env/env/dev/docker-compose.tmp.yml --project-name tutor_dev stop
docker-compose -f /home/dafna/madrasa/maple-env/env/local/docker-compose.yml -f /home/dafna/madrasa/maple-env/env/local/docker-compose.prod.yml -f /home/dafna/madrasa/maple-env/env/local/docker-compose.tmp.yml --project-name tutor_local up --remove-orphans --build -d
Removing orphan container "tutor_local-permissions-1"
Pulling mysql (docker.io/mysql:5.7.35)...
5.7.35: Pulling from library/mysql
b380bbd43752: Pull complete
f23cbf2ecc5d: Pull complete
30cfc6c29c0a: Pull complete
b38609286cbe: Pull complete
8211d9e66cd6: Pull complete
2313f9eeca4a: Pull complete
7eb487d00da0: Pull complete
bb9cc5c700e7: Pull complete
88676eb32344: Pull complete
8fea0b38a348: Pull complete
3dc585bfc693: Pull complete
Digest: sha256:b8814059bbd9c80b78fe4b2b0b70cd70fe3772b3c5d8ee1edfa46791db3224f9
Status: Downloaded newer image for mysql:5.7.35
Building mfe
[+] Building 189.0s (76/76) FINISHED                                                     docker:default
 => [internal] load build definition from Dockerfile                                               0.0s
 => => transferring dockerfile: 7.92kB                                                             0.0s
 => WARN: FromAsCasing: 'as' and 'FROM' keywords' casing do not match (line 177)                   0.0s
 => [internal] load metadata for docker.io/library/caddy:2.4.6                                     2.8s
 => [internal] load metadata for docker.io/library/node:12-bullseye-slim                           2.3s
 => [internal] load .dockerignore                                                                  0.0s
 => => transferring context: 2B                                                                    0.0s
 => [internal] load build context                                                                  0.0s
 => => transferring context: 3.52kB                                                                0.0s
 => [base 1/4] FROM docker.io/library/node:12-bullseye-slim@sha256:730e5fe497e70bac60bb2bb6ec550  38.4s
 => => resolve docker.io/library/node:12-bullseye-slim@sha256:730e5fe497e70bac60bb2bb6ec55007dded  0.0s
 => => sha256:730e5fe497e70bac60bb2bb6ec55007ddedbf6c49ce577820614c4873399ee7e 1.21kB / 1.21kB     0.0s
 => => sha256:5c138c93c5b62404b4957afdd72d049561589ded5999e44f4d018fbcf3e5b931 1.37kB / 1.37kB     0.0s
 => => sha256:2cbcf13e4ab7dc51b5559f1bcf13992cd416d29e924354a933401defbe81b434 6.94kB / 6.94kB     0.0s
 => => sha256:1fe172e4850f03bb45d41a20174112bc119fbfec42a650edbbd8491aee32e3c3 31.38MB / 31.38MB   3.5s
 => => sha256:e668081a27339473567eb3eafa1abbd3f5ceefaa67434d1748f8c46d4fdf6f93 4.18kB / 4.18kB     0.8s
 => => sha256:a55e0b57fcd30ebb40be77646f93a5b6b1f2192f8ae80e1ce17e6d58dd2807a8 24.15MB / 24.15MB  37.5s
 => => sha256:123f877d197e4f445fc1a369664841d4fb1ba8c5ec3e9fce20230cac953fa6f9 2.78MB / 2.78MB     1.6s
 => => sha256:cc38f6504a4fb899e298e859041af9cfb475106d59ee0f46cffc6b94fc64965a 449B / 449B         2.2s
 => => extracting sha256:1fe172e4850f03bb45d41a20174112bc119fbfec42a650edbbd8491aee32e3c3          0.5s
 => => extracting sha256:e668081a27339473567eb3eafa1abbd3f5ceefaa67434d1748f8c46d4fdf6f93          0.0s
 => => extracting sha256:a55e0b57fcd30ebb40be77646f93a5b6b1f2192f8ae80e1ce17e6d58dd2807a8          0.6s
 => => extracting sha256:123f877d197e4f445fc1a369664841d4fb1ba8c5ec3e9fce20230cac953fa6f9          0.0s
 => => extracting sha256:cc38f6504a4fb899e298e859041af9cfb475106d59ee0f46cffc6b94fc64965a          0.0s
 => [production 1/7] FROM docker.io/library/caddy:2.4.6@sha256:53e1462eb68d51b5b2995be1c5d0c631fa  5.7s
 => => resolve docker.io/library/caddy:2.4.6@sha256:53e1462eb68d51b5b2995be1c5d0c631fa67824f3fe37  0.0s
 => => sha256:53e1462eb68d51b5b2995be1c5d0c631fa67824f3fe37d692fe73ca714a7236f 1.68kB / 1.68kB     0.0s
 => => sha256:c8555e2ca66576a4404c2b5f31d843a5378dea6134acb500502901b563efebcf 1.36kB / 1.36kB     0.0s
 => => sha256:1ace180df3e668bd7937be4555305fdb7686c68acf2b5514665e2bac99bd266a 8.10kB / 8.10kB     0.0s
 => => sha256:8663204ce13b2961da55026a2034abb9e5afaaccf6a9cfb44ad71406dcd07c7b 2.82MB / 2.82MB     3.4s
 => => extracting sha256:8663204ce13b2961da55026a2034abb9e5afaaccf6a9cfb44ad71406dcd07c7b          0.0s
 => => sha256:fe024ea85c2d7fb47ce4f044038d4227cee2a982bca3e26a0ea4772b8b652f9 291.23kB / 291.23kB  4.7s
 => => sha256:438e4a77a6e9c40c3bf1fb392618ac596307733f97d294edb86383ce8ff7e51d 5.83kB / 5.83kB     4.1s
 => => sha256:2a6d2ebbfc8548ecc1dbf4c7568459e52549b81522cb450d42ada1bf82513a8d 11.73MB / 11.73MB   5.5s
 => => extracting sha256:fe024ea85c2d7fb47ce4f044038d4227cee2a982bca3e26a0ea4772b8b652f9a          0.0s
 => => extracting sha256:438e4a77a6e9c40c3bf1fb392618ac596307733f97d294edb86383ce8ff7e51d          0.0s
 => => sha256:e5c5f60dbd2d0286f964c9769a4a3396935a60d0d71ac0e3f8eea5c4c20711fb 153B / 153B         5.3s
 => => extracting sha256:2a6d2ebbfc8548ecc1dbf4c7568459e52549b81522cb450d42ada1bf82513a8d          0.1s
 => => extracting sha256:e5c5f60dbd2d0286f964c9769a4a3396935a60d0d71ac0e3f8eea5c4c20711fb          0.0s
 => [production 2/7] RUN mkdir -p /openedx/dist                                                    0.9s
 => [base 2/4] RUN apt update   && apt install -y git     gcc git libgl1 libxi6 make     autocon  48.1s
 => [base 3/4] RUN mkdir -p /openedx/app /openedx/env                                              0.2s 
 => [base 4/4] WORKDIR /openedx/app                                                                0.0s 
 => [i18n 1/3] COPY ./i18n /openedx/i18n                                                           0.1s 
 => [profile-src 1/2] RUN git clone https://github.com/edx/frontend-app-profile --branch open-rel  1.0s 
 => [learning-src 1/2] RUN git clone https://github.com/edx/frontend-app-learning --branch open-r  1.1s 
 => [gradebook-src 1/2] RUN git clone https://github.com/edx/frontend-app-gradebook --branch open  1.2s 
 => [account-src 1/2] RUN git clone https://github.com/edx/frontend-app-account --branch open-rel  1.2s
 => [i18n 2/3] RUN chmod a+x /openedx/i18n/*.js                                                    0.2s
 => [i18n 3/3] RUN echo "copying i18n data"   && mkdir -p /openedx/i18n/account   && mkdir -p /op  0.2s
 => [profile-src 2/2] RUN stat /openedx/app/src/i18n/messages 2> /dev/null || (echo "missing mess  0.3s
 => [learning-src 2/2] RUN stat /openedx/app/src/i18n/messages 2> /dev/null || (echo "missing mes  0.3s
 => [gradebook-src 2/2] RUN stat /openedx/app/src/i18n/messages 2> /dev/null || (echo "missing me  0.4s
 => [account-src 2/2] RUN stat /openedx/app/src/i18n/messages 2> /dev/null || (echo "missing mess  0.4s
 => [profile-dev 1/5] COPY --from=profile-src /openedx/app/package.json /openedx/app/package.json  0.1s
 => [profile-i18n 1/4] COPY --from=profile-src /openedx/app/src/i18n/messages /openedx/app/src/i1  0.1s
 => [profile-i18n 2/4] COPY --from=i18n /openedx/i18n/profile /openedx/i18n/profile                0.1s
 => [profile-dev 2/5] COPY --from=profile-src /openedx/app/package-lock.json /openedx/app/package  0.1s
 => [learning-dev 1/5] COPY --from=learning-src /openedx/app/package.json /openedx/app/package.js  0.1s
 => [learning-i18n 1/4] COPY --from=learning-src /openedx/app/src/i18n/messages /openedx/app/src/  0.2s
 => [profile-i18n 3/4] COPY --from=i18n /openedx/i18n/i18n-merge.js /openedx/i18n/i18n-merge.js    0.2s
 => [profile-dev 3/5] RUN npm clean-install --no-audit --no-fund --registry=https://registry.npm  32.5s
 => [learning-dev 2/5] COPY --from=learning-src /openedx/app/package-lock.json /openedx/app/packa  0.2s
 => [gradebook-dev 1/5] COPY --from=gradebook-src /openedx/app/package.json /openedx/app/package.  0.2s
 => [gradebook-i18n 1/4] COPY --from=gradebook-src /openedx/app/src/i18n/messages /openedx/app/sr  0.2s
 => [account-i18n 1/4] COPY --from=account-src /openedx/app/src/i18n/messages /openedx/app/src/i1  0.2s
 => [account-dev 1/5] COPY --from=account-src /openedx/app/package.json /openedx/app/package.json  0.2s
 => [learning-i18n 2/4] COPY --from=i18n /openedx/i18n/learning /openedx/i18n/learning             0.2s
 => [profile-i18n 4/4] RUN /openedx/i18n/i18n-merge.js /openedx/app/src/i18n/messages /openedx/i1  0.3s
 => [learning-dev 3/5] RUN npm clean-install --no-audit --no-fund --registry=https://registry.np  33.8s
 => [gradebook-dev 2/5] COPY --from=gradebook-src /openedx/app/package-lock.json /openedx/app/pac  0.2s
 => [gradebook-i18n 2/4] COPY --from=i18n /openedx/i18n/gradebook /openedx/i18n/gradebook          0.2s
 => [account-i18n 2/4] COPY --from=i18n /openedx/i18n/account /openedx/i18n/account                0.2s
 => [account-dev 2/5] COPY --from=account-src /openedx/app/package-lock.json /openedx/app/package  0.2s
 => [learning-i18n 3/4] COPY --from=i18n /openedx/i18n/i18n-merge.js /openedx/i18n/i18n-merge.js   0.1s
 => [gradebook-dev 3/5] RUN npm clean-install --no-audit --no-fund --registry=https://registry.n  41.8s
 => [learning-i18n 4/4] RUN /openedx/i18n/i18n-merge.js /openedx/app/src/i18n/messages /openedx/i  0.4s
 => [gradebook-i18n 3/4] COPY --from=i18n /openedx/i18n/i18n-merge.js /openedx/i18n/i18n-merge.js  0.1s
 => [account-i18n 3/4] COPY --from=i18n /openedx/i18n/i18n-merge.js /openedx/i18n/i18n-merge.js    0.1s
 => [account-dev 3/5] RUN npm clean-install --no-audit --no-fund --registry=https://registry.npm  32.4s
 => [account-i18n 4/4] RUN /openedx/i18n/i18n-merge.js /openedx/app/src/i18n/messages /openedx/i1  0.4s
 => [gradebook-i18n 4/4] RUN /openedx/i18n/i18n-merge.js /openedx/app/src/i18n/messages /openedx/  0.4s
 => [profile-dev 4/5] COPY --from=profile-src /openedx/app /openedx/app                            0.2s
 => [profile-dev 5/5] COPY --from=profile-i18n /openedx/app/src/i18n/messages /openedx/app/src/i1  0.2s
 => [profile 1/3] COPY ./env/production /openedx/env/production                                    0.1s
 => [account-dev 4/5] COPY --from=account-src /openedx/app /openedx/app                            0.1s
 => [profile 2/3] RUN touch /openedx/env/production.override   && echo "ENABLE_LEARNER_RECORD_MFE  0.2s
 => [account-dev 5/5] COPY --from=account-i18n /openedx/app/src/i18n/messages /openedx/app/src/i1  0.1s
 => [account 1/3] COPY ./env/production /openedx/env/production                                    0.1s
 => [profile 3/3] RUN bash -c "set -a && source /openedx/env/production && source /openedx/env/p  45.4s
 => [account 2/3] RUN touch /openedx/env/production.override   && echo "COACHING_ENABLED=''" >> /  0.4s
 => [account 3/3] RUN bash -c "set -a && source /openedx/env/production && source /openedx/env/p  56.5s
 => [learning-dev 4/5] COPY --from=learning-src /openedx/app /openedx/app                          0.1s
 => [learning-dev 5/5] COPY --from=learning-i18n /openedx/app/src/i18n/messages /openedx/app/src/  0.1s
 => [learning 1/3] COPY ./env/production /openedx/env/production                                   0.0s
 => [learning 2/3] RUN touch /openedx/env/production.override   && echo "done setting production   0.2s
 => [learning 3/3] RUN bash -c "set -a && source /openedx/env/production && source /openedx/env/  62.5s
 => [gradebook-dev 4/5] COPY --from=gradebook-src /openedx/app /openedx/app                        0.1s
 => [gradebook-dev 5/5] COPY --from=gradebook-i18n /openedx/app/src/i18n/messages /openedx/app/sr  0.1s
 => [gradebook 1/3] COPY ./env/production /openedx/env/production                                  0.1s
 => [gradebook 2/3] RUN touch /openedx/env/production.override   && echo "done setting production  0.2s
 => [gradebook 3/3] RUN bash -c "set -a && source /openedx/env/production && source /openedx/env  43.6s
 => [production 3/7] COPY --from=account /openedx/app/dist /openedx/dist/account                   0.1s
 => [production 4/7] COPY --from=gradebook /openedx/app/dist /openedx/dist/gradebook               0.1s
 => [production 5/7] COPY --from=learning /openedx/app/dist /openedx/dist/learning                 0.1s
 => [production 6/7] COPY --from=profile /openedx/app/dist /openedx/dist/profile                   0.0s
 => [production 7/7] COPY ./Caddyfile /etc/caddy/Caddyfile                                         0.0s
 => exporting to image                                                                             0.2s
 => => exporting layers                                                                            0.1s
 => => writing image sha256:6d6591b1eb160d4d4297f66e3b3c45118ca89c783c3c9bf95c2092e4cac5a7d9       0.0s
 => => naming to docker.io/overhangio/openedx-mfe:13.0.6                                           0.0s

 2 warnings found (use docker --debug to expand):
 - FromAsCasing: 'as' and 'FROM' keywords' casing do not match (line 177)
 - LegacyKeyValueFormat: "ENV key=value" should be used instead of legacy "ENV key value" format (line 14)
Pulling cms-permissions (docker.io/overhangio/openedx-permissions:13.3.2)...
13.3.2: Pulling from overhangio/openedx-permissions
4e9f2cdf4387: Already exists
7e75cfc7be5b: Pull complete
70eab1fc11a5: Pull complete
Digest: sha256:8aa045182058843804e212377ffa4c6c8d21376a0a07d9c0a8ad4a5b69362ba6
Status: Downloaded newer image for overhangio/openedx-permissions:13.3.2
Pulling elasticsearch (docker.io/elasticsearch:7.10.1)...
7.10.1: Pulling from library/elasticsearch
3c72a8ed6814: Pull complete
e0812c7c6d71: Pull complete
ae1d3d20a65c: Pull complete
f38df76a58b2: Pull complete
2eca3bea9f3c: Pull complete
8d0e26c84dc9: Pull complete
739cff10e6d4: Pull complete
ebb4b2f0826b: Pull complete
a93ad4ceb967: Pull complete
Digest: sha256:7cd88158f6ac75d43b447fdd98c4eb69483fa7bf1be5616a85fe556262dc864a
Status: Downloaded newer image for elasticsearch:7.10.1
Pulling smtp (docker.io/devture/exim-relay:4.95-r0-2)...
4.95-r0-2: Pulling from devture/exim-relay
3c4e9198e8c1: Pull complete
7fac779fd4a6: Pull complete
Digest: sha256:711f1bcea3ba84879a942759787713c0dea5e11300139f45a6cc3cf787da9790
Status: Downloaded newer image for devture/exim-relay:4.95-r0-2
Pulling redis (docker.io/redis:6.2.6)...
6.2.6: Pulling from library/redis
1fe172e4850f: Already exists
6fbcd347bf99: Pull complete
993114c67627: Pull complete
2a560260ca39: Pull complete
b7179886a292: Pull complete
8901ffe2be84: Pull complete
Digest: sha256:b7fd1a2c89d09a836f659d72c52d27b9f71202c97014a47639f87c992e8c0f1b
Status: Downloaded newer image for redis:6.2.6
Pulling mongodb (docker.io/mongo:4.2.17)...
4.2.17: Pulling from library/mongo
284055322776: Pull complete
090cf866f956: Pull complete
332385499d8b: Pull complete
efb4c37d09b9: Pull complete
a3e230a6fc17: Pull complete
e4db0538af92: Pull complete
630eb1711c2f: Pull complete
78faf905d5ce: Pull complete
541075ad9c81: Pull complete
8ba7cdf424db: Pull complete
Digest: sha256:484efdf166555d6ecdc463b900ac1e74d064377368b3ab47f5ec15095a886251
Status: Downloaded newer image for mongo:4.2.17
Pulling lms (docker.io/overhangio/openedx:13.3.2)...
13.3.2: Pulling from overhangio/openedx
edaedc954fb5: Pull complete
af794270536e: Pull complete
5919be9a5023: Pull complete
b12f6aeb908f: Pull complete
666234190093: Pull complete
49a1306b2efb: Pull complete
1533122aa32a: Pull complete
eaa36a9a10d6: Pull complete
3ad2d0153d85: Pull complete
d24c73e9591c: Pull complete
db975bb5f053: Pull complete
4c7966594708: Pull complete
4f4fb700ef54: Pull complete
fe4e253b4d52: Pull complete
bef9accffc53: Pull complete
3cbb46b0fc52: Pull complete
3959ec3d34de: Pull complete
37b9ddcd2e7e: Pull complete
095ff76f919b: Pull complete
8290bbe2fc41: Pull complete
9bc3015a4964: Pull complete
d15e548740fe: Pull complete
68a597107456: Pull complete
820b984d4db4: Pull complete
8106d5589fae: Pull complete
1e86892e0b1b: Pull complete
62129ca32f60: Pull complete
948f8f729087: Pull complete
Digest: sha256:318554f0c1d626e7bc486788a7669a13c42e3cfd62f6bc81ca6419cbbc768167
Status: Downloaded newer image for overhangio/openedx:13.3.2
Pulling caddy (docker.io/caddy:2.4.6)...
2.4.6: Pulling from library/caddy
8663204ce13b: Already exists
fe024ea85c2d: Already exists
438e4a77a6e9: Already exists
2a6d2ebbfc85: Already exists
e5c5f60dbd2d: Already exists
Digest: sha256:53e1462eb68d51b5b2995be1c5d0c631fa67824f3fe37d692fe73ca714a7236f
Status: Downloaded newer image for caddy:2.4.6
Recreating tutor_local-smtp-1 ... 
Recreating tutor_local-mfe-1  ... 
Recreating tutor_local-mysql-1 ... 
Recreating tutor_local-caddy-1 ... 
Creating tutor_local_lms-permissions_1 ... 
Creating tutor_local_mysql-permissions_1 ... 
Creating tutor_local_mongodb-permissions_1 ... 
Creating tutor_local_redis-permissions_1   ... 
Creating tutor_local_cms-permissions_1     ... 
Creating tutor_local_elasticsearch-permissions_1 ... 

ERROR: for tutor_local-smtp-1  'ContainerConfig'
Creating tutor_local_lms-permissions_1           ... done
ERROR: for tutor_local-mfe-1  'ContainerConfig'
Creating tutor_local_mongodb-permissions_1       ... done
Creating tutor_local_redis-permissions_1         ... done
Creating tutor_local_cms-permissions_1           ... done
Creating tutor_local_mysql-permissions_1         ... done
Recreating tutor_local-redis-1                   ... 

ERROR: for tutor_local-redis-1  'ContainerConfig'
Creating tutor_local_elasticsearch-permissions_1 ... done

ERROR: for tutor_local-mongodb-1  'ContainerConfig'
Recreating tutor_local-elasticsearch-1           ... 

ERROR: for tutor_local-elasticsearch-1  'ContainerConfig'

ERROR: for smtp  'ContainerConfig'

ERROR: for mfe  'ContainerConfig'

ERROR: for mysql  'ContainerConfig'

ERROR: for caddy  'ContainerConfig'

ERROR: for redis  'ContainerConfig'

ERROR: for mongodb  'ContainerConfig'

ERROR: for elasticsearch  'ContainerConfig'
Traceback (most recent call last):
  File "/usr/bin/docker-compose", line 33, in <module>
    sys.exit(load_entry_point('docker-compose==1.29.2', 'console_scripts', 'docker-compose')())
             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/compose/cli/main.py", line 81, in main
    command_func()
  File "/usr/lib/python3/dist-packages/compose/cli/main.py", line 203, in perform_command
    handler(command, command_options)
  File "/usr/lib/python3/dist-packages/compose/metrics/decorator.py", line 18, in wrapper
    result = fn(*args, **kwargs)
             ^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/compose/cli/main.py", line 1186, in up
    to_attach = up(False)
                ^^^^^^^^^
  File "/usr/lib/python3/dist-packages/compose/cli/main.py", line 1166, in up
    return self.project.up(
           ^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/compose/project.py", line 697, in up
    results, errors = parallel.parallel_execute(
                      ^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/compose/parallel.py", line 108, in parallel_execute
    raise error_to_reraise
  File "/usr/lib/python3/dist-packages/compose/parallel.py", line 206, in producer
    result = func(obj)
             ^^^^^^^^^
  File "/usr/lib/python3/dist-packages/compose/project.py", line 679, in do
    return service.execute_convergence_plan(
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/compose/service.py", line 579, in execute_convergence_plan
    return self._execute_convergence_recreate(
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/compose/service.py", line 499, in _execute_convergence_recreate
    containers, errors = parallel_execute(
                         ^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/compose/parallel.py", line 108, in parallel_execute
    raise error_to_reraise
  File "/usr/lib/python3/dist-packages/compose/parallel.py", line 206, in producer
    result = func(obj)
             ^^^^^^^^^
  File "/usr/lib/python3/dist-packages/compose/service.py", line 494, in recreate
    return self.recreate_container(
           ^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/compose/service.py", line 612, in recreate_container
    new_container = self.create_container(
                    ^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/compose/service.py", line 330, in create_container
    container_options = self._get_container_create_options(
                        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/compose/service.py", line 921, in _get_container_create_options
    container_options, override_options = self._build_container_volume_options(
                                          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/compose/service.py", line 960, in _build_container_volume_options
    binds, affinity = merge_volume_bindings(
                      ^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/compose/service.py", line 1548, in merge_volume_bindings
    old_volumes, old_mounts = get_container_data_volumes(
                              ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/compose/service.py", line 1579, in get_container_data_volumes
    container.image_config['ContainerConfig'].get('Volumes') or {}
    ~~~~~~~~~~~~~~~~~~~~~~^^^^^^^^^^^^^^^^^^^
KeyError: 'ContainerConfig'
Error: Command failed with status 1: docker-compose -f /home/dafna/madrasa/maple-env/env/local/docker-compose.yml -f /home/dafna/madrasa/maple-env/env/local/docker-compose.prod.yml -f /home/dafna/madrasa/maple-env/env/local/docker-compose.tmp.yml --project-name tutor_local up --remove-orphans --build -d

```
