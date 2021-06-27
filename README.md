# Creating-ReplicaSets-with-YAML-K8
A ReplicaSet's purpose is to maintain a stable set of replica Pods running at any given time.

## Simple example to ReplicaSets in Declarative method with YAML
Steps followed-
*As Root*
```

1. Create the YAML file
vim replicaSet.yaml

Type the following YAML

apiVersion: apps/v1
kind: ReplicaSet
metadata:
        name: frontend
spec:
  replicas: 1
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      name: myPod
      labels:
        app: myapp
    spec:
      containers:
      - name: mycontainer
        image: nginx
        ports:
        - containerPort: 80 
        
2. Run the YAML file
kubectl apply -f replicaSet.yaml

3. Checkout the Pod created.
kubectl get pods -o wide

4. Delete the Pod created through replicaSet.yaml
kubectl delete pod <Pod name>

5. Check if replica Pod is created.
kubectl get pods -o wide

 
 ```
*As Root*
