<img src="https://raw.githubusercontent.com/TianMeds/image--stocks-for-coding/main/Laravel-AWS.png" alt="Laravel x AWS" />

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
</ol>


