# A pod can only be scheduled to a node if it tolerates the node’s taints.
# Taints allow rejecting deployment of pods to certain nodes by only adding taints to the node without having to modify existing pods.

# kubectl taint node dyhpoon2c.mylabserver.com node-type=production:NoSchedule
# kubectl run test --image busybox --replicas 5 -- sleep 99999
