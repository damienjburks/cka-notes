# Taints and Tolerations

[Udemy Video Link](https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/16063306#content)
[Practice Test Video](https://uklabs.kodekloud.com/topic/practice-test-taints-and-tolerations-2/)

## Notes

- **Taints** are used to control pod scheduling on specific nodes.
  - When a node is tainted, pods will not be scheduled on it unless they have matching tolerations.
  - This mechanism helps in dedicating nodes for specific workloads or ensuring certain nodes are avoided by pods.
- **Tolerations** are pod specifications that allow them to be scheduled on tainted nodes.
  - They act as exceptions to taints.
  - Only pods with appropriate tolerations can be scheduled on tainted nodes.
- **Key Point**: Taints are applied to nodes, while tolerations are defined in pod specifications.

```bash
# Setting Taints
kubectl taint nodes node-name key=value:taint-effect
```

- There are three types of taint effects: `NoSchedule`, `PreferNoSchedule`, and `NoExecute`.

```bash
kubectl taint nodes node1 app=blue:NoSchedule
```

```bash
# Removing a taint from a node
kubectl taint nodes controlplane node-role.kubernetes.io/control-plane:NoSchedule-
```

- **Tolerations Example**

```yaml
apiVersion: v1
kind: Pod
metadata:
    name: myapp-pod
spec:
    containers:
        - name: nginx-container
            image: nginx
    tolerations:
        - key: app
            operator: "Equal"
            value: "blue"
            effect: "NoSchedule"
```

- A taint is set on the master node by default to prevent any pods from being scheduled on it.
  - Best practice is to avoid deploying workloads on a master node.
