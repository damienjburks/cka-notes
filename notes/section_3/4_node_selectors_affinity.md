# Node Selectors & Node Affinity

[Udemy Video Link](https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/16063312#content)

## Notes

- Identifies the right node to place pods on.
- To label a node, use the kubectl command: `kubectl label nodes <node-name> key=value`
- Node Selector has limitations. It can only match nodes with specific labels.

- Node Affinity ensures that pods are hosted on particular nodes. It provides more advanced expressions compared to Node Selectors.
  - Provides advanced features for placing a pod on a particular node.
  - Contains key, operator, and values.
- The type of node affinity defines the behavior of the scheduler and stages in the lifecycle of the pod.

- Two available affinity types: `requiredDuringSchedulingIgnoredDuringExecution` & `preferredDuringSchedulingIgnoredDuringExecution`: - During Scheduling - the pod doesn't exist and is being created for the first time. - During Execution - the state where a pod has been running and a change affects the node affinity.
  - Affinity operator types are as follows: In, NotIn, Exists, DoesNotExist, Gt, Lt

## Examples of Supported Affinity Type

### RequiredDuringSchedulingIgnoredDuringExecutio

This type of affinity rule must be met for the pod to be scheduled onto a node. If no nodes meet the criteria, the pod will not be scheduled

````yaml
apiVersion: v1
kind: Pod
metadata:
    name: nginx-pod
spec:
    affinity:
        nodeAffinity:
            requiredDuringSchedulingIgnoredDuringExecution:
                nodeSelectorTerms:
                - matchExpressions:
                    - key: disktype
                        operator: In
                        values:
                        - ssd
    containers:
    - name: nginx
        image: nginx
``
### PreferredDuringSchedulingIgnoredDuringExecutio
This type of affinity rule specifies preferences rather than strict requirements. The scheduler will try to place the pod on a node that meets the criteria, but if no such node is available, the pod will still be scheduled
```yaml
apiVersion: v1
kind: Pod
metadata:
    name: nginx-pod
spec:
    affinity:
        nodeAffinity:
            preferredDuringSchedulingIgnoredDuringExecution:
            - weight: 1
                preference:
                    matchExpressions:
                    - key: disktype
                        operator: In
                        values:
                        - ssd
    containers:
    - name: nginx
        image: nginx
````
