# simulate how resource request works in scheduler on k8s
kubectl apply -f requests-pods.yaml
kubectl run requests-pod-2 --image=busybox --restart Never --requests='cpu=800m,memory=20Mi' -- dd if=/dev/zero of=/dev/null
kubectl run requests-pod-3 --image=busybox --restart Never --requests='cpu=1,memory=20Mi' -- dd if=/dev/zero of=/dev/null
kubectl describe po requests-pod-3
kubectl describe nodes
# you should be able to schedule pod-3
kubectl delete po requests-pod-2