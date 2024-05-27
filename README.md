

# Step by Step Deploying Dockerized Laravel in AWS

## AWS Services
<ul>
  <li>AWS EC2 Instance</li>
  <li>AWS RDS</li>
</ul>

## AWS RDS

<ol>
  <li>
    Search Amazon RDS in AWS Console then press the service.
  </li>
  <ul>
    <li>Press Create Database</li>
    <li>Choose a database creation method: <b>Standard Create</b></li>
    <li>Engine Option: <b>MySQL (This will depend on your database development)</b></li>
    <li>Templates: <b>Production</b></li>
    <li>Settings:</li>
      <ul>
        <li>DB cluster identifier: Depending on your database name</li>
        <li>Credential Settings: Depends on your preference</li>
      </ul>
    <li>Cluster storage configuration - new: <b>Aurora Standard</b></li>
    <li>Instance configuration: Depends on the CPU and RAM you need to your project</li>
    <li>Availability & durability: <b>Create an Aurora Replica </b></li>
    <li>Connectivity: Maintain all default except for <b>Public Access - Yes</b></li>
  </ul>
  <li><b>Create Database</b></li>
  <li>Open your MySQL Workbench (If you use other Database Software)</li>
  <li>Connect your Endpoint generated in AWS RDS and put to MySQL Workbench</li>
  <img src="https://raw.githubusercontent.com/TianMeds/image--stocks-for-coding/main/image_2024-05-26_200106290.png"/>
  <ul>
    <li>Connection Name: DB Name that you want</li>
    <li>Connection Method: Standard (TCP/IP)</li>
    <li>HostName: IP Address in the AWS RDS if not working get the Endpoint in RDS </li>
    <li>Username & Password : What you input in the RDS before creating the database</li>
  </ul>
  <li>Test Connection now and should be able to have a connection with RDS and MySQL Workbench</li>
  <li>Test the IP Address using Postman or You can now insert data in that database</li>
</ol>

## AWS EC2 Instance

<ol>
  <li>
    Search EC2 in AWS and press the Launch Instance
  </li>
  <ul>
    <li>Name and Tags: Backend-Server</li>
    <li>Application and OS Images (Amazon Machine Image): <b>Debian</b> and the rest make it default</li>
    <li>Instance type: <b>t.2.micro</b></li>
    <li>Key pair (login) <b>Create a new key pair and this will be downloaded to your system</b></li>
    <i>Note: this key pair will be used in your local system later so make sure to put that in the Local Linux system of your file</i>
    <li>Make sure to maintain it all default as is </li>
  </ul>
  <li>Press Launch Instance below now and wait the status to be Available and 2/2 status checked in the Instance Dashboard</li>
  <li>Press the Instance you created and press Connect</li>
  <li>You will be redirect to a new page and press the SSH Client there and copy the SSH with your keypair its stated below there</li>
  <br/>
  <img src="https://raw.githubusercontent.com/TianMeds/image--stocks-for-coding/main/SSH-CLIENT.png"/>

  <li>You can now go to your linux for mine i use Debian so i'll open Debian in my system</li>
  <li>Make sure to install these before cloning your Repo</li>
  <ul>
    <li>Git</li>
    <li>Docker</li>
    <li>Docker-compose</li>
    <li>PHP</li>
  </ul>
  <li>
    <br/>

    cd /var/www

  </li>


  <li>Now clone your Repo and the file structure be like this</li>
  <br/>
  <img src="https://raw.githubusercontent.com/TianMeds/image--stocks-for-coding/main/Repo%20Structure.png"/>

  ```
    git clone https://github.com/TianMeds/GJJSP.git
```

  <i>Note: This is the file structure looks like:  One Parent Folder -> One Folder for the whole project or the Laravel</i>
  <li>Now lets clone also laradock</li>

  ```
  git clone https://github.com/Laradock/laradock.git
  ```

  <li>First, lets move all the way to the root folder of the VM</li>
  
 
    sudo rm -rf gjjsp-frontend
    ls
    sudo mv gjjsp-backend ../
    ls
    cd ..
    ls
    sudo rm -rf GJJSP-SIS
    ls 
    sudo cp gjjsp-backend gjjsp-backend2
    sudo cp gjjsp-backend gjjsp
    sudo cp -r gjjsp-backend gjjsp 
    sudo rm -rf gjjsp-backend
    cd gjjsp
    sudo mv gjjsp-backend ../
    cd ..
    sudo rm -rf gjjsp
    cd gjjsp-backend


<i>Note: Please make sure that your file is in the root folder of the VM it should look like this</i>
<br/>
<img src="https://raw.githubusercontent.com/TianMeds/image--stocks-for-coding/main/FileStructureinVM.png"/>
<li>After now change the .env of laravel file and laradock file</li>    

```
sudo cp .env.example .env
```

<li>Then configure the database connection and other things in your both .env</li>
<li>Then run the docker in the laradock folder</li>
  
  ```
  docker-compose up -d nginx
  ```
<li>Configure your NGINX in the laradock folder</li>

```
1. Open /nginx/sites/
2. Duplicate laravel.conf.example
3. Rename the duplicate to `your-project-name`.conf
4. Change these Lines 18-19
		server_name `Your IP-Address`; // add that to your machines /etc/hosts
    root /var/www/`your-project-name`/public;
```

<li>Now redirect or cd your-project-folder </li>

```
cd your-project-folder
composer install
```


<li>Now lets hop on the Issues so if you check now your folder its either one of these two what will you experience</li>
<ul>
  <li>404 not found:: Can’t access the static laravel front-end </li>
  <p>Make sure your in the laradock folder to run this</p>
  <br/>
  <img src="https://raw.githubusercontent.com/TianMeds/image--stocks-for-coding/main/image_2024-05-27_205905308.png"/>

<p><b>Solution: </b></p>

  ```
    docker-compose exec workspace chmod -R 755
  ```
<li>The stream or file "/storage/logs/laravel.log" could not be opened in append mode: failed to open stream: Permission denied</li>
<p>Make sure now that your in the project folder</p>
<br/>
<img src="https://raw.githubusercontent.com/TianMeds/image--stocks-for-coding/main/image_2024-05-27_210856810.png"/>

<p><b>Solution: </b></p>

```
sudo chmod -R ugo+rw storage
```


</ul>

<li>Now to make sure now that it is working you want to search for the IP you have in your browser and should output like this</li>

<img src="https://raw.githubusercontent.com/TianMeds/image--stocks-for-coding/main/image_2024-05-27_211235181.png"/>

</ol>

