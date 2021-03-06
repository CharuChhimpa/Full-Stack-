# Logs Analysis Project

This project contains a news dataset and we have to explore the dataset.

## Prerequisites to run the code
1. Python
2. Virtual Machine
3. Vagrant

## Procedure to run the code
1. Download and Install Virtual Machine on your computer. This is the link to install one :  
    
    https://www.virtualbox.org/wiki/Downloads  

2. Download and Install Vagrant. Link :   
    https://www.vagrantup.com/downloads.html  
    
3. Check that Vagrant is properly installed or not by typing the command :   

    ``` vagrant --version ```

4. Download the VM configuration by downloading the code in your local PC.  

6. Start the Virtual Machine using commands :   

    ``` vagrant up ```  
    ``` vagrant ssh ```

7. Now execute the code using the final command :   

    ``` python3 logs_analysis.py```   


## Views Description
For executing article_view is used. The sql statement for creating article_view is :   
``` create view article_view as select title, author, count(*) as views from articles, log where log.path like concat('%',articles.slug) group by articles.title, articles.author order by views desc; ```   

Then for executing the third query error_requests and total_requests two views are used. The sql statement for those are :   
``` create view error_requests as select date(time), count(*) as errors from log where status like '404%' group by date(time) order by errors desc; ```    

``` create view total_requests as select date(time), count(*) as requests from log group by date(time) order by requests desc; ```
