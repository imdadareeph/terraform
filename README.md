# terraform

configure terraform in aws instance EC2

Major commands :
ssh -i "privatekey.pem" ec2-user@ec2-XX-XX-XXX-XXX.compute-1.amazonaws.com
sudo yum install wget git
git version
wget https://releases.hashicorp.com/terraform/0.11.3/terraform_0.11.3_linux_amd64.zip
unzip terraform_0.11.3_linux_amd64.zip
sudo mv terraform /usr/local/bin/

```javascript
Imdads-Mackee:Desktop imdadareeph$ ssh -i "privatekey.pem" ec2-user@ec2-XX-XX-XXX-XXX.compute-1.amazonaws.com
Last login: Thu Mar  X XX:XX:XX 2018 from XX.XXX.XXX.XXX

       __|  __|_  )
       _|  (     /   Amazon Linux AMI
      ___|\___|___|

https://aws.amazon.com/amazon-linux-ami/2017.09-release-notes/
6 package(s) needed for security, out of 8 available
Run "sudo yum update" to apply all updates.
-bash: warning: setlocale: LC_CTYPE: cannot change locale (UTF-8): No such file or directory
[ec2-user@ip-XXX-XX-XX-XXX ~]$ sudo yum install wget git
Failed to set locale, defaulting to C
Loaded plugins: priorities, update-motd, upgrade-helper
Package wget-1.18-3.28.amzn1.x86_64 already installed and latest version
Resolving Dependencies
--> Running transaction check
---> Package git.x86_64 0:2.13.6-2.56.amzn1 will be installed
--> Processing Dependency: perl-Git = 2.13.6-2.56.amzn1 for package: git-2.13.6-2.56.amzn1.x86_64
--> Processing Dependency: perl(Term::ReadKey) for package: git-2.13.6-2.56.amzn1.x86_64
--> Processing Dependency: perl(Git::I18N) for package: git-2.13.6-2.56.amzn1.x86_64
--> Processing Dependency: perl(Git) for package: git-2.13.6-2.56.amzn1.x86_64
--> Processing Dependency: perl(Error) for package: git-2.13.6-2.56.amzn1.x86_64
--> Running transaction check
---> Package perl-Error.noarch 1:0.17020-2.9.amzn1 will be installed
---> Package perl-Git.noarch 0:2.13.6-2.56.amzn1 will be installed
---> Package perl-TermReadKey.x86_64 0:2.30-20.9.amzn1 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

======================================================================================================================================================================================================================================================
 Package                                                       Arch                                                Version                                                            Repository                                                 Size
======================================================================================================================================================================================================================================================
Installing:
 git                                                           x86_64                                              2.13.6-2.56.amzn1                                                  amzn-updates                                               11 M
Installing for dependencies:
 perl-Error                                                    noarch                                              1:0.17020-2.9.amzn1                                                amzn-main                                                  33 k
 perl-Git                                                      noarch                                              2.13.6-2.56.amzn1                                                  amzn-updates                                               69 k
 perl-TermReadKey                                              x86_64                                              2.30-20.9.amzn1                                                    amzn-main                                                  33 k

Transaction Summary
======================================================================================================================================================================================================================================================
Install  1 Package (+3 Dependent packages)

Total download size: 12 M
Installed size: 29 M
Is this ok [y/d/N]: y
Downloading packages:
(1/4): perl-TermReadKey-2.30-20.9.amzn1.x86_64.rpm                                                                                                                                                                             |  33 kB  00:00:00     
(2/4): perl-Git-2.13.6-2.56.amzn1.noarch.rpm                                                                                                                                                                                   |  69 kB  00:00:00     
(3/4): perl-Error-0.17020-2.9.amzn1.noarch.rpm                                                                                                                                                                                 |  33 kB  00:00:00     
(4/4): git-2.13.6-2.56.amzn1.x86_64.rpm                                                                                                                                                                                        |  11 MB  00:00:07     
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                                                                                                 1.4 MB/s |  12 MB  00:00:07     
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : 1:perl-Error-0.17020-2.9.amzn1.noarch                                                                                                                                                                                              1/4 
  Installing : perl-TermReadKey-2.30-20.9.amzn1.x86_64                                                                                                                                                                                            2/4 
  Installing : perl-Git-2.13.6-2.56.amzn1.noarch                                                                                                                                                                                                  3/4 
  Installing : git-2.13.6-2.56.amzn1.x86_64                                                                                                                                                                                                       4/4 
  Verifying  : 1:perl-Error-0.17020-2.9.amzn1.noarch                                                                                                                                                                                              1/4 
  Verifying  : perl-Git-2.13.6-2.56.amzn1.noarch                                                                                                                                                                                                  2/4 
  Verifying  : perl-TermReadKey-2.30-20.9.amzn1.x86_64                                                                                                                                                                                            3/4 
  Verifying  : git-2.13.6-2.56.amzn1.x86_64                                                                                                                                                                                                       4/4 

Installed:
  git.x86_64 0:2.13.6-2.56.amzn1                                                                                                                                                                                                                      

Dependency Installed:
  perl-Error.noarch 1:0.17020-2.9.amzn1                                            perl-Git.noarch 0:2.13.6-2.56.amzn1                                            perl-TermReadKey.x86_64 0:2.30-20.9.amzn1                                           

Complete!
[ec2-user@ip-XXX-XX-XX-XXX ~]$ git version
git version 2.13.6
[ec2-user@ip-XXX-XX-XX-XXX ~]$ wget https://releases.hashicorp.com/terraform/0.11.3/terraform_0.11.3_linux_amd64.zip
--2018-03-08 10:11:26--  https://releases.hashicorp.com/terraform/0.11.3/terraform_0.11.3_linux_amd64.zip
Resolving releases.hashicorp.com (releases.hashicorp.com)... 151.101.201.183, 2a04:4e42:2f::439
Connecting to releases.hashicorp.com (releases.hashicorp.com)|151.101.201.183|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16466291 (16M) [application/zip]
Saving to: 'terraform_0.11.3_linux_amd64.zip'

terraform_0.11.3_linux_amd64.zip                              100%[===============================================================================================================================================>]  15.70M  58.4MB/s    in 0.3s    

2018-03-08 10:11:26 (58.4 MB/s) - 'terraform_0.11.3_linux_amd64.zip' saved [16466291/16466291]

[ec2-user@ip-XXX-XX-XX-XXX ~]$ ls
terraform_0.11.3_linux_amd64.zip
[ec2-user@ip-XXX-XX-XX-XXX ~]$ unzip terraform_0.11.3_linux_amd64.zip 
Archive:  terraform_0.11.3_linux_amd64.zip
  inflating: terraform               
[ec2-user@ip-XXX-XX-XX-XXX ~]$ ls
terraform  terraform_0.11.3_linux_amd64.zip
[ec2-user@ip-XXX-XX-XX-XXX ~]$ mv terraform /usr/local/bin/
mv: cannot move 'terraform' to '/usr/local/bin/terraform': Permission denied
[ec2-user@ip-XXX-XX-XX-XXX ~]$ sudo mv terraform /usr/local/bin/
```
