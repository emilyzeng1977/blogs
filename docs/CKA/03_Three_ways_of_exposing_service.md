## Three ways to expose service
https://blog.csdn.net/qq_21187515/article/details/112363072

```markdown
kubectl expose deployment deploy-nginx-demo --name=service-nginx-demo --port=9090 --target-port=80 --type=NodePort -o yaml --dry-run=client > service-nginx-demo.yaml
```
```markdown
1. deploy-nginx-demo 为指定的service对象名称
2. --port指定集群内部访问的端口 ???
3. --target-port指定容器内跑服务的端口
4. --type=NodePort 指定类型 集群外部访问
5. –dry-run表示测试不在k8s运行（不会具体执行该命令）
6. -o yaml 生成yaml格式
7. 最后面的 “> deploy.yaml” 表示将生成yaml内容输出到deploy.yaml文件
```

```markdown
# kubectl get services
NAME                 TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service-nginx-demo   NodePort    10.99.59.140   <none>        9090:32444/TCP   168m

# kubectl describe svc ser
Name:                     service-nginx-demo
Namespace:                default
Labels:                   app=service-nginx-demo
Selector:                 app=deploy-nginx-demo
Type:                     NodePort
IP Families:              <none>
IP:                       10.99.59.140
IPs:                      10.99.59.140      // ???
Port:                     <unset>  9090/TCP // ???
TargetPort:               80/TCP
NodePort:                 <unset>  32444/TCP
Endpoints:                192.168.1.5:80
```
NodeIP:NodePort
http://10.151.30.22:32444/ 
