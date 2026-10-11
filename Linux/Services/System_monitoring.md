The six main areas
```
             LINUX SYSTEM MONITORING
                      |
       +--------------+--------------+
       |              |              |
      CPU           Memory          Disk
       |              |              |
    top, mpstat    free, vmstat    df, du
       |
       +--------------+--------------+
                      |
                Other Components
                      |
              +-------+-------+
              |       |       |
           Process  Network  Services
              |       |       |
             ps      ss     systemctl
```
High CPU usage is not necessarily a problem. A server processing a large workload might operate at 90% CPU utilization normally.The important question is whether the workload is expected and whether applications are responding properly.

## CPU
```
lscpu (To display CPU architecture, Number of CPUs and cores, CPU model, CPU frequency information, Virtualization capabilities)
nproc (To display number of processors)
top (To display CPU usage)
```

## RAM
When available memory becomes insufficient, Linux may use swap space or invoke the Out-Of-Memory (OOM) killer.
```
free -h (To display memory usage)
```

## Disk and Filesystem Monitoring
Disk monitoring answers two important questions:
- How much storage space is available?
- Is the storage performing well?
```
df -h (To Check filesystem capacity)
df -i (To check inode usage)
lsblk (To check disk devices, partitions and mount points)
```

## Process Monitoring
A process is a running instance of a program.
```
ps aux (To list running processes)
pgrep -a <process_name(sshd)> (To search for a specific process)
kill PID (To stop a process)
```

## Network Monitoring
Network monitoring helps diagnose:
- Whether an interface is up.
- Which IP addresses are configured.
- Whether the server is listening on the expected port.
- Whether connections are established.
- Whether packets are being dropped.
```
ip a (To display network interfaces and their assigned IP addresses)
ip route (To Check routing)
sudo ss -lntup (To Check listening ports)
ping -c 4 8.8.8.8 (Test connectivity to an IP address)
getent hosts google.com (Test DNS resolution)
curl -I --max-time 5 https://example.com (Test HTTPS connectivity)
```

## Service Monitoring with systemd
```
systemctl status <service_name> (Check service status)
systemctl --failed (Check failed services)
systemctl is-enabled <service_name> (Check whether a service starts automatically)
sudo journalctl -u <service_name> (Check service logs, add -f to follow new log messages live)
```

## Tuned
tuned is a service that applies performance-tuning profiles to supported Linux systems.
Different workloads have different performance requirements.
