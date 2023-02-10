# minikube

minikube quickly sets up a local Kubernetes cluster on macOS, Linux, and Windows. We proudly focus on helping application developers and new Kubernetes users.

## 常用命令

**我从以前的笔记里拿出来的，待整理。**

* minikube start --driver=docker
* minikube start
* minikube delete && minikube start --driver=docker

* kubectl --help
* kubectl controls the Kubernetes cluster manager.

* minikube dashboard
  * 图形用户界面

* kubectl cluster-info
  * 获取集群信息
* kubectl get services
  * 获取服务信息
* kubectl version
* kubectl get services
* kubectl get pods
  * kubectl get po -A
* kubectl describe deployments
* kubectl get events
* kubectl apply -f https://k8s.io/examples/controllers/nginx-deployment.yaml
* kubectl exec -it petclinic -- /bin/sh
* kubectl logs kube-tomcat-6f9b9d4bc-kqln7
* kubectl delete service nginx-service-nodeport
* kubectl create deployment my-demo --image=my-demo --dry-run=client
* kubectl get all -n rulin

## 参考文献

1. [minikube start](https://minikube.sigs.k8s.io/docs/start)
2. [minikube docker](https://minikube.sigs.k8s.io/docs/drivers/docker)
