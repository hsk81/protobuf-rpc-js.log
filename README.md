# protobuf-rpc-js.log

[matplotlib]: http://matplotlib.org/

Client command to create log files for `ack` messages (when the Node.js server is running):

```bash
for i in 1 2 3 4 ; do for j in a b ; do 
  ./example/client/js/rpc-client.js -a0 -s0 -m0 -d0 --n-ack=$i > log/diff-js.ack@$i-$j.log ; 
done ; 
done ;
```

Client command to create log files for `ack` messages (when the Python server is running):

```bash
for i in 1 2 3 4 ; do for j in a b ; do 
  ./example/client/js/rpc-client.js -a0 -s0 -m0 -d0 --n-ack=$i > log/diff-py.ack@$i-$j.log ; 
done ; 
done ;
```

Plot command to create histograms from the log files (requires a Python installation with the [matplotlib] plotting library):

```bash
for LOG in $(ls *.log) ; do 
  echo $LOG ; cat $LOG | cut -d' ' -f2 | ./plot.py --xlabel="RTT [ms]" --suptitle="$LOG" -n 3.0 histogram ;
done ;
```
