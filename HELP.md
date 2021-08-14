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
 

 k config set-context ${k config current-context} --namespace=prod

 kubectl create deployment --image=nginx nginx --dry-run -o yaml

 ns 

 --no-headers | wc l

 kubectl create deployment nginx --image=nginx --replicas=4

 kubectl scale deployment nginx --replicas=4

 kubectl expose pod redis --port=6379 --name redis-service --dry-run=client -o yaml

 kubectl expose pod nginx --port=80 --name nginx-service --type=NodePort --dry-run=client -o yaml

 kubectl create service clusterip redis --tcp=6379:6379 --dry-run=client -o yaml
 kubectl create service nodeport nginx --tcp=80:80 --node-port=30080 --dry-run=client -o yaml

 kubectl create deployment webapp --image=kodekloud/webapp-color --replicas=3

kubectl run custom-nginx --image=nginx --port=8080

k run httpd --image=httpd --port:80 --expose 



kubectl get pod nginx -o yaml > output.yaml m

kubectl explain pods --recursive | grep 


kubectl describe node node01 | grep -i taints

Create a taint on node01 with key of spray, value of mortein and effect of NoSchedule
kubectl taint nodes node01 spray=mortein:NoSchedule


apiVersion: v1
kind: Pod
metadata:
  name: bee
spec:
  containers:
  - image: nginx
    name: bee
  tolerations:
  - key: spray
    value: mortein
    effect: NoSchedule
    operator: Equal


kubectl taint nodes controlplane node-role.kubernetes.io/master:NoSchedule-

kubectl label node node01 color=blue


k get nodes node1 --show-labels

k get pods -o wide

k get deplouments blue -o u=yaml > xxx.yml


apiVersion: v1
kind: Pod
metadata:
  name: yellow
spec:
  containers:
  - name: lemon
    image: busybox
    command:
      - sleep
      - "1000"

  - name: gold
    image: redis



kubectl -n elastic-stack logs kibana

kubectl describe pod app -n elastic-stack

kubectl -n elastic-stack exec -it app -- cat /log/app.log



apiVersion: v1
kind: Pod
metadata:
  name: app
  namespace: elastic-stack
  labels:
    name: app
spec:
  containers:
  - name: app
    image: kodekloud/event-simulator
    volumeMounts:
    - mountPath: /log
      name: log-volume

  - name: sidecar
    image: kodekloud/filebeat-configured
    volumeMounts:
    - mountPath: /var/log/event-simulator/
      name: log-volume

  volumes:
  - name: log-volume
    hostPath:
      # directory location on host
      path: /var/log/webapp
      # this field is optional
      type: DirectoryOrCreate



for i in {1..20}; do
  kubectl exec --namespace=kube-public curl -- sh -c 'test=`wget -qO- -T 2  http://webapp-service.default.svc.cluster.local:8080/ready 2>&1` && echo "$test OK" || echo "Failed"';
  echo ""