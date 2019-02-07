# AWSUbuntuSetupWithGUI
Step by step setting up Ubuntu on AWS and connecting to GUI with MS Remote Desktop Connection

## Register an account with AWS 
Link: https://aws.amazon.com/ 
![awsaccountsignup](https://user-images.githubusercontent.com/42085040/52391432-1d1fc780-2a6b-11e9-8ff6-ebb3cc7d2977.PNG)

## How to set up Unbuntu with AWS?
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


