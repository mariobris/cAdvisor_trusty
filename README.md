# cAdvisor_trusty

*  cAdvisor file downloaded from `cadvisor/artful 0.25.0+dfsg-1 amd64` 
*  extracted & new cAdvisor binary replaced
*  etc/init.d/cadvisor file modified from
```
    stop)
        ...
        R=$(start-stop-daemon --stop --oknodo --name $NAME --pidfile $PIDFILE --remove-pidfile --retry=$RETRY 2>&1)
        ...
```
to
```
    stop)
        ...
        R=$(start-stop-daemon --stop --oknodo --name $NAME --pidfile $PIDFILE --retry=$RETRY 2>&1)
        ...
        rm $PIDFILE
```
--remove-pidfile is not supported in trusty `start-stop-daemon`
