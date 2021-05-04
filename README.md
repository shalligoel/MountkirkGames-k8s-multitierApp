# Mountkirk Games Implementation on Google Kubernetes Engine (GKE) 
A WebGL maze game built with Three.js and Box2dWeb. 
Credits & Source from: https://github.com/wwwtyro/Astray

## PHASE - 1: Set up Single Node Kubernetes Cluster on GCE VM for first setting up your application.
#### 1. Create a custom VPC with three subnets, one in usa region, asia region and Europe region. Create appropriate firewall rules.

#### 2. Create a Google Compute Engine (GCE) with following configuration:
a. Machine Type : n1-standard-1 <br>
b. Operating System: Ubuntu-20.04 <br>
c. Disk Type: Standard Disk <br>
d. Disk-size: 15 GB <br>
e. VPC: Custom <br>
f. External IP Address: Yes <br>
g. Protect VM from Deletion <br>
Use other options of default or your choice. <br>

#### 3. SSH into VM and install following software on VM: <br><br/>
sudo apt update <br/>
sudo apt install -y git <br/>
sudo apt install mysql-server
sudo apt install -y apache2 <br/>
#### Set Database on mysql server
a. sudo mysql -uroot -p <br>
#### Create a new user
b. create user 'myuser'@'localhost' identified by 'mypwd';<br>
c. GRANT ALL PRIVILEGES ON *.* to 'myuser'@'localhost;<br>
d. exit<br>
#### Download Source Code From Github
sudo cd /var/www/html <br/>
git clone https://github.com/shalligoel/MountkirkGames.git <br>
Open http://EXTERNAL-IP-GCE/MountkirkGames in your browser <br>
Enjoy!<br>
#### Go Back to terminal and create a database for the next phase.<br>
mysql -umyuser -pmypwd < database.sql<br>
mysql -umyuser -pmypwd<br>
show databases;<br>
use mountkirkGames;<br>
show tables;<br>
select * from users;<br>
#### 4. Now set up Docker and Kubernetes on this VM.





## PHASE -2: Setting up simple multi-layer application<br>

#### 1. Go to simple Web Application Folder<br>
cd MountkirkGames/SimpleApp<br>


