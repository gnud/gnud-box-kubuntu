
Tell me where am I (which terminaL)

```bash
ps ax | grep $$ | awk '{print $2}'
```

Out:

```bash
pts/2
pts/2
```

Show me open files handles

fd stands for file descriptor

```bash
ls -l /proc/$$/fd
```

Out:

```bash
total 0
lrwx------ 1 user user 64 sep  1 00:00 0 -> /dev/pts/2
lrwx------ 1 user user 64 sep  1 00:00 1 -> /dev/pts/2
lrwx------ 1 user user 64 sep  1 00:00 2 -> /dev/pts/2
lrwx------ 1 user user 64 sep  1 00:00 255 -> /dev/pts/2
```

What's my default route ip

```bash
hostname -I | grep -Eo '192.168\.[0-9]{1,3}\.[0-9]{1,3}' | head -n1
```

Which proxy IP's are being used at the moment?

```bash
sudo lsof -i4 -i6 -a -p $(pgrep -i $name_of_program) | awk -F ' ' '{ print $9 }' | tail -n +2 |awk -F ':' '{ print $1 }'

Filter off the current ip:

```bash
sudo lsof -i4 -i6 -a -p $(pgrep -i $name_of_program) | awk -F ' ' '{ print $9 }' | tail -n +2 |awk -F ':' '{ print $1 }' | grep -v $(hostname -I | grep -Eo '192.168\.[0-9]{1,3}\.[0-9]{1,3}' | head -n1)
```

List live which files are being written at the moment.
Useful to find out which program is dumping huge amount of data.

```bash
sudo fatrace -c -t -f w -p $(pgrep $name_of_program) 
```
