# VivecraftForOracleSetup
Includes all necessary commands to install a Vivecraft server on Oracle Cloud 

## Create an Ampere instance 
For this tutorial, make an instance with 0.2 CPU and 10GB Ram

## Connect to your server via SSH
Guides for this are on the internet

## Installing JDK17
Type the following command:

```sudo yum install jdk-17.aarch64```

Enter "y" if it asks to do so.

## Install git
Run the following command

```sudo yum install git```

## Spigot Installation

Run the following commands:

```wget https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar```

```git config --global --unset core.autocrlf```

```java -jar BuildTools.jar --rev 1.19.2```

The last one may take some time.

## Run our server (Not complete yet!)
For changes to apply properly, run the following command

```java -Xmx8192M -Xms8192M -jar spigot-1.19.3.jar nogui```

The server will ask to accept eula.

Type ```ls``` to see the files and folders. You should see "eula.txt"

Type ```nano eula.txt``` and change the false to true.

Press CTRL + o, Enter, Then CTRL + x

## Install Vivecraft plugin

Enter the following commands

```cd plugins```

```wget https://github.com/TheScruffyKat/scruffy-resources/blob/main/Vivecraft_Spigot_Extensions.jar``` 

(This is 1.19.2 version of Vivecraft which I am hosting for ease of access :>)

```cd ..```

## Allowing Connections

In your Oracle dashboard, go to your instance's page and select the linked subnet. Select the default security rules. Press Add Ingress Rule

Ensure it is CIDR - 0.0.0.0/0 - And that the destnation port range is 25565.

Add another rule anc copy all info.  change the TCP to UDP. Save

Head back to your terminal and enter these commands:

```sudo firewall-cmd --permanent --zone=public --add-port=25565/tcp```

```sudo firewall-cmd --permanent --zone=public --add-port=25565/udp```

```sudo firewall-cmd --reload```

## Run it!

```java -Xmx8192M -Xms8192M -jar spigot-1.19.3.jar nogui```

## Connect in java!
Find the public IP in the instance properties. Enter into minecraft and have a blast playing with friends!
