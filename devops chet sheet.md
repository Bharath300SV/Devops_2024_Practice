
	to download httpd server
	 #yum install httpd -y
	 
	to start & enable http service
	 #systemctl start httpd
	 #systemctl enable httpd
	 
	to launch a static website move the static website which you have downloaded from the internet
	 #mv home/ec2-user/tomcat/neogym-html/* /var/www/html/
	 
	1st to download java-11 in EC2 instance
	 #yum install java-11 -y
	
	to download tomcat in EC2 instance
	 #wget tomcat web link
	 
	follow the steps to install tomcat server
	 #tar -xvf tomactfilename
	 
	edit the context.xml to change the permission
	 #cd /home/ec2-user/tomcat/apache-tomcat-8.5.99/webapps/host-manager/META-INF
	 #vi context.xml (comment the below lines in the context.xml file)
	  <!-- <Valve className="org.apache.catalina.valves.RemoteAddrValve"
			allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->

	 #cd /home/ec2-user/tomcat/apache-tomcat-8.5.99/webapps/manager/META-INF
	 #vi context.xml (comment the below lines in the context.xml file)
	 
	  <!-- <Valve className="org.apache.catalina.valves.RemoteAddrValve"
			allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->
			
	 #cd /home/ec2-user/tomcat/apache-tomcat-8.5.99/conf
	 #vi tomcat-users.xml	
		<role rolename="manager-gui"/>
		<role rolename="manager-script"/>
		<role rolename="manager-jmx"/>
		<role rolename="manager-status"/>
		<user username="admin" password="admin" roles="manager-gui, manager-script, manager-jmx, manager-status"/>
		<user username="deployer" password="deployer" roles="manager-script"/>
		<user username="tomcat" password="s3cret" roles="manager-gui"/>

	to start tomcat service eneter the below command in root user mode
	 #/home/ec2-user/tomcat/apache-tomcat-8.5.99/bin/startup.sh
	 
	to stop tomcat service eneter the below command in root user mode
	 #/home/ec2-user/tomcat/apache-tomcat-8.5.99/bin/shutdonw.sh
	 
	to change the tomcat port
	 #cd /home/ec2-user/tomcat/apache-tomcat-8.5.99/conf/
	 vi server.xml
	 Port=8081
	 
	to install docker
	 #yum install docker -y
	 #systemctl start docker
	 #systemctl enable docker
	 
	to install tomact with help to docker container
	 #docker run -p 8080:80808 tomcat:9.0
	 
	to check which all are the container running in the ec2-user/tomcat/apache-tomcat
	 #docker ps
	 
	to see all the container status in the ec2 machine docker status
	 #docker ps -a
	
	to install jekins using the docker
	 #docker run -p 8081:8080 -p 50000:50000 jenkins/jenkins:lts -y
	 
	to login to container
	 #docker exec -it container-id /bin/bash
	 
	to pull the image from docker
	 #docker pull 'image-name'
	 
	to see the docker list of images
	 #docker images
			OR
	 #docker image ls
	 
	to run the docker image
	 #docker run 'image-name'
	 
	to run the httpd in docker image
	 #docker run -d -p 80:80 httpd
	 
	to run the tomcat in docker image
	 #docker run -d --name mytomcat3 -p 8081:8080 tomcat
	 
	to delete the docker specific image
	 #docker rmi <image-id>
			OR
	 #docker image rm <image-name>
	
	to delete the docker image forcefully
	 #docker rmi -f <image-id>
	 
	to delete all the docker container available in your machine
	 #docker rm -f (docker ps -a | awk '{print $1}')
	
	to run the ubuntu in docker image
	 #dockeer run -it ubuntu
	 
	to connect aws cli via desktop cli promt
	 #aws configure
		AWS Access Key ID [****************I2GN]: AKIATRI2C6HNLMZLI2GN/access key id
		AWS Secret Access Key [****************V/3e]: /V5KXEysj+9P0Q1xGxyOI6XNoxjZhrzjox06V/3e/access secret key
		Default region name [ap-south-1]: ap-south-1
		Default output format [json]: json
		
		aws configure set aws_access_key_id AKIATRI2C6HNP4MC2C7J;
		aws configure set aws_secret_access_key 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;
		aws configure set default.region ap-south-1;
		aws configure set default.output json;
	
	 
	to fetch the kubernetes cluster configuration from AWS vai desktop cli promt
	 #aws eks --region ap-south-1 update-kubeconfig --name kubernetes-name/eks-devops-demo
	 
	to view the kubernetes cluster details 
	 #kubectl config view
	 
	to view the kubernetes service running
	 #kubectl get svc
	 
	to check the number of nodes
	 #kubectl get nodes
	 
	to check the number of pods
	 #kubectl get pods
	 
	to get the specific pod details
	 #kubectl describe pod pod-name	
	 
	to check the status of the kubernetes cluster 
	 #aws eks --region ap-south-1 describe-cluster --name eks-devops-demo --query cluster.status
	 
	to launch a html web page download yaml from internet & chnage the file as per requirenement
	
	to creat the html container
	 before that go to yaml file loaction and then execute the command
	 #kubectl apply -f filename
	 
	to check which pod is running and the detailed details
	 #kubectl get pods --output=wide
	 
	to delete the pods
	 #kubeectl delete pod name/eks-devops-demo
	 
	to check how many relica is activated in pod
	 #kubectl get rs
	 
	to check the website source of the pod
	 #kubectl get deployment
	 
	to expose the pod port which have been created with container
	 #kubectl expose deployment websitename-deployment --type=NodePort
	 
	to delete the exposed service Node Port
	 #kubectl delete service websitename-deployment
	 	 
	to delete all the pods
	 #kubectl delete pods --all
	
	to delete the deployment 
	 #kubectl delete deployment websitename-deployment
	 
	to install Ansible
	 #yum install ansible
	 
	next generate ssh key in the ansible server and then copy that id_ras.pub key to node/host server whch is to be added to cluster 
	 #sudo su (become root)
	 #cd /root/.ssh/
	 #ssh-keygen
	 #cd /root/.ssh/
	 ls
	 id_rsa id_rsa.pub
	 cat id_rsa.pub
	 copy the content of id_rsa.pub file..
	 
	next login to host/node server
	 #sudo su (brcome root)
	 #cd .ssh/
	 ls
	 authorized.ssh
	 #vi authorized.ssh
	 paste the id_rsa.pub content to authorized.ssh file
	
	next login to ansible server and all the host server to file /etc/ansible/
	 #cd /etc/ansible/
	 #vi hosts
	  Sevrer-1
	  ip-1
	  
	  Server-2
	  ip-2
	  ip-3
	 then save the file
	 
	to check the disk partition of all the host server from ansible server
	 #ansible all -i hosts -m shell -a "df -h"
	 
	to check the ping status of all the server
	 #ansible -m ping all
	 
	to run an ansible playbook
	 #ansible-playbook -i hosts file.yml
		eg: 1 #ansible-playbook -i hosts httpd_start.yml
			2 #ansible-playbook -i hosts docker.yml
    
	