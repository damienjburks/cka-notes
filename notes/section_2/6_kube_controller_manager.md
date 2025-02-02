# Kube Controller Manager

Udemy Video Link: <https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/14298428#content>

## Notes

- A controller is a process that continuously monitors the state of various components within the system and works toward getting everything functional.
  - Node controller keeps nodes running, checks the status of the nodes every 5 seconds, and communicates with kube-apiserver.
  - Waits 40 seconds until it marks the node as unreachable.
    - Pod eviction timeout = 5m.
- How to install it?
  - Download from Kubernetes release page.
  - Node-monitor period, grace, and eviction timeout are all configurable.
  - By default, all controllers are enabled, but you can choose which ones you want to enable.
  - Kube-controller-manager options are located in the `/etc/kubernetes/manifests/kube-controller-manager.yaml` file.
  - Also a part of systemd as well.
