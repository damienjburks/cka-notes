# Default Scheduler

**Udemy Video Link:** [Certified Kubernetes Administrator with Practice Tests](https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/14295588#content)

**Lab Link:** [Practice Test: Multiple Schedulers](https://uklabs.kodekloud.com/topic/practice-test-multiple-schedulers-2/)

## Notes

Refer to the [Kubernetes documentation](https://kubernetes.io/docs/tasks/extend-kubernetes/configure-multiple-schedulers/) for configuring multiple schedulers.

### Viewing Events

To confirm the scheduler is being used, view the events with:

```sh
kubectl get events -o wide
```

### Viewing Scheduler Logs

To view the logs of the custom scheduler, use:

```sh
kubectl logs my-custom-scheduler --namespace=kube-system
```

## Custom Scheduler YAML

Create a YAML file to define a custom scheduler:

```yaml
apiVersion: v1
kind: Pod
metadata:
    name: my-custom-scheduler
    namespace: kube-system
    labels:
        component: my-custom-scheduler
spec:
    containers:
    - name: my-custom-scheduler
        image: k8s.gcr.io/kube-scheduler:v1.20.0
        command:
        - kube-scheduler
        - --scheduler-name=my-custom-scheduler
        - --kubeconfig=/etc/kubernetes/scheduler.conf
        volumeMounts:
        - name: config
            mountPath: /etc/kubernetes/
            readOnly: true
    volumes:
    - name: config
        hostPath:
            path: /etc/kubernetes/scheduler.conf
```

## Mapping a Pod to a Custom Scheduler

To map a pod to use the custom scheduler, specify the `schedulerName` field in the pod's YAML definition. Example:

```yaml
apiVersion: v1
kind: Pod
metadata:
    name: my-pod
spec:
    schedulerName: my-custom-scheduler
    containers:
    - name: my-container
        image: nginx
```

In this example, the pod named `my-pod` will be scheduled using `my-custom-scheduler` instead of the default scheduler.
