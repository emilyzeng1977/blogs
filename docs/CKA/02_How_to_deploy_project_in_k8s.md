## How to deploy a project in k8s
我们可以在k8s上创建一个Pod对象来运行我们的项目。k8s的最小调度单位是Pod，Pod是一组容器。
但是通常我们不会单独创建一个Pod对象，而是通过Deployment来管理Pod。

### Why we use Deployment instead of creating Pod directly
为什么一般不单独创建Pod对象呢？
因为单独创建的pod对象，如果挂掉是不会被k8s感知和重启的。
创建Deployment对象可以管理pod对象，如果pod挂掉了，则Deployment对象会再重新拷贝一个pod的副本出来。

### An example YAML
```markdown
# pod的最基础的yaml文件最少需要以下的几个参数
apiVersion: v1 # API版本号，注意：具有多个，不同的对象可能会使用不同API
kind: Pod  # 对象类型，pod
metadata:  # 元数据
  name: string # POD名称
  namespace: string # 所属的命名空间
spec: # specification of the resource content(资源内容的规范)
  containers: # 容器列表
    - name: string # 容器名称
      image: string # 容器镜像
```

#### Pod
```markdown
kubectl run nginx-demo --image=nginx --dry-run=client -o yaml  > pod-nginx-demo.yaml
```
#### Deployment
```markdown
kubectl create deployment deploy-nginx-demo --image=nginx --dry-run=client -o yaml  > deploy-nginx-demo.yaml
```
