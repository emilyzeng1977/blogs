## NodePort
将服务的类型设置成NodePort
- 每个集群节点在节点本身（因此得名叫NodePort)上打开一个端口，并将在该端口上接收到的流量重定向到一个Service, 该Service仅在内部集群可访问。

### Create Service YAML file
```markdown
kubectl expose deployment deploy-nginx-demo --name=service-nginx-demo --port=9090 --target-port=80 --type=NodePort -o yaml --dry-run=client > service-nginx-demo.yaml
```
```markdown
1. deploy-nginx-demo 为指定的service对象名称
2. --port指定集群内部访问的端口service端口
3. --target-port指定容器内跑服务的端口
4. --type=NodePort 指定类型 集群外部访问
5. –dry-run表示测试不在k8s运行（不会具体执行该命令）
6. -o yaml 生成yaml格式
7. 最后面的 “> deploy.yaml” 表示将生成yaml内容输出到deploy.yaml文件
```

```markdown
# kubectl get services
NAME                 TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE   SELECTOR
service-nginx-demo   NodePort    10.110.134.218   <none>        9090:32374/TCP   10h   app=deploy-nginx-demo

[root@master3 vagrant]# kubectl describe svc ser
Name:                     service-nginx-demo
Namespace:                default
Labels:                   app=deploy-nginx-demo
Annotations:              <none>
Selector:                 app=deploy-nginx-demo
Type:                     NodePort
IP Families:              <none>
IP:                       10.110.134.218
IPs:                      <none>
Port:                     <unset>  9090/TCP
TargetPort:               80/TCP
NodePort:                 <unset>  32374/TCP
Endpoints:                10.244.1.16:80 ???
Session Affinity:         None
External Traffic Policy:  Cluster
Events:                   <none>
```
### k8s集群内外的访问方式
```markdown
NodeIP:NodePort             // 通过这个方法可以在k8s集群外访问
POD IP:80                   // 只能在POD内部访问
Service Cluster IP:port     // 只能在POD内部访问，解决POD IP变化问题
Endpoints                   // 只能在POD内部访问，解决POD IP变化问题
```
