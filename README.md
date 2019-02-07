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
