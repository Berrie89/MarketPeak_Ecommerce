# E-commerce Website Deployment with Git, Linux and AWS.
The objective of this project is to develop an e-commerce website for a company called MarketPeak in a linux environment, deploy this website on an AWS EC2 instance and using Git for verion control.
## Implementation
### Implementing Version Control with Git.
Git is a free and open source version control system that keep tracks versions of files. It allows programmers to collaborate effectively.
I took the following steps to implement version control with git.
1. Initializing git repository: this allows you to create a new repository in your current working directory. I used the command git init. Find screenshot below.
### Obtaining and preparing the eCommerce Website
1. I downloaded an html template from free-css.com.
2. I customised the template by editing the logo and and modifying some texts to suit the MarketPeak brand identity. I used the Visual Studio Code editor to achieve this. Find screenshot of the website below.
![alt text](<Screenshot from 2024-09-19 14-06-01.png>)
### Staging and commiting the template to git.
1. I added the website files to my MarketPeak_Ecommerce Git repository with the command 'git add'
2. I commited my changes with a clear and descriptive message with the command "git commit -m 'my website update'".
### Pushing the website to a remote Github Repository
1. I created a new repository on Github called MarketPeak_Ecommerce
2. I linked my local repository to github with the command 'git remote add origin https://github.com/Berrie89/MarketPeak_Ecommerce.git'
3. I pushed my local repository content to github with the command 'git push -u origin main'
### AWS Deployment
1. I created an EC2 instance on AWS
2. I set up a security group that allows traffic on port 22 for SSH and port 80 for http.
3. I created a key pair called 'MarketPear.pem' which would allow me to securely connect to the EC2 instance.
I ran the command chmod 400 "MarketPear.pem" on the linux 
I logged in to the EC2 instance using the command 'ssh -i 'terminal to make sure the key is not publicly viewable.
I logged into the EC2 instance with the command 'ssh -i "MarketPear.pem" ec2-user@ec2-3-208-12-138.compute-1.amazonaws.com' 
I installed git on the EC2 instance using the commands 'sudo yum update' and 'sudo yum install git' 
I cloned the git repository on EC2 instance using the code 'git clone https://github.com/Berrie89/MarketPeak_Ecommerce.git'
I installed Apache on the EC2 instance. Apache is a free and open source web server that serves html files and content over the internet. Installing it would allow me to host the MarketPeak_Ecommerce website. I ued the following commands to install Apache; 'sudo yum update', 'sudo yum install httpd', 'sudo systemctl start httpd', 'sudo systemctl enable httpd'
Note that httpd is used to install Apache on systems that uses yum package manager.
When Apache is installed, it automatically creates a default directory called '/var/www/html/'
I cleared the content of the default directory with the command 'sudo rm -rf /var/www/html/*' and copied the content of the MarketPeak_Ecommerce directory into the default directory using the command 'sudo rm -r ~/MarketPeak_Ecommerce/* /var/www/html/'
I changed to the default directory using the command 'cd /var/www/html/' and used the command 'ls' to ensure all files has been copied.
I applied the changes by reloading httpd using the command 'sudo systemctl reload http'.
I logged into the AWS management console, got the public address of the EC2 instance, opened a web browser and launched the website. Find screenshot below.
### Continuos Integration and Deployment Workflow.
1. To achieve this I need both development environment to make changes and production environment to deploy updates. My local terminal was used as the development terminal while the EC2 instance was used as the production terminal.
2. I changed to the MarketPeak_Ecommerce directory to develop new features and fixes.
3. I created and switched to a new branch called development using the command 'git checkout -b development'.
4. I updated the web pages.
5. I staged all changes with the command 'git add'.
6. I commited all changes with the command 'git commit -m 'updated web pages'.
7. I uploaded all changeds to github with the command 'git push origin development'.
8. I navigated to github to create a pull request. This merges the development branch to the main branch.
9. I reviewed all changes made to make sure there are no issues, then merged the pull request to the main branch to incorporate the features into the production codebase.
10. I deployed my updates to the production server.
11. I securely connected to my EC2 instance through SSH.
12. I pulled the latest changes on the server using the command 'git pull origin main'
13. I changed to the MarketPeak_Ecommerce directory and copied all changes to the default directory using 'sudo rm -r ~/MarketPeak_Ecommerce/* /var/www/html/'
14. I changed to the default directory using the command 'cd /var/www/html/'.
15. I reloaded apache using the command 'sudo systemctl reload httpd'.
16. I got the public address of the EC2 instance, opened a web browser and launched the website to test the new feature. Find screenshot below.
![alt text](<Screenshot from 2024-09-19 18-00-35.png>)