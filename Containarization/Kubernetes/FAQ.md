# Kubernetes:
## 1.what happens if a pod fails?
what happens depends on *why* it failed and how it was created.

* **Container crashes:** Kubernetes usually restarts the container according to its `restartPolicy` (commonly `Always` for Pods managed by Deployments).
* **Pod becomes unhealthy:** If readiness/liveness probes are configured, Kubernetes may stop sending traffic to it or restart the container.
* **Pod is deleted or the node fails:** A controller such as a **Deployment, ReplicaSet, or StatefulSet** can create a replacement Pod to maintain the desired number of replicas.
* **Pod keeps crashing:** Kubernetes repeatedly tries to restart it, potentially resulting in **CrashLoopBackOff**, with increasing delays between attempts.
* **No controller manages the Pod:** If you created a standalone Pod and it dies, Kubernetes generally **does not create a replacement Pod**.

A useful mental model is:

**Container fails → kubelet restarts container → if Pod itself disappears → controller creates a new Pod (if one exists).**

## 2.Services need to communicate How/How Pods communicate with each other?
services communicate with each other mainly through **Kubernetes Services + DNS**.

### Typical flow

**Service A → Kubernetes Service → Pod(s) running Service B**

For example:

```text
frontend Pod
     |
     | HTTP request
     v
backend Service
     |
     v
backend Pod(s)
```

### How it works

1. **Create a Service** for your backend Pods.
2. Kubernetes gives that Service a stable **IP address and DNS name**.
3. The frontend calls the backend using the Service name, for example:

```text
http://backend-service:8080
```

4. Kubernetes DNS resolves `backend-service` to the Service.
5. The Service forwards the request to one of the matching backend Pods.

### Why use a Service?

Pods are **ephemeral. Their IP addresses can change when Pods are recreated.**

A Service provides a **stable endpoint** even when the underlying Pods change:

```text
             ┌─── Pod 1
Frontend ──> Service ─── Pod 2
             └─── Pod 3
```

If Pod 2 dies and Kubernetes creates Pod 4, the frontend doesn't need to know. The Service automatically routes traffic to the available Pods.

**In short:** Kubernetes services communicate using **Service DNS names**, and the Service handles discovering and routing to the appropriate Pods.
