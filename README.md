# Seguranca-de-Redes-
Projeto realizado no contexto da unidade curricular Segurança de Redes 






<h2>Project Description</h2>
<ol>

  <li>Application Server</li>
  <ul>
    <li> MYSQL </li>
    <ul>
      <li>For permanent storing , we used a relational database.</li>
    </ul>
    <li> Nginx </li>
    <ul>
      <li> We used Nginx for dealing with diferent tasks , the most importants to note are:</li>
      <ul>
        <li> Watching streams via the internet. (not relevant for this project)</li>
        <li> Act as a reverse proxy to the main aplication (this allows us to implement some extra securitie features, susch as https, DDOS mitigation, etc...)</li>
        <li>Mediating an ecrypted communication between application's and Application Server (using https).</li>
      </ul>
    </ul>
    <li> Jetty+Jersey </li>
    <ul>
      <li>It's used as a foundation of the Application Server, and it was developed using the maven building tool.</li>
      <li>For each uploaded movie , it generates two versions (360p and 1080p) with the help of ffmpeg.</li>
      <li>It's also responsible for storing information in the Database.</li>
    </ul>
  </ul>
</ol>

<h2>Versions of software used</h2>
<ol>
  <li>Apache Maven 3.6.3</li>
  <li>openjdk version "11.0.20.1" 2023-08-24</li>
  <li>mysql  Ver 8.0.35</li>
  <li>nginx version: nginx/1.20.2</li>
  <li>Postman: 11.2.0 (only used to test some requests)</li>
</ol>


<h2>Download and extract Seguranca-de-Redes.rar</h2>
Firts you need to extract 
<h3>How to run</h3>

<ol>
  	<li>Chosse wich application we want to run </li>
    <li>Go to the directory ../jax-rs/jersey/jersey-jetty/</li>
    <ul>
      <li>$ cd .../jax-rs/jersey/jersey-jetty/</li>
    </ul>
    <li>run the command's:  </li>
  <ul>
    <li>mvn clean package</li>
    <li>java -jar target/jersey-jetty.jar</li>
  </ul>
    
</ol>


<h3> Where are the src files</h3>

<ol>
  <li>Chosse wich application we want to run</li>
  <li>(example for secure app )</li>
  <ul>
    <li> cd ./Seguranca-de-Redes-/secure app/mkyong/jax-rs/jersey/jersey-jetty/src/main/java/com/mkyong
  </ul>
</ol>



<h2>Example requests - "Secure" app (with nginx reverse-proxy and https configured)</h2>

<ol>
  <li>https://localhost/api/connect/all/usr?apiKey=1234567890abcdef</li>
  <ul>
    <li>list all users in database</li>
  </ul>

  <li>Removal of a user (capture in postman)</li>

  ![image](https://github.com/user-attachments/assets/ef14cabb-1797-42cc-a731-269c384dd647)

  <li>Upload of movie (capture in postman)</li>

  ![image](https://github.com/user-attachments/assets/89d83a83-ce0a-4adc-ab47-08f57f54449e)

  <li>curl -X GET "http://localhost:8080/ping/safe/www.google.com"</li>
  <ul>
    makes a ping command to www.google.com
  </ul>
</ol>

<h2>Example requests - UnSecure app </h2>

<ol>
  <li>http://localhost:8080/connect/all/usr</li>
  <ul>
    <li>list all users in database</li>
  </ul>
  <li>SQL injection in user login</li>

  ![image](https://github.com/user-attachments/assets/cf5fb86d-f380-4fec-a665-f4754ff2f285)


  <li>curl -X GET "http://localhost:8080/ping/unsafe/www.google.com&&dir%20~"</li>
  <ul>
    <li>Executes a ping to www.google.com and then list the directories in ~</li>
  </ul>
</ol>



