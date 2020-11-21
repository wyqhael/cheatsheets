<div style="text-align:center"><img src="./fleur.png" alt="flower" style="zoom:35%;" /></div>



---

# CheatSheet : Docker

---

## Sommaire

[TOC]





## Installation

``` shell
sudo pacman -Sy docker
```

Enable docker and start it :

``` shell
sudo systemctl enable docker
sudo systemctl start docker
systemctl status docker
● docker.service - Docker Application Container Engine
     Loaded: loaded (/usr/lib/systemd/system/docker.service; enabled; vendor preset: disabled)
     Active: active (running) since Sat 2020-11-21 12:02:29 CET; 7min ago
TriggeredBy: ● docker.socket
       Docs: https://docs.docker.com
   Main PID: 4563 (dockerd)
      Tasks: 10
     Memory: 36.7M
     CGroup: /system.slice/docker.service
             └─4563 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock
```

Run `docker info` :

``` shell
Client:
 Debug Mode: false

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 19.03.13-ce
 Storage Driver: overlay2
  Backing Filesystem: extfs
  Supports d_type: true
  Native Overlay Diff: false
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
 containerd version: c623d1b36f09f8ef6536a057bd658b3aa8632828.m
 runc version: ff819c7e9184c13b7c2607fe6c30ae19403a7aff
 init version: fec3683
 Security Options:
  apparmor
  seccomp
   Profile: default
 Kernel Version: 5.8.18-1-MANJARO
 Operating System: Manjaro Linux
 OSType: linux
 Architecture: x86_64
 CPUs: 4
 Total Memory: 15.33GiB
 Name: debu
 ID: N7F3:YHOO:KUCP:ZRWT:FY5A:AQZS:NLYK:LNPE:XWWN:NUSD:RPAC:BQWC
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 Registry: https://index.docker.io/v1/
 Labels:
 Experimental: false
 Insecure Registries:
  127.0.0.0/8
 Live Restore Enabled: false
```

When running `docker info` as non-root user you can get the following error :

``` shell
Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get http://%2Fvar%2Frun%2Fdocker.sock/v1.40/containers/json: dial unix /var/run/docker.sock: connect: permission denied
```

Make sure the **docker group** exist :

``` shell
cat /etc/group | grep docker
```

If not create it :

``` shell
sudo groupadd docker
```

And just add your user to the **docker group** with `usermod` :

``` shell
sudo usermod -aG docker <user>
```

Then try running `docker info`.
