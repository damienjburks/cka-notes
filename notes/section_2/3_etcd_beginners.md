# ETCD for Beginners

Udemy Video Link: <https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/14298420#overview>

## Notes

### What is ETCD?

ETCD is a distributed key-value store that is simple, secure, and fast. It stores information as documents or pages, typically in an unstructured format.

### Installing ETCD

Refer to the [official documentation](https://etcd.io/docs/v3.5/install/) for detailed instructions.

To install ETCD on a Linux system, use the following commands:

```bash
wget https://github.com/etcd-io/etcd/releases/download/v3.5.17/etcd-v3.5.17-linux-amd64.tar.gz

tar -xvf etcd-v3.5.17-linux-amd64.tar.gz
mv etcd-v3.5.17-linux-amd64 etcd
cd etcd && ./etcd
```

> **Note**: This is the method I used to install ETCD on my Linux machine.

### Operating ETCD

- To put a key-value pair: `./etcdctl put key value`
- To retrieve a value by key: `./etcdctl get key`
- To check the version: `./etcdctl version`

    ```
    etcdctl version: 3.5.17
    API version: 3.5
    ```
