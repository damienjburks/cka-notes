# Operating System Upgrades

[Udemy Video Link](https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/14296046#content)

Lab Link: https://uklabs.kodekloud.com/topic/practice-test-os-upgrades-2/

## Notes

- If nodes are down for more than five minutes, all pods are terminated.
  - The master node waits for five minutes before considering the node dead.
- Drain the node to move the pods to another node in the cluster.
  - When drained, nodes are marked as unschedulable. To schedule pods on it again, you must uncordon the node.

```sh
/*
 * This script contains commands to manage Kubernetes nodes during an OS upgrade.
 *
 * Commands:
 * 1. kubectl drain node-1
 *    - This command safely evicts all pods from the node 'node-1' and marks it as unschedulable.
 *      It ensures that no new pods are scheduled on this node and existing pods are moved to other nodes.
 *
 * 2. kubectl cordon node-2
 *    - This command marks the node 'node-2' as unschedulable, preventing new pods from being scheduled on it.
 *      However, it does not evict existing pods from the node.
 *
 * 3. kubectl uncordon node-1
 *    - This command marks the node 'node-1' as schedulable again, allowing new pods to be scheduled on it.
 */
kubectl drain node-1
kubectl cordon node-2
kubectl uncordon node-1
```
