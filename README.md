# RSHomework
Set up a TSDB with Influxdb and graph it with Grafana using Docker

BEFORE WE START. Install docker on your machine. 
            
            sudo apt-get install docker-engine -y
            
 Start docker and run "hello world" to test if it's set up properly.
 
            sudo service docker start
            sudo docker run hello-world


## To Run this file 
1. Clone this repository to your local machine. 
2. Open a terminal and and navigate to your copy of this repository
3. execute:
                 
                 $ docker-compose up -d

### Influxdb admin page
  
    http://localhost:8083
  
    login: root
    passwd: root
    host: localhost
    port: 8086
    
    Database: Collectd
  
  Use Query Templates to navigate data


### Grafana login page

  http://localhost:3000

    login: admin
    passwd: admin  
  
## To visualize data... 
 
 ### a. add data source
  
      name: (any name goes here)
      type: influxDB
      URL: http://influxdb:8086
      Access: proxy
      Database: collectd
    
  Save and test if source is working
   
  ### b. Navigate back to home and find the "create new Dashboard" button. 
     From the tab located on the left select "Add Panel" --> "Graph"
     
  ### c. Name the panel as you like, and navigate to the "Metrics" tab.
     For Metric "A"
     
        From: default XXX
        Where: type_instance = used
        Select: field(value) mean()
        Group By: time($interval) fill(null(
        Alias By: used 
        Format as: Time series
        
        Panel data sourecd: influxdb
   
   ### d. Navigate to the Axes tab and change the unit to XXX.
   
   ### e. select "Back to dashboard" and analyze away!
   
  
  

