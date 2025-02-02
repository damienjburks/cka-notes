# Kubelet Overview (High-Level)

[Video Link](https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/14298432#content)

## Notes

- The kubelet on each worker node registers the node with the cluster.
- It communicates with the kube-apiserver to request the container runtime to create pods.
- It continuously monitors the status of pods after they are deployed.
- **Note:** kubeadm does not deploy kubelets.
