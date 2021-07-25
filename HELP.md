kubectl run nginx --image=nginx
kubectl describe pod newpods-4z7kp

kubectl get rs 

kubect edit pod redis 

kubectl edit replicaset new-replica-set

kubectl scale rs new-replica-set --replicas=5

kubectl run redis --image=redis --dry-run=client -o yaml > pod.yaml


kubectl create deployment nginx --image=nginx 

 k api-resources

 k get pods --all-namespaces   

 k get namespace

 kubectl scale --replicas=6 -f replicaFile.yaml

 kubectl scale --replicas=6 replicaset app-lables-replicaset

 k get all 

 k set image deployment/myapp-deployment nginx=nginx:1.9.1

 k rollout undo deployment/my-app-deploument

 k rollout status deployment/my-app-deploument

  k set image deployment nginx-deployment nginx-deployment=nginx1.8  

  --record=true


svc = service 

kubectl expose deployment simplewebapp --name=simple-web-app --target-port=8080 --type=NodePort --port=8080 --dry-run=client -o yaml > o.yml
 