# kubectl Commands Engineers Run First During Panic

| # | Command | What It Does | Why I Run It | Emotional State |
|---|---------|--------------|---------------|-----------------|
| 1 | `kubectl get pods -A` | Lists all pods in all namespaces | First check – what's running? | Let's see the damage... 👀 |
| 2 | `kubectl get pods -o wide` | Shows pods with node & IP info | See where pods are running | Where are you running?! 🤔 |
| 3 | `kubectl describe pod <pod> -n <ns>` | Detailed info about the pod | Find issues, events, reasons | Okay, what went wrong? 😟 |
| 4 | `kubectl logs <pod> -n <ns>` | Shows logs from current container | Find the actual error | Show me the truth! 🤓 |
| 5 | `kubectl logs <pod> -n <ns> --previous` | Shows logs from previous container | If pod crashed & restarted | Maybe last time it worked... 😭 |
| 6 | `kubectl get events -A --sort-by=.lastTimestamp` | Shows recent events in the cluster | Find warnings, failures, errors | Events never lie... 👀 |
| 7 | `kubectl top pod -A` | Shows CPU & memory usage of pods | Check resource usage issues | Is something eating CPU? 😨 |
| 8 | `kubectl top node` | Shows CPU & memory of nodes | Check node resource pressure | Are nodes in pain? 😖 |
| 9 | `kubectl get nodes` | Lists all cluster nodes | Check node status (Ready?) | Are all nodes healthy? 🤨 |
| 10 | `kubectl get svc -A` | Lists all services | Check if service exists | Is the service even there? 😟 |
| 11 | `kubectl get ingress -A` | Lists all ingress resources | Check routing / traffic issues | Why is traffic not reaching?? 😭 |
| 12 | `kubectl get endpoints -A` | Lists all service endpoints | Check if service is connected | Where are my endpoints? 😩 |
| 13 | `kubectl exec -it <pod> -n <ns> -- /bin/sh` | Open a shell inside the pod | Debug from inside the pod | Time to go deep inside... 😎 |
| 14 | `kubectl get configmap -A` | Lists all ConfigMaps | Check configuration data | Is config correct? 🤔 |
| 15 | `kubectl get secret -A` | Lists all Secrets | Check sensitive configs | Secret problems... 💀 |
| 16 | `kubectl rollout status deployment/<name> -n <ns>` | Check status of rollout | See if deployment is healthy | Almost there... hope so! 🤞 |
| 17 | `kubectl rollout undo deployment/<name> -n <ns>` | Roll back to previous version | Quick fix: rollback | ROLLBACK! SAVE ME! 🚨 |
| 18 | `kubectl get hpa -A` | Shows autoscaler info | Check autoscaling status | Why isn't it scaling? 😡 |
| 19 | `kubectl get pvc -A` | Lists all PersistentVolumeClaims | Check storage claims | Storage again?! 😩 |
| 20 | `kubectl cluster-info` | Shows cluster information | Verify cluster connectivity | Is the cluster even alive? 💀 |

**Panic Workflow** (My Survival Flow)
1. Get Pods
2. Describe
3. Logs
4. Events
5. Resource Check
6. Exec
7. Fix / Rollback

**Golden Rule**
> **When in doubt, `kubectl logs` is always the first friend! ❤️**
