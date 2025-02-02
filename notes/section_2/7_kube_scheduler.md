# Kube Scheduler

Video Link: <https://udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/14298430#content>

## Notes

- The scheduler determines which nodes to assign pods to based on resource availability.
- It operates in two phases:
  - **Filtering**: Excludes nodes that do not meet the pod's requirements (e.g., insufficient CPU or memory).
  - **Scoring**: Ranks the remaining nodes to find the optimal placement for the pod, scoring them from 0 to 10.
- The scheduler can be customized, or you can implement your own scheduler if needed.
