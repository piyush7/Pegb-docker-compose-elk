1. Run the command - docker-compose up.  (If you are using docker-on-mac or similar docker running on local laptop,  increase the docker VM size from default 2 GB to atleast 4 GB or more or else elasticsearch container gets OOM killed with status code 137)

2. You should be able to access the Kibana UI by using - http://0.0.0.0:5601/


### Convert docker-compose to Kubernetes objects

We can use kompose to convert docker-compose file to Kubernetes objects.


- To convert the docker-compose file to Kubernetes objects, download kompose and install it  as per  the steps mentioned  (https://kubernetes.io/docs/tasks/configure-pod-container/translate-compose-kubernetes/ )

-  Then, run the command - kompose convert

You should get Kubernetes objects such as deployments,Statefulsets, services, configmaps, secrets etc. created as per the docker-compose file. ( I am unable to run this currently because kompose is taking a long time to get downloaded)



Depending upon the need to have this cluster have internal or external access, we can change the service types of services like Kibana ( to access the Kibana UI) to node Port or loadbalancer, similarly you can create persistent volumes and persistent volume claims to store the elastic search data. 

We can volume classes that support Snapshot and dynamic expansion of volumes to create snapshots and expansion of volumes that hold elasticsearch data. 

