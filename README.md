#Kubernetes is a platform that helps us to manage containerized applications, making it easier to scale and handle complex setups. 
-A very powerful aspect of Kubernetes is the way it allows different pods to communicate with each other within a cluster.

-There are three different ways: 

1- #Using_Service_Pod_IP_Addresses: 
-we can connect pods by directly using their services IP addresses. 
-To find the IP address of a pod service, run “kubectl get services” . 
-After getting the IP, we can manually configure the application code to use it by using environment variables and to hard-code the IP value in the kubernetes deployment file, which means we will need to update it if the IP changes in case a service deleted and reapplied.
#NOTE: we shouldn't use pod IP address "kubectl get pods -o wide" as if pods fail and restart the IP_address will change so insteade we use the service IP_address that is fixed to the pod. 

2- #Using_Kubernetes_Environment_Variables:
-Kubernetes can automatically generate environment variables for our pods services. These variables contain the necessary information for connecting between pods services. 
-So simply reference these variables in the application code is all what is needed without the need to manually configure them in the kubernetes deployment file.

3- #Using_Domain_Names:
-Another way to connect pods is by using domain names, which Kubernetes automatically generates for services. These domain names are only known within kubernetes cluster and provide a more readable and amazing way to connect pods. This is often a preferred method as it avoids the complexities of dealing with IP addresses.
-It need to be configured in both the Application code as an environment variable and in the kubernetes development file in a specific context as in the attached project code.

-And as this way is the most common way used in pod-pod connections 
-So I want to share with you my #project in which I use #kubernetes to manage and orchestrate containers and I used kubernetes Domain Names and Kubernetes Environment Variables both to allow pod-pod connections. 

-It is a nodeJS application that based on 3 main components:
-users code: allow to signup "using kubernetes Domain Names" and login "using Kubernetes Environment Variables" by configuring email and password.
-auth code: that return back a token after login in.
-tasks code: that allow for configuring tasks and storing it in tasks.txt in tasks folder "using kubernetes Domain Names". 

Note: 
-It’s important to mention that users service as well as tasks service are accessible through the internet using #Service_LoadBalancer type while auth code isn’t it’s only accessible inside the cluster using #Service_ClusterIP type.
-That’s way you will find the service type is different between the users/tasks and auth service object.
-With the help of the amazing client tool #Postman I checked out my code and it was a great experience.

Hope that is helpful ✌️
