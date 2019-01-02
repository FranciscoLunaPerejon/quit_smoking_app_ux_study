# App support system for quit smoking.
This project includes code of each part of the system used to analyze the user experience of an Andorid app to support to stop smoking.

The system consist of a version developed in the EU [SmokeFreeBrain project](http://smokefreebrain.eu/).

## Installation steps
Both database and server was installed on Windows OS.
### PostgreSQL database
The server database is implemented in PosgreSQL 9.6. We used PgAdmin for the database administration and development. 
Although PgAdmin 4 is the most recommended version, PgAdmin 3 eases the database dump and has a more usable interface on more devices. 
That can be downloaded [here](https://www.postgresql.org/download/) 
(if don’t exist a package for your SO that includes pgadmin 3, download it [here](https://www.pgadmin.org/download/)).

The following steps explain the installation using PgAdmin 3:

0. Install PostgresSQL 9.6 and PgAdmin 3
1. Using PgAdmin 3, create a new database in localhost server. In this manual we named it *UXResearchDB*. 
2. Right click on the database created and select “Restore…”. Introduce the PostgreSQL database backup file path in “Filename” field.
3. In tab “Restore Options #1”, select “Owner” in “Don’t save” field. 
4. Finally click on “Restore” button.

### Mirth Connect server
The Mirth Connect version used was 3.5.1. It can be downloaded [here](http://downloads.mirthcorp.com/archive/connect/).
In this guide we have installed both database and server in the same host. 

First of all, is recommended to modifiy the server xml files where the database is called. 
If not, changes must be made within the Mirth Connect Administrator tool, which is a slower and more difficult process. 
On each xml file, introduce the database information (DB name, user and password established in the PosgreSQL database) 
in each call to the function *DatabaseConnectionFactory.createDatabaseConnection*.   
To install the server:

0. Install Mirth Connect 3.5.1. Follow the steps in section “Download and Installation” of the *installation guide* 
(it can be downloaded [here](https://www.nextgen.com/products-and-services/NextGen-Connect-Integration-Engine-Downloads).)
until you log in as administrator in “Mirth Connect Administrator”.
1. Click on “Edit Code Templates” in menu “Channel task”. Select “Import libraries” in “Code Template
Ta…”, below “Mirth Connect” menu. Select one XML script file contained in the "Auxiliary libraries" folder and click “Open” button. Do
the same with all XML script files in this folder.
2. In “Channels” section (menu “Mirth Connect, up-left corner”), select “import channel” in menu
“Channel task” (below “Mirth Connect” menu). Select one channel XML script file and click “Open”
button. Do the same with all channel XML script files (except the XML scripts provided in the "Auxiliary libraries" folder).

#### Ports
The server use some ports for the connection with the app. 
It can be necessary to configure the firewall to allow a correct connection. The ports used are: 903, 913, 914.

It can be necessary open the additional ports 5228, 5229 and 5230

### Android app
To establish a correct connection between the server and the application, it is necessary to modify the "XMLHttpPost.java" file 
by adding the IP where is allocated the Mirth Connect server. 
This file is in "APPPATH\app\src\main\java\com\salumedia\quitandreturn\session\server". 
The app project must to be import in and IDE such as Android Studio. 
On this IDE it is possible to generate the app apk required to install the application in an Android smartphone.
