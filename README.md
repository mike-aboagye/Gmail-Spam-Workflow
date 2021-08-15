# Gmail-Spam-Workflow   

This workflow ping the Google's imap server first. If the server is the alive, then the operator connects to a user's gmail account 
to retrieve messages flagged by Google as spam messages and non-spam messages. 

Next it passes the retrieved messages to a trained Naive Bayes model for spam classification.

## Installation   

Execute the following command to install necessary packages  as shown below:   

```
pip install -r requirements.txt  
```    

## Start Apache-Airflow Server 

Run the following command to initialize the database, create a user, start the web server as well as the scheduler:   

<!---
Run the command below to initialize airflow database
-->

```python
airflow db init 
```   

<!---
Th command below creates and assign password to a user
-->

```python
airflow users create --username admin --firstname mike --lastname michael --role Admin --email  mike@company.com 
```  

<!---
The command below starts the scheduler.
-->

```python
airflow scheduler 
```

## Task For Gmail-Spam-Workflow    

- ping_imap_server:   
      
      The `ping_imap_server` task is to ping the imap server to check whether it is alive or not.    
      
- get_recent_spam:   

      The `get_recent_spam` task is to login and retrieve recent spam and non-spam messages from a user's gmail account 
      
- naive_classifier:   

      The `native-classifier` task takes a spam or non-spam message as input and display whether the message is spam or not.
