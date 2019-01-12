# create cluster roles
kubectl create clusterrole psp-default --verb=use --resource=podsecuritypolicies --resource-name=default
kubectl create clusterrole psp-privileged --verb=use --resource=podsecuritypolicies --resource-name=privileged

# bind the psp-default ClusterRole to all authenticated users, not only to Alice
kubectl create clusterrolebinding psp-all-users --clusterrole=psp-default --group=system:authenticated

# bind psp-privileged ClusterRole only to Bob
kubectl create clusterrolebinding psp-bob --clusterrole=psp-privileged --user=bob
# As an authenticated user, Alice should now have access to the default PodSecurityPolicy
# whereas Bob should have access to both the default and the privileged PodSecurityPolicies

