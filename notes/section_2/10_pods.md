# Understanding Pods

[Video Link](https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/14298578#content)

## Notes

- Assumptions:

  1. Docker images are available.
  2. A Kubernetes cluster is already set up (either single-node or multi-node).

- Containers are encapsulated into a Kubernetes object called a pod.
- A pod is the smallest deployable unit in Kubernetes.
- It represents a single instance of an application.
- Pods typically have a one-to-one relationship with containers.
- Scaling up involves creating new pods.
- Scaling down involves removing pods.

### Multi-Container Pods

- Usually consist of different types of containers, often including a helper container.
- Containers within a pod can communicate with each other directly using `localhost` and share the same storage space.

### Creating Pods with Latest Images

- Use the following command to create a pod with the latest Nginx image:

  ```sh
  kubectl run nginx --image=nginx
  ```

  - Note: This command does not expose a service.
