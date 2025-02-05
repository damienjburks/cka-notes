# Manual Scheduling Overview

[Udemy Video Link](https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/14295580#content)
[Lab](https://uklabs.kodekloud.com/topic/practice-test-manual-scheduling-2/)

## Notes

- The scheduler will look for the `nodeName` parameter. If it does not find any, it will use its algorithm to automatically assign the pod to a node.
- Pods remain in a pending state if there is no scheduler.

  - The easiest way to schedule a pod on a node is to set the `nodeName` field in the pod specification file.
  - You can only specify the node name at creation time.
    - Kubernetes does not allow modifying the node name property of a pod. To assign a node to an existing pod, create a binding object and send a POST request to the pod's binding API.

- Example of manually scheduling a pod:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
    - image: nginx
      name: nginx
  nodeName: node01
```
