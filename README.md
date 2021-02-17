This repository contains IBM ADP data files that must be added to the project databases at time of creation.  The data files contain initial required data libraries along with sample documents that can be used for training and demo purposes.  

Loading the data files will overwrite any existing data, so should only be performed on a new project database or where it is okay to erase the existing data.

Demo pattern deployment instructions:
-------------------------------------
1. Download the import.tar.xz file from the ACA/DB2/imports folder to the host machine.
2. Extract the data files to create an imports folder.  
     `tar -xvf import.tar.xz`
3. After the deployment is complete, copy the imports folder to the DB2 container.  
     `oc cp imports db2u-release-db2u-0:/mnt/blumeta0/home/db2inst1/DB2`
4. Open a command shell.  
     `oc rsh db2u-release-db2u-0`
5. Change to the DB2 directory and update permissions.  
     `cd /mnt/blumeta0/home/db2inst1/DB2 && chown -R db2inst1:db2iadm1 imports`
6. Change to the db2inst1 user.  
     `su db2inst1`
7. Run the script to load the first ontology.  
     `./LoadDefaultData.sh`  
     When prompted, provide the database name as CP4ADB and the Ontology name as ONT1.
8. Run the script to load the second ontology.  
     `./LoadDefaultData.sh`  
     When prompted, provide the database name as CP4ADB and the Ontology name as ONT2.
     
Enterprise pattern deployment instructions:
-------------------------------------------
1. Download the import.tar.xz file from the ACA/DB2/imports folder to the DB2 folder containing the scripts that will be run to build the project databases.
2. Extract the data files to create an imports folder.  
     `tar -xvf import.tar.xz`
3. After creating each project (tenant) database, load the data files.  
     `./LoadDefaultData.sh`
4. As prompted, enter the project database name and ontology specified when the database was created.
5. Repeat steps 3 and 4 for each project database.
