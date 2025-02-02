# Replica Sets & Replication Controllers

[Udemy Video Link](https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/14298658#content)

[Corresponding Lab Link](https://uklabs.kodekloud.com/topic/practice-test-replicasets-2/)

## Notes

### Replication Controller

- A Replication Controller ensures multiple instances of a single pod run in a Kubernetes cluster.
  - Automatically creates a new pod if an existing one fails.
- It also helps with load balancing across multiple nodes within a cluster.
- Balances demand across different nodes.
- The Replication Controller is being replaced by Replica Sets.
- To create a Replication Controller:

  ```yaml
  # rc-definition.yaml
  apiVersion: v1
  kind: ReplicationController
  metadata:
      name: myapp-rc
      labels:
          app: myapp
          type: front-end
  spec:
      replicas: 3
      template:
          metadata:
              name: my-app
              labels:
                  app: myapp
                  type: front-end
          spec:
              containers:
              - name: nginx-container
                  image: nginx
  ```

- Create the controller and verify its existence:

  ```bash
  kubectl create -f rc-definition.yaml
  kubectl get replicationcontroller
  kubectl get pods
  ```

### Replica Sets

- Requires a selector definition to determine which pods it manages.

  - This allows Replica Sets to manage pods not created by the Replica Set itself.

    ```yaml
    # replicaset-definition.yaml
    apiVersion: apps/v1
    kind: ReplicaSet
    metadata:
        name: myapp-replicaset
        labels:
            app: myapp
            type: front-end
    spec:
        replicas: 3
        selector:
            matchLabels:
                type: front-end
        template:
            metadata:
                name: my-app
                labels:
                    app: myapp
                    type: front-end
            spec:
                containers:
                - name: nginx-container
                    image: nginx
    ```

- Create the Replica Set and verify its existence:

  ```bash
  kubectl create -f replicaset-definition.yaml
  kubectl get replicaset # or kubectl get rs
  kubectl get pods
  ```

- Labels can be used as filters in the Replica Set using the `matchLabels` key.
- Scale the replicas manually with the following commands:

  ```bash
  kubectl replace -f replicaset-definition.yaml # After editing the file
  kubectl scale --replicas=6 -f replicaset-definition.yaml
  kubectl scale --replicas=6 replicaset myapp-replicaset
  ```
