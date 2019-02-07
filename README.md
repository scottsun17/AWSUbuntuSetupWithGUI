# AWSUbuntuSetupWithGUI
Step by step setting up Ubuntu on AWS and connecting to GUI with MS Remote Desktop Connection on a windows computer

## what you need to start
   - Windows Computer (mine is windows 7)
   - Remote Desktop Connection (come with windows)
   - AWS account (link below to register)
   - PuTTY (link below to download)

## Register an account with AWS 
Link: https://aws.amazon.com/ 
![awsaccountsignup](https://user-images.githubusercontent.com/42085040/52391432-1d1fc780-2a6b-11e9-8ff6-ebb3cc7d2977.PNG)

## How to set up Unbuntu with AWS and connect to the instance from our local computer?
1. sign in to the console

2. Under Build a solution, select Launch a virtual machine
![launchavm](https://user-images.githubusercontent.com/42085040/52391550-aafbb280-2a6b-11e9-8d0d-5830a243a172.PNG)

3. On the right side where all different type of OS are listed, select Ubuntu Server 16.04 LTS (HVM), SSD Volume Type
    The reason why I choose this version is that MS Remote Desktop Connection does work on this version and I don't 
    want to figure out if the same method work for the other version (Ubuntu Server 18.04 LTS (HVM), SSD Volume Type).
![choosevm](https://user-images.githubusercontent.com/42085040/52391655-5e64a700-2a6c-11e9-8637-9d3524f2bcd1.PNG)

4. Click Review and Launch if you want the free version. Nothing for you to set up.

5. Again, click launch

6. Now you are promoted with Selecting a new key pair. It is like username and password combination for your VM at AWS.
If you never created VM at AWS before, you won't have any existing key pair. So select create a new key pair.
Name it however you want - Mine is CallMeMaybe~~~
Click Download Key Pair and you will get a file "whatever you named it".pem
This is the love of your life and you should keep it save and never delete it
![keypair](https://user-images.githubusercontent.com/42085040/52391806-36297800-2a6d-11e9-9a40-75f6ce5323f6.PNG)

7. Click launch and Your Instances are now launching; scroll all the way down, you will see View Instance at the bottom right corner
 
8. Click View Instance and you will see something like the picture below:
    Import thing includes but not limited to the following:
- Name of instance, you can name it however you want. Name it so you dont confused it with others. AWS free version allow 
      up to two instance running at the same time. So you can get a Windows and a Linux running at the same time~~ way to go Amazon~
- Instance ID is important 
- IPv4 public IP is important
![viewinstance](https://user-images.githubusercontent.com/42085040/52391957-e8613f80-2a6d-11e9-8114-1409b926668a.PNG)

9. Now you are done with Ubuntu set up. We now need a tool to connect to our VM - PuTTY
-Go to: https://www.putty.org/ 
- Click Download PuTTY
![putty](https://user-images.githubusercontent.com/42085040/52392212-d2a04a00-2a6e-11e9-8b85-faccbc41f528.PNG)
- Download whichever bit apply to you. Mine is 64-bit.
![putty2](https://user-images.githubusercontent.com/42085040/52392346-5b1eea80-2a6f-11e9-8ac6-46dce45f80cc.PNG)

10. Following the Installation instruction. There is nothing to set up...

11. Once your PuTTY is installed, go to start menu:
-All Programs
-PuTTY Folder
-PuTTYgen
and you will get the following program:
![puttygen](https://user-images.githubusercontent.com/42085040/52392474-eef0b680-2a6f-11e9-9e50-1f1c0fc0b943.PNG)

12. The program is used to load the Key Pair(CallMeMaybe.pem as I generated in step 6) and generate private key
-Click Load
-Navigate to the folder where you saved your Key Pair. You will not be able to see the Key Pair because the file selection
is default to PuTTY Private Key Files(.ppk). Change to All Files and you will see your AWS Key Pair
![keyload](https://user-images.githubusercontent.com/42085040/52392571-80602880-2a70-11e9-8150-2b0d3e512a68.PNG)
![openkeyload](https://user-images.githubusercontent.com/42085040/52392609-a4236e80-2a70-11e9-81b7-dcec185b07dc.PNG)
![succe](https://user-images.githubusercontent.com/42085040/52392635-c2896a00-2a70-11e9-88f7-2d63220b09df.PNG)

13. If you see the above picture, Key Pair is loaded. 
-Now you need to set password(passphrase) for your private key
-Select RSA as the type of Key to generate
-Number of bits in a generated key: 2048
-save Private Key (CallMeMaybe.ppk)
-exit PuTTYgen
![savepk](https://user-images.githubusercontent.com/42085040/52392771-552a0900-2a71-11e9-8abb-73ab84316b74.PNG)

14. Now let's connect to your AWS Ubuntu through PuTTY
-Start menu:
-All Programs
-PuTTY Folder
-PuTTY
-Now you see the PuTTY Configuration
![puttymenu](https://user-images.githubusercontent.com/42085040/52392869-b94ccd00-2a71-11e9-83f3-1311bc49593e.PNG)

15. At the PuTTY landing Page (Session tab on the left menu), we need to fill out the following information (Go to Step 8 to find the information)
- a. Host Name (or IP Address) - IPv4 public IP from the AWS Console Instance Page 
- b. Port 22 (Default)
- c. Connection Type SSH (Default)
- d. DO NOT load yet, we are not done
![ipv4](https://user-images.githubusercontent.com/42085040/52393075-95d65200-2a72-11e9-8b30-062daeffe269.PNG)

16. On the left side menu, click Connection -> SSH -> Auth    
- Now you land on the Options controlling SSH authentication page
- I kept all the default selection (see picture below)
- click Browse
- loack CallMeMaybe.PPK file (It's the PPK file generated by the PuTTYgen, not the pem file you download from AWS)!!!!
- DO NOT Click Open!!!
![loadppk](https://user-images.githubusercontent.com/42085040/52393252-4f352780-2a73-11e9-9bdd-0f4550349016.PNG)

17. Now we navigate back to the Session page - > Name the session(CallMeMaybe Instance) -> Save -> and you will see the name appear inside the Saved Session box. Now click Open.   See picture below:
![session](https://user-images.githubusercontent.com/42085040/52393431-ff0a9500-2a73-11e9-8a55-722afd4d3a01.PNG)

18. This is the first time you connect to the VM through PuTTY, you will get a scary msg like the picture below. Just ignore it and click Yes :D
![scarymsg](https://user-images.githubusercontent.com/42085040/52393478-3aa55f00-2a74-11e9-9a71-debc04547186.PNG)

19. Now you are in the DOS where we need to login to our Ubuntu System.
User Name: ubuntu
Password: whatever password you set up for the private key - see step 13
![dos](https://user-images.githubusercontent.com/42085040/52393633-1007d600-2a75-11e9-8054-d5a92910b05e.PNG)

## Now let's get GUI for our Ubuntu OS.
1. Following the above step, you are login to the system. We need to check for Update; Type or copy the following to the DOC (please include "sudo", it's part of the cm...
```
sudo apt update && sudo apt upgrade
```
You will be promoted to install more in the additional disk(see below picture). Type Y.
![y](https://user-images.githubusercontent.com/42085040/52393833-f5822c80-2a75-11e9-8000-20adf8073ce7.PNG)

You will see the following page.. Select "Keep the local version currenly installed" - press enter
![enter](https://user-images.githubusercontent.com/42085040/52393863-31b58d00-2a76-11e9-9de1-03b17e50f3a5.PNG)

2. Once you are done, let's config sshd_config file to allow password authentication on our ubuntu
```
sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/' /etc/ssh/sshd_config
```

3. We need to restart the SSH daemon for the new sshd config to take effect
```
sudo /etc/init.d/ssh restart
```
![2code](https://user-images.githubusercontent.com/42085040/52394032-e485eb00-2a76-11e9-9d39-ed57ca096490.PNG)

4. Get temporarry root privileges and change the password more security
```
sudo passwd ubuntu
```
Enter another password.. please dont forget it. you will need it to log in to the system.
![password](https://user-images.githubusercontent.com/42085040/52394164-6e35b880-2a77-11e9-9c58-4d4dc78e9cb5.PNG)

5. Install the xfce4 desktop environment - xrdp
```
sudo apt install xrdp xfce4 xfce4-goodies tightvncserver
```
It will ask you if you want to continue. I typed Y too fast and forgot to screenshot.. Just type Y and wait for it to install

6. set xfce4 as the default manager for RDP connections
```
echo xfce4-session> /home/ubuntu/.xsession
```

7. Copy .xsession to the /etc/skel folder and Run the sed command to update the [xrdp1] section
```
sudo cp /home/ubuntu/.xsession /etc/skel
sudo sed -i '0,/-1/s//ask-1/' /etc/xrdp/xrdp.ini
```
![67](https://user-images.githubusercontent.com/42085040/52394434-472bb680-2a78-11e9-85d9-7cecec1d493b.PNG)

8. Restart xrdp
```
sudo service xrdp restart
```

9. Now you are almost done! We now need to roboot the system.
```
sudo roboot
```

10. We need to go back and config PuTTY again
- at landing page (Session), select your saved session - mine is CallMeMaybe Instance
- click load
![load](https://user-images.githubusercontent.com/42085040/52394652-f8325100-2a78-11e9-909b-9351e130cfe9.PNG)

11. On the left side Menu, select Connection -> SSH ->Tunnel and we need to do the following:
-Source port: can be anything as long as they are not in conflict. we use 8888 here
-Destination: It is the Private IPs from your AWS Ubuntu Instance + ":3389" (Dont forget the semicolon )
-See picture below for a more clear view
![3389](https://user-images.githubusercontent.com/42085040/52394828-c1a90600-2a79-11e9-9ca1-1128be2cc149.PNG)

12. Click add and it will appear in Forwarded Ports
![add](https://user-images.githubusercontent.com/42085040/52394875-f321d180-2a79-11e9-8ec0-7202d53ded7e.PNG)

13. Go back to Session page, click Save so next time you dont have to config again.

14. Click Open and login

15. Type in the following code to see if the port is connected
```
netstat -antp
```
![3389dos](https://user-images.githubusercontent.com/42085040/52395009-82c78000-2a7a-11e9-8e3c-10631a024527.PNG)

16. If you find 0.0.0.0:3389, then you are connected. Now we can work on the Remote Desktop Connection

17. Launch Remote Desktop Connection and type in the computer field; 
8888 is the port number you set in the above step(step 11). If you set a different number, you should go back and check what the number
```
127.0.0.1:8888
```
![8888](https://user-images.githubusercontent.com/42085040/52395184-1305c500-2a7b-11e9-82c8-de1579ce75ed.PNG)

18. Click Connect and Remote Desktop Connection will launch. Now type in username and password
username: ubuntu
password: Same Password you set in Step 4
![msremote](https://user-images.githubusercontent.com/42085040/52395222-45172700-2a7b-11e9-9e84-b130e39b95e5.PNG)

19. You are in the GUI!! Select Default Config
![gui](https://user-images.githubusercontent.com/42085040/52395313-a63efa80-2a7b-11e9-97e5-fed3035ac49e.PNG)

20. Now lets get you a browser
- click Application
- click Terminal Emulator
- Type in the following code
```
sudo apt-get install firefox
```
- Type Y to continue
and now you have a brower to do whatever you want~~~
![browser](https://user-images.githubusercontent.com/42085040/52395558-aee40080-2a7c-11e9-82d7-b4a74093a7c0.PNG)






