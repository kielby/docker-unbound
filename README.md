# docker-unbound
**Building image**

> docker build -t kielby/unbound .

**Unbound configuration file**

>mkdir -p /srv/unbound </br>
>nano /srv/unbound/unbound.conf

Sample unbound.conf
>server:</br>
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;verbosity: 1</br>
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;interface: 0.0.0.0</br>
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;access-control: 0.0.0.0/0 allow</br>
></br>
>forward-zone:</br>
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name: "."</br>
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;forward-addr: 8.8.4.4</br>
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;forward-addr: 8.8.8.8

**Running container**

>docker run -d \\</br>
>-p 53:53/tcp \\</br>
>-p 53:53/udp \\</br>
>-v /srv/unbound/:/etc/unbound \\</br>
>--name unbound \\</br>
>--restart unless-stopped \\</br>
>kielby/unbound
