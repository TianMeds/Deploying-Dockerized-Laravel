

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
```bash
   cd /var/www
    ```
  </li>
  <li>Now clone your Repo and the file structure be like this</li>
  <br/>
  <img src="https://raw.githubusercontent.com/TianMeds/image--stocks-for-coding/main/Repo%20Structure.png"/>
  <i>Note: This is the file structure looks like:  One Parent Folder -> One Folder for the whole project or the Laravel</i>
  <li>Now lets clone also laradock</li>

  
</ol>

