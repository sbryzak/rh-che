These definition files allow quotas to be set in a local minishift environment that mimic the quotas available on the free-int cluster.

To apply the quotas:

1. Login as the system user:

  oc login -u system:admin
  
2. Apply the quotas:

  oc create -f compute-resources.yaml -n eclipse-che
  oc create -f compute-resources-time-bound.yaml -n eclipse-che
  oc create -f object-counts.yaml -n eclipse-che
  oc create -f limitrange.yaml -n eclipse-che
  
3. Finished!


To list quotas assigned to the eclipse-che project:
 
shane@shane-ThinkPad-W541:~/project/che-workspace/quotas$ oc get quota -n eclipse-che
NAME                           AGE
compute-resources              27m
compute-resources-time-bound   27m
object-counts                  53m
  
  
To delete all of the assigned quotas, use "oc delete quota <quota-name> -n eclipse-che", eg:

  oc delete quota compute-resources -n eclipse-che
  oc delete quota compute-resources-time-bound -n eclipse-che
  oc delete quota object-counts -n eclipse-che
  oc delete quota limit  

To list the configured limitranges:

  oc get limitranges
  
To delete the limitranges:  
  
  oc delete limitranges resource-limits -n eclipse-che