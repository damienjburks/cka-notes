# Labels and Selectors

[Udemy Video Link](https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/14295582#content)
[Lab](https://uklabs.kodekloud.com/topic/practice-test-labels-and-selectors-2/)

## Notes

- **Labels**: Key-value pairs attached to Kubernetes objects for identification and organization.
- **Selectors**: Mechanisms to filter and query objects based on their labels.

  - Attach labels to objects as needed.
  - Use selectors to filter and select objects based on specified label criteria.

- To select a pod with specific labels:

  ```bash
  kubectl get pods --selector app=App1
  ```

- **ReplicaSet**:

  - Labels defined under the `template` section are applied to the pods.
  - Labels inside the `metadata` section are applied to the ReplicaSet itself.
  - When a service is created, it selects pods based on the labels defined in the ReplicaSet's pod template.

- **Annotations**:
  - Used to store additional metadata for informational purposes.
  - Can be utilized for integration with external systems.
