## Others
http://www.mydlq.club/article/78/
https://www.zze.xyz/archives/linux-update-kernel.html

https://kubernetes.io/docs/tasks/administer-cluster/dns-debugging-resolution/


### 02 Task
#### cordon

```markdown
kubectl cordon node's name
```
#### drain
- 用于从某个节点安全逐出所有的Pods(即运行安全的终止该节点中的所有Pod)
- 通常用于在对节点执行维护之前执行
- 
https://kubernetes.io/zh/docs/tasks/administer-cluster/safely-drain-node/
```markdown
kubectl drain node's name --delete-local-data --ignore-daemonsets --force
```
