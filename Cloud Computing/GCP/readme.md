# Google Compute Engine: 
GCP's **VM service**. The provisioning process is, you choose a machine type and a boot disk (OS image). A key difference is GCP's ability to use **preemptible VMs**, which are significantly cheaper but can be terminated by Google at any time, making them suitable for fault-tolerant, batch-processing workloads.

## Preemptible VMs are ideal for workloads that are:

- Fault-tolerant
- Batch processing jobs
- Data analysis / ETL pipelines
- CI/CD builds
- Rendering or simulations
Example: Running large-scale experiments where restarting isn’t a big deal.
