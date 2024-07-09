## Set-User-Pass-ELK

sudo systemctl stop elasticsearch

Open the elasticsearch.yml configuration file, usually located in /etc/elasticsearch/ or config/ directory.


# Add the following lines to enable security features:
----
xpack.security.enabled: true
xpack.security.transport.ssl.enabled: true  ---optional

# Create Passwords for Built-In Users

# Run the following command to set passwords for the built-in users:
  
-----
   /usr/share/elasticsearch/bin/elasticsearch-setup-passwords interactive
   /usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic

   
    
# Follow the prompts to set passwords for the various users, such as elastic, kibana_system, and others.


 # Edit the Kibana Configuration
 
Open the kibana.yml configuration file, usually located in /etc/kibana/ or config/ directory.

# Add the following lines to enable security features:
    
    elasticsearch.username: "kibana_system"
    elasticsearch.password: "<kibana_system_password>"
    xpack.security.enabled: true
    sudo systemctl restart kibana.service
    sudo systemctl start elasticsearch.service


# test 
  curl -u elastic:<new_password> http://172.0.0.1:9200/_security/_authenticate?pretty
  curl -X GET "localhost:9200/?pretty"


# Reset the Password Using Alternative Method (If Cluster Health is Good)
   curl -X POST "localhost:9200/_security/user/elastic/_password" -H "Content-Type: application/json" -d '{
     "password" : "new_password"
    }'





