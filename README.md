# cpsc416_proj_johnnybc_mikuh_nbosse_jmhirsch_sassansh_fbcaiado

## Server Failure Detection with Paxos

<br>

### Members:

- Sassan Shokoohi (sassansh)
- Naithan Bosse (nbosse)
- Johnny Li (johnnybc)
- Felipe Caiado (fbcaiado)
- Ken Utsunomiya (mikuh)
- Jonathan Hirsch (jmhirsch)

<br>

### References

1. Adapted A3
2. Method signatures for Proposer.go, Acceptor.go, and Learner.go are informed by the following project: https://pkg.go.dev/github.com/kkdai/paxos



### To use cloudrun.sh

1. Make sure you have sshpass installed by running `brew install hudochenkov/sshpass/sshpass` on macOS, or by installing the package using your preferred package manager
2. Run `./cloudrun.sh -r`
3. The first time you use the script, type `i 1 2 3 4 5 6 7 8 9 10 11 t c` into the interactive shell.
4. You can now use any of the commands in the interactive shell. (use `help` to see the list of commands)
5. You can also run `./cloudrun.sh -h` to view the available commands in non-interactive mode. 


The interactive mode supports the following commands:
```
#separate server numbers in <[servers]> with a space#

help | h - prints this help message
setup | i <[servers]> - sets up specified servers
ssh <server> - ssh into server, 'c' for client, 't' for tracing server
upload | u <path> - uploads folder at <path> to all servers"
exit | q - exits interactive mode
showPorts | sp <[server]> - shows ports used by specified server, 'c' for cloud client,       
      't' for tracing server. Runs until canceled
        
client | c - start the cloud client
 start | s - <[servers]> starts specified servers
startAll | sa - starts all servers
startAndTrace | st <[servers]> - starts the tracing server and specified servers
trace | t - starts tracing on server
gettrace | gt - copies the traces from the tracing server to the current directory

kill | k <[servers]> - kills specified servers
killall | ka - kills all servers
killClient | kc - kill the cloud client
killTrace | kt - kills tracing server

partition | p <server1> <[servers]> - partitions server <server1> from server <[servers]>
unpartition | up <server1> <[servers]> - unpartitions server <server1> from <[servers]>
unpartitionall | upa - unpartitions all servers by resetting their IPTables
```
