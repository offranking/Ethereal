Static Website Using Nginx as Load Balancer

This project demonstrates how to deploy a static HTML website** using **Nginx** as a Layer 7 Load Balancer**, with domain resolution via DuckDNS and server hosting on **AWS EC2**. SSL was configured using Let's Encrypt.


##Tech Stack
- AWS EC2 (Ubuntu Server)**
- Nginx
- DuckDNS (Free Dynamic DNS)**
- Let's Encrypt (SSL via Certbot)**
- SCP (Secure Copy Protocol)**
- DIG (DNS Lookup)
- OpenSSL (SSL Verification)


##Steps Followed

### 1. Domain Registration
- Created a subdomain using [DuckDNS] https://boyals.duckdns.org


###2. Server Setup on AWS
- Launched an Ubuntu EC2 instance on AWS.
- Assigned an Elastic IP to ensure a static public IP.
- SSH'd into the instance:
  ```bash
  ssh ubuntu@<your-elastic-ip>

###3.  Installed Nginx
- sudo apt update
- sudo apt install nginx -y

###4. Deployed Static Website /Ethereal
scp -r ./Ethereal ubuntu@<elastic-ip>:/var/www/html

### 5. Verified Website via IP
http://<elastic-ip>

###6. DNS Configuration with DuckDNS
- Created an A record on DuckDNS pointing to the Elastic IP.
-  Verified DNS record using:
boyals.duckdns.org

###7. SSL Setup with Let's Encrypt
sudo apt install certbot python3-certbot-nginx -y
sudo certbot --nginx -d boyals.duckdns.org

###8. SSL Certificate Validation
openssl s_client -connect boyals.duckdns.org:443







