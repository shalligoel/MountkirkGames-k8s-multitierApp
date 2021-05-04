# Mountkirk Games Implementation on Google Kubernetes Engine (GKE) 
A WebGL maze game built with Three.js and Box2dWeb. 
Credits & Source from: https://github.com/wwwtyro/Astray

### Launching
Create a custom VPC with three subnets, one in usa, asia and Europe. Create appropriate firewall rules.

1. Provision a Google Compute Engine (GCE) with Apache Web Server and Git Installed using below startup script. <br/><br/>
apt update <br/>
apt install -y git <br/>
apt install -y apache2 <br/>
cd /var/www/html <br/>
git clone https://github.com/shalligoel/MountkirkGames.git <br/>

2. Open http://EXTERNAL-IP-GCE/MountkirkGames in your browser
3. Enjoy!


Phase -2
   Golden image, instance , instance template, instance group, load balancer ( Refer Dress4win Repository)
