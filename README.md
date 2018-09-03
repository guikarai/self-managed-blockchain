# self-managed-blockchain
Deploying a self-managed blockchain based on Hyperledger on Linux on IBM Z and LinuxONE


# Monitoring the Docker Infrastructure
```
root@ghtstjav:~# docker pull portainer/portainer
Using default tag: latest
latest: Pulling from portainer/portainer
d1e017099d17: Pull complete 
ae7244702902: Pull complete 
Digest: sha256:ab096b92ed177b47adfa8a9a99e304d36596efa557b9627c066cee164cc39910
Status: Downloaded newer image for portainer/portainer:latest

root@ghtstjav:~# docker volume create portainer_data
portainer_data

root@ghtstjav:~# docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer
5f802e174e52956443c01228d213536b315c4411157c194138ea5fc223bbaf79
```

# Installing Apache2 to host the Blockchain portal UI
```
root@ghtstjav:~# sudo apt-get install apache2 libapache2-modsecurity
```

```
vi /etc/apache2/mods-available/ssl.conf
```

From there, please change as the following, the default apache engine with ibmca.
```
```

Save and quit vi issuing **:wq** .
```
root@ghtstjav:/etc/apache2/mods-available# service apache2 restart
```

Please check the status witht the following command:
```
root@ghtstjav:/etc/apache2/mods-available# service apache2 status
* apache2.service - LSB: Apache2 web server
   Loaded: loaded (/etc/init.d/apache2; bad; vendor preset: enabled)
  Drop-In: /lib/systemd/system/apache2.service.d
           `-apache2-systemd.conf
   Active: active (running) since Mon 2018-09-03 14:15:07 CEST; 2min 2s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 54265 ExecStop=/etc/init.d/apache2 stop (code=exited, status=0/SUCCESS)
  Process: 54287 ExecStart=/etc/init.d/apache2 start (code=exited, status=0/SUCCESS)
    Tasks: 55
   Memory: 55.2M
      CPU: 129ms
   CGroup: /system.slice/apache2.service
           |-54306 /usr/sbin/apache2 -k start
           |-54309 /usr/sbin/apache2 -k start
           `-54310 /usr/sbin/apache2 -k start

Sep 03 14:15:05 ghtstjav.mop.fr.ibm.com systemd[1]: Stopped LSB: Apache2 web server.
Sep 03 14:15:05 ghtstjav.mop.fr.ibm.com systemd[1]: Starting LSB: Apache2 web server...
Sep 03 14:15:05 ghtstjav.mop.fr.ibm.com apache2[54287]:  * Starting Apache httpd web server apache2
Sep 03 14:15:07 ghtstjav.mop.fr.ibm.com apache2[54287]:  *
Sep 03 14:15:07 ghtstjav.mop.fr.ibm.com systemd[1]: Started LSB: Apache2 web server.
```


