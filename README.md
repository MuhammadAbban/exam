# exam
login root
services  > go to s3
create bucket top right
uncheck Block all public access
check I acknowledge ... objects within becoming public.
Bucket Versioning disable
default encryption  disable
Create Bucket.
------------------------
Access isn't public
Click bucket
Click upload
upload ur passportsize img
Click Upload
Close
--------------------------------
Objects > Click our image > copy object url 
paste in new tab > access denied
still object isn't public.
We have to made policy to make it public
Buckets > Click our bucket > permissions
scroll down -> EDIT
click Policy generator
Policy Type  "S3 Bucket Policy"
Effect "Allow"
Principal "*"
Actions "GetObject"
ARN ?? 
Buckets > our bucket > properties > copy ARN
ADD Statement
Generate policy
Copy Policy
our Bucket > permissions > edit > paste there
edit Resource attribute, append "/*" at the end of attribute value
eg: "arn:aws:s3:::demo_bucket/*"
SAVE CHANGES
now check our bucket's access is public
no click on our object, copy it's url and paste in new tab, image will be live.
---------------------------------------------
Now put this object url in CV's Html inside an image's  source attribute. after we will put this html file on our ec2 instance on a new port given by sir.

Services > EC2
Launch Instances
give a Name 
AMI > "Ubuntu" search, select 1st one
create ney key pair > give a name > select .ppk file format.
Network Settings > Check Allow SSH, HTTPS, HTTP.
LAUNCH INSTANCE 
now select our instance and connect to CLI.
-------------------------------
COPY publicIP drom CLI window, open in new tab.
CLI -> sudo apt update
sudo apt upgrade
sudo apt install apache2
sudo service apache2 restart
check in apache tab if it is live.
then change the ports settings.
ec2 > our instance > security > click  security groups url
EDIT INBOUND RULES
ADD RULE
Custom TCP, TCP, desired portnumber, anywhere, 0.0.0.0/0 
Save Rules
CLI -> sudo nano /etc/apache2/ports.conf -> edit port number
sudo nano /etc/apache2/sites-available/000-default.conf -> edit port number
sudo service apache2 restart
ipAddress:newport
reload apache tab
CLI -> cd /var/www/html
ls 
sudo nano filename.html
paste html code from orignal file to this
ipAddress:newport/cv.html.
 done.
