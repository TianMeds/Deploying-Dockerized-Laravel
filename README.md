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
    <li>Connectivity: Maintain all default except for <b>Public Access</b></li>
    <li><b>Create Database</b></li>
  </ul>
</ol>


