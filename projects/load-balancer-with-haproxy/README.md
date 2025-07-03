# How to Deploy

## Docker Installation

Check **docker** is installed:

```sh
docker --version
```

You should see an output similar to:

```sh
Docker version 28.1.1+1, build 068a01e
```

If not, run:

```sh
sudo snap install docker
```

## Containerlab Installation

```sh
echo "deb [trusted=yes] https://netdevops.fury.site/apt/ /" | sudo tee -a /etc/apt/sources.list.d/netdevops.list
sudo apt update && sudo apt install containerlab
```

## Run Deploy Scripts

```sh
cd projects/load-balancer-with-haproxy/lab-files
clab deploy
```

You can check the containerlab deployment at anytime with:

```sh
sudo clab inspect haproxylab.clab.yaml
```

You should see a similar output to:

```sh
21:21:33 INFO Parsing & checking topology file=haproxylab.clab.yaml
╭────────────────────────────────┬───────────────────────────────────┬─────────┬───────────────────╮
│              Name              │             Kind/Image            │  State  │   IPv4/6 Address  │
├────────────────────────────────┼───────────────────────────────────┼─────────┼───────────────────┤
│ clab-basic-haproxylab1-haproxy │ linux                             │ running │ 172.20.20.2       │
│                                │ haproxytech/haproxy-ubuntu:latest │         │ 3fff:172:20:20::2 │
├────────────────────────────────┼───────────────────────────────────┼─────────┼───────────────────┤
│ clab-basic-haproxylab1-web1    │ linux                             │ running │ 172.20.20.3       │
│                                │ ubuntu/apache2:latest             │         │ 3fff:172:20:20::3 │
├────────────────────────────────┼───────────────────────────────────┼─────────┼───────────────────┤
│ clab-basic-haproxylab1-web2    │ linux                             │ running │ 172.20.20.4       │
│                                │ ubuntu/apache2:latest             │         │ 3fff:172:20:20::4 │
╰────────────────────────────────┴───────────────────────────────────┴─────────┴───────────────────╯

```
