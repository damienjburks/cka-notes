# Init Containers

[Lab Link](https://uklabs.kodekloud.com/topic/practice-test-init-containers-2/)

## Notes

In a multi-container pod, each container is expected to run a process that remains active throughout the pod's lifecycle. For example, in a multi-container pod with a web application and a logging agent, both containers should remain active continuously. The logging agent's process should run as long as the web application is active. If either process fails, the pod restarts.

However, there are scenarios where you need to run a process that completes its task and then terminates. For instance, a process that pulls code or binaries from a repository for the main web application, which only needs to run once when the pod is created. Or a process that waits for an external service or database to be ready before starting the main application. This is where init containers come into play.

An init container is configured in a pod like any other container but is specified within an `initContainers` section, as shown below:

```yaml
apiVersion: v1
kind: Pod
metadata:
    name: myapp-pod
    labels:
        app: myapp
spec:
    containers:
    - name: myapp-container
        image: busybox:1.28
        command: ['sh', '-c', 'echo The app is running! && sleep 3600']
    initContainers:
    - name: init-myservice
        image: busybox
        command: ['sh', '-c', 'git clone <some-repository-that-will-be-used-by-application> ; done;']
```

When a pod is first created, the init container runs, and its process must complete before the main application container starts.

You can configure multiple init containers, similar to multi-container pods. In this case, each init container runs sequentially, one at a time. If any init container fails to complete, Kubernetes restarts the pod repeatedly until the init container succeeds.

```yaml
apiVersion: v1
kind: Pod
metadata:
    name: myapp-pod
    labels:
        app: myapp
spec:
    containers:
    - name: myapp-container
        image: busybox:1.28
        command: ['sh', '-c', 'echo The app is running! && sleep 3600']
    initContainers:
    - name: init-myservice
        image: busybox:1.28
        command: ['sh', '-c', 'until nslookup myservice; do echo waiting for myservice; sleep 2; done;']
    - name: init-mydb
        image: busybox:1.28
        command: ['sh', '-c', 'until nslookup mydb; do echo waiting for mydb; sleep 2; done;']
```
