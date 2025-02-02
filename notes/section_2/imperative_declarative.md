# Imperative vs Declarative

[Udemy Video Link](https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/21500820#content)

## Notes

- **Imperative**: Specifies the exact steps required to achieve a desired state.
- **Declarative**: Defines the desired state and allows the system to determine the steps to achieve it.

### Kubernetes Commands

#### Imperative

**Create Objects:**

```bash
kubectl run --image=nginx nginx
kubectl create deployment --image=nginx nginx
kubectl expose deployment nginx --port 80
```

**Update Objects:**

```bash
kubectl edit deployment nginx
kubectl replace -f nginx.yaml
kubectl replace --force -f nginx.yaml
kubectl scale deployment nginx --replicas=5
kubectl set image deployment nginx nginx=nginx:1.18
```

**Create Objects (Configuration Files):**

```bash
kubectl create -f nginx.yaml
```

**Delete Objects:**

```bash
kubectl delete -f nginx.yaml
```

- Use `kubectl edit` for quick updates, but it's generally better to edit the configuration file and use `kubectl replace`.
- If an object already exists, use `kubectl replace` instead of `kubectl create`.

#### Declarative

**Create/Update Objects:**

```bash
kubectl apply -f nginx.yaml
```

### Exam Tips

- Use the imperative approach for quick tasks. Practice these commands!
- For complex requirements, use the declarative approach with configuration files. While you will mostly work in a declarative manner using definition files, imperative commands can help with one-time tasks and quickly generate definition templates. This can save considerable time during exams. Before we begin, familiarize yourself with two useful options for the commands below:
  - `--dry-run=client`: This option allows you to test your command without creating the resource. It verifies if the resource can be created and if the command is correct.
  - `-o yaml`: This option outputs the resource definition in YAML format on the screen.
