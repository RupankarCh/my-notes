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
