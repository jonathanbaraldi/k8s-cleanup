## k8s-cleanup

3 maneiras de limpar seu cluster kubernetes:

* Limpar containers, imagens, coisas pendentes, volumes, etc. -  DaemonSet (`docker-clean.yml`).
* Limpar replicaset's, jobs, pods, itens não recicládos pelo Kubernetes. CronJob (`k8s-clean.yml`).
* Limpar diretórios não mais usados pelo etcd. CronJob (`etcd-empty-dir-cleanup.yml`).


### Env vars
No Daermonset (`docker-clean.yml`) você pode setar  `DOCKER_CLEAN_INTERVAL` para modificar o intervalo.Padrão é de to 30min (1800s).

No CronJob (`k8s-clean.yml`) você pode setar  `DAYS` para modificar o máximo de idade que as velhas réplicasset podem ter. Padrão é de 7 dias.

### Deployment

```sh
$ kubectl -n kube-system apply -f rbac.yml
$ kubectl -n kube-system apply -f docker-clean.yml
$ kubectl -n kube-system apply -f k8s-clean.yml
$ kubectl -n kube-system apply -f etcd-empty-dir-cleanup.yml
```


## Agradecimentos:


Este repositório é baseado no:
https://github.com/onfido/k8s-cleanup  
Todos méritos a ele que fez. 

Porém tem alguns erros e itens desatualizados, foi corrigido e coloquei a disposição no curso.

https://www.udemy.com/course/devops-mao-na-massa-docker-kubernetes-rancher