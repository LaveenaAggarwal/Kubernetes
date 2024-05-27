KUBERNETES IS EASY | INTRODUCTION TO KUBERNETES

Docker-> Container Platform
Kubernetes-> Container Orchestration Platform
Containers are ephemeral (short living) in nature.

Docker Problems:
1)	Single Host
C1	C2	C3	C40	C50	C60	C70	C80	C90	C100
Docker
Host/Local Machine/ EC2 instance
There is single host, on top of which you install docker, on top of which you created 100 containers.
If c1 is taking too much memory/resources then it will impact other container like c100. C100 will not be created/started or will die (Because it doesn’t have enough resources)
This happens because there is single host.
2)	Auto Healing
If someone killed your container, application running inside container will not be accessible. Unless somebody start this container manually.
In docker, container will not start automatically if it is killed. So, there is auto healing problem as well.
3)	Auto Scaling
Manually you have to create containers when required. We can do it using load balancer which equally distribute the load among containers but this feature is missing in docker. Here Containers will not be automatically created when load will increase.
4)	Docker Doesn’t provide any Enterprise level support
	Load balancer
	Firewall
	Auto Scaling
	Auto Healing
	API Gateway etc.
There all are the enterprise level standards but docker doesn’t support enterprise level standards.

Kubernetes solve all these problems.
By default, Kubernetes is a cluster (Group of nodes).
	Previously we installing docker on one personal laptop/one EC2 instance but in general in production use case Kubernetes installed on master node architecture (one master node and multiple nodes)
	Kubernetes can not be installed on one single node?
We can do it but only in developer environment but in general in production environment Kubernetes is installed as cluster (Group of nodes).
Single Host Problem Solved:
C1	C2	C3	C40	C50	C60	C70	C80	C90	C100
Docker
Host/Local Machine/ EC2 instance

Now in case of Kubernetes if C100 is affected by C1 then Kubernetes will immediately shift C100 from node 1 to node2.
C1	C2	C40	C99	C100	C100				
Node1	Node2
Kubernetes

Auto Healing Problem Solved:
	Healing simply means here is whenever there is a damage Kubernetes control and fix that damage
	There are 1000 reasons due to which container goes down 
	Suppose from any reason one container goes down Kubernetes will start a new container
	In Kubernetes we have API Gateway, when API Gateway receive signal that one container is going down immediately Kubernetes starts a new pod/container.
Auto Scaling Problem Solved:
	Kubernetes has Replica set/Replication controller.
	In Kubernetes everything is in YAML files, so in any of the file like replica_set.yaml file/ Replication_controller.yaml file/ deployment.yaml file and increase replicas from 1 to 10 because traffic is increasing but this is manually procedure.
	Kubernetes also support HPA (Horizontal Pod AutoScaler). It will automatically increase the pod/container when there is a traffic. Like when one container reach threshold 80% just spin up new container.
Enterprise level support Problem Solved:
	Docker is never used in production because it doesn’t support capabilities like auto healing, auto scaling, load balancer, firewall.
	But Kubernetes support all these capabilities.

