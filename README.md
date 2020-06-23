# nse-flask-ui-poc
basic pages in flask to be hosted on AWS Lambda

# Installation Instructions

1) Create a folder called aws at the root level<br>

       mkdir .aws
     
2) Create AWS Credentials<br>
   a)Goto IAM role in AWS dashboard.<br>
     Nagivate to Users.<br>
   b)Click on the Security credentials tab, and go down to Access Key, note down the access_key_id.<b> secret_access_key is only visible when you are creating new user </b>, so
     you need to note down both the access_key_id and secre_access_key at the time of user creation only. <br>
   c)To generate a new access_key, click on the create access key button

3) Create a file <b>credentials</b> in <b>.aws</b><br>
    Add the following lines to it:<br>
    
          ###~/.aws/credentials<br>
          [default]<br>
          aws_access_key_id=[...]<br>
          aws_secret_access_key=[...]<br>
          
4)Install AWS cli <br>
    
    pip install awscli
    
5) Make a folder to store project files<br>
  
       mkdir flask-app  
  If you clone this project, delete the <b>zappa_setting.json</b> file

6) Create a Virtual Environment and Activate it
    
        cd flask-app
        virtualenv .env
        .env/bin/activate
7)Getting the project requirements<br>
             
            #Project requirements are listed in the requirements.txt file
            #Install required packages
            pip install -r requirements.txt
8)Create Zappa settings json
          
          zappa init
  After the above command you will go through the procedure below:<br>
         
          FULL OUTPUT TRUNCATED... 
          What do you want to call this environment (default 'dev'):
          What do you want call your bucket? (default 'zappa-ip7znwymz'):
          Where is your app's function? (default 'app.init.app'):
          Would you like to deploy this application globally? (default 'n') [y/n/(p)primary]:
          Does this look okay? (default 'y') [y/n]:
  Open the zappa_setting.json file<br>
  If region is not automatically added to the JSON, we have to create it manually.
        
          eg: "aws_region": "ap-south-1"
  
  9) Deploy the application
        
            zappa deploy dev
            
            (Werkzeug 1.0.1 (c:\users\natha\flask-app\.env\lib\site-packages), Requirement.parse('Werkzeug<1.0'), {'zappa'})
            Calling deploy for stage dev..
            Downloading and installing dependencies..
           - typed-ast==1.4.1: Downloading
            100%|██████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 738k/738k                 [00:01<00:00, 659kB/s]
             - sqlalchemy==1.3.17: Downloading
            100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 1.25M/1.25M      [00:01<00:00, 903kB/s]
             - markupsafe==1.1.1: Using locally cached manylinux wheel
             - lazy-object-proxy==1.4.3: Downloading
            100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 56.5k/56.5k [00:00<00:00, 188kB/s]
            Packaging project as zip.
            Uploading flask-app-dev-1592945601.zip (9.0MiB)..
            100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 9.45M/9.45M [00:07<00:00, 1.27MB/s]
            Scheduling..
            Unscheduled flask-app-dev-zappa-keep-warm-handler.keep_warm_callback.
            Scheduled flask-app-dev-zappa-keep-warm-handler.keep_warm_callback with expression rate(4 minutes)!
            Uploading flask-app-dev-template-1592945794.json (1.6KiB)..
            100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 1.62k/1.62k [00:00<00:00, 17.0kB/s]
            Deploying API Gateway..
            Deployment complete!: https://***********.execute-api.ap-south-1.amazonaws.com/dev (how the link will look like)
            
  10) Update the Application
  
            zappa update dev
            
  
  
