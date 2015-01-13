# carrier
centos docker in docker


在boot2docker v1.3.0执行:

    docker build -t carrier . 
    docker run --privileged -i -t -v /lib/modules/3.16.4-tinycore64/:/lib/modules/3.16.4-tinycore64/ carrier /bin/bash

启动docker carrier

进入docker carrier,运行：

    service docker start
    docker run -i -t -v /bin:/carrier/bin -v /usr/bin/:/carrier/usr/bin -v /usr/sbin/:/carrier/usr/sbin -v /lib64:/carrier/lib64 -v /usr/lib64:/carrier/usr/lib64 ubuntu /bin/bash

在新启动的实例里，设置环境变量

    export LD_LIBRARY_PATH=/lib/x86_64-linux-gnu:/lib:/lib64:/carrier/lib64/:/carrier/usr/lib64/
    export PATH=/bin:/usr/bin:/usr/sbin:/carrier/bin/:/carrier/usr/bin/:/carrier/usr/sbin/:$PATH

后，不需安装可以直接使用docker carrier上面的命令,例如vim,ping,nmap,python,perl等.
