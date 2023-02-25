# LOAD-BALANCER-SOLUTION-WITH-NGINX-AND-SSL-TLS
In this project we will configure an Nginx Load Balancer solution and also ensure a secured connection using SSL/TLS. The Architecture will look like this:
 
  
 ![ec2](./images/Architecture.png)

------------
____________
### Task
This project consists of two parts:
1. Configure Nginx as a Load Balancer
2. Register a new domain name and configure secured connection using SSL/TLS certificates

-----------
__________
## CONFIGURE NGINX AS A LOAD BALANCER
* Create an EC2 VM based on Ubuntu Server 20.04 LTS and name it Nginx LB (do not forget to open TCP port 80 for HTTP connections, also open TCP port 443 – this port is used for secured HTTPS connections).

 
 ![ec2](./images/nginx%20instance%20image.png)

* Update /etc/hosts file for local DNS with Web Servers’ names (e.g. Web1 and Web2) and their local IP addresses.

   `sudo vi /etc/hosts`

   ![etc-host](./images/etc-hosts.png)

* Install and configure Nginx as a load balancer to point traffic to the resolvable DNS names of the webservers.

      sudo apt update
      sudo apt install nginx


  ![install](./images/install%20nginx.png)

* Configure Nginx LB using Web Servers’ names defined in /etc/hosts.

Configure Nginx LB using Web Servers’ names defined in /etc/hosts. Open the default nginx configuration file
`sudo vi /etc/nginx/nginx.conf`

  ![load balancer](./images/load%20balancer%20config.png))

* Restart Nginx and make sure the service is up and running.

      sudo systemctl restart nginx
      sudo systemctl status nginx
  ![status](./images/restart%20nginx.png)

-----------
___________

## REGISTER A NEW DOMAIN NAME AND CONFIGURE SECURED CONNECTION USING SSL/TLS CERTIFICATES
Make necessary configurations to allow connections to our Tooling Web Solution secured!
In order to get a valid SSL certificate – you need to register a new domain name, you can do it using any Domain name registrar – a company that manages reservation of domain names. The most popular ones are: Godaddy.com, namecheap, WHogohost, Domain.com, Bluehost.com.

* Register a new domain name with any registrar of your choice in any domain zone (e.g. .com, .net, .org, .edu, .info, .online, .xyz or any other).

* Assign an Elastic IP to your Nginx LB server and associate your domain name with this Elastic IP. An Elastic IP is a static IP address that does not change when restart or stop/start your EC2 instance.

  ![elastic ip](./images/elastic%20ip.png)

* Update [A record](https://www.cloudflare.com/learning/dns/dns-records/dns-a-record/) in your registrar to point to Nginx LB using Elastic IP address. Using Route53, perform the following:

    * Create a hosted zone
    * Create records with paramters as shown below
    * In your domain name portal, Update the DNS with values gotten from route 53.

    ![hosted zone](./images/hosted%20zone.png)

    ![records](./images/Load%20balancer%20public%20ip.png)





