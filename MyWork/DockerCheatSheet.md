Date of Notes : 21-12-2020

> docker version

> docker info

--  create a container from image named hello-world and then start this created container
Old command
> docker run hello-world

or

new command
> docker container run hello-world


-- remove image
> docker image rm -f hello-world
Untagged: hello-world:latest
Untagged: hello-world@sha256:1a523af650137b8accdaed439c17d684df61ee4d74feac151b5b337bd29e7eec
Deleted: sha256:bf756fb1ae65adf866bd8c456593cd24beb6a0a061dedf42b26a993176745f6b


-- how to use help command
> docker image --help
unknown docker image COMMANDin -elp
See 'docker image --help'.
Manage images
Usage:
Commands:
  build       Build an image from a Dockerfile
  history     Show the history of an image
  import      Import the contents from a tarball to create a filesystem image
  inspect     Display detailed information on one or more images
  load        Load an image from a tar archive or STDIN
  ls          List images
  prune       Remove unused images
  pull        Pull an image or a repository from a registry
  push        Push an image or a repository to a registry
  rm          Remove one or more images
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE

Run 'docker image COMMAND --help' for more information on a command.

-- create a container from image at the Docker Hub and then start
> docker container run --name firstcontainer ozgurozturknet/app1
Unable to find image 'ozgurozturknet/app1:latest' locally
latest: Pulling from ozgurozturknet/app1
169185f82c45: Pull complete
1e929b64ace7: Pull complete
3bd64be52cfe: Pull complete
d5d6362eff06: Pull complete
Digest: sha256:31acbf06b10306dc403bb57ecd2be4e870d9ecacacbff006a56c1f5e40f762d6
Status: Downloaded newer image for ozgurozturknet/app1:latest
Merhaba arkadaslar ben App1 uygulamasiyim

-- show containers which is running
> docker container ls
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES

-- show all container
> docker container ls -a
CONTAINER ID        IMAGE                 COMMAND             CREATED             STATUS                         PORTS               NAMES
9dbc857ba4bf        ozgurozturknet/app1   "java app1"         About an hour ago   Exited (0) About an hour ago                       firstcontainer
14a8371f7cfa        bf756fb1ae65          "/hello"            2 hours ago         Exited (0) 2 hours ago                             blissful_newton
7c50837145b5        bf756fb1ae65          "/hello"            2 hours ago         Exited (0) 2 hours ago                             vigorous_lederberg
d9101e17afa0        bf756fb1ae65          "/hello"            2 hours ago         Exited (0) 2 hours ago                             determined_nobel

-- created a new container from DocherHub
> docker container run -p 80:80 ozgurozturknet/adanzyedocker
Unable to find image 'ozgurozturknet/adanzyedocker:latest' locally
latest: Pulling from ozgurozturknet/adanzyedocker
9d48c3bd43c5: Pull complete
d3565940ff69: Pull complete
1cc6c921162a: Pull complete
17877ce0de23: Pull complete
4e10ed3cf6fc: Pull complete
84d0ceb32a5d: Pull complete
1587ec6e5583: Pull complete
e7daf8feccda: Pull complete
49641b0d4586: Pull complete
1c5aa5048b34: Pull complete
Digest: sha256:10631a62b96b8dc8c468fe482aff70871c6c81f4a49ea4c5350ce765cf9f2185
Status: Downloaded newer image for ozgurozturknet/adanzyedocker:latest
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
[Mon Dec 21 23:34:03.854449 2020] [mpm_event:notice] [pid 1:tid 140605397114184] AH00489: Apache/2.4.41 (Unix) configured -- resuming normal operations
[Mon Dec 21 23:34:03.854975 2020] [core:notice] [pid 1:tid 140605397114184] AH00094: Command line: 'httpd -D FOREGROUND'

> docker container ls
CONTAINER ID        IMAGE                          COMMAND              CREATED             STATUS              PORTS                NAMES
3da00776cecb        ozgurozturknet/adanzyedocker   "httpd-foreground"   3 minutes ago       Up 3 minutes        0.0.0.0:80->80/tcp   silly_turing

-- showed logs with container_id which has a unique code
> docker container logs 3da00776cecb
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
[Mon Dec 21 23:34:03.854449 2020] [mpm_event:notice] [pid 1:tid 140605397114184] AH00489: Apache/2.4.41 (Unix) configured -- resuming normal operations
[Mon Dec 21 23:34:03.854975 2020] [core:notice] [pid 1:tid 140605397114184] AH00094: Command line: 'httpd -D FOREGROUND'
> docker container logs 3da
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
[Mon Dec 21 23:34:03.854449 2020] [mpm_event:notice] [pid 1:tid 140605397114184] AH00489: Apache/2.4.41 (Unix) configured -- resuming normal operations
[Mon Dec 21 23:34:03.854975 2020] [core:notice] [pid 1:tid 140605397114184] AH00094: Command line: 'httpd -D FOREGROUND'


> docker container ls
CONTAINER ID        IMAGE                          COMMAND              CREATED             STATUS              PORTS                NAMES
3da00776cecb        ozgurozturknet/adanzyedocker   "httpd-foreground"   10 minutes ago      Up 11 minutes       0.0.0.0:80->80/tcp   silly_turing

-- We changed previous running app(java app1) instead of default app and gave diffirent names with --name parameter
> docker container run --name denemecon ozgurozturknet/adanzyedocker java app1
Merhaba arkadaslar ben App1 uygulamasiyim

> docker container ls
CONTAINER ID        IMAGE                          COMMAND              CREATED             STATUS              PORTS                NAMES
3da00776cecb        ozgurozturknet/adanzyedocker   "httpd-foreground"   18 minutes ago      Up 18 minutes       0.0.0.0:80->80/tcp   silly_turing

> docker container ls -a
CONTAINER ID        IMAGE                          COMMAND              CREATED             STATUS                      PORTS                NAMES
5ab40a3b4172        ozgurozturknet/adanzyedocker   "java app1"          53 seconds ago      Exited (0) 57 seconds ago                        denemecon
3da00776cecb        ozgurozturknet/adanzyedocker   "httpd-foreground"   18 minutes ago      Up 18 minutes               0.0.0.0:80->80/tcp   silly_turing
9dbc857ba4bf        ozgurozturknet/app1            "java app1"          2 hours ago         Exited (0) 2 hours ago                           firstcontainer
14a8371f7cfa        bf756fb1ae65                   "/hello"             2 hours ago         Exited (0) 2 hours ago                           blissful_newton
7c50837145b5        bf756fb1ae65                   "/hello"             2 hours ago         Exited (0) 2 hours ago                           vigorous_lederberg
d9101e17afa0        bf756fb1ae65                   "/hello"             3 hours ago         Exited (0) 3 hours ago                           determined_nobel

-- stopped container with id
> docker container stop 3da
3da

> docker container ls -a
CONTAINER ID        IMAGE                          COMMAND              CREATED             STATUS                     PORTS               NAMES
5ab40a3b4172        ozgurozturknet/adanzyedocker   "java app1"          2 minutes ago       Exited (0) 2 minutes ago                       denemecon
3da00776cecb        ozgurozturknet/adanzyedocker   "httpd-foreground"   20 minutes ago      Exited (0) 4 seconds ago                       silly_turing
9dbc857ba4bf        ozgurozturknet/app1            "java app1"          2 hours ago         Exited (0) 2 hours ago                         firstcontainer
14a8371f7cfa        bf756fb1ae65                   "/hello"             2 hours ago         Exited (0) 2 hours ago                         blissful_newton
7c50837145b5        bf756fb1ae65                   "/hello"             2 hours ago         Exited (0) 2 hours ago                         vigorous_lederberg
d9101e17afa0        bf756fb1ae65                   "/hello"             3 hours ago         Exited (0) 3 hours ago                         determined_nobel

-- how to create and start container without connection with shell (parameter -d)
> docker container run -d -p 80:80 ozgurozturknet/adanzyedocker
6944c46f2507a8cc2f7b529cd7b5b253feddec3a52201c28392594f24885d706

> docker container ls
CONTAINER ID        IMAGE                          COMMAND              CREATED             STATUS              PORTS                NAMES
6944c46f2507        ozgurozturknet/adanzyedocker   "httpd-foreground"   3 seconds ago       Up 7 seconds        0.0.0.0:80->80/tcp   peaceful_albattani

> docker container ls -a
CONTAINER ID        IMAGE                          COMMAND              CREATED             STATUS                      PORTS                NAMES
6944c46f2507        ozgurozturknet/adanzyedocker   "httpd-foreground"   16 seconds ago      Up 20 seconds               0.0.0.0:80->80/tcp   peaceful_albattani
5ab40a3b4172        ozgurozturknet/adanzyedocker   "java app1"          44 minutes ago      Exited (0) 44 minutes ago                        denemecon
3da00776cecb        ozgurozturknet/adanzyedocker   "httpd-foreground"   About an hour ago   Exited (0) 42 minutes ago                        silly_turing
9dbc857ba4bf        ozgurozturknet/app1            "java app1"          2 hours ago         Exited (0) 2 hours ago                           firstcontainer
14a8371f7cfa        bf756fb1ae65                   "/hello"             3 hours ago         Exited (0) 3 hours ago                           blissful_newton
7c50837145b5        bf756fb1ae65                   "/hello"             3 hours ago         Exited (0) 3 hours ago                           vigorous_lederberg
d9101e17afa0        bf756fb1ae65                   "/hello"             4 hours ago         Exited (0) 4 hours ago                           determined_nobel

-- to do same job with 'docker container ls' command
> docker ps
CONTAINER ID        IMAGE                          COMMAND              CREATED             STATUS              PORTS                NAMES
6944c46f2507        ozgurozturknet/adanzyedocker   "httpd-foreground"   2 minutes ago       Up 2 minutes        0.0.0.0:80->80/tcp   peaceful_albattani

> docker ps -a
CONTAINER ID        IMAGE                          COMMAND              CREATED             STATUS                      PORTS                NAMES
6944c46f2507        ozgurozturknet/adanzyedocker   "httpd-foreground"   2 minutes ago       Up 2 minutes                0.0.0.0:80->80/tcp   peaceful_albattani
5ab40a3b4172        ozgurozturknet/adanzyedocker   "java app1"          46 minutes ago      Exited (0) 46 minutes ago                        denemecon
3da00776cecb        ozgurozturknet/adanzyedocker   "httpd-foreground"   About an hour ago   Exited (0) 44 minutes ago                        silly_turing
9dbc857ba4bf        ozgurozturknet/app1            "java app1"          2 hours ago         Exited (0) 2 hours ago                           firstcontainer
14a8371f7cfa        bf756fb1ae65                   "/hello"             3 hours ago         Exited (0) 3 hours ago                           blissful_newton
7c50837145b5        bf756fb1ae65                   "/hello"             3 hours ago         Exited (0) 3 hours ago                           vigorous_lederberg
d9101e17afa0        bf756fb1ae65                   "/hello"             4 hours ago         Exited (0) 4 hours ago                           determined_nobel

-- removed exited container
> docker container rm 694 5ab 3da 9db 14a 7c5 d91
5ab
3da
9db
14a
7c5
d91
Error response from daemon: You cannot remove a running container 6944c46f2507a8cc2f7b529cd7b5b253feddec3a52201c28392594f24885d706. Stop the container before attempting removal or force remove

> docker ps -a
CONTAINER ID        IMAGE                          COMMAND              CREATED             STATUS              PORTS                NAMES
6944c46f2507        ozgurozturknet/adanzyedocker   "httpd-foreground"   3 minutes ago       Up 3 minutes        0.0.0.0:80->80/tcp   peaceful_albattani

-- force remove for opened container
> docker container rm -f 694
694

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES


--------------------------------------------------------------------

Date of Notes : 22-12-2020


> docker container run --name websunucu -p 84:84 -d ozgurozturknet/adanzyedocker
fb450d9276eeb54340c908af1379f098ba9c1a87cd188e4f21c7ce7fb8aaf816

> docker ps
CONTAINER ID        IMAGE                          COMMAND              CREATED                  STATUS              PORTS                        NAMES
fb450d9276ee        ozgurozturknet/adanzyedocker   "httpd-foreground"   Less than a second ago   Up 5 seconds        80/tcp, 0.0.0.0:84->84/tcp   websunucu

-- connected container named 'websunucu' this command, we used here sh parameter because this container consist this shell 
> docker container exec -it websunucu sh
/usr/src/myapp # pwd
/usr/src/myapp
/usr/src/myapp # ls -l
total 8
-rwxr-xr-x    1 root     root           443 Sep 20  2019 app1.class
-rwxr-xr-x    1 root     root           151 Sep 20  2019 app1.java
/usr/src/myapp # java app1
Merhaba arkadaslar ben App1 uygulamasiyim
/usr/src/myapp # cd /usr/local/apache2/htdocs/
/usr/local/apache2/htdocs # ls
index.html
/usr/local/apache2/htdocs # echo "I added that" >> index.html
/usr/local/apache2/htdocs # ps
PID   USER     TIME  COMMAND
    1 root      0:00 httpd -DFOREGROUND
    7 daemon    0:00 httpd -DFOREGROUND
    8 daemon    0:00 httpd -DFOREGROUND
    9 daemon    0:00 httpd -DFOREGROUND
  117 root      0:00 sh
  134 root      0:00 ps
/usr/local/apache2/htdocs # exit

-- container is still working
> docker ps
CONTAINER ID        IMAGE                          COMMAND              CREATED             STATUS              PORTS                        NAMES
fb450d9276ee        ozgurozturknet/adanzyedocker   "httpd-foreground"   15 minutes ago      Up 15 minutes       80/tcp, 0.0.0.0:84->84/tcp   websunucu

> docker container exec -it websunucu sh
/usr/src/myapp # ps
PID   USER     TIME  COMMAND
    1 root      0:00 httpd -DFOREGROUND  // Docker is running here!!
    7 daemon    0:00 httpd -DFOREGROUND
    8 daemon    0:00 httpd -DFOREGROUND
    9 daemon    0:00 httpd -DFOREGROUND
   91 root      0:00 sh
   96 root      0:00 ps
/usr/src/myapp # kill 1
>  

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES

> docker start websunucu
websunucu

> docker ps
CONTAINER ID        IMAGE                          COMMAND              CREATED             STATUS              PORTS                        NAMES
fb450d9276ee        ozgurozturknet/adanzyedocker   "httpd-foreground"   33 minutes ago      Up 7 seconds        80/tcp, 0.0.0.0:84->84/tcp   websunucu

> docker stop websunucu
websunucu

> docker container run --name websunucu2 -p 80:80 ozgurozturknet/adanzyedocker
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
[Tue Dec 22 12:18:19.905296 2020] [mpm_event:notice] [pid 1:tid 139812057718088] AH00489: Apache/2.4.41 (Unix) configured -- resuming normal operations
[Tue Dec 22 12:18:19.905735 2020] [core:notice] [pid 1:tid 139812057718088] AH00094: Command line: 'httpd -D FOREGROUND'

> docker ps
CONTAINER ID        IMAGE                          COMMAND              CREATED             STATUS              PORTS                NAMES
3bc8646b8fce        ozgurozturknet/adanzyedocker   "httpd-foreground"   20 seconds ago      Up 25 seconds       0.0.0.0:80->80/tcp   websunucu2

> docker stop websunucu2
websunucu2

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES

> docker ps -a
CONTAINER ID        IMAGE                          COMMAND              CREATED             STATUS                      PORTS               NAMES
3bc8646b8fce        ozgurozturknet/adanzyedocker   "httpd-foreground"   23 minutes ago      Exited (0) 15 seconds ago                       websunucu2
fb450d9276ee        ozgurozturknet/adanzyedocker   "httpd-foreground"   59 minutes ago      Exited (0) 24 minutes ago                       websunucu

-- removed all stopped containers.
> docker container prune
WARNING! This will remove all stopped containers.
Are you sure you want to continue? [y/N] y
Deleted Containers:
3bc8646b8fcefc030a4de7d3442fa07715f29391b301419e0bfa6b757ba51dc8
fb450d9276eeb54340c908af1379f098ba9c1a87cd188e4f21c7ce7fb8aaf816

Total reclaimed space: 246B

-- listed all loaded image
> docker image ls
REPOSITORY                     TAG                 IMAGE ID            CREATED             SIZE
ozgurozturknet/adanzyedocker   latest              2b4647565690        14 months ago       284MB
ozgurozturknet/app1            latest              353d147de1ee        15 months ago       126MB

-- removed all images
> docker image prune -a
WARNING! This will remove all images without at least one container associated to them.
Are you sure you want to continue? [y/N] y
Deleted Images:
untagged: ozgurozturknet/adanzyedocker:latest
untagged: ozgurozturknet/adanzyedocker@sha256:10631a62b96b8dc8c468fe482aff70871c6c81f4a49ea4c5350ce765cf9f2185
deleted: sha256:2b4647565690601db6596445de527a5a3b58ca1ad3b1ab7c65d8951c005a010b
deleted: sha256:964446c988fd1e5fee2abac9e1a933bc87798a470c05cf4c1847078e61006e6d
deleted: sha256:9bdda1f65436233523dba5cd6d6a1a2d11e440d2476cc65ecf96e4359a4ede26
deleted: sha256:3fabdeb6341f5fe0b6d74c71ffbae59943ad7987262ec7138a923f41db38a027
deleted: sha256:0d65a7390e0db582196371e3cd2604cacf0d7aeb7cd0bcd6caae5806747fa813
deleted: sha256:64f7d41b0ee7a64a8813cdda3c28e2faa9a8fc63491979ebee51f157d5b379b0
deleted: sha256:d4f8488f29f67595a5f71f2a1a06ed4789f75e8a28d68424d8355c8239729950
deleted: sha256:3b1c73e3b013e3d8105168baf99d5c70bc0d50034a26b1bbeb3380cb2eb3974e
deleted: sha256:f1968fce613534a5984f094d1ccac8565d23c8f6b8519dcbccdd97e3d1c31fc1
deleted: sha256:2adceec975613b737e86933ed34395c9a729827b1e506ba64debb27720869c29
deleted: sha256:03901b4a2ea88eeaad62dbe59b072b28b6efa00491962b8741081c5df50c65e0
untagged: ozgurozturknet/app1:latest
untagged: ozgurozturknet/app1@sha256:31acbf06b10306dc403bb57ecd2be4e870d9ecacacbff006a56c1f5e40f762d6
deleted: sha256:353d147de1eeedddf3898f1f16912d57bf59d464a42c943b3aa2efb187dc1bdb
deleted: sha256:49282dd5cd75d962a835848877635f16d986061d60919c525f58b728e0f5a9d7
deleted: sha256:bcbb28e2357ac01735d3773630d4379c8b84a02a0003de04c165b3a3e0d223bc
deleted: sha256:9a11d33865b43fe3be3353f22a1c9cd22911daab3d7845f77f95dbc9083f0527
deleted: sha256:767f936afb51c8a3ad9a96592a4be092048bb70f2ca410028a0b3f64b826acbb

Total reclaimed space: 410.1MB

> docker image ls
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE

-- downloaded alpine operation system which is for first layer of Docker infrastructure
> docker image pull alpine
Using default tag: latest
latest: Pulling from library/alpine
801bfaa63ef2: Pull complete		**That shows it has 2 layer.
Digest: sha256:3c7497bf0c7af93428242d6176e8f7905f2201d8fc5861f45be7a346b5f23436
Status: Downloaded newer image for alpine:latest
docker.io/library/alpine:latest

-- how to pull image from docker-hub, NOTES: if we downloaded a image before, and then we want to download a diffirent image. As a result, it will not download base layer again. (etc.alpine) 
> docker image pull ozgurozturknet/hello-app
Using default tag: latest
latest: Pulling from ozgurozturknet/hello-app
aad63a933944: Pull complete		**That shows it has 2 layer.
e7f2aa010900: Pull complete
Digest: sha256:a4b3acfb88eafb47a7b5f1266f25ff114d3148186d130dad5d4319086b26c4c2
Status: Downloaded newer image for ozgurozturknet/hello-app:latest
docker.io/ozgurozturknet/hello-app:latest

--- DOCKER Volume Management (it provides to keep our data somewhere out of containers)

-- created a volume name firstvolume
> docker volume create firstvolume
firstvolume

-- looking firstvolume detail
> docker volume inspect firstvolume
[
    {
        "CreatedAt": "2020-12-22T14:56:14Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/mnt/sda1/var/lib/docker/volumes/firstvolume/_data",
        "Name": "firstvolume",
        "Options": {},
        "Scope": "local"
    }
] 

> docker container  run -it -v firstvolume:/uygulama alpine sh
/ # ls
bin       etc       lib       mnt       proc      run       srv       tmp       uygulama
dev       home      media     opt       root      sbin      sys       usr       var
/ # cd uygulama/
/uygulama # ls
abc.txt
/uygulama # cat abc.txt
/uygulama # echo "added from first container" >> abc.txt
/uygulama # cat abc.txt
added from first container
/uygulama # exit

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
91508456fd54        alpine              "sh"                5 minutes ago       Up 6 minutes                            optimistic_visvesvaraya

> docker container rm 915
Error response from daemon: You cannot remove a running container 91508456fd545a43a0382b6f421ec353fa9db4ff38eb5658c1d5d222f91c093e. Stop the container before attempting removal or force remove

> docker container rm -f 915
915

> docker volume ls
DRIVER              VOLUME NAME
local               firstvolume

c1
> docker container run -it -v firstvolume:/deneme alpine sh
/ # ls
bin     deneme  dev     etc     home    lib     media   mnt     opt     proc    root    run     sbin    srv     sys     tmp     usr     var
/ # cd deneme/
/deneme # ls
abc.txt
/deneme # cat abc.txt
added from first container
/deneme # touch klm.txt
/deneme # ls
abc.txt  klm.txt
/deneme # ls
abc.txt    klm.txt    third.txt
/deneme # cat third.txt
test
/deneme #

-- They two container can work within same volume, and see same items 

C2
> docker container run -it -v firstvolume:/deneme2 centos sh
sh-4.4# ls
bin  deneme2  dev  etc  home  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
sh-4.4# cd deneme2/
sh-4.4# ls
abc.txt  klm.txt
sh-4.4# cat abc.txt
added from first container
sh-4.4# touch third.txt
sh-4.4# ls
abc.txt  klm.txt  third.txt
sh-4.4# echo "test" >> third.txt


--  can reach firstvolume volume just read only with 'ro' parameter
C3
> docker container run -it -v firstvolume:/deneme3:ro centos sh
sh-4.4# ls
bin  deneme3  dev  etc  home  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
sh-4.4# cd deneme3/
sh-4.4# ls
abc.txt  klm.txt  third.txt
sh-4.4# touch forth.txt
touch: cannot touch 'forth.txt': Read-only file system 

--  rm parameter: provide to close container after container stop
> docker container run --rm -it ozgurozturknet/adanzyedocker sh
/usr/src/myapp # ls
app1.class  app1.java
/usr/src/myapp # exit

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES


--  When we have a full volume, Its items will appear in the mounted folder.
> docker volume create deneme1
deneme1

> docker volume ls
DRIVER              VOLUME NAME
local               deneme1
local               firstvolume

> docker container run --rm -it -v deneme1:/test ozgurozturknet/adanzyedocker sh
/usr/src/myapp # cd /
/ # ls
bin    dev    etc    home   lib    media  mnt    opt    proc   root   run    sbin   srv    sys    test   tmp    usr    var
/ # cd test/
/test # ls
/test # exit

> docker container run --rm -it -v deneme1:/usr/src/myapp ozgurozturknet/adanzyedocker sh
/usr/src/myapp # ls
app1.class  app1.java
/usr/src/myapp # exit

> docker container run --rm -it -v deneme1:/xyz alpine sh
/ # ls
bin    dev    etc    home   lib    media  mnt    opt    proc   root   run    sbin   srv    sys    tmp    usr    var    xyz
/ # cd xyz/
/xyz # ls
app1.class  app1.java
/xyz # touch adanzyedocker.txt
/xyz # ls
adanzyedocker.txt  app1.class         app1.java
/xyz # exit

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES

> docker volume ls
DRIVER              VOLUME NAME
local               deneme1
local               firstvolume

> docker container run --rm -it -v deneme1:/usr/src/myapp ozgurozturknet/adanzyedocker sh
/usr/src/myapp # ls
adanzyedocker.txt  app1.class         app1.java

---  Bind Mounts
 
-- created a container from nginx image and started 
> docker container run -d -p 80:80 --name firstweb nginx
Unable to find image 'nginx:latest' locally
latest: Pulling from library/nginx
6ec7b7d162b2: Pull complete
cb420a90068e: Pull complete
2766c0bf2b07: Pull complete
e05167b6a99d: Pull complete
70ac9d795e79: Pull complete
Digest: sha256:4cf620a5c81390ee209398ecc18e5fb9dd0f5155cd82adcbae532fec94006fb9
Status: Downloaded newer image for nginx:latest
17fce2776a11ca43566ab43d323bbc1a055aef5a6f8acd62da69d964204d1f42

--  connected this container
> docker exec -it 17f sh
# cd /usr/share/nginx/html
# ls
50x.html  index.html
# cat index.html
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
# exit


> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED                  STATUS              PORTS                NAMES
17fce2776a11        nginx               "/docker-entrypoint."   Less than a second ago   Up 5 minutes        0.0.0.0:80->80/tcp   firstweb

> docker rm -f 17f
17f

-- how to bind a folder from own local computer folders
> docker container run -d -p 80:80 -v E:\AdanZyeDocker\kisim3\bolum28\websitesi:/usr/share/nginx/html nginx
C:\Program Files\Docker Toolbox\docker.exe: Error response from daemon: invalid mode: /usr/nginx/html.
See 'C:\Program Files\Docker Toolbox\docker.exe run --help'.

Important Notes: it didn't work because I didn't find where I can permit at docker UI to reach my local disk(C or E). 
Also we shouldn't use binding metod with production. It can just use at development device. 

--------------------------------------------------------------------

Date of Notes : 23-12-2020
Docker Network Objects

-- listed networks
> docker network ls
NETWORK ID          NAME                DRIVER              SCOPE
2bb8ee186599        bridge              bridge              local
bc224eb7a822        host                host                local
8ad1749707e8        none                null                local

-- looked detail of 'bridge' network. Additional, Bridge is a default network when we create a container.
> docker network inspect bridge
[
    {
        "Name": "bridge",
        "Id": "2bb8ee186599385733e6e6b2f04cea2e9869841449b7a9a567194064c2ef461b",
        "Created": "2020-12-23T09:52:41.629108948Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": [
                {
                    "Subnet": "172.17.0.0/16",
                    "Gateway": "172.17.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {},
        "Options": {
            "com.docker.network.bridge.default_bridge": "true",
            "com.docker.network.bridge.enable_icc": "true",
            "com.docker.network.bridge.enable_ip_masquerade": "true",
            "com.docker.network.bridge.host_binding_ipv4": "0.0.0.0",
            "com.docker.network.bridge.name": "docker0",
            "com.docker.network.driver.mtu": "1500"
        },
        "Labels": {}
    }
]

-- we realized that the bridge is a default network when we create a container.
> docker container run -d ozgurozturknet/adanzyedocker
ee41242045cdb78d0bb01c0004223984dbe88cc8a1418223256c0ef27713a50d

> docker network inspect bridge
[
    {
        "Name": "bridge",
        "Id": "2bb8ee186599385733e6e6b2f04cea2e9869841449b7a9a567194064c2ef461b",
        "Created": "2020-12-23T09:52:41.629108948Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": [
                {
                    "Subnet": "172.17.0.0/16",
                    "Gateway": "172.17.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "ee41242045cdb78d0bb01c0004223984dbe88cc8a1418223256c0ef27713a50d": {
                "Name": "cranky_roentgen",
                "EndpointID": "6524e0fa985459a9e9b6785955a28f2458f537eabfe9c66eb13454bc8f57d198",
                "MacAddress": "02:42:ac:11:00:02",
                "IPv4Address": "172.17.0.2/16",
                "IPv6Address": ""
            }
        },
        "Options": {
            "com.docker.network.bridge.default_bridge": "true",
            "com.docker.network.bridge.enable_icc": "true",
            "com.docker.network.bridge.enable_ip_masquerade": "true",
            "com.docker.network.bridge.host_binding_ipv4": "0.0.0.0",
            "com.docker.network.bridge.name": "docker0",
            "com.docker.network.driver.mtu": "1500"
        },
        "Labels": {}
    }
]


> docker ps
CONTAINER ID        IMAGE                          COMMAND              CREATED             STATUS              PORTS               NAMES
ee41242045cd        ozgurozturknet/adanzyedocker   "httpd-foreground"   40 seconds ago      Up 41 seconds       80/tcp              cranky_roentgen

-- we look that the container take a ip from the bridge network
> docker exec -it ee41242045cd  sh
/usr/src/myapp # ifconfig
eth0      Link encap:Ethernet  HWaddr 02:42:AC:11:00:02
          inet addr:172.17.0.2  Bcast:172.17.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:976 (976.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

/usr/src/myapp # ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=117 time=25.10 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=117 time=50.0 ms
^C
--- 8.8.8.8 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 3ms
rtt min/avg/max/mdev = 25.964/38.000/50.037/12.038 ms
/usr/src/myapp # read escape sequence

> docker ps
CONTAINER ID        IMAGE                          COMMAND              CREATED             STATUS              PORTS               NAMES
ee41242045cd        ozgurozturknet/adanzyedocker   "httpd-foreground"   4 minutes ago       Up 4 minutes        80/tcp              cranky_roentgen

> docker container run -it --name deneme ozgurozturknet/adanzyedocker sh
/usr/src/myapp # ifconfig
eth0      Link encap:Ethernet  HWaddr 02:42:AC:11:00:03
          inet addr:172.17.0.3  Bcast:172.17.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:516 (516.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

/usr/src/myapp # ping 172.17.0.2
PING 172.17.0.2 (172.17.0.2) 56(84) bytes of data.
64 bytes from 172.17.0.2: icmp_seq=1 ttl=64 time=0.145 ms
64 bytes from 172.17.0.2: icmp_seq=2 ttl=64 time=0.063 ms
^C
--- 172.17.0.2 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 4ms
rtt min/avg/max/mdev = 0.063/0.104/0.145/0.041 ms
/usr/src/myapp # exit

> docker network ls
NETWORK ID          NAME                DRIVER              SCOPE
2bb8ee186599        bridge              bridge              local
bc224eb7a822        host                host                local
8ad1749707e8        none                null                local

> docker container run -it --name deneme22 ozgurozturknet/adanzyedocker sh
/usr/src/myapp # ifconfig
eth0      Link encap:Ethernet  HWaddr 02:42:AC:11:00:03
          inet addr:172.17.0.3  Bcast:172.17.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:516 (516.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

/usr/src/myapp # exit

-- we can use parameter '--net' to choose a diffirent network like here none
> docker container run -it --name deneme34 --net none ozgurozturknet/adanzyedocker sh
/usr/src/myapp # ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

/usr/src/myapp # ping 8.8.8.8
connect: Network unreachable

-- The container is connected to host network
[node1] (local) root@192.168.0.23 ~
$ docker container run -it --name deneme1 --net host ozgurozturknet/adanzyedocker sh
Unable to find image 'ozgurozturknet/adanzyedocker:latest' locally
latest: Pulling from ozgurozturknet/adanzyedocker
9d48c3bd43c5: Pull complete 
d3565940ff69: Pull complete 
1cc6c921162a: Pull complete 
17877ce0de23: Pull complete 
4e10ed3cf6fc: Pull complete 
84d0ceb32a5d: Pull complete 
1587ec6e5583: Pull complete 
e7daf8feccda: Pull complete 
49641b0d4586: Pull complete 
1c5aa5048b34: Pull complete 
Digest: sha256:10631a62b96b8dc8c468fe482aff70871c6c81f4a49ea4c5350ce765cf9f2185
Status: Downloaded newer image for ozgurozturknet/adanzyedocker:latest
/usr/src/myapp # ifconfig
docker0   Link encap:Ethernet  HWaddr 02:42:79:E6:9A:AF  
          inet addr:172.17.0.1  Bcast:172.17.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr FA:2F:A5:21:38:47  
          inet addr:192.168.0.23  Bcast:0.0.0.0  Mask:255.255.254.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1296 (1.2 KiB)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 02:42:AC:12:00:3A  
          inet addr:172.18.0.58  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86097 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:125928654 (120.0 MiB)  TX bytes:436249 (426.0 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:12701 (12.4 KiB)  TX bytes:12701 (12.4 KiB)

-- how to do port publish
$ docker container run -d -p 8080:80 ozgurozturknet/adanzyedocker
$ docker container run -d --publish 53:53/udp ozgurozturknet/adanzyedocker

$ docker container run -d --publish 8080:80 ozgurozturknet/adanzyedocker
bc52449f7b603562778baca56b8e6c208dcb2bd5c9689ae47ef87c55476348e1

[node1] (local) root@192.168.0.23 ~
$ docker ps
CONTAINER ID   IMAGE                          COMMAND              CREATED          STATUS          PORTS                  NAMES
bc52449f7b60   ozgurozturknet/adanzyedocker   "httpd-foreground"   19 seconds ago   Up 18 seconds   0.0.0.0:8080->80/tcp   competent_goldberg

-- Lets check those two container are not connected. 
> docker container run -d --name websunucu1 ozgurozturknet/adanzyedocker
bbcb44d4582ce77cee5d4c8d678bee21ab1c80a82ffe6b0154ef13d4683d1a2f

-- We couldn't ping with name of container
> docker container run -it --name database1 ozgurozturknet/adanzyedocker sh
/usr/src/myapp # ping websunucu1
ping: websunucu1: Name does not resolve
/usr/src/myapp # ping 172.17.0.2
PING 172.17.0.2 (172.17.0.2) 56(84) bytes of data.
64 bytes from 172.17.0.2: icmp_seq=1 ttl=64 time=0.070 ms
64 bytes from 172.17.0.2: icmp_seq=2 ttl=64 time=0.139 ms
^C
--- 172.17.0.2 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 9ms
rtt min/avg/max/mdev = 0.070/0.104/0.139/0.035 ms
/usr/src/myapp # exit

> docker ps -a
CONTAINER ID        IMAGE                          COMMAND              CREATED              STATUS                      PORTS               NAMES
7efadfbe130e        ozgurozturknet/adanzyedocker   "sh"                 57 seconds ago       Exited (0) 21 seconds ago                       database1
bbcb44d4582c        ozgurozturknet/adanzyedocker   "httpd-foreground"   About a minute ago   Up About a minute           80/tcp              websunucu1

> docker container rm -f 7ef bbc
7ef
bbc

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES

-- how to create Network 
> docker network create bridge1
df6f410dc3837433cbfaece7b6724564b9a4a791c58dbc1ddf768176f2086adb

> docker network ls
NETWORK ID          NAME                DRIVER              SCOPE
2bb8ee186599        bridge              bridge              local
df6f410dc383        bridge1             bridge              local
bc224eb7a822        host                host                local
8ad1749707e8        none                null                local

> docker network inspect bridge1
[
    {
        "Name": "bridge1",
        "Id": "df6f410dc3837433cbfaece7b6724564b9a4a791c58dbc1ddf768176f2086adb",
        "Created": "2020-12-23T17:30:18.988810011Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "172.19.0.0/16",
                    "Gateway": "172.19.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {},
        "Options": {},
        "Labels": {}
    }
]

-- created a conatiner named 'websunucu' in bridge1 network with using '-dit' parameter to reach later
> docker container run -dit --name websunucu --net bridge1 ozgurozturknet/adanzyedocker sh
154bac3221a033f060edde72f2ba067c5978b5f2e226423b0c911bab1cc550e5

-- created a conatiner named 'database' in bridge1 network with using '-dit' parameter to reach later
> docker container run -dit --name database --net bridge1 ozgurozturknet/adanzyedocker sh
981c5e69174824af13723c43935f933e8b43cd69c48bffbce55137c452ba02c1

> docker ps
CONTAINER ID        IMAGE                          COMMAND             CREATED             STATUS              PORTS               NAMES
981c5e691748        ozgurozturknet/adanzyedocker   "sh"                6 seconds ago       Up 8 seconds        80/tcp              database
154bac3221a0        ozgurozturknet/adanzyedocker   "sh"                19 seconds ago      Up 21 seconds       80/tcp              websunucu

> docker network inspect bridge1
[
    {
        "Name": "bridge1",
        "Id": "df6f410dc3837433cbfaece7b6724564b9a4a791c58dbc1ddf768176f2086adb",
        "Created": "2020-12-23T17:30:18.988810011Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "172.19.0.0/16",
                    "Gateway": "172.19.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "154bac3221a033f060edde72f2ba067c5978b5f2e226423b0c911bab1cc550e5": {
                "Name": "websunucu",
                "EndpointID": "96e8b6aa5dc1963988228b4ba33ffa3ccc81cf92e73e5b366573643b90321412",
                "MacAddress": "02:42:ac:13:00:02",
                "IPv4Address": "172.19.0.2/16",
                "IPv6Address": ""
            },
            "981c5e69174824af13723c43935f933e8b43cd69c48bffbce55137c452ba02c1": {
                "Name": "database",
                "EndpointID": "f765ec233548beed8cc9fe85d70c6e541112b9472a1505814fd8877f2d8db8c3",
                "MacAddress": "02:42:ac:13:00:03",
                "IPv4Address": "172.19.0.3/16",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {}
    }
]

-- entered websunucu container, pinged another container which name is database and see that they connected each other
> docker attach websunucu
/usr/src/myapp # ping database
PING database (172.19.0.3) 56(84) bytes of data.
64 bytes from database.bridge1 (172.19.0.3): icmp_seq=1 ttl=64 time=0.091 ms
64 bytes from database.bridge1 (172.19.0.3): icmp_seq=2 ttl=64 time=0.143 ms
^C
--- database ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 3ms
rtt min/avg/max/mdev = 0.091/0.117/0.143/0.026 ms
/usr/src/myapp # read escape sequence

-- entered database container, pinged another container which name is websunucu and see that they connected each other
> docker attach database
/usr/src/myapp # ping websunucu
PING websunucu (172.19.0.2) 56(84) bytes of data.
64 bytes from websunucu.bridge1 (172.19.0.2): icmp_seq=1 ttl=64 time=0.063 ms
64 bytes from websunucu.bridge1 (172.19.0.2): icmp_seq=2 ttl=64 time=0.245 ms
64 bytes from websunucu.bridge1 (172.19.0.2): icmp_seq=3 ttl=64 time=0.168 ms
^C
--- websunucu ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 39ms
rtt min/avg/max/mdev = 0.063/0.158/0.245/0.076 ms

> docker ps
CONTAINER ID        IMAGE                          COMMAND             CREATED             STATUS              PORTS               NAMES
981c5e691748        ozgurozturknet/adanzyedocker   "sh"                3 minutes ago       Up 3 minutes        80/tcp              database
154bac3221a0        ozgurozturknet/adanzyedocker   "sh"                3 minutes ago       Up 3 minutes        80/tcp              websunucu

-- how to create a specific network to arrange some properties, we created bridge2 for that
> docker network create --driver=bridge --subnet=10.10.0.0/16 --ip-range=10.10.10.0/24 --gateway=10.10.10.10 bridge2
8877105e80aae8a7070a6136dc0ecb0a36e89a52e9cac7f53396df7bbf679d79

> docker network ls
NETWORK ID          NAME                DRIVER              SCOPE
2bb8ee186599        bridge              bridge              local
df6f410dc383        bridge1             bridge              local
8877105e80aa        bridge2             bridge              local
bc224eb7a822        host                host                local
8ad1749707e8        none                null                local

> docker network inspect bridge2
[
    {
        "Name": "bridge2",
        "Id": "8877105e80aae8a7070a6136dc0ecb0a36e89a52e9cac7f53396df7bbf679d79",
        "Created": "2020-12-23T17:39:26.976799888Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "10.10.0.0/16",
                    "IPRange": "10.10.10.0/24",
                    "Gateway": "10.10.10.10"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {},
        "Options": {},
        "Labels": {}
    }
]

> docker attach database
/usr/src/myapp # ifconfig
eth0      Link encap:Ethernet  HWaddr 02:42:AC:13:00:03
          inet addr:172.19.0.3  Bcast:172.19.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1594 (1.5 KiB)  TX bytes:658 (658.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:437 (437.0 B)  TX bytes:437 (437.0 B)

-- we can bind a container to two different networks
> docker network connect bridge2 database

> docker attach database
/usr/src/myapp # ifconfig
eth0      Link encap:Ethernet  HWaddr 02:42:AC:13:00:03
          inet addr:172.19.0.3  Bcast:172.19.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1664 (1.6 KiB)  TX bytes:658 (658.0 B)

eth1      Link encap:Ethernet  HWaddr 02:42:0A:0A:0A:00
          inet addr:10.10.10.0  Bcast:10.10.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1242 (1.2 KiB)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:437 (437.0 B)  TX bytes:437 (437.0 B)


-- The database container was diconnected bridge2 network 
> docker network disconnect bridge2 database

> docker network inspect bridge2
[
    {
        "Name": "bridge2",
        "Id": "8877105e80aae8a7070a6136dc0ecb0a36e89a52e9cac7f53396df7bbf679d79",
        "Created": "2020-12-23T17:39:26.976799888Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "10.10.0.0/16",
                    "IPRange": "10.10.10.0/24",
                    "Gateway": "10.10.10.10"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {},
        "Options": {},
        "Labels": {}
    }
]

-- if someone connects a network we can not remove this network 
> docker network rm bridge1
Error response from daemon: error while removing network: network bridge1 id df6f410dc3837433cbfaece7b6724564b9a4a791c58dbc1ddf768176f2086adb has active endpoints

> docker network inspect bridge1
[
    {
        "Name": "bridge1",
        "Id": "df6f410dc3837433cbfaece7b6724564b9a4a791c58dbc1ddf768176f2086adb",
        "Created": "2020-12-23T17:30:18.988810011Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "172.19.0.0/16",
                    "Gateway": "172.19.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "154bac3221a033f060edde72f2ba067c5978b5f2e226423b0c911bab1cc550e5": {
                "Name": "websunucu",
                "EndpointID": "96e8b6aa5dc1963988228b4ba33ffa3ccc81cf92e73e5b366573643b90321412",
                "MacAddress": "02:42:ac:13:00:02",
                "IPv4Address": "172.19.0.2/16",
                "IPv6Address": ""
            },
            "981c5e69174824af13723c43935f933e8b43cd69c48bffbce55137c452ba02c1": {
                "Name": "database",
                "EndpointID": "f765ec233548beed8cc9fe85d70c6e541112b9472a1505814fd8877f2d8db8c3",
                "MacAddress": "02:42:ac:13:00:03",
                "IPv4Address": "172.19.0.3/16",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {}
    }
]

-- deleted bridge2 network
> docker network rm bridge2
bridge2

-- deleted 'websunucu and database' container with using force
> docker container rm -f websunucu database
websunucu
database

-- Finally we removed bridge1 which has no longer connected container
> docker network rm bridge1
bridge1

> docker network ls
NETWORK ID          NAME                DRIVER              SCOPE
2bb8ee186599        bridge              bridge              local
bc224eb7a822        host                host                local
8ad1749707e8        none                null                local

--------------------------------------------------------------------

Date of Notes : 24-12-2020

---- Docker Logs

> docker container run -d --name appone ozgurozturknet/app1
f7913b5107c90ca7c6d201495c028b878e56d5f990882530ef713944cec3c8ef

> docker logs appone
Merhaba arkadaslar ben App1 uygulamasiyim

> docker container run -d --name con1 -p 80:80 nginx
79b89d2ef2abbface4ac6ffb9106f8cafd3916650086558fd15b53a0ecf3dc6a

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                NAMES
79b89d2ef2ab        nginx               "/docker-entrypoint."   4 seconds ago       Up 6 seconds        0.0.0.0:80->80/tcp   con1

-- how to look logs of containers
> docker logs con1
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Configuration complete; ready for start up

--  We can see with 'docker logs' command for nginx logs beacuse of that above link (access.log -> /dev/stdout). Those two folders connected.
> docker exec -it con1 sh
# cd /var/log/nginx
# ls
access.log  error.log
# ls -l
total 0
lrwxrwxrwx 1 root root 11 Dec 15 20:20 access.log -> /dev/stdout
lrwxrwxrwx 1 root root 11 Dec 15 20:20 error.log -> /dev/stderr

> docker logs --help

Usage:  docker logs [OPTIONS] CONTAINER

Fetch the logs of a container

Options:
      --details        Show extra details provided to logs
  -f, --follow         Follow log output
      --since string   Show logs since timestamp (e.g.
                       2013-01-02T13:23:37) or relative (e.g. 42m for 42
                       minutes)
      --tail string    Number of lines to show from the end of the logs
                       (default "all")
  -t, --timestamps     Show timestamps
      --until string   Show logs before a timestamp (e.g.
                       2013-01-02T13:23:37) or relative (e.g. 42m for 42
                       minutes)

> docker container run -d --name con1 -p 80:80 nginx
55023dd07f684ff44e27bd6ce92e1710484c99a9eae6735a27a06fbe121743fe

> docker logs con1
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Configuration complete; ready for start up

> docker logs --details con1
 /docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
 /docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
 /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
 10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
 10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
 /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
 /docker-entrypoint.sh: Configuration complete; ready for start up

--  looks at logs with timestamp
> docker logs -t con1
2020-12-24T11:42:07.562302532Z /docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
2020-12-24T11:42:07.562533275Z /docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
2020-12-24T11:42:07.566558778Z /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
2020-12-24T11:42:07.573026724Z 10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
2020-12-24T11:42:07.584589832Z 10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
2020-12-24T11:42:07.585064060Z /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
2020-12-24T11:42:07.589955979Z /docker-entrypoint.sh: Configuration complete; ready for start up

> docker logs --until 2020-12-24T11:42:07.573026724Z con1
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf


> docker logs --since 2020-12-24T11:42:07.573026724Z con1
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Configuration complete; ready for start up


> docker logs con1
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Configuration complete; ready for start up

--  how to look at last three line log
> docker logs --tail 3 con1
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Configuration complete; ready for start up

--  how to look at last one line log
> docker logs --tail 1 con1
/docker-entrypoint.sh: Configuration complete; ready for start up

--  how to trace instant(live) logs with using -f parameter
> docker logs -f con1
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Configuration complete; ready for start up

--  Lets look at which driver we use for logging (default json-file)
> docker info
Client:
 Debug Mode: false

Server:
 Containers: 2
  Running: 1
  Paused: 0
  Stopped: 1
 Images: 7
 Server Version: 19.03.12
 Storage Driver: overlay2
  Backing Filesystem: extfs
  Supports d_type: true
  Native Overlay Diff: true
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local logentries splunk syslog
 Swarm: inactive
 Runtimes: runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: 7ad184331fa3e55e52b890ea95e65ba581ae3429
 runc version: dc9208a3303feef5b3839f4323d9beb36df0a9dd
 init version: fec3683
 Security Options:
  seccomp
   Profile: default
 Kernel Version: 4.19.130-boot2docker
 Operating System: Boot2Docker 19.03.12 (TCL 10.1)
 OSType: linux
 Architecture: x86_64
 CPUs: 1
 Total Memory: 985.4MiB
 Name: default
 ID: PJQ7:KCNZ:BRBQ:QDZH:GSB7:HK6M:JI24:HVHS:WDY4:QETZ:ZFF5:VLRU
 Docker Root Dir: /mnt/sda1/var/lib/docker
 Debug Mode: false
 Username: gunerhanale
 Registry: https://index.docker.io/v1/
 Labels:
  provider=virtualbox
 Experimental: false
 Insecure Registries:
  127.0.0.0/8
 Live Restore Enabled: false
 Product License: Community Engine

-- we can change logging driver when create a container
> docker container run --log-driver splunk nginx
C:\Program Files\Docker Toolbox\docker.exe: Error response from daemon: failed to initialize logging driver: splunk: splunk-url is expected.


- Docker Stats and Top (to manage all container status)

--  We can see without a connection which process is working in a container (like linux command 'ps')
> docker top con1
UID                 PID                 PPID                C                   STIME               TTY                 TIME                CMD
root                3315                3295                0                   11:42               ?                   00:00:00            nginx: master process nginx -g daemon off;
101                 3364                3315                0                   11:42               ?                   00:00:00            nginx: worker process 

--  We can look at that how much all working containers use CPU, RAM, IO etc.
> docker stats
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT     MEM %               NET I/O             BLOCK I/O           PIDS
55023dd07f68        con1                0.00%               2.207MiB / 985.4MiB   0.22%               1.33kB / 0B         0B / 8.19kB         2

> docker stats con1


---- Container Cpu and Memory Limit

--  default value is limitless 
> docker container run -d ozgurozturknet/adanzyedocker
7a63d892af121782416c596afdd4e463209e7ddfdf372d60f97fd2ca6a66fb6f

> docker stats
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT     MEM %               NET I/O             BLOCK I/O           PIDS
17aa303dbdbd        unruffled_galileo   0.01%               4.445MiB / 985.4MiB   0.45%               656B / 0B           4.6MB / 0B          82
55023dd07f68        con1                0.00%               2.121MiB / 985.4MiB   0.22%               1.4kB / 0B          0B / 8.19kB         2

--  we can set memory size (b,k,m or g) with using '--memory'
> docker container run -d --memory=100m ozgurozturknet/adanzyedocker
3c4474d961dffcb6047b38a2d75fc09989b32834f223758b71eac72e82e17a84

> docker stats
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT     MEM %               NET I/O             BLOCK I/O           PIDS
3c4474d961df        exciting_rhodes     0.02%               4.234MiB / 100MiB     4.23%               726B / 0B           0B / 0B             82
7a63d892af12        busy_lewin          0.01%               4.262MiB / 985.4MiB   0.43%               866B / 0B           0B / 0B             82

--  we can set Swap size of (b,k,m or g) with using '--memory-swap' and Swap should be bigger than memory size. When the memory is over, swap helps us to maintain.
> docker container run -d --memory=100m --memory-swap=200m ozgurozturknet/adanzyedocker
484c0291bff6f5e0ec6796f2f2be157291df031c060f000f0c1bc97e72d42096

> docker stats
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT     MEM %               NET I/O             BLOCK I/O           PIDS
484c0291bff6        musing_cohen        0.00%               4.344MiB / 100MiB     4.34%               866B / 0B           0B / 0B             82
3c4474d961df        exciting_rhodes     0.02%               4.215MiB / 100MiB     4.21%               936B / 0B           0B / 0B             82
7a63d892af12        busy_lewin          0.00%               4.262MiB / 985.4MiB   0.43%               1.01kB / 0B         0B / 0B             82

-- we can set how much core we want to use with using '--cpus' (--cpus="0.5", --cpus="1.5", --cpus="2")
> docker container run -d --cpus="0.5" ozgurozturknet/adanzyedocker
7345b73051f9100d0f57753e62be8d40eaacac0831b33f748676de882adb941b

-- we can set which number of cores we want to use with using '--cpuset-cpus' (--cpuset-cpus="0", --cpuset-cpus="0,3")
> docker container run -d --cpus="0.5" --cpuset-cpus="0" ozgurozturknet/adanzyedocker
8a52cd2c00a47238401d309b7b093ae8495108402feb34047037f9cfdf3b9700


---- Environment Variables

--  how to list Environment Variables for Windows
> Get-ChildItem Env:

Name                           Value
----                           -----
ALLUSERSPROFILE                C:\ProgramData
APPDATA                        C:\Users\ebubekir\AppData\Roaming
CommonProgramFiles             C:\Program Files\Common Files
CommonProgramFiles(x86)        C:\Program Files (x86)\Common Files
CommonProgramW6432             C:\Program Files\Common Files
COMPOSE_CONVERT_WINDOWS_PATHS  true
COMPUTERNAME                   DESKTOP-DL2IOOE
ComSpec                        C:\Windows\system32\cmd.exe
DOCKER_CERT_PATH               C:\Users\ebubekir\.docker\machine\machines\default
DOCKER_HOST                    tcp://192.168.99.100:2376
DOCKER_MACHINE_NAME            default
DOCKER_TLS_VERIFY              1
DOCKER_TOOLBOX_INSTALL_PATH    C:\Program Files\Docker Toolbox
HOMEDRIVE                      C:
HOMEPATH                       \Users\ebubekir
JAVA_HOME                      C:\Program Files\Java\jdk1.8.0_45
JAVA_OPTIONS                   -Dfile.encoding=UTF-8 -Duser.language=en
JRE_HOME                       C:\Program Files\Java\jre1.8.0_45
LOCALAPPDATA                   C:\Users\ebubekir\AppData\Local
LOGONSERVER                    \\DESKTOP-DL2IOOE
NO_PROXY                       192.168.99.100
NUMBER_OF_PROCESSORS           4
OneDrive                       C:\Users\ebubekir\OneDrive
OS                             Windows_NT
Path                           C:\oraclexe\app\oracle\product\11.2.0\server\bin;C:\ProgramData\Oracle\Java\javapath;C:\Windows\system32;C:\...
PATHEXT                        .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC;.CPL
PROCESSOR_ARCHITECTURE         AMD64
PROCESSOR_IDENTIFIER           Intel64 Family 6 Model 58 Stepping 9, GenuineIntel
PROCESSOR_LEVEL                6
PROCESSOR_REVISION             3a09
ProgramData                    C:\ProgramData
ProgramFiles                   C:\Program Files
ProgramFiles(x86)              C:\Program Files (x86)
ProgramW6432                   C:\Program Files
PSModulePath                   C:\Users\ebubekir\Documents\WindowsPowerShell\Modules;C:\Program Files\WindowsPowerShell\Modules;C:\Windows\...
PUBLIC                         C:\Users\Public
SESSIONNAME                    Console
SystemDrive                    C:
SystemRoot                     C:\Windows
TEMP                           C:\Users\ebubekir\AppData\Local\Temp
TMP                            C:\Users\ebubekir\AppData\Local\Temp
USERDOMAIN                     DESKTOP-DL2IOOE
USERDOMAIN_ROAMINGPROFILE      DESKTOP-DL2IOOE
USERNAME                       ebubekir
USERPROFILE                    C:\Users\ebubekir
VBOX_MSI_INSTALL_PATH          C:\Program Files\Oracle\VirtualBox\
windir                         C:\Windows

--  how to look at a environment variable for Windows
> $Env:JAVA_HOME
C:\Program Files\Java\jdk1.8.0_45

--  how to add a new environment variable for Windows
> $Env:test="denemedir"
> $Env:test
denemedir
> Get-ChildItem Env:

Name                           Value
----                           -----
ALLUSERSPROFILE                C:\ProgramData
APPDATA                        C:\Users\ebubekir\AppData\Roaming
CommonProgramFiles             C:\Program Files\Common Files
CommonProgramFiles(x86)        C:\Program Files (x86)\Common Files
CommonProgramW6432             C:\Program Files\Common Files
COMPOSE_CONVERT_WINDOWS_PATHS  true
COMPUTERNAME                   DESKTOP-DL2IOOE
ComSpec                        C:\Windows\system32\cmd.exe
DOCKER_CERT_PATH               C:\Users\ebubekir\.docker\machine\machines\default
DOCKER_HOST                    tcp://192.168.99.100:2376
DOCKER_MACHINE_NAME            default
DOCKER_TLS_VERIFY              1
DOCKER_TOOLBOX_INSTALL_PATH    C:\Program Files\Docker Toolbox
HOMEDRIVE                      C:
HOMEPATH                       \Users\ebubekir
JAVA_HOME                      C:\Program Files\Java\jdk1.8.0_45
JAVA_OPTIONS                   -Dfile.encoding=UTF-8 -Duser.language=en
JRE_HOME                       C:\Program Files\Java\jre1.8.0_45
LOCALAPPDATA                   C:\Users\ebubekir\AppData\Local
LOGONSERVER                    \\DESKTOP-DL2IOOE
NO_PROXY                       192.168.99.100
NUMBER_OF_PROCESSORS           4
OneDrive                       C:\Users\ebubekir\OneDrive
OS                             Windows_NT
Path                           C:\oraclexe\app\oracle\product\11.2.0\server\bin;C:\ProgramData\Oracle\Java\javapath;C:\Windows\system32;C:\...
PATHEXT                        .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC;.CPL
PROCESSOR_ARCHITECTURE         AMD64
PROCESSOR_IDENTIFIER           Intel64 Family 6 Model 58 Stepping 9, GenuineIntel
PROCESSOR_LEVEL                6
PROCESSOR_REVISION             3a09
ProgramData                    C:\ProgramData
ProgramFiles                   C:\Program Files
ProgramFiles(x86)              C:\Program Files (x86)
ProgramW6432                   C:\Program Files
PSModulePath                   C:\Users\ebubekir\Documents\WindowsPowerShell\Modules;C:\Program Files\WindowsPowerShell\Modules;C:\Windows\...
PUBLIC                         C:\Users\Public
SESSIONNAME                    Console
SystemDrive                    C:
SystemRoot                     C:\Windows
TEMP                           C:\Users\ebubekir\AppData\Local\Temp
test                           denemedir
TMP                            C:\Users\ebubekir\AppData\Local\Temp
USERDOMAIN                     DESKTOP-DL2IOOE
USERDOMAIN_ROAMINGPROFILE      DESKTOP-DL2IOOE
USERNAME                       ebubekir
USERPROFILE                    C:\Users\ebubekir
VBOX_MSI_INSTALL_PATH          C:\Program Files\Oracle\VirtualBox\
windir                         C:\Windows

--  how to create a ubuntu container
> docker run -it ubuntu bash
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
da7391352a9b: Pull complete
14428a6d4bcd: Pull complete
2c2d948710f2: Pull complete
Digest: sha256:c95a8e48bf88e9849f3e0f723d9f49fa12c5a00cfc6e60d2bc99d87555295e4c
Status: Downloaded newer image for ubuntu:latest

--  how to list environment variables for linux
root@ebefd76eea45:/# printenv
HOSTNAME=ebefd76eea45
PWD=/
HOME=/root
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
TERM=xterm
SHLVL=1
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
_=/usr/bin/printenv

--  how to list a new environment variable for linux
root@ebefd76eea45:/# echo $TERM
xterm

--  how to add a new environment variable for Windows
root@ebefd76eea45:/# export test="denemedir"

root@ebefd76eea45:/# echo $test
denemedir

--  How to set Environment variables when docker container creates
> docker container run -it --env VAR1=deneme1 --env VAR2=deneme2 ubuntu bash
root@78bc40790750:/# printenv
HOSTNAME=78bc40790750
PWD=/
HOME=/root
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
TERM=xterm
SHLVL=1
VAR1=deneme1
VAR2=deneme2
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
_=/usr/bin/printenv


-- how to set an environment variable from our computer's variables when we create a container
> docker container run -it --env JAVA_HOME ubuntu bash
root@07d5e11cb0b7:/# printenv
HOSTNAME=07d5e11cb0b7
JAVA_HOME=C:\Program Files\Java\jdk1.8.0_45
PWD=/
HOME=/root
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
TERM=xterm
SHLVL=1
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
_=/usr/bin/printenv
root@07d5e11cb0b7:/# exit

-- how to add Environment variable list from own computer folder when create a container 
> cd C:\AdanZyeDocker\kisim4\bolum42
> docker container run -it --env-file .\env.list ubuntu bash
root@45dffb9b281c:/# printenv
var3=deneme3
HOSTNAME=45dffb9b281c
PWD=/
HOME=/root
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
TERM=xterm
SHLVL=1
VAR1=deneme1
VAR2=deneme2
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
Var4=deneme4
_=/usr/bin/printenv
root@45dffb9b281c:/# exit
exit

-- We can use an environment variable to determine which database we use. Ex:This image expect us to set an environment variable named 'veritabani'.
> docker container run --env database=test.pizzashop.com ozgurozturknet/env1
Unable to find image 'ozgurozturknet/env1:latest' locally
latest: Pulling from ozgurozturknet/env1
169185f82c45: Already exists
1e929b64ace7: Already exists
041d4f4c8c88: Pull complete
6edcf4321129: Pull complete
Digest: sha256:1e05debfdde6e4ec9e33af6b8b58820e26666c7f016ba6a1d90c58749467a726
Status: Downloaded newer image for ozgurozturknet/env1:latest
Baglanilan veritabani: null

> docker container run --env veritabani=test.pizzashop.com ozgurozturknet/env1
Baglanilan veritabani: test.pizzashop.com

> docker container run --env veritabani=prod.pizzashop.com ozgurozturknet/env1
Baglanilan veritabani: prod.pizzashop.com


-------------------------------------------------------------------------


Date of Notes : 26-12-2020

---- Images Tags and Named

> docker image pull ozgurozturknet/adanzyedocker
Using default tag: latest
latest: Pulling from ozgurozturknet/adanzyedocker
Digest: sha256:10631a62b96b8dc8c468fe482aff70871c6c81f4a49ea4c5350ce765cf9f2185
Status: Image is up to date for ozgurozturknet/adanzyedocker:latest
docker.io/ozgurozturknet/adanzyedocker:latest

> docker image pull ubuntu
Using default tag: latest
latest: Pulling from library/ubuntu
Digest: sha256:c95a8e48bf88e9849f3e0f723d9f49fa12c5a00cfc6e60d2bc99d87555295e4c
Status: Image is up to date for ubuntu:latest
docker.io/library/ubuntu:latest   (Official Images)

> docker image pull gcr.io/google-containers/busybox
Using default tag: latest
latest: Pulling from google-containers/busybox
a3ed95caeb02: Pull complete
138cfc514ce4: Pull complete
Digest: sha256:d8d3bc2c183ed2f9f10e7258f84971202325ee6011ba137112e01e30f206de67
Status: Downloaded newer image for gcr.io/google-containers/busybox:latest
gcr.io/google-containers/busybox:latest

> docker pull ozgurozturknet/adanzyedocker:v1
v1: Pulling from ozgurozturknet/adanzyedocker
9d48c3bd43c5: Already exists
d3565940ff69: Already exists
1cc6c921162a: Already exists
17877ce0de23: Already exists
4e10ed3cf6fc: Already exists
21e5a7e65c47: Pull complete
a43a0e78be9e: Pull complete
e0901adfff3d: Pull complete
80318ccc635a: Pull complete
d94141d9ce4d: Pull complete
Digest: sha256:d8121aa20720e34ed37845b7c0490110481723463e85716afa3ab169c6afe6e4
Status: Downloaded newer image for ozgurozturknet/adanzyedocker:v1
docker.io/ozgurozturknet/adanzyedocker:v1

> docker pull ozgurozturknet/adanzyedocker:v2
v2: Pulling from ozgurozturknet/adanzyedocker
9d48c3bd43c5: Already exists
d3565940ff69: Already exists
1cc6c921162a: Already exists
17877ce0de23: Already exists
4e10ed3cf6fc: Already exists
21e5a7e65c47: Already exists
a43a0e78be9e: Already exists
e0901adfff3d: Already exists
80318ccc635a: Already exists
13de18232897: Pull complete
Digest: sha256:74b49d0ad4a8bba936659051cdd3c93f5a0381286bcb60b273045e1326968ae9
Status: Downloaded newer image for ozgurozturknet/adanzyedocker:v2
docker.io/ozgurozturknet/adanzyedocker:v2

> docker image pull ubuntu:20.04
20.04: Pulling from library/ubuntu
Digest: sha256:c95a8e48bf88e9849f3e0f723d9f49fa12c5a00cfc6e60d2bc99d87555295e4c
Status: Downloaded newer image for ubuntu:20.04
docker.io/library/ubuntu:20.04

> docker image ls
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
httpd                              alpine              5d779ff71c18        8 days ago          55.5MB
alpine                             latest              389fef711851        9 days ago          5.58MB
nginx                              latest              ae2feff98a0c        10 days ago         133MB
centos                             latest              300e315adb2f        2 weeks ago         209MB
ubuntu                             20.04               f643c72bc252        4 weeks ago         72.9MB
ubuntu                             latest              f643c72bc252        4 weeks ago         72.9MB
ozgurozturknet/hello-app           latest              7feb3d617d2d        8 months ago        5.6MB
ozgurozturknet/webdb               latest              3e6048caa2a4        11 months ago       437MB
ozgurozturknet/webkayit            latest              3b8929349c0b        11 months ago       483MB
ozgurozturknet/env1                latest              8c4c4f717b65        11 months ago       126MB
ozgurozturknet/adanzyedocker       latest              2b4647565690        14 months ago       284MB
ozgurozturknet/adanzyedocker       v2                  b97509fa9f19        14 months ago       283MB
ozgurozturknet/adanzyedocker       v1                  a5a841543d41        14 months ago       283MB
ozgurozturknet/app1                latest              353d147de1ee        15 months ago       126MB
gcr.io/google-containers/busybox   latest              e7d168d7db45        5 years ago         2.43MB 


> docker pull mysql
Using default tag: latest
latest: Pulling from library/mysql
6ec7b7d162b2: Already exists
fedd960d3481: Pull complete
7ab947313861: Pull complete
64f92f19e638: Pull complete
3e80b17bff96: Pull complete
014e976799f9: Pull complete
59ae84fee1b3: Pull complete
ffe10de703ea: Pull complete
657af6d90c83: Pull complete
98bfb480322c: Pull complete
6aa3859c4789: Pull complete
1ed875d851ef: Pull complete
Digest: sha256:78800e6d3f1b230e35275145e657b82c3fb02a27b2d8e76aac2f5e90c1c30873
Status: Downloaded newer image for mysql:latest
docker.io/library/mysql:latest

> docker pull mysql:8
8: Pulling from library/mysql
Digest: sha256:78800e6d3f1b230e35275145e657b82c3fb02a27b2d8e76aac2f5e90c1c30873
Status: Downloaded newer image for mysql:8
docker.io/library/mysql:8

> docker pull mysql:5
5: Pulling from library/mysql
6ec7b7d162b2: Already exists
fedd960d3481: Already exists
7ab947313861: Already exists
64f92f19e638: Already exists
3e80b17bff96: Already exists
014e976799f9: Already exists
59ae84fee1b3: Already exists
7d1da2a18e2e: Pull complete
301a28b700b9: Pull complete
529dc8dbeaf3: Pull complete
bc9d021dc13f: Pull complete
Digest: sha256:c3a567d3e3ad8b05dfce401ed08f0f6bf3f3b64cc17694979d5f2e5d78e10173
Status: Downloaded newer image for mysql:5
docker.io/library/mysql:5

> docker pull mysql:5.7
5.7: Pulling from library/mysql
Digest: sha256:c3a567d3e3ad8b05dfce401ed08f0f6bf3f3b64cc17694979d5f2e5d78e10173
Status: Downloaded newer image for mysql:5.7
docker.io/library/mysql:5.7

> docker image ls
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
mysql                              5                   f07dfa83b528        4 days ago          448MB
mysql                              5.7                 f07dfa83b528        4 days ago          448MB
mysql                              8                   a347a5928046        4 days ago          545MB
mysql                              latest              a347a5928046        4 days ago          545MB
httpd                              alpine              5d779ff71c18        8 days ago          55.5MB
alpine                             latest              389fef711851        9 days ago          5.58MB
nginx                              latest              ae2feff98a0c        10 days ago         133MB
centos                             latest              300e315adb2f        2 weeks ago         209MB
ubuntu                             20.04               f643c72bc252        4 weeks ago         72.9MB
ubuntu                             latest              f643c72bc252        4 weeks ago         72.9MB
ozgurozturknet/hello-app           latest              7feb3d617d2d        8 months ago        5.6MB
ozgurozturknet/webdb               latest              3e6048caa2a4        11 months ago       437MB
ozgurozturknet/webkayit            latest              3b8929349c0b        11 months ago       483MB
ozgurozturknet/env1                latest              8c4c4f717b65        11 months ago       126MB
ozgurozturknet/adanzyedocker       latest              2b4647565690        14 months ago       284MB
ozgurozturknet/adanzyedocker       v2                  b97509fa9f19        14 months ago       283MB
ozgurozturknet/adanzyedocker       v1                  a5a841543d41        14 months ago       283MB
ozgurozturknet/app1                latest              353d147de1ee        15 months ago       126MB
gcr.io/google-containers/busybox   latest              e7d168d7db45        5 years ago         2.43MB


---- How to create a docker image

//We wrote Docker file in this folder
> code .
> ls


    Directory: C:\AdanZyeDocker\kisim5\bolum48


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----       26.12.2020     14:55                myapp
-a----       26.12.2020     14:55            134 Dockerfile


PS C:\AdanZyeDocker\kisim5\bolum48> docker image build -t gunerhanale/hello .
Sending build context to Docker daemon  4.608kB
Step 1/6 : FROM ubuntu:18.04
18.04: Pulling from library/ubuntu
f22ccc0b8772: Pull complete
3cf8fb62ba5f: Pull complete
e80c964ece6a: Pull complete
Digest: sha256:fd25e706f3dea2a5ff705dbc3353cf37f08307798f3e360a13e9385840f73fb3
Status: Downloaded newer image for ubuntu:18.04
 ---> 2c047404e52d
Step 2/6 : RUN apt-get update -y
 ---> Running in f277ff79e047
Get:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
Get:2 http://archive.ubuntu.com/ubuntu bionic InRelease [242 kB]
Get:3 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [1372 kB]
Get:4 http://archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:5 http://archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Get:6 http://archive.ubuntu.com/ubuntu bionic/multiverse amd64 Packages [186 kB]
Get:7 http://archive.ubuntu.com/ubuntu bionic/restricted amd64 Packages [13.5 kB]
Get:8 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages [1344 kB]
Get:9 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [1816 kB]
Get:10 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages [11.3 MB]
Get:11 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 Packages [15.3 kB]
Get:12 http://security.ubuntu.com/ubuntu bionic-security/restricted amd64 Packages [237 kB]
Get:13 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [2244 kB]
Get:14 http://archive.ubuntu.com/ubuntu bionic-updates/restricted amd64 Packages [266 kB]
Get:15 http://archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 Packages [53.8 kB]
Get:16 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [2136 kB]
Get:17 http://archive.ubuntu.com/ubuntu bionic-backports/universe amd64 Packages [11.4 kB]
Get:18 http://archive.ubuntu.com/ubuntu bionic-backports/main amd64 Packages [11.3 kB]
Fetched 21.5 MB in 20s (1052 kB/s)
Reading package lists...
Removing intermediate container f277ff79e047
 ---> 17bb265f635d
Step 3/6 : RUN apt-get install default-jre -y
 ---> Running in 30cb4bc6abdb
Reading package lists...
Building dependency tree...
Reading state information...
...
...
...
Setting up default-jre (2:1.11-68ubuntu1~18.04.1) ...
Processing triggers for libc-bin (2.27-3ubuntu1.3) ...
Processing triggers for ca-certificates (20201027ubuntu0.18.04.1) ...
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...

done.
done.
Removing intermediate container 30cb4bc6abdb
 ---> c2360b9f7ad0
Step 4/6 : WORKDIR /merhaba
 ---> Running in 7aca6ceb0c4b
Removing intermediate container 7aca6ceb0c4b
 ---> baa3afeb4244
Step 5/6 : COPY /myapp .
 ---> e385e04ab5ec
Step 6/6 : CMD ["java", "merhaba"]
 ---> Running in b4693fcadeca
Removing intermediate container b4693fcadeca
 ---> e9dc642dd346
Successfully built e9dc642dd346
Successfully tagged gunerhanale/hello:latest
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.

> docker image ls
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
gunerhanale/hello                latest              e9dc642dd346        42 seconds ago      477MB
mysql                              5                   f07dfa83b528        4 days ago          448MB
mysql                              5.7                 f07dfa83b528        4 days ago          448MB
mysql                              8                   a347a5928046        4 days ago          545MB
mysql                              latest              a347a5928046        4 days ago          545MB
httpd                              alpine              5d779ff71c18        9 days ago          55.5MB
alpine                             latest              389fef711851        9 days ago          5.58MB
nginx                              latest              ae2feff98a0c        10 days ago         133MB
centos                             latest              300e315adb2f        2 weeks ago         209MB
ubuntu                             20.04               f643c72bc252        4 weeks ago         72.9MB
ubuntu                             latest              f643c72bc252        4 weeks ago         72.9MB
ubuntu                             18.04               2c047404e52d        4 weeks ago         63.3MB
ozgurozturknet/hello-app           latest              7feb3d617d2d        8 months ago        5.6MB
ozgurozturknet/webdb               latest              3e6048caa2a4        11 months ago       437MB
ozgurozturknet/webkayit            latest              3b8929349c0b        11 months ago       483MB
ozgurozturknet/env1                latest              8c4c4f717b65        11 months ago       126MB
ozgurozturknet/adanzyedocker       latest              2b4647565690        14 months ago       284MB
ozgurozturknet/adanzyedocker       v2                  b97509fa9f19        14 months ago       283MB
ozgurozturknet/adanzyedocker       v1                  a5a841543d41        14 months ago       283MB
ozgurozturknet/app1                latest              353d147de1ee        15 months ago       126MB
gcr.io/google-containers/busybox   latest              e7d168d7db45        5 years ago         2.43MB

> docker container run gunerhanale/hello
Merhaba arkadaslar. Ben merhaba isimli Java konsol uygulamas?y?m

> docker image history gunerhanale/hello
IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
e9dc642dd346        2 minutes ago       /bin/sh -c #(nop)  CMD ["java" "merhaba"]       0B
e385e04ab5ec        2 minutes ago       /bin/sh -c #(nop) COPY dir:89fe398503f2ed78f   653B
baa3afeb4244        2 minutes ago       /bin/sh -c #(nop) WORKDIR /merhaba              0B
c2360b9f7ad0        2 minutes ago       /bin/sh -c apt-get install default-jre -y       380MB
17bb265f635d        4 minutes ago       /bin/sh -c apt-get update -y                    34.6MB
2c047404e52d        4 weeks ago         /bin/sh -c #(nop)  CMD ["/bin/bash"]            0B
<missing>           4 weeks ago         /bin/sh -c mkdir -p /run/systemd && echo 'do   7B
<missing>           4 weeks ago         /bin/sh -c [ -z "$(apt-get indextargets)" ]     0B
<missing>           4 weeks ago         /bin/sh -c set -xe   && echo '#!/bin/sh' > /   745B
<missing>           4 weeks ago         /bin/sh -c #(nop) ADD file:6ef542de9959c3061   63.3MB

> docker image history gunerhanale/hello
IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
e9dc642dd346        16 minutes ago      /bin/sh -c #(nop)  CMD ["java" "merhaba"]       0B
e385e04ab5ec        16 minutes ago      /bin/sh -c #(nop) COPY dir:89fe398503f2ed78f   653B
baa3afeb4244        16 minutes ago      /bin/sh -c #(nop) WORKDIR /merhaba              0B
c2360b9f7ad0        16 minutes ago      /bin/sh -c apt-get install default-jre -y       380MB
17bb265f635d        18 minutes ago      /bin/sh -c apt-get update -y                    34.6MB
2c047404e52d        4 weeks ago         /bin/sh -c #(nop)  CMD ["/bin/bash"]            0B
<missing>           4 weeks ago         /bin/sh -c mkdir -p /run/systemd && echo 'do   7B
<missing>           4 weeks ago         /bin/sh -c [ -z "$(apt-get indextargets)" ]     0B
<missing>           4 weeks ago         /bin/sh -c set -xe   && echo '#!/bin/sh' > /   745B
<missing>           4 weeks ago         /bin/sh -c #(nop) ADD file:6ef542de9959c3061   63.3MB

> docker image history ubuntu:18.04
IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
2c047404e52d        4 weeks ago         /bin/sh -c #(nop)  CMD ["/bin/bash"]            0B
<missing>           4 weeks ago         /bin/sh -c mkdir -p /run/systemd && echo 'do   7B
<missing>           4 weeks ago         /bin/sh -c [ -z "$(apt-get indextargets)" ]     0B
<missing>           4 weeks ago         /bin/sh -c set -xe   && echo '#!/bin/sh' > /   745B
<missing>           4 weeks ago         /bin/sh -c #(nop) ADD file:6ef542de9959c3061   63.3MB

> docker image push gunerhanale/hello
The push refers to repository [docker.io/gunerhanale/hello]
16cb125f1ebc: Pushed
236f6217591d: Pushed
b6bb456b95fe: Pushed
abd43f8b7b6e: Pushed
fe6d8881187d: Pushed
23135df75b44: Pushed
b43408d5f11b: Pushed
latest: digest: sha256:e64804023a52f4447430d950ccb71812496ff78b8af35276be498c842644a40b size: 1782

> docker container run gunerhanale/hello
Merhaba arkadaslar. Ben merhaba isimli Java konsol uygulamas?y?m

> docker image ls
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
ebubekirnet/merhaba                latest              e9dc642dd346        27 minutes ago      477MB
gunerhanale/hello                  latest              e9dc642dd346        27 minutes ago      477MB
mysql                              5                   f07dfa83b528        4 days ago          448MB
mysql                              5.7                 f07dfa83b528        4 days ago          448MB
mysql                              8                   a347a5928046        4 days ago          545MB
mysql                              latest              a347a5928046        4 days ago          545MB
httpd                              alpine              5d779ff71c18        9 days ago          55.5MB
alpine                             latest              389fef711851        9 days ago          5.58MB
nginx                              latest              ae2feff98a0c        10 days ago         133MB
centos                             latest              300e315adb2f        2 weeks ago         209MB
ubuntu                             20.04               f643c72bc252        4 weeks ago         72.9MB
ubuntu                             latest              f643c72bc252        4 weeks ago         72.9MB
ubuntu                             18.04               2c047404e52d        4 weeks ago         63.3MB
ozgurozturknet/hello-app           latest              7feb3d617d2d        8 months ago        5.6MB
ozgurozturknet/webdb               latest              3e6048caa2a4        11 months ago       437MB
ozgurozturknet/webkayit            latest              3b8929349c0b        11 months ago       483MB
ozgurozturknet/env1                latest              8c4c4f717b65        11 months ago       126MB
ozgurozturknet/adanzyedocker       latest              2b4647565690        14 months ago       284MB
ozgurozturknet/adanzyedocker       v2                  b97509fa9f19        14 months ago       283MB
ozgurozturknet/adanzyedocker       v1                  a5a841543d41        14 months ago       283MB
ozgurozturknet/app1                latest              353d147de1ee        15 months ago       126MB
gcr.io/google-containers/busybox   latest              e7d168d7db45        5 years ago         2.43MB

> docker image rm e9dc
Error response from daemon: conflict: unable to delete e9dc642dd346 (must be forced) - image is referenced in multiple repositories

> docker image rm gunerhanale/hello
Untagged: gunerhanale/hello:latest
Untagged: gunerhanale/hello@sha256:e64804023a52f4447430d950ccb71812496ff78b8af35276be498c842644a40b

> docker image rm gunerhanale/hello:latest
Error: No such image: gunerhanale/hello:latest

> docker image ls
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
ebubekirnet/merhaba                latest              e9dc642dd346        28 minutes ago      477MB
mysql                              5                   f07dfa83b528        4 days ago          448MB
mysql                              5.7                 f07dfa83b528        4 days ago          448MB
mysql                              8                   a347a5928046        4 days ago          545MB
mysql                              latest              a347a5928046        4 days ago          545MB
httpd                              alpine              5d779ff71c18        9 days ago          55.5MB
alpine                             latest              389fef711851        9 days ago          5.58MB
nginx                              latest              ae2feff98a0c        10 days ago         133MB
centos                             latest              300e315adb2f        2 weeks ago         209MB
ubuntu                             20.04               f643c72bc252        4 weeks ago         72.9MB
ubuntu                             latest              f643c72bc252        4 weeks ago         72.9MB
ubuntu                             18.04               2c047404e52d        4 weeks ago         63.3MB
ozgurozturknet/hello-app           latest              7feb3d617d2d        8 months ago        5.6MB
ozgurozturknet/webdb               latest              3e6048caa2a4        11 months ago       437MB
ozgurozturknet/webkayit            latest              3b8929349c0b        11 months ago       483MB
ozgurozturknet/env1                latest              8c4c4f717b65        11 months ago       126MB
ozgurozturknet/adanzyedocker       latest              2b4647565690        14 months ago       284MB
ozgurozturknet/adanzyedocker       v2                  b97509fa9f19        14 months ago       283MB
ozgurozturknet/adanzyedocker       v1                  a5a841543d41        14 months ago       283MB
ozgurozturknet/app1                latest              353d147de1ee        15 months ago       126MB
gcr.io/google-containers/busybox   latest              e7d168d7db45        5 years ago         2.43MB

> docker image rm ebubekirnet/merhaba
Error response from daemon: conflict: unable to remove repository reference "ebubekirnet/merhaba" (must force) - container d5410c06ad68 is using its referenced image e9dc642dd346

> docker image rm e9dc
Error response from daemon: conflict: unable to delete e9dc642dd346 (must be forced) - image is being used by stopped container d5410c06ad68

> docker image rm -f  e9dc
Untagged: ebubekirnet/merhaba:latest
Deleted: sha256:e9dc642dd346e08ec0aa9daa738485a9f16ee91d12c811cbb998cf5a7206788a
Deleted: sha256:e385e04ab5ec2a004121ccb226f83425678dbeb14511d6e1583c79e5ed870d6b
Deleted: sha256:baa3afeb42448826001cab4da1fbb240d7b916147cfaaed023289828c8d7c7e9
Deleted: sha256:c2360b9f7ad0a06345c83a6989255bcf58fb69b3f2c9977e76a0e46484a2f281
Deleted: sha256:17bb265f635d1d52c4f5dc76da5ed0704dac9d334b2c3c07bd22a21c37a25a00

> docker image ls
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
mysql                              5                   f07dfa83b528        4 days ago          448MB
mysql                              5.7                 f07dfa83b528        4 days ago          448MB
mysql                              8                   a347a5928046        4 days ago          545MB
mysql                              latest              a347a5928046        4 days ago          545MB
httpd                              alpine              5d779ff71c18        9 days ago          55.5MB
alpine                             latest              389fef711851        9 days ago          5.58MB
nginx                              latest              ae2feff98a0c        10 days ago         133MB
centos                             latest              300e315adb2f        2 weeks ago         209MB
ubuntu                             20.04               f643c72bc252        4 weeks ago         72.9MB
ubuntu                             latest              f643c72bc252        4 weeks ago         72.9MB
ubuntu                             18.04               2c047404e52d        4 weeks ago         63.3MB
ozgurozturknet/hello-app           latest              7feb3d617d2d        8 months ago        5.6MB
ozgurozturknet/webdb               latest              3e6048caa2a4        11 months ago       437MB
ozgurozturknet/webkayit            latest              3b8929349c0b        11 months ago       483MB
ozgurozturknet/env1                latest              8c4c4f717b65        11 months ago       126MB
ozgurozturknet/adanzyedocker       latest              2b4647565690        14 months ago       284MB
ozgurozturknet/adanzyedocker       v2                  b97509fa9f19        14 months ago       283MB
ozgurozturknet/adanzyedocker       v1                  a5a841543d41        14 months ago       283MB
ozgurozturknet/app1                latest              353d147de1ee        15 months ago       126MB
gcr.io/google-containers/busybox   latest              e7d168d7db45        5 years ago         2.43MB

> docker container run gunerhanale/hello
Unable to find image 'gunerhanale/hello:latest' locally
latest: Pulling from gunerhanale/hello
f22ccc0b8772: Already exists
3cf8fb62ba5f: Already exists
e80c964ece6a: Already exists
8a72761f5381: Already exists
7f008cb103da: Already exists
28dfc487c900: Already exists
8ea572452c53: Already exists
Digest: sha256:e64804023a52f4447430d950ccb71812496ff78b8af35276be498c842644a40b
Status: Downloaded newer image for gunerhanale/hello:latest
Merhaba arkadaslar. Ben merhaba isimli Java konsol uygulamas?y?m

> docker image ls
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
gunerhanale/hello                  latest              e9dc642dd346        29 minutes ago      477MB
mysql                              5                   f07dfa83b528        4 days ago          448MB
mysql                              5.7                 f07dfa83b528        4 days ago          448MB
mysql                              8                   a347a5928046        4 days ago          545MB
mysql                              latest              a347a5928046        4 days ago          545MB
httpd                              alpine              5d779ff71c18        9 days ago          55.5MB
alpine                             latest              389fef711851        9 days ago          5.58MB
nginx                              latest              ae2feff98a0c        10 days ago         133MB
centos                             latest              300e315adb2f        2 weeks ago         209MB
ubuntu                             20.04               f643c72bc252        4 weeks ago         72.9MB
ubuntu                             latest              f643c72bc252        4 weeks ago         72.9MB
ubuntu                             18.04               2c047404e52d        4 weeks ago         63.3MB
ozgurozturknet/hello-app           latest              7feb3d617d2d        8 months ago        5.6MB
ozgurozturknet/webdb               latest              3e6048caa2a4        11 months ago       437MB
ozgurozturknet/webkayit            latest              3b8929349c0b        11 months ago       483MB
ozgurozturknet/env1                latest              8c4c4f717b65        11 months ago       126MB
ozgurozturknet/adanzyedocker       latest              2b4647565690        14 months ago       284MB
ozgurozturknet/adanzyedocker       v2                  b97509fa9f19        14 months ago       283MB
ozgurozturknet/adanzyedocker       v1                  a5a841543d41        14 months ago       283MB
ozgurozturknet/app1                latest              353d147de1ee        15 months ago       126MB
gcr.io/google-containers/busybox   latest              e7d168d7db45        5 years ago         2.43MB


PS C:\AdanZyeDocker\kisim5\bolum50> code .
PS C:\AdanZyeDocker\kisim5\bolum50> cd .\py\
PS C:\AdanZyeDocker\kisim5\bolum50\py> ls


    Directory: C:\AdanZyeDocker\kisim5\bolum50\py


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       21.12.2020     16:48            118 Dockerfile
-a----       21.12.2020     16:48            134 Dockerfile.ozgurozturknet_merhaba
-a----       21.12.2020     16:48            238 index.py
-a----       21.12.2020     16:48              5 requirements.txt


PS C:\AdanZyeDocker\kisim5\bolum50\py> docker image build -t gunerhanale/py .
Sending build context to Docker daemon   5.12kB
Step 1/6 : FROM python:alpine
alpine: Pulling from library/python
801bfaa63ef2: Already exists
8723b2b92bec: Pull complete
4e07029ccd64: Pull complete
594990504179: Pull complete
140d7fec7322: Pull complete
Digest: sha256:7492c1f615e3651629bd6c61777e9660caa3819cf3561a47d1d526dfeee02cf6
Status: Downloaded newer image for python:alpine
 ---> d4d4f50f871a
Step 2/6 : COPY . /app
 ---> 59508dc1ff3c
Step 3/6 : WORKDIR /app
 ---> Running in c1386a5d6ca8
Removing intermediate container c1386a5d6ca8
 ---> 737fc25e2210
Step 4/6 : RUN pip install -r requirements.txt
 ---> Running in 16d9e700aef9
Collecting flask
  Downloading Flask-1.1.2-py2.py3-none-any.whl (94 kB)
Collecting click>=5.1
  Downloading click-7.1.2-py2.py3-none-any.whl (82 kB)
Collecting itsdangerous>=0.24
  Downloading itsdangerous-1.1.0-py2.py3-none-any.whl (16 kB)
Collecting Jinja2>=2.10.1
  Downloading Jinja2-2.11.2-py2.py3-none-any.whl (125 kB)
Collecting MarkupSafe>=0.23
  Downloading MarkupSafe-1.1.1.tar.gz (19 kB)
Collecting Werkzeug>=0.15
  Downloading Werkzeug-1.0.1-py2.py3-none-any.whl (298 kB)
Building wheels for collected packages: MarkupSafe
  Building wheel for MarkupSafe (setup.py): started
  Building wheel for MarkupSafe (setup.py): finished with status 'done'
  Created wheel for MarkupSafe: filename=MarkupSafe-1.1.1-py3-none-any.whl size=12629 sha256=cfd16ad4d533223bc666dacda2885910252e02c08f00f6d018c5c100d65f3376
  Stored in directory: /root/.cache/pip/wheels/e0/19/6f/6ba857621f50dc08e084312746ed3ebc14211ba30037d5e44e
Successfully built MarkupSafe
Installing collected packages: MarkupSafe, Werkzeug, Jinja2, itsdangerous, click, flask
Successfully installed Jinja2-2.11.2 MarkupSafe-1.1.1 Werkzeug-1.0.1 click-7.1.2 flask-1.1.2 itsdangerous-1.1.0
Removing intermediate container 16d9e700aef9
 ---> 7d0668fc0d7b
Step 5/6 : EXPOSE 5000
 ---> Running in 8bb427b8232a
Removing intermediate container 8bb427b8232a
 ---> 0cbeb6c3eb51
Step 6/6 : CMD python ./index.py
 ---> Running in 53653e2887aa
Removing intermediate container 53653e2887aa
 ---> eb55156a81c2
Successfully built eb55156a81c2
Successfully tagged gunerhanale/py:latest
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.

PS C:\AdanZyeDocker\kisim5\bolum50\py> docker image ls
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
gunerhanale/py                     latest              eb55156a81c2        57 minutes ago      55.2MB
gunerhanale/hello                  latest              e9dc642dd346        2 hours ago         477MB
mysql                              5                   f07dfa83b528        4 days ago          448MB
mysql                              5.7                 f07dfa83b528        4 days ago          448MB
mysql                              8                   a347a5928046        4 days ago          545MB
mysql                              latest              a347a5928046        4 days ago          545MB
httpd                              alpine              5d779ff71c18        9 days ago          55.5MB
python                             alpine              d4d4f50f871a        9 days ago          44.2MB
alpine                             latest              389fef711851        9 days ago          5.58MB
nginx                              latest              ae2feff98a0c        10 days ago         133MB
centos                             latest              300e315adb2f        2 weeks ago         209MB
ubuntu                             20.04               f643c72bc252        4 weeks ago         72.9MB
ubuntu                             latest              f643c72bc252        4 weeks ago         72.9MB
ubuntu                             18.04               2c047404e52d        4 weeks ago         63.3MB
ozgurozturknet/hello-app           latest              7feb3d617d2d        8 months ago        5.6MB
ozgurozturknet/webdb               latest              3e6048caa2a4        11 months ago       437MB
ozgurozturknet/webkayit            latest              3b8929349c0b        11 months ago       483MB
ozgurozturknet/env1                latest              8c4c4f717b65        11 months ago       126MB
ozgurozturknet/adanzyedocker       latest              2b4647565690        14 months ago       284MB
ozgurozturknet/adanzyedocker       v2                  b97509fa9f19        14 months ago       283MB
ozgurozturknet/adanzyedocker       v1                  a5a841543d41        14 months ago       283MB
ozgurozturknet/app1                latest              353d147de1ee        15 months ago       126MB
gcr.io/google-containers/busybox   latest              e7d168d7db45        5 years ago         2.43MB

PS C:\AdanZyeDocker\kisim5\bolum50\py> docker container run --rm -p 80:5000 gunerhanale/py
 * Serving Flask app "index" (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: on
 * Running on http://0.0.0.0:5000/ (Press CTRL+C to quit)
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 227-939-784
192.168.99.1 - - [26/Dec/2020 14:50:39] "GET / HTTP/1.1" 200 -
192.168.99.1 - - [26/Dec/2020 14:50:39] "GET / HTTP/1.1" 200 -
192.168.99.1 - - [26/Dec/2020 14:50:40] "GET / HTTP/1.1" 200 -
PS C:\AdanZyeDocker\kisim5\bolum50\py> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                  NAMES
9f87a78dfebe        gunerhanale/py      "/bin/sh -c 'python "   57 minutes ago      Up 55 seconds       0.0.0.0:80->5000/tcp   dazzling_lewin

PS C:\AdanZyeDocker\kisim5\bolum50\py> docker stop 9f8
9f8

PS C:\AdanZyeDocker\kisim5\bolum50\py> cd ..
PS C:\AdanZyeDocker\kisim5\bolum50> cd .\nodejs\
PS C:\AdanZyeDocker\kisim5\bolum50\nodejs> ls


    Directory: C:\AdanZyeDocker\kisim5\bolum50\nodejs


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       21.12.2020     16:48            406 Dockerfile
-a----       21.12.2020     16:48            276 package.json
-a----       21.12.2020     16:48            291 server.js


PS C:\AdanZyeDocker\kisim5\bolum50\nodejs> docker image build -t gunerhanale/node .
Sending build context to Docker daemon  4.096kB
Step 1/7 : FROM node:10
10: Pulling from library/node
22f9b9782fc3: Pull complete
072739d44e4f: Pull complete
5111f27e9600: Pull complete
dc22afea6082: Pull complete
0ad0b403cda0: Pull complete
bca65cadbc25: Pull complete
4c7d04f68114: Pull complete
e12fb7d7d7a0: Pull complete
7f9efcb97b17: Pull complete
Digest: sha256:57e6dc91af813f8d1c7e05d60871eca8cba67b1e120c1ae7192315114cf68de2
Status: Downloaded newer image for node:10
 ---> 4ee0f07a0e63
Step 2/7 : WORKDIR /usr/src/app
 ---> Running in cf9f59d30883
Removing intermediate container cf9f59d30883
 ---> 3552b7a57eef
Step 3/7 : COPY package*.json ./
 ---> 894035ac09c5
Step 4/7 : RUN npm install
 ---> Running in 356a9f16c3b5
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN docker_web_app@1.0.0 No repository field.
npm WARN docker_web_app@1.0.0 No license field.

added 50 packages from 37 contributors and audited 50 packages in 4.01s
found 0 vulnerabilities

Removing intermediate container 356a9f16c3b5
 ---> 9a0a2c9022b9
Step 5/7 : COPY server.js .
 ---> 089f50ff0a5d
Step 6/7 : EXPOSE 8080
 ---> Running in 817d58e469d9
Removing intermediate container 817d58e469d9
 ---> 4e3faf8de439
Step 7/7 : CMD [ "node", "server.js" ]
 ---> Running in b3c940adf48a
Removing intermediate container b3c940adf48a
 ---> f9f1a9fb06b7
Successfully built f9f1a9fb06b7
Successfully tagged gunerhanale/node:latest
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.

PS C:\AdanZyeDocker\kisim5\bolum50\nodejs> docker image build -t gunerhanale/node .
Sending build context to Docker daemon  4.096kB
Step 1/7 : FROM node:10
 ---> 4ee0f07a0e63
Step 2/7 : WORKDIR /usr/src/app
 ---> Using cache
 ---> 3552b7a57eef
Step 3/7 : COPY package*.json ./
 ---> Using cache
 ---> 894035ac09c5
Step 4/7 : RUN npm install
 ---> Using cache
 ---> 9a0a2c9022b9
Step 5/7 : COPY server.js .
 ---> Using cache
 ---> 089f50ff0a5d
Step 6/7 : EXPOSE 8080
 ---> Using cache
 ---> 4e3faf8de439
Step 7/7 : CMD [ "node", "server.js" ]
 ---> Using cache
 ---> f9f1a9fb06b7
Successfully built f9f1a9fb06b7
Successfully tagged gunerhanale/node:latest
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.

PS C:\AdanZyeDocker\kisim5\bolum50\nodejs> docker image ls
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
gunerhanale/node                   latest              f9f1a9fb06b7        20 seconds ago      914MB
gunerhanale/py                     latest              eb55156a81c2        About an hour ago   55.2MB
gunerhanale/hello                  latest              e9dc642dd346        2 hours ago         477MB
mysql                              5                   f07dfa83b528        4 days ago          448MB
mysql                              5.7                 f07dfa83b528        4 days ago          448MB
mysql                              8                   a347a5928046        4 days ago          545MB
mysql                              latest              a347a5928046        4 days ago          545MB
node                               10                  4ee0f07a0e63        8 days ago          911MB
httpd                              alpine              5d779ff71c18        9 days ago          55.5MB
python                             alpine              d4d4f50f871a        9 days ago          44.2MB
alpine                             latest              389fef711851        9 days ago          5.58MB
nginx                              latest              ae2feff98a0c        10 days ago         133MB
centos                             latest              300e315adb2f        2 weeks ago         209MB
ubuntu                             20.04               f643c72bc252        4 weeks ago         72.9MB
ubuntu                             latest              f643c72bc252        4 weeks ago         72.9MB
ubuntu                             18.04               2c047404e52d        4 weeks ago         63.3MB
ozgurozturknet/hello-app           latest              7feb3d617d2d        8 months ago        5.6MB
ozgurozturknet/webdb               latest              3e6048caa2a4        11 months ago       437MB
ozgurozturknet/webkayit            latest              3b8929349c0b        11 months ago       483MB
ozgurozturknet/env1                latest              8c4c4f717b65        11 months ago       126MB
ozgurozturknet/adanzyedocker       latest              2b4647565690        14 months ago       284MB
ozgurozturknet/adanzyedocker       v2                  b97509fa9f19        14 months ago       283MB
ozgurozturknet/adanzyedocker       v1                  a5a841543d41        14 months ago       283MB
ozgurozturknet/app1                latest              353d147de1ee        15 months ago       126MB
gcr.io/google-containers/busybox   latest              e7d168d7db45        5 years ago         2.43MB

PS C:\AdanZyeDocker\kisim5\bolum50\nodejs> docker image build -t gunerhanale/node .
Sending build context to Docker daemon  4.096kB
Step 1/7 : FROM node:10
 ---> 4ee0f07a0e63
Step 2/7 : WORKDIR /usr/src/app
 ---> Using cache
 ---> 3552b7a57eef
Step 3/7 : COPY package*.json ./
 ---> Using cache
 ---> 894035ac09c5
Step 4/7 : RUN npm install
 ---> Using cache
 ---> 9a0a2c9022b9
Step 5/7 : COPY server.js .
 ---> 6f34e36b9804
Step 6/7 : EXPOSE 8080
 ---> Running in 81ce603a91dd
Removing intermediate container 81ce603a91dd
 ---> e6b684ea69f3
Step 7/7 : CMD [ "node", "server.js" ]
 ---> Running in c44551aa6333
Removing intermediate container c44551aa6333
 ---> 369b881d949d
Successfully built 369b881d949d
Successfully tagged gunerhanale/node:latest
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.
PS C:\AdanZyeDocker\kisim5\bolum50\nodejs>

PS C:\AdanZyeDocker\kisim5\bolum50\nodejs2> docker image build -t node2 .
Sending build context to Docker daemon  4.096kB
Step 1/7 : FROM node:10
 ---> 4ee0f07a0e63
Step 2/7 : WORKDIR /usr/src/app
 ---> Using cache
 ---> 3552b7a57eef
Step 3/7 : COPY package.json .
 ---> f28ceb6ab91b
Step 4/7 : COPY server.js .
 ---> 92c64f053e0c
Step 5/7 : RUN npm install
 ---> Running in bfdc098826a0
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN docker_web_app@1.0.0 No repository field.
npm WARN docker_web_app@1.0.0 No license field.

added 50 packages from 37 contributors and audited 50 packages in 5.313s
found 0 vulnerabilities

Removing intermediate container bfdc098826a0
 ---> 6ad7b17829c8
Step 6/7 : EXPOSE 8080
 ---> Running in d15594b8a52d
Removing intermediate container d15594b8a52d
 ---> f1c0fa75944b
Step 7/7 : CMD [ "node", "server.js" ]
 ---> Running in 31b1b540fea9
Removing intermediate container 31b1b540fea9
 ---> 015d8a720466
Successfully built 015d8a720466
Successfully tagged node2:latest
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.

PS C:\AdanZyeDocker\kisim5\bolum50\nodejs2> docker container run -d -p 80:8080 node2
24100443bccad022351ed1397937472358bf6688c2b50a88c42aa2bc617ace64

PS C:\AdanZyeDocker\kisim5\bolum50\nodejs2> docker image build -t node2 .
Sending build context to Docker daemon  4.096kB
Step 1/7 : FROM node:10
 ---> 4ee0f07a0e63
Step 2/7 : WORKDIR /usr/src/app
 ---> Using cache
 ---> 3552b7a57eef
Step 3/7 : COPY package.json .
 ---> Using cache
 ---> f28ceb6ab91b
Step 4/7 : COPY server.js .
 ---> 475b892b7007
Step 5/7 : RUN npm install
 ---> Running in 82e83080ca9e
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN docker_web_app@1.0.0 No repository field.
npm WARN docker_web_app@1.0.0 No license field.

added 50 packages from 37 contributors and audited 50 packages in 4.353s
found 0 vulnerabilities

Removing intermediate container 82e83080ca9e
 ---> c9428a31a855
Step 6/7 : EXPOSE 8080
 ---> Running in 0182c52e23f1
Removing intermediate container 0182c52e23f1
 ---> 4b3a99580038
Step 7/7 : CMD [ "node", "server.js" ]
 ---> Running in c5bfe71b8ec5
Removing intermediate container c5bfe71b8ec5
 ---> 324d3f0ec7c2
Successfully built 324d3f0ec7c2
Successfully tagged node2:latest
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.

PS C:\AdanZyeDocker\kisim5\bolum50\nodejs2> docker image build -t node2 .
Sending build context to Docker daemon  4.096kB
Step 1/7 : FROM node:10
 ---> 4ee0f07a0e63
Step 2/7 : WORKDIR /usr/src/app
 ---> Using cache
 ---> 3552b7a57eef
Step 3/7 : COPY package.json .
 ---> Using cache
 ---> f28ceb6ab91b
Step 4/7 : RUN npm install
 ---> Running in f445c9423aca
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN docker_web_app@1.0.0 No repository field.
npm WARN docker_web_app@1.0.0 No license field.

added 50 packages from 37 contributors and audited 50 packages in 4.143s
found 0 vulnerabilities

Removing intermediate container f445c9423aca
 ---> 3e578feb60af
Step 5/7 : COPY server.js .
 ---> aab5adf53d5b
Step 6/7 : EXPOSE 8080
 ---> Running in 15ea455029bb
Removing intermediate container 15ea455029bb
 ---> c9d70e2c3b04
Step 7/7 : CMD [ "node", "server.js" ]
 ---> Running in ce19e8a246da
Removing intermediate container ce19e8a246da
 ---> a3ea4e4d797b
Successfully built a3ea4e4d797b
Successfully tagged node2:latest
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.

//Commands line is changed.
PS C:\AdanZyeDocker\kisim5\bolum50\nodejs2> docker image build -t node2 .
Sending build context to Docker daemon  4.096kB
Step 1/7 : FROM node:10
 ---> 4ee0f07a0e63
Step 2/7 : WORKDIR /usr/src/app
 ---> Using cache
 ---> 3552b7a57eef
Step 3/7 : COPY package.json .
 ---> Using cache
 ---> f28ceb6ab91b
Step 4/7 : RUN npm install
 ---> Using cache
 ---> 3e578feb60af
Step 5/7 : COPY server.js .
 ---> 4e035ee88dfc
Step 6/7 : EXPOSE 8080
 ---> Running in e0b9a165975f
Removing intermediate container e0b9a165975f
 ---> c1cd55b3171e
Step 7/7 : CMD [ "node", "server.js" ]
 ---> Running in cfd5e08d2cfa
Removing intermediate container cfd5e08d2cfa
 ---> ddd29ef51525
Successfully built ddd29ef51525
Successfully tagged node2:latest
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.

PS C:\AdanZyeDocker\kisim5\bolum50\nodejs2> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                  NAMES
24100443bcca        015d8a720466        "docker-entrypoint.s"   7 minutes ago       Up 7 minutes        0.0.0.0:80->8080/tcp   affectionate_chebyshev

PS C:\AdanZyeDocker\kisim5\bolum50\nodejs2> docker rm -f 241
241

PS C:\AdanZyeDocker\kisim5\bolum50\nodejs2> docker container run -d -p 80:8080 node2
60af3053a10d34f57a124be897bafb8fb17e058df4464555cadfdbdbac664ad2

PS C:\AdanZyeDocker\kisim5\bolum50\nodejs2> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                  NAMES
60af3053a10d        node2               "docker-entrypoint.s"   5 seconds ago       Up 6 seconds        0.0.0.0:80->8080/tcp   agitated_pike

Date of Notes : 27-12-2020 

**Schell notes**

1. '>' : add some notes
root@5b63847f6133:/# echo $SHELL
/bin/bash
root@5b63847f6133:/# echo $SHELL > test.txt
root@5b63847f6133:/# cat test.txt
/bin/bash
root@5b63847f6133:/#

2. '&' Ampersand : work as a background
root@5b63847f6133:/# ./test.sh &

3. 'jobs' : listed which jobs have been working at the background
root@5b63847f6133:/# jobs
[1]+ Running                ./test.sh & 

4. 'grep' : to find sth in text
root@5b63847f6133:/# cat abc.txt
123456
root@5b63847f6133:/# grep 3 abc.txt
123456

5. '|' pipe : the left side will be an input of the right side
root@5b63847f6133:/# cat abc.txt | grep 3
123456

6. ';' semicolon : run more than one command in the same line (command1;command2;command3)
root@5b63847f6133:/# ls
abc.txt  boot  etc   lib    lib64   media  opt   root  sbin  sys      test.txt  usr
bin      dev   home  lib32  libx32  mnt    proc  run   srv   test.sh  tmp       var
root@5b63847f6133:/# date
Sun Dec 27 20:38:28 UTC 2020
root@5b63847f6133:/# ls;date
abc.txt  boot  etc   lib    lib64   media  opt   root  sbin  sys      test.txt  usr
bin      dev   home  lib32  libx32  mnt    proc  run   srv   test.sh  tmp       var
Sun Dec 27 20:38:33 UTC 2020

7. '&&' double ampersand : If the left side of && works, the right side of && will be working!
root@5b63847f6133:/# cat abc.txt
123456
root@5b63847f6133:/# cat def.txt
cat: def.txt: No such file or directory
root@5b63847f6133:/# cat abc.txt && echo "the file was found"
123456
the file was found
root@5b63847f6133:/# cat def.txt && echo "the file was found"
cat: def.txt: No such file or directory

8. '||' double pipe : If the left side of || works, the right side of || will not be working! (Opposite of &&)
root@5b63847f6133:/# cat abc.txt || echo "test"
123456
root@5b63847f6133:/# cat def.txt || echo "test"
cat: def.txt: No such file or directory
test


**How to use CMD and HEALTHCHECK commands in the docker file**
PS C:\AdanZyeDocker\kisim5\bolum52\hello-docker> docker image build -t gunerhanale/hello-docker .
Sending build context to Docker daemon  14.34kB
Step 1/12 : FROM nginx:latest
 ---> ae2feff98a0c
Step 2/12 : LABEL maintainer="Ozgur Ozturk @ozgurozturknet"
 ---> Running in 12dc1f6a535b
Removing intermediate container 12dc1f6a535b
 ---> 627be6fa1661
Step 3/12 : LABEL version="1.0"
 ---> Running in bef8c6563f38
Removing intermediate container bef8c6563f38
 ---> be16768d262d
Step 4/12 : LABEL name="hello-docker"
 ---> Running in 4970388d22d8
Removing intermediate container 4970388d22d8
 ---> 99ad6a649592
Step 5/12 : ENV KULLANICI="Dunyali"
 ---> Running in 4f022d8dd68a
Removing intermediate container 4f022d8dd68a
 ---> 346999083b00
Step 6/12 : RUN printf "deb http://archive.debian.org/debian/ jessie main\ndeb-src http://archive.debian.org/debian/ jessie main\ndeb http://security.debian.org jessie/updates main\ndeb-src http://security.debian.org jessie/updates main" > /etc/apt/sources.list
 ---> Running in 14cec9fd1a7c
Removing intermediate container 14cec9fd1a7c
 ---> 6f9ce8c69470
Step 7/12 : RUN apt-get update
 ---> Running in 35cec7cc3d6b
Ign:1 http://archive.debian.org/debian jessie InRelease
Get:2 http://archive.debian.org/debian jessie Release [148 kB]
Get:3 http://security.debian.org jessie/updates InRelease [44.9 kB]
Get:4 http://archive.debian.org/debian jessie Release.gpg [2420 B]
Get:5 http://archive.debian.org/debian jessie/main Sources [7063 kB]
Get:6 http://security.debian.org jessie/updates/main Sources [366 kB]
Get:7 http://security.debian.org jessie/updates/main amd64 Packages [781 kB]
Get:8 http://archive.debian.org/debian jessie/main amd64 Packages [6818 kB]
Fetched 15.2 MB in 55s (275 kB/s)
Reading package lists...
Removing intermediate container 35cec7cc3d6b
 ---> bec371f2b15a
Step 8/12 : RUN apt-get install curl -y
 ---> Running in 83f1e3610f25
Reading package lists...
Building dependency tree...
Reading state information...
curl is already the newest version (7.64.0-4+deb10u1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Removing intermediate container 83f1e3610f25
 ---> aebc88ee3ccc
Step 9/12 : WORKDIR /usr/share/nginx/html
 ---> Running in 7e267852471a
Removing intermediate container 7e267852471a
 ---> b7edcdc865d9
Step 10/12 : COPY Hello_docker.html /usr/share/nginx/html
 ---> 3e15c77f27b0
Step 11/12 : HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 CMD curl -f http://localhost/ || exit 1
 ---> Running in 4c5ce4a36502
Removing intermediate container 4c5ce4a36502
 ---> c91824e85846
Step 12/12 : CMD sed -e s/Kullanici/"$KULLANICI"/ Hello_docker.html > index1.html && sed -e s/Hostname/"$HOSTNAME"/ index1.html > index.html ; rm index1.html Hello_docker.html; nginx -g 'daemon off;'
 ---> Running in 6980a6347dc6
Removing intermediate container 6980a6347dc6
 ---> 1e868e9a350e
Successfully built 1e868e9a350e
Successfully tagged gunerhanale/hello-docker:latest
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.


PS C:\AdanZyeDocker\kisim5\bolum52\hello-docker> docker container run -d --name hellodocker -p 80:80 gunerhanale/hello-docker
bf94821cc66b79fe3f2897e4410a63665b429de74264bcfffe8461e6a747f394

PS C:\AdanZyeDocker\kisim5\bolum52\hello-docker> docker ps
CONTAINER ID        IMAGE                      COMMAND                  CREATED              STATUS                        PORTS                NAMES
bf94821cc66b        gunerhanale/hello-docker   "/docker-entrypoint."   About a minute ago   Up About a minute (healthy)   0.0.0.0:80->80/tcp   hellodocker

PS C:\AdanZyeDocker\kisim5\bolum52\hello-docker> docker container run -d --name hellodocker2 -p 8090:80 gunerhanale/hello-docker
21ed49d42d397eb740d01532dcdb1615798837ff15e317ee5705154945be9d07

PS C:\AdanZyeDocker\kisim5\bolum52\hello-docker> docker ps
CONTAINER ID        IMAGE                      COMMAND                  CREATED             STATUS                            PORTS                  NAMES
21ed49d42d39        gunerhanale/hello-docker   "/docker-entrypoint."   1 second ago        Up 2 seconds (health: starting)   0.0.0.0:8090->80/tcp   hellodocker2
bf94821cc66b        gunerhanale/hello-docker   "/docker-entrypoint."   5 minutes ago       Up 5 minutes (healthy)            0.0.0.0:80->80/tcp     hellodocker

PS C:\AdanZyeDocker\kisim5\bolum52\hello-docker> docker ps
CONTAINER ID        IMAGE                      COMMAND                  CREATED             STATUS                   PORTS                  NAMES
21ed49d42d39        gunerhanale/hello-docker   "/docker-entrypoint."   2 minutes ago       Up 2 minutes (healthy)   0.0.0.0:8090->80/tcp   hellodocker2
bf94821cc66b        gunerhanale/hello-docker   "/docker-entrypoint."   7 minutes ago       Up 7 minutes (healthy)   0.0.0.0:80->80/tcp     hellodocker

**reduced steps as 8 step
PS C:\AdanZyeDocker\kisim5\bolum52\hello-docker> docker image build -t gunerhanale/hello-docker .
Sending build context to Docker daemon  17.92kB
Step 1/8 : FROM nginx:latest
 ---> ae2feff98a0c
Step 2/8 : LABEL maintainer="Ebubekir Gunerhanal @gunerhanale" version="1.0" name="hello-docker"
 ---> Running in 7093e11602b9
Removing intermediate container 7093e11602b9
 ---> 79dacdc0bc31
Step 3/8 : ENV KULLANICI="Dunyali"
 ---> Running in 53c822384a38
Removing intermediate container 53c822384a38
 ---> 98566e2bfa0c
Step 4/8 : RUN printf "deb http://archive.debian.org/debian/ jessie main\ndeb-src http://archive.debian.org/debian/ jessie main\ndeb http://security.debian.org jessie/updates main\ndeb-src http://security.debian.org jessie/updates main" > /etc/apt/sources.list && apt-get update && apt-get install curl -y
 ---> Running in 2c0ba5eb1d93
Ign:1 http://archive.debian.org/debian jessie InRelease
Get:2 http://security.debian.org jessie/updates InRelease [44.9 kB]
Get:3 http://archive.debian.org/debian jessie Release [148 kB]
Get:4 http://security.debian.org jessie/updates/main Sources [366 kB]
Get:5 http://archive.debian.org/debian jessie Release.gpg [2420 B]
Get:6 http://security.debian.org jessie/updates/main amd64 Packages [781 kB]
Get:7 http://archive.debian.org/debian jessie/main Sources [7063 kB]
Get:8 http://archive.debian.org/debian jessie/main amd64 Packages [6818 kB]
Fetched 15.2 MB in 19s (811 kB/s)
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
curl is already the newest version (7.64.0-4+deb10u1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Removing intermediate container 2c0ba5eb1d93
 ---> 2bc19af4ebe6
Step 5/8 : WORKDIR /usr/share/nginx/html
 ---> Running in 5a184362a191
Removing intermediate container 5a184362a191
 ---> ee892d03b4d9
Step 6/8 : COPY Hello_docker.html /usr/share/nginx/html
 ---> 1ccc85615212
Step 7/8 : HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 CMD curl -f http://localhost/ || exit 1
 ---> Running in e871f8fc18f5
Removing intermediate container e871f8fc18f5
 ---> 29677c1cbdf8
Step 8/8 : CMD sed -e s/Kullanici/"$KULLANICI"/ Hello_docker.html > index1.html && sed -e s/Hostname/"$HOSTNAME"/ index1.html > index.html ; rm index1.html Hello_docker.html; nginx -g 'daemon off;'
 ---> Running in 8273cb598090
Removing intermediate container 8273cb598090
 ---> 0303df2d19f7
Successfully built 0303df2d19f7
Successfully tagged gunerhanale/hello-docker:latest
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.

**we can set env with two different way(-e or --env)**
PS C:\AdanZyeDocker\kisim5\bolum52\hello-docker> docker container run -d -p 8095:80 --name hd2 -e KULLANICI="Ebubekir" gunerhanale/hello-docker
8bdf55a0d6cb3d7977632d0533296aef85187cd6328250c0eb5ad47b418ac59b
PS C:\AdanZyeDocker\kisim5\bolum52\hello-docker> docker exec -it hd2 sh
# echo $HOSTNAME
8bdf55a0d6cb
# echo $KULLANICI
Ebubekir


