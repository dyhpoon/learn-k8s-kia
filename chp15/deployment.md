apiVersion: extensions/v1beta1
kind: Deployment
metadata:
  name: kubia
spec:
  replicas: 3                    
  template:
    metadata:
      name: kubia
      labels:
        app: kubia
    spec:
      containers:
      - image: luksa/kubia:v1    
        name: nodejs
        resources:              
          requests:             
            cpu: 100m           

# enable horizontal autoscaling
# kubectl autoscale deployment kubia --cpu-percent=30 --min=1 --max=5
# kubectl describe hpa kubia
