# Pods & YAMLs

[Video Link](https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/16214484#content)

[Corresponding Lab Link](https://uklabs.kodekloud.com/topic/practice-test-pods-2/)

## Notes

- `pod-definition.yml` example:

  ```yaml
  apiVersion: v1 # Specifies the API version.
  kind: Pod # Defines the type of Kubernetes object (e.g., Pod, ReplicaSet, Deployment, Service).
  metadata: # Metadata about the object, such as its name and labels.
    name: my-app # Name of the pod.
    labels: # Labels for the pod.
      app: myapp
  spec: # Specification of the desired behavior of the pod.
    containers: # List of containers within the pod.
      - name: nginx-container
        image: nginx
  ```

- To create the pod, run: `kubectl create -f pod-definition.yml`
- The `metadata` field is always a dictionary.
- To view the created pods, run: `kubectl get pods`
- To see detailed information about the pod, run: `kubectl describe pod my-app`
- The `kind` field is case-sensitive.
- Specify the full path to the image if it is not hosted on Docker Hub by default.
