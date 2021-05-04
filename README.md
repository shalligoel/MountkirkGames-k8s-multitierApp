# Mountkirk Games Implementation on Google Kubernetes Engine (GKE) 
A WebGL maze game built with Three.js and Box2dWeb. 
Credits & Source from: https://github.com/wwwtyro/Astray

### PHASE - 1: Set up Single Node Kubernetes Cluster on GCE VM for first setting up your application.
1. Create a custom VPC with three subnets, one in usa region, asia region and Europe region. Create appropriate firewall rules.

2. Create a Google Compute Engine (GCE) with following configuration:
a. Machine Type : n1-standard-1
b. Operating System: Ubuntu-20.04
c. Disk Type: Standard Disk
d. Disk-size: 15 GB
e. VPC: Custom
f. External IP Address: Yes
g. Protect VM from Deletion
Use other options of default or your choice.


3. SSH into VM and install following software on VM: <br/><br/>
sudo apt update <br/>
sudo apt install -y git <br/>
sudo apt install -y apache2 <br/>
sudo cd /var/www/html <br/>
git clone https://github.com/shalligoel/MountkirkGames.git <br/>

. Open http://EXTERNAL-IP-GCE/MountkirkGames in your browser
. Enjoy!

4. Now set up Docker and Kubernetes on this VM.





### Phase -2: Setting up simple multi-layer application
   Golden image, instance , instance template, instance group, load balancer ( Refer Dress4win Repository)
