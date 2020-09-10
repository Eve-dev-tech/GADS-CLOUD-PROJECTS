

# MY CODE TRANSLATION PROJECTS
# 1.) Error Reporting and Debugging 

##Objectives

In this lab, you learn how to perform the following tasks:

Launch a simple Google App Engine application

Introduce an error into the application

Explore Cloud Error Reporting

Use Cloud Debugger to identify the error in the code

Fix the bug and monitor in Cloud Operations

# Task 1: Create an application

#### To create a local folder and get the App Engine Hello world application, run the following commands:
#### code to run
    mkdir appengine-hello
     cd appengine-hello
     gsutil cp gs://cloud-training/archinfra/gae-hello/* 

#### result code

      Copying gs://cloud-training/archinfra/gae-hello/app.yaml...
       Copying gs://cloud-training/archinfra/gae-hello/main.py...
      Copying gs://cloud-training/archinfra/gae-hello/main.pyc...
        Copying gs://cloud-training/archinfra/gae-hello/main_test.py...
        - [4 files][  2.5 KiB/  2.5 KiB]
       Operation completed over 4 objects/2.5 KiB.
         student_02_50e463c4a699@cloudshell:~/appengine-hello$
       student_02_50e463c4a699@cloudshell:~/appengine-hello$
         student_02_50e463c4a699@cloudshell:~/appengine-hello$

### run the application using the local development server in Cloud Shell, run the following command:

    dev_appserver.py $(pwd)

#### result code
     Python 2 is deprecated. Upgrade to Python 3 as soon as possible.
     See https://cloud.google.com/python/docs/python2-sunset
     To suppress this warning, create an empty ~/.cloudshell/no-python-warning file.
       The command will automatically proceed in  seconds or on any key.
       ********************************************************************************
       INFO     2020-09-09 09:49:47,875 devappserver2.py:289] Skipping SDK update check.
       WARNING  2020-09-09 09:49:48,180 simple_search_stub.py:1198] Could not read search indexes from /tmp/appengine.None.student_
      02_50e463c4a699/search_indexes
       INFO     2020-09-09 09:49:48,182 api_server.py:282] Starting API server at: http://0.0.0.0:38611
      INFO     2020-09-09 09:49:48,187 dispatcher.py:267] Starting module "default" running at: http://0.0.0.0:8080
      INFO     2020-09-09 09:49:48,188 admin_server.py:150] Starting admin server at: http://0.0.0.0:8000
     INFO     2020-09-09 09:49:51,209 instance.py:294] Instance PID: 1620
      INFO     2020-09-09 09:58:14,160 module.py:865] default: "GET /?authuser=0 HTTP/1.1" 200 13

#### output on webpreview
       Hello, World!

## Deploy the application to App Engine
##### deploy the application to App Engine
##### code to run
      gcloud app deploy app.yaml
##### output code
        Please enter your numeric choice:  14
        Creating App Engine application in project [qwiklabs-gcp-02-6ead55c5436a] and region [us-central]....done.
         Services to deploy:
          descriptor:      [/home/student_02_50e463c4a699/appengine-hello/app.yaml]
          source:          [/home/student_02_50e463c4a699/appengine-hello]
         target project:  [qwiklabs-gcp-02-6ead55c5436a]
        target service:  [default]
         target version:  [20200909t130845]
          target url:      [https://qwiklabs-gcp-02-6ead55c5436a.uc.r.appspot.com]
          Do you want to continue (Y/n)?  Y
          Beginning deployment of service [default]...
          ╔════════════════════════════════════════════════════════════╗
           ╠═ Uploading 3 files to Google Cloud Storage                ═╣
           ╚════════════════════════════════════════════════════════════╝
        File upload done.
        Updating service [default]...done.
         Setting traffic split for service [default]...done.
         Deployed service [default] to [https://qwiklabs-gcp-02-6ead55c5436a.uc.r.appspot.com]
          You can stream logs from the command line by running:
          $ gcloud app logs tail -s default
         To view your application in the web browser run:
          $ gcloud app browse
  
##### When the process is done, verify that the application is working by running the following command:
#### code to run
          gcloud app browse
##### result code
              Did not detect your browser. Go to this link to view your app:
               https://qwiklabs-gcp-02-6ead55c5436a.uc.r.appspot.com
##### output after accessing the above URL



# PROJECT TRANSLATION 2

# App Dev: Setting up a Development Environment v1.1

## Objectives
In this lab, you will learn how to perform the following tasks:

Provision a Google Compute Engine instance.

Connect to the instance using SSH.

Install software on the instance.

Verify the software installation.

Setup

### Task 1: Creating a Compute Engine Virtual Machine Instance
##### In the Cloud Platform Console, on the Navigation menu, click Compute Engine.

On the VM Instances page, click Create.

On the Create an instance page, for Name type dev-instance, select us-central1 for region and us-central1-a for the zone.

GCP Regions and Zones

Google Cloud Platform offers products and services in multiple distinct geographic locations, called regions.

Each region has multiple distinct zones. Each zone is isolated from other zones in terms of power and internet connectivity.

In the Identity and API access > Access Scopes section, select Allow full access to all Cloud APIs.

In the Firewall section, enable Allow HTTP traffic.

Leave the remaining settings as their defaults, and click Create.

It takes about 20 seconds for the virtual machine to be provisioned and started.

On the VM instances page, in the row for the dev-instance, click SSH (in the Connect column).

This launches a browser-hosted SSH session. If you have a popup blocker, you may need to click twice.

There's no need to configure or manage SSH keys.

#### Task 2: Install software on the VM instance
In the SSH session, to update the Debian package list, execute the following command:
##### code to run
       sudo apt-get update

##### result code
        Get:21 http://deb.debian.org/debian buster-backports/main Sources 2020-09-05-0805.01.pdiff [4552 B]
       Get:22 http://deb.debian.org/debian buster-backports/main Sources    2020-09-05-1401.17.pdiff [5310 B]
        Get:23 http://deb.debian.org/debian buster-backports/main Sources 2020-09-05-2007.28.pdiff [1499 B]
        Get:24 http://deb.debian.org/debian buster-backports/main Sources   2020-09-06-0210.41.pdiff [55 B]
         Get:25 http://deb.debian.org/debian buster-backports/main Sources 2020-09-06-0806.49.pdiff [1156 B]
         Get:26 http://deb.debian.org/debian buster-backports/main Sources 2020-09-06-1400.34.pdiff [791 B]
        Get:27 http://deb.debian.org/debian buster-backports/main Sources 2020-09-06-2011.11.pdiff [672 B]
         Get:28 http://deb.debian.org/debian buster-backports/main Sources          2020-09-07-0210.17.pdiff [31 B]
         Get:29 http://deb.debian.org/debian buster-backports/main Sources 2020-09-07-1400.59.pdiff [4724 B]
          Get:30 http://deb.debian.org/debian buster-backports/main Sources 2020-09-07-2008.11.pdiff [825 B]
         Get:31 http://deb.debian.org/debian buster-backports/main Sources 2020-09-08-0201.16.pdiff [2263 B]
           Get:32 http://deb.debian.org/debian buster-backports/main Sources    2020-09-08-0803.16.pdiff [55 B]
           Get:33 http://deb.debian.org/debian buster-backports/main Sources 2020-09-08-1402.49.pdiff [922 B]
          Get:34 http://deb.debian.org/debian buster-backports/main Sources 2020-09-08-2004.17.pdiff [44 B]
           Get:35 http://deb.debian.org/debian buster-backports/main Sources 2020-09-09-0205.29.pdiff [630 B]
           Get:36 http://packages.cloud.google.com/apt google-cloud-packages-archive-keyring-buster/main amd64 Packages [396 B
              ]
             Get:37 http://deb.debian.org/debian buster-backports/main Sources 2020-09-09-0802.17.pdiff [31 B]
             Get:38 http://deb.debian.org/debian buster-backports/main amd64 Packages 2020-09-02-0202.21.pdiff [200 B]
                   Get:39 http://deb.debian.org/debian buster-backports/main amd64 Packages 2020-09-03-0801.39.pdiff [376 B]
                   Get:40 http://deb.debian.org/debian buster-backports/main amd64 Packages 2020-09-03-1404.30.pdiff [363 B]
                 Get:41 http://deb.debian.org/debian buster-backports/main amd64 Packages 2020-09-05-0805.01.pdiff [2038 B]
                 Get:42 http://deb.debian.org/debian buster-backports/main amd64 Packages 2020-09-05-2007.28.pdiff [19.1 kB]
                 Get:43 http://deb.debian.org/debian buster-backports/main amd64 Packages 2020-09-06-0210.41.pdiff [16.0 kB]
                 Get:44 http://deb.debian.org/debian buster-backports/main amd64 Packages 2020-09-06-1400.34.pdiff [210 B]
                 Get:45 http://deb.debian.org/debian buster-backports/main amd64 Packages 2020-09-06-2011.11.pdiff [1051 B]
                Get:46 http://deb.debian.org/debian buster-backports/main amd64 Packages 2020-09-07-0210.17.pdiff [263 B]
               Get:37 http://deb.debian.org/debian buster-backports/main Sources 2020-09-09-0802.17.pdiff [31 B]
                Get:47 http://packages.cloud.google.com/apt google-compute-engine-buster-stable/main amd64 Packages [1773 B]
                   Get:48 http://deb.debian.org/debian buster-backports/main amd64 Packages 2020-09-07-1400.59.pdiff [3495 B]
                   Get:49 http://deb.debian.org/debian buster-backports/main amd64 Packages 2020-09-07-2008.11.pdiff [626 B]
                   Get:50 http://deb.debian.org/debian buster-backports/main amd64 Packages 2020-09-08-0201.16.pdiff [253 B]
                    Get:51 http://deb.debian.org/debian buster-backports/main amd64 Packages 2020-09-08-0803.16.pdiff [1888 B]
                    Get:52 http://deb.debian.org/debian buster-backports/main amd64 Packages  2020-09-08-2004.17.pdiff [826 B]
                    Get:53 http://deb.debian.org/debian buster-backports/main amd64 Packages 2020-09-09-0802.17.pdiff [193 B]
                      Get:54 http://deb.debian.org/debian buster-backports/main Translation-en 2020-09-05-1401.17.pdiff [282 B]
                        Get:53 http://deb.debian.org/debian buster-backports/main amd64 Packages 2020-09-09-0802.17.pdiff [193 B]
                      Get:55 http://deb.debian.org/debian buster-backports/main Translation-en 2020-09-07-1400.59.pdiff [1770 B]
                    Get:56 http://deb.debian.org/debian buster-backports/main Translation-en 2020-09-08-0803.16.pdiff [149 B]
                  Get:56 http://deb.debian.org/debian buster-backports/main Translation-en                  2020-09-08-0803.16.pdiff [149 B]
                    Fetched 826 kB in 1s (649 kB/s)                            
                     Reading package lists... Done
##### code to run
To install Git, execute the following command:

                sudo apt-get install git
##### result code
           (Reading database ... 37655 files and directories currently installed.)
              Preparing to unpack .../0-perl-modules-5.28_5.28.1-6+deb10u1_all.deb ...
             Unpacking perl-modules-5.28 (5.28.1-6+deb10u1) ...
               Selecting previously unselected package libgdbm-compat4:amd64.
              Preparing to unpack .../1-libgdbm-compat4_1.18.1-4_amd64.deb ...
                 Unpacking libgdbm-compat4:amd64 (1.18.1-4) ...
                 Selecting previously unselected package libperl5.28:amd64.
                 Preparing to unpack .../2-libperl5.28_5.28.1-6+deb10u1_amd64.deb ...
                 Unpacking libperl5.28:amd64 (5.28.1-6+deb10u1) ...
                Selecting previously unselected package perl.
                Preparing to unpack .../3-perl_5.28.1-6+deb10u1_amd64.deb ...
                 Unpacking perl (5.28.1-6+deb10u1) ...
                 Selecting previously unselected package libcurl3-gnutls:amd64.
                     Preparing to unpack .../4-libcurl3-gnutls_7.64.0-4+deb10u1_amd64.deb ...
                   Unpacking libcurl3-gnutls:amd64 (7.64.0-4+deb10u1) ...
                   Selecting previously unselected package libpcre2-8-0:amd64.
                   Preparing to unpack .../5-libpcre2-8-0_10.32-5_amd64.deb ...
                    Unpacking libpcre2-8-0:amd64 (10.32-5) ...
                      Selecting previously unselected package liberror-perl.
                 Preparing to unpack .../6-liberror-perl_0.17027-2_all.deb ...
              Unpacking liberror-perl (0.17027-2) ...
                Selecting previously unselected package git-man.
                Preparing to unpack .../7-git-man_1%3a2.20.1-2+deb10u3_all.deb ...
                 Unpacking git-man (1:2.20.1-2+deb10u3) ...
                  Selecting previously unselected package git.
                Preparing to unpack .../8-git_1%3a2.20.1-2+deb10u3_amd64.deb ...
               Unpacking git (1:2.20.1-2+deb10u3) ...
                 Selecting previously unselected package patch.
                  Preparing to unpack .../9-patch_2.7.6-3+deb10u1_amd64.deb ...
                   Unpacking patch (2.7.6-3+deb10u1) ...
                 Setting up perl-modules-5.28 (5.28.1-6+deb10u1) ...
                  Setting up libcurl3-gnutls:amd64 (7.64.0-4+deb10u1) ...
                Setting up patch (2.7.6-3+deb10u1) ...
                    Setting up libgdbm-compat4:amd64 (1.18.1-4) ...
                  Setting up libpcre2-8-0:amd64 (10.32-5) ...
                Setting up libperl5.28:amd64 (5.28.1-6+deb10u1) ...
                 Setting up git-man (1:2.20.1-2+deb10u3) ...
                  Setting up perl (5.28.1-6+deb10u1) ...
                   Setting up liberror-perl (0.17027-2) ...
                  Setting up git (1:2.20.1-2+deb10u3) ...
                 Processing triggers for man-db (2.8.5-2) ...
                  Processing triggers for libc-bin (2.28-10) ...

If prompted, press Enter.

##### To download the Node.js setup script, execute the following command:

         curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
##### result code
            `Hit:7 http://deb.debian.org/debian buster-backports InRelease
              Fetched 6384 B in 1s (7220 B/s)
                 Reading package lists... Done
## Confirming "buster" is supported...
```yaml
+ curl -sLf -o /dev/null 'https://deb.nodesource.com/node_6.x/dists/buster/Release'
## Adding the NodeSource signing key to your keyring...
+ curl -s https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add -
OK
## Creating apt sources list file for the NodeSource Node.js 6.x LTS Boron repo...
+ echo 'deb https://deb.nodesource.com/node_6.x buster main' > /etc/apt/sources.list.d/nodesource.list
+ echo 'deb-src https://deb.nodesource.com/node_6.x buster main' >> /etc/apt/sources.list.d/nodesource.list
## Running `apt-get update` for you...
+ apt-get update
Hit:1 http://deb.debian.org/debian buster InRelease
Hit:2 http://security.debian.org/debian-security buster/updates InRelease
Hit:3 http://deb.debian.org/debian buster-updates InRelease
Hit:4 http://deb.debian.org/debian buster-backports InRelease                    
Hit:5 http://packages.cloud.google.com/apt cloud-sdk-buster InRelease            
Get:6 http://packages.cloud.google.com/apt google-cloud-packages-archive-keyring-buster InRelease [3874 B]
Hit:7 http://packages.cloud.google.com/apt google-compute-engine-buster-stable InRelease
Get:8 https://deb.nodesource.com/node_6.x buster InRelease [4634 B]        
Get:9 https://deb.nodesource.com/node_6.x buster/main amd64 Packages [1004 B]
Fetched 9512 B in 1s (7903 B/s)     
Reading package lists... Done
## Run `sudo apt-get install -y nodejs` to install Node.js 6.x LTS Boron and npm
## You may also need development tools to build native addons:
     sudo apt-get install gcc g++ make
## To install the Yarn package manager, run:
     curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
     echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
     sudo apt-get update && sudo apt-get install yarn`````
```

##### To install npm and Node.js, execute the following command:

          sudo apt install nodejs

##### result code
```yaml
Get:6 http://deb.debian.org/debian buster/main amd64 libnode64 amd64 10.21.0~dfsg-1~deb10u1 [5629 kB]
Get:7 http://deb.debian.org/debian buster/main amd64 nodejs amd64 10.21.0~dfsg-1~deb10u1 [87.0 kB]
Get:8 http://deb.debian.org/debian buster/main amd64 nodejs-doc all 10.21.0~dfsg-1~deb10u1 [973 kB]
Fetched 15.5 MB in 1s (23.3 MB/s)   
Selecting previously unselected package libatomic1:amd64.
(Reading database ... 40562 files and directories currently installed.)
Preparing to unpack .../0-libatomic1_8.3.0-6_amd64.deb ...
Unpacking libatomic1:amd64 (8.3.0-6) ...
Selecting previously unselected package libbrotli1:amd64.
Preparing to unpack .../1-libbrotli1_1.0.7-2_amd64.deb ...
Unpacking libbrotli1:amd64 (1.0.7-2) ...
Selecting previously unselected package libc-ares2:amd64.
Preparing to unpack .../2-libc-ares2_1.14.0-1_amd64.deb ...
Unpacking libc-ares2:amd64 (1.14.0-1) ...
Selecting previously unselected package libicu63:amd64.
Preparing to unpack .../3-libicu63_63.1-6+deb10u1_amd64.deb ...
Unpacking libicu63:amd64 (63.1-6+deb10u1) ...
Selecting previously unselected package libuv1:amd64.
Preparing to unpack .../4-libuv1_1.24.1-1_amd64.deb ...
Unpacking libuv1:amd64 (1.24.1-1) ...
Selecting previously unselected package libnode64:amd64.
Preparing to unpack .../5-libnode64_10.21.0~dfsg-1~deb10u1_amd64.deb ...
Unpacking libnode64:amd64 (10.21.0~dfsg-1~deb10u1) ...
Selecting previously unselected package nodejs.
Preparing to unpack .../6-nodejs_10.21.0~dfsg-1~deb10u1_amd64.deb ...
Unpacking nodejs (10.21.0~dfsg-1~deb10u1) ...
Selecting previously unselected package nodejs-doc.
Preparing to unpack .../7-nodejs-doc_10.21.0~dfsg-1~deb10u1_all.deb ...
Unpacking nodejs-doc (10.21.0~dfsg-1~deb10u1) ...
Setting up libbrotli1:amd64 (1.0.7-2) ...
Setting up libc-ares2:amd64 (1.14.0-1) ...
Setting up libicu63:amd64 (63.1-6+deb10u1) ...
Setting up libuv1:amd64 (1.24.1-1) ...
Setting up libatomic1:amd64 (8.3.0-6) ...
Setting up nodejs-doc (10.21.0~dfsg-1~deb10u1) ...
Setting up libnode64:amd64 (10.21.0~dfsg-1~deb10u1) ...
Setting up nodejs (10.21.0~dfsg-1~deb10u1) ...
update-alternatives: using /usr/bin/nodejs to provide /usr/bin/js (js) in auto mode
Processing triggers for libc-bin (2.28-10) ...
Processing triggers for man-db (2.8.5-2) ...
```


## Task 3: Configure the VM to Run Application Software
In this section, you will verify the software installation and run some sample codes.

##### To check the version of Node.js, execute the following command:
##### code to run
       node -v
##### result code
           v10.21.0

You should see the Node.js version number for version 6.

##### To clone the class repository, execute the following command:
##### code to run
           git clone https://github.com/GoogleCloudPlatform/training-data-analyst
##### result code
```yaml
Unpacking libatomic1:amd64 (8.3.0-6) ...
Selecting previously unselected package libbrotli1:amd64.
Preparing to unpack .../1-libbrotli1_1.0.7-2_amd64.deb ...
Unpacking libbrotli1:amd64 (1.0.7-2) ...
Selecting previously unselected package libc-ares2:amd64.
Preparing to unpack .../2-libc-ares2_1.14.0-1_amd64.deb ...
Unpacking libc-ares2:amd64 (1.14.0-1) ...
Selecting previously unselected package libicu63:amd64.
Preparing to unpack .../3-libicu63_63.1-6+deb10u1_amd64.deb ...
Unpacking libicu63:amd64 (63.1-6+deb10u1) ...
Selecting previously unselected package libuv1:amd64.
Preparing to unpack .../4-libuv1_1.24.1-1_amd64.deb ...
Unpacking libuv1:amd64 (1.24.1-1) ...
Selecting previously unselected package libnode64:amd64.
Preparing to unpack .../5-libnode64_10.21.0~dfsg-1~deb10u1_amd64.deb ...
Unpacking libnode64:amd64 (10.21.0~dfsg-1~deb10u1) ...
Selecting previously unselected package nodejs.
Preparing to unpack .../6-nodejs_10.21.0~dfsg-1~deb10u1_amd64.deb ...
Unpacking nodejs (10.21.0~dfsg-1~deb10u1) ...
Selecting previously unselected package nodejs-doc.
Preparing to unpack .../7-nodejs-doc_10.21.0~dfsg-1~deb10u1_all.deb ...
Unpacking nodejs-doc (10.21.0~dfsg-1~deb10u1) ...
Setting up libbrotli1:amd64 (1.0.7-2) ...
Setting up libc-ares2:amd64 (1.14.0-1) ...
Setting up libicu63:amd64 (63.1-6+deb10u1) ...
Setting up libuv1:amd64 (1.24.1-1) ...
Setting up libatomic1:amd64 (8.3.0-6) ...
Setting up nodejs-doc (10.21.0~dfsg-1~deb10u1) ...
Setting up libnode64:amd64 (10.21.0~dfsg-1~deb10u1) ...
Setting up nodejs (10.21.0~dfsg-1~deb10u1) ...
update-alternatives: using /usr/bin/nodejs to provide /usr/bin/js (js) in auto mode
Processing triggers for libc-bin (2.28-10) ...
Processing triggers for man-db (2.8.5-2) ...
student-02-0ea0ea599599@dev-instance:~$ node -v
v10.21.0
student-02-0ea0ea599599@dev-instance:~$ git clone https://github.com/GoogleCloudPlatform/training-data-analyst
Cloning into 'training-data-analyst'...
remote: Enumerating objects: 40244, done.
remote: Total 40244 (delta 0), reused 0 (delta 0), pack-reused 40244
Receiving objects: 100% (40244/40244), 446.23 MiB | 32.97 MiB/s, done.
Resolving deltas: 100% (25032/25032), done.
Checking out files: 100% (7936/7936), done.
```


#### To change the working directory, execute the following command:
##### code to run
            cd ~/training-data-analyst/courses/developingapps/nodejs/devenv/

##### result code
             student-02-0ea0ea599599@dev-instance:~/training-data-analyst/courses/developingapps/nodejs/devenv$ 

#### To run a simple web server, execute the following command:
##### code to run

                sudo node server/app.js

##### result code

           opingapps/nodejs/devenv$ 
              -bash: student-02-0ea0ea599599@dev-instance:~/training-data-analyst/courses/developingapps/nodejs/devenv$: No such file or directory

##### result code
              Server starting...
                  started.
                 Request received...
                    Request received...

#### i could not understand why it said there was no such file.

#### Return to the Cloud Console VM instances list, and click on the External IP address for the dev-instance.

You should see a Hello GCP dev! message from Node.js.

Return to the SSH window, and stop the application by pressing Ctrl+C.

#### To install the Node.js library for Compute Engine, execute the following command:
##### code to run
             npm install
##### result code
                      -bash: npm: command not found
#### To run a simple Node.js application that lists Compute Engine instances, execute the following command:
##### code to run
                 node list-gce-instances.js
##### result code

# PROJECT TRANSLATION 3

## Previewing the Case Study Application
In this section, you will access Cloud Shell, clone the git repository containing the Quiz application, and run the application.

#### On the Cloud Platform Console, click Activate Google Cloud Shell.

 #### If a dialog box appears, click Start Cloud Shell.

##### To clone the repository for the class, execute the following command:

                git clone https://github.com/GoogleCloudPlatform/training-data-analyst

##### result code 
                Cloning into 'training-data-analyst'...
                 remote: Enumerating objects: 40244, done.
                 remote: Total 40244 (delta 0), reused 0 (delta 0), pack-reused 40244
                  Receiving objects: 100% (40244/40244), 446.23 MiB | 22.79 MiB/s, done.
                   Resolving deltas: 100% (25038/25038), done.
                   Checking out files: 100% (7936/7936), done.
                   
#### Configure and run the case study application
To change the working directory, execute the following command:

         cd ~/training-data-analyst/courses/developingapps/nodejs/datastore/start
         
##### result code

     student_03_49df1cd4435f@cloudshell:~/training-data-analyst/courses/developingapps/nodejs/datastore/start (qwiklabs-gcp-03-13f7d1bb2a87)$



To export an environment variable, GCLOUD_PROJECT that references the GCP Project ID, execute the following command:

        export GCLOUD_PROJECT=$DEVSHELL_PROJECT_ID
    
##### result code
              student_03_49df1cd4435f@cloudshell:~/training-data-analyst/courses/developingapps/nodejs/datastore/start (qwiklabs-gcp-03-13f7d1bb2a87)
              $

##### To install the application dependencies, execute the following command:

             npm install
##### result code
        > node scripts/postinstall
        npm notice created a lockfile as package-lock.json. You should commit this file.
          npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@^1.2.7 (node_modules/chokidar/node_modules/fsevents):
           npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.13: wanted     {"os":"darwin","arch":"any"} (current: {
           "os":"linux","arch":"x64"})
            added 900 packages from 874 contributors in 47.136s
            21 packages are looking for funding
            run `npm fund` for details
           student_03_49df1cd4435f@cloudshell:~/training-data-analyst/courses/developingapps/nodejs/datastore/start (qwiklabs-gcp-03-13f7d1bb2a87)
            $

##### To run the application, execute the following command:

            npm start
            
##### result code
  
           > quite-interesting-quiz-lab2@1.0.0 start /home/student_03_49df1cd4435f/training-data-analyst/courses/developingapps/nodejs/datastore/start
            > node server/app.js
            App listening on port 8080
            
### Examining the casestudy application
#### path /training-data-analyst/courses/developingapps/nodejs/datastore/start/server/datastore/start/server/app.js
                 // Copyright 2017, Google, Inc.
                 // Licensed under the Apache License, Version 2.0 (the "License");
                 // you may not use this file except in compliance with the License.
                 // You may obtain a copy of the License at
                 //
                //    http://www.apache.org/licenses/LICENSE-2.0
                    //
                // Unless required by applicable law or agreed to in writing, software
               // distributed under the License is distributed on an "AS IS" BASIS,
              // WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
               // See the License for the specific language governing permissions and
                   // limitations under the License.

               'use strict';

             const path = require('path');
                    const express = require('express');
                      const config = require('./config');

                      const app = express();

                     // Static files
                     app.use(express.static('server/public/'));

                     app.disable('etag');
                       app.set('views', path.join(__dirname, 'web-app/views'));
                       app.set('view engine', 'pug');
                      app.set('trust proxy', true);
                      app.set('json spaces', 2);

                    // Questions
                     app.use('/questions', require('./web-app/questions'));

                    // Quizzes API
                  app.use('/api/quizzes', require('./api'));

               // Display the home page
                 app.get('/', (req, res) => {
                res.render('home.pug');
                  });

               // Basic 404 handler
                app.use((req, res) => {
                  res.status(404).send('Not Found');
                     });

                     // Basic error handler
                      app.use((err, req, res, next) => {
                       /* jshint unused:false */
                         console.error(err);
                              // If our routes specified a specific response, then send that. Otherwise,
                             // send a generic message so as not to leak anything.
                                 res.status(500).send(err.response || 'Something broke!');
                                   });

                                    if (module === require.main) {
                                      // Start the server
                                       const server = app.listen(config.get('PORT'), () => {
                            const port = server.address().port;
                                   console.log(`App listening on port ${port}`);
                                     });
                                       }

                                module.exports = app;
                                
                                





#### Create an App Engine application to provision Cloud Datastore
````gcloud app create --region "us-central"


````// Copyright 2017, Google, Inc.
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at
//
//    http://www.apache.org/licenses/LICENSE-2.0
//
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.

'use strict';

// TODO: Load the ../config module

const config = require('../config');

// END TODO

// TODO: Load the @google-cloud/datastore module

const Datastore = require('@google-cloud/datastore');

// END TODO

// TODO: Create a Datastore client object, ds
// The Datastore(...) factory function accepts an options // object which is used to specify which project's  
// Datastore should be used via the projectId property. 
// The projectId is retrieved from the config module. This // module retrieves the project ID from the GCLOUD_PROJECT // environment variable.

const ds = Datastore({
 projectId: config.get('GCLOUD_PROJECT')
});


// END TODO

// TODO: Declare a constant named kind
//The Datastore key is the equivalent of a primary key in a // relational database.
// There are two main ways of writing a key:
// 1. Specify the kind, and let Datastore generate a unique //    numeric id
// 2. Specify the kind and a unique string id

const kind = 'Question';
// END TODO


// [START create]
function create({ quiz, author, title, answer1, answer2, answer3, answer4, correctAnswer }) function uses an
// ECMAScript 2015 destructuring assignment to extract
// properties from the form data passed to the function
function create({ quiz, author, title, answer1, answer2,
                  answer3, answer4, correctAnswer }) {
  

  // TODO: Declare the entity key, 
  // with a Datastore generated id
const key = ds.key(kind);


  // END TODO

  // TODO: Declare the entity object, with the key and data
  const entity = {
   key,
// The entity's members are represented in a data property.
// This is an array where each element represents one
// member in the entity. Each element is an object with a // name and a value
   data: [
     { name: 'quiz', value: quiz },
     { name: 'author', value: author },
     { name: 'title', value: title },
     { name: 'answer1', value: answer1 },
     { name: 'answer2', value: answer2 },
     { name: 'answer3', value: answer3 },
     { name: 'answer4', value: answer4 },
     { name: 'correctAnswer', value: correctAnswer },
   ]
 };


  // END TODO

  // TODO: Save the entity, return a promise
  // The ds.save(...) method returns a Promise to the  
  // caller, as it runs asynchronously.

 return ds.save(entity);

  // END TODO

}
// [END create]


// Lists all questions in a Quiz (defaults to 'gcp').
// Returns a promise
// [START list]
function list(quiz = 'gcp') {
  // BONUS TODO: Remove Placeholder statement
  return Promise.resolve({
    questions: [{
      id: -1,
      title: 'Dummy question',
      answer1: 'Dummy answer1',
      answer2: 'Dummy answer2',
      answer3: 'Dummy answer3',
      answer4: 'Dummy answer4',
      correctAnswer: 2
    }],
    nextPageToken: 'NO_MORE_RESULTS'
  });
  // END TODO

  // BONUS TODO: Create the query
  // The Datastore client has a ds.createQuery() method that   
  // allows you to specify the kind(s) of entities to be 
  // retrieved.
  // The query can be customized to filter the Question 
  // entities for one quiz.




  // END TODO

  // BONUS TODO: Execute the query
  // The ds.runQuery() method returns a Promise as it runs 
  // asynchronously



  // END TODO

  // TODO: Return the transformed results
  // Cloud Datastore returns the query response as an array. 
  // The first element references the data, the second 
  // contains an object indicating if there are more results 
  // and provides a token to paginate through the results. 


  // TODO: For each question returned from Datastore


  // TODO: Add in an id property using the Entity id
  // The reason that we need to do this is that we want to 
  // know which question a student has answered (using the 
  // Entity's key gives a unique id) and to avoid giving the 
  // answer away in the JSON data.
  // Cloud Datastore references an entity's key using an 
  // ECMAScript symbol named Datastore.KEY. 
  // One way to reshape the data is to use the JavaScript
  // array map(...) method to apply the modification to each 
  // element in the array.



  // TODO: Remove the correctAnswer property


  // END TODO

  // TODO: return the transformed item


  // END TODO


  // Reshape the data


  // TODO: Return the questions

  // TODO: Return a property to allow the client
  // to request the next page of results

  // This will  pass the set of transformed entities back 
  // from the model to the client - in this case the Quiz 
  // application's API

}
// [END list]


// [START exports]
module.exports = {
  create,
  list
};
// [END exports]













