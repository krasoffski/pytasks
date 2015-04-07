Python Home Task 02
===================


## Helpful information

Study following links:
 - https://docs.python.org/2.7/library/multiprocessing.html
 - https://docs.python.org/2.7/library/threading.html
 - https://www.youtube.com/watch?v=CObboy8XzaM
 - https://www.youtube.com/watch?v=Obt-vMVdM8s
 - https://wiki.python.org/moin/Concurrency/99Bottles
 - http://doughellmann.com/2007/10/01/multiprocessing.html
 - http://eli.thegreenplace.net/2012/01/16/python-parallelizing-cpu-bound-tasks-with-multiprocessing/

Additional topics which might help you with home task (tips):
 - https://docs.python.org/2/library/basehttpserver.html
 - https://docs.python.org/2/library/socketserver.html


## Subtask 1

 Create *very* simple http server which can execute shell (not all, due to HTTP URL restrictions) command on host and returns stdout as plain text: `http:/<IP>:<PORT>/shell;<CMD>`
 - Use only standard python library.
 - At the same time can be executed a few commands.
 - Pay attention on HTTP headers and encoding (respects cyrillic alphabet).
 - Make sure there are no errors in developers console (firefox).

### For example:

Using internet browser:

![browser example](https://git.epam.com/yury_krasouski/pycourse-tasks/raw/master/images/browser.png)

And at the same time:
```bash
$ curl -s 'http:// 192.168.1.2:8080/shell;ip%20a'
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:1f:d0:5a:37:e6 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.2/24 brd 192.168.1.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::21f:d0ff:fe5a:37e6/64 scope link
       valid_lft forever preferred_lft forever

$ curl –s 'http:// 192.168.1.2:8080/shell;date'
Вс. февр.  8 12:31:46 MSK 2015

```