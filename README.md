## Set-User-Pass-ELK
# Set User-Pass ELK
sudo systemctl stop elasticsearch
Open the elasticsearch.yml configuration file, usually located in /etc/elasticsearch/ or config/ directory.
Add the following lines to enable security features:
xpack.security.enabled: true
xpack.security.transport.ssl.enabled: true  ---optional

# Create Passwords for Built-In Users
    •	Run the following command to set passwords for the built-in users:
      sh
      /usr/share/elasticsearch/bin/elasticsearch-setup-passwords interactive
    •	Follow the prompts to set passwords for the various users, such as elastic, kibana_system, and others.


 # Edit the Kibana Configuration
 
    •	Open the kibana.yml configuration file, usually located in /etc/kibana/ or config/ directory.
    •	Add the following lines to enable security features:
    
    elasticsearch.username: "kibana_system"
    elasticsearch.password: "<kibana_system_password>"
    xpack.security.enabled: true
    sudo systemctl restart kibana.service

