## Three ways to expose service


```markdown
kubectl expose deployment deploy-nginx-demo --name=service-nginx-demo --port=9090 --target-port=80 --type=NodePort -o yaml --dry-run=client > service-nginx-demo.yaml
```

1. countgame 为指定的service对象名称
2. --port指定集群内部访问的端口
3. --target-port指定容器内跑服务的端口
4. --type=NodePort 指定类型 集群外部访问
5. –dry-run表示测试不在k8s运行（不会具体执行该命令）
6. -o yaml 生成yaml格式
7. 最后面的 “> deploy.yaml” 表示将生成yaml内容输出到deploy.yaml文件

