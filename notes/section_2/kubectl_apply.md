# Kubectl Apply Command Overview

[Udemy Video Link](https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/21500826#overview)

## Notes

When you run an apply command, such as `kubectl apply -f nginx.yaml`, the following occurs:

- Kubernetes checks if the configuration already exists:
    - If it exists, Kubernetes compares the current object configuration with the new one and updates it if there are differences.
    - If it does not exist, Kubernetes creates the object.
    - Kubernetes also logs the last applied configuration for auditing and tracking purposes.
