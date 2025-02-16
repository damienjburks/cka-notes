# Commands and Arguments

**Udemy Video:** [Certified Kubernetes Administrator](https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/14296012#overview)

**Lab:** [Practice Test - Commands and Arguments](https://uklabs.kodekloud.com/topic/practice-test-commands-and-arguments-2/)

## Notes

- The following Kubernetes Pod configuration is equivalent to the Docker command:

```bash
docker run --name ubuntu-sleeper sleep 10
```

```yaml
apiVersion: v1
kind: Pod
metadata:
    name: ubuntu-sleeper
spec:
    containers:
    - name: ubuntu-sleeper
        image: ubuntu
        command: ["sleep", "10"]
```

- **Entrypoint**: The command that runs at startup.
- **CMD**: The default parameter passed to the command.
- Note: The `command` field in Kubernetes overrides the CMD instruction.
