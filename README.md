# load-balancer-solution-with-apache


To deploy and configure Apache Load balancer for DevOps Tooling Website solution on a separate Ubuntu EC2 instance and ensuring users can be served by the web servers through the load balancer

### PREREQUISITES

1. TEO RHEL 8 Web servers
   
2. One MySQL DB server ( based on Ubuntu 20.04)

3. One RHEL 8 NFS server



   ![image](https://github.com/user-attachments/assets/f25a4a61-68af-4560-8893-00443a8a0e72)



 ###  Configure Apache as a Load Balancer
 
Create an EC2 Instance
First, we create an Ubuntu Server 20.04 EC2 instance and name it `Project-8-apache-lb`. This will serve as our load balancer.

![image](https://github.com/user-attachments/assets/ab162804-0376-4503-a44c-976fb9098fba)


Open TCP Port 80 
Next, we open TCP port 80 on our `Project-8-apache-lb` instance by creating an inbound rule in the security group to allow HTTP traffic.

![image](https://github.com/user-attachments/assets/3bc421cb-5815-4f63-814b-c796eb4b1240)


Install Apache Load Balancer
After setting up the instance, we install Apache on the Project-8-apache-lb server and configure it to distribute incoming traffic to both web servers. Follow these steps:

- Update the package list and install Apache
  
       sudo apt update
       sudo apt install apache2 -y

![image](https://github.com/user-attachments/assets/608bef6c-4d03-40d7-a8bc-077e7c8ef5d8)


- Install necessary development libraries
  
      sudo apt-get install libxml2-dev
  

![image](https://github.com/user-attachments/assets/79accb13-91b9-430a-808f-398fa4b961f5)
  

- Enable the following Apache modules for load balancing

  

       sudo a2enmod rewrite
       sudo a2enmod proxy
       sudo a2enmod proxy_balancer
       sudo a2enmod proxy_http
       sudo a2enmod headers
       sudo a2enmod lbmethod_bytraffic


- Restart Apache to apply the changes

       sudo systemctl restart apache2

  

   


   
