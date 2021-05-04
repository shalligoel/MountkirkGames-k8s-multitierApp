# MountkirkGames Implementation on Google Kubernetes Engine(GKE) 
A WebGL maze game built with Three.js and Box2dWeb. 
Credits & Source from: https://github.com/wwwtyro/Astray

## PHASE - 1:<br> Set up Single Node Kubernetes Cluster on GCE VM for first setting up your application.
#### 1. Create a custom VPC with three subnets, one in usa region, asia region and Europe region. Create appropriate firewall rules.
#### 2. Create a Google Compute Engine (GCE) with following configuration:
a. Machine Type : n1-standard-1 <br>
b. Operating System: Ubuntu-20.04 <br>
c. Disk Type: Standard Disk <br>
d. Disk-size: 15 GB <br>
e. VPC: Custom <br>
f. External IP Address: Yes <br>
g. Protect VM from Deletion <br>
Use other options of default or your choice.
#### 3. SSH into VM and install following software on VM: <br>
sudo apt update <br/>
sudo apt install -y git <br/>
sudo apt install mysql-server
sudo apt install -y apache2
#### Set Database on mysql server
a. sudo mysql -uroot -p 
#### Create a new user
b. create user 'myuser'@'localhost' identified by 'mypwd';<br>
c. GRANT ALL PRIVILEGES ON *.* to 'myuser'@'localhost;<br>
d. exit
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
select * from users;
#### 4. Now set up Docker and Kubernetes on this VM.
Reference: https://docs.docker.com/engine/install/ubuntu/<br>
sudo apt-get update<br>
sudo apt-get install apt-transport-https ca-certificates curl gnupg lsb-release<br>
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg<br>
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \\
$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null<br>
sudo apt-get update<br>
sudo apt-get install docker-ce docker-ce-cli containerd.io<br>
#### Verify that Docker Engine is installed correctly by running the hello-world image.
sudo docker run hello-world
### Great!! Docker is installed
#### To create the docker group and add your user:
a. Create the docker group.<br>
 sudo groupadd docker<br>
b. Add your user to the docker group.<br>
sudo usermod -aG docker $USER<br>
c. Log out and log back in so that your group membership is re-evaluated.<br>
d. Verify that you can run docker commands without sudo.<br>
docker run hello-world
## PHASE -2: Setting up simple multi-layer application

#### 1. Go to simple Web Application Folder<br>
cd MountkirkGames/SimpleApp<br>
#### Deploy the Python Flask-Based Frontend<br>
# The frontend is created using a Python based Web framework called Flask. There is a Docker File called Dockerfile that will be used to create Docker image called mkgames in # which the application's source code is imported. The application's code is executed when a container created from that image runs.<br>
#### Run the following command:
docker build -t mkgames:v1 .
#### Run the image in the container
docker run --rm --name mkgames mkgaes:v1


# While creating the Deployment for the frontend, we are passing the name of the MongoDB Service, mongodb, as an environment variable, which is expected by our frontend.
# Notice that in the ports section we mentioned the containerPort 5000, and given it the web-port name. We will be using the referenced web-port name while creating the # # Service for the rsvp application. This is useful, as we can change the underlying containerPort without making any changes to our Service.

kubectl create -f rsvp-web-deployment.yaml

kubectl create -f rsvp-web-service.yaml

Check Out the Available Deployments and Services
kubectl get deployments

kubectl get services

Scale the Frontend
kubectl scale --replicas=4 -f /tmp/rsvp-web.yaml

