# SAP Commerce Cloud Sample Repository for Data Hub

This sample repository contains the files and folders that are required to set up Data Hub in SAP Commerce Cloud.  You can clone this sample repository and then update the example files with your specific Data Hub details. 

When your files are ready, push them to your SAP Commerce Cloud repository.  Data Hub is automatically deployed when SAP Commerce Cloud is set up. 

### Requirements

- You have a public-facing code repository.
- You have an active SAP Commerce Cloud subscription that includes Data Hub version 6.7.0.0 or higher.
- You have a license for SAP Commerce version 1808 or higher.
- You have not set up SAP Commerce Cloud yet.  Once Commerce Cloud is installed, you cannot go back and add Data Hub.  If you already installed Commerce Cloud, contact the Support team for assistance.

## Supported Versions
Data Hub is supported with all versions of SAP Commerce that are supported by SAP Commerce Cloud. 

You can find the supported SAP Commerce versions listed in the Compatibility help topic at https://help.hybris.com/scc/pcd/31ac209eb08f41bc92e9bbe5772fb949.html.

The version of Data Hub does not have to match the version of SAP Commerce.  Use the most recent version of Data Hub.

## Configuration

These instructions walk you through the process of cloning the repository and then updating the sample files with your specific Data Hub requirements. 

The following folders and files are included in the sample repository.

  Root level 
	•	manifest.json: The Commerce Cloud manifest.json that includes required Data Hub properties.
	•	datahub folder: This folder contains all of the folders and files that support Data Hub.

  datahub folder
	•	manifest.json: The Data Hub manifest.json file that defines the Data Hub application and extensions.
	•	<custom-extension> folder: This folder is a generic folder that you can build out for custom extensions.
	•	config folder: This folder contains the Data Hub configuration files and folders.

  config folder
	•	lib folder: An optional folder where you can add pre-compiled extensions.  The JAR files and Java libraries that support the pre-compiled extensions should reside in this folder.
	•	logback.xml: This file defines logging details.
	•	datahub-environment.conf: This file contains the properties shared by all environments in a basic Data Hub configuration.
	•	datahub-environment-[environment_code].conf: This file contains unique properties that are assigned to specific environments.

### Clone Repository

Clone the sample repository. The files are copied to your local machine.


### Update the Custom Extensions

1.	Update the <custom-extension> folder.
	1.	Change the generic folder name to the name of your custom extension. 
	2.	Add the extension configuration information to the folder.
2.	Repeat these steps for each custom extension.
3.	If you don’t have custom extensions, you can delete the <custom-extension> folder.

### Update the Data Hub manifest.json

	1.	Open the manifest.json file inside the datahub folder.  This is the Data Hub manifest.json. 
	2.	Update the “datahub_version” with the version of Data Hub that you plan to use. Refer to the Version section of this readme for more information.
	3.	Save the changes.

### Update the Data Hub Environment Configuration File

	1.	Open the config folder.
	2.	Find the datahub-environment.conf file.
	3.	Open the configuration file and replace the default user names and passwords with the values that support your environment.
	4.	Save the changes. 

### Add an Optional Environment Variable File for Environments that Require Unique Properties

	1.	Open the config folder.
	2.	Open the datahub-environment-[environment_code].conf file.
	3.	Add environment properties for each unique property that you want to apply to the environment.
	4.	Name the file datahub-environment[environment_code].conf.
	⁃	To find the environment code for an environment, see the instructions in the SAP Commerce Cloud help at https://help.hybris.com/scc/pcd/1f6dfab4981347db8ab221acaf37960f.html.
	5.	Create a separate datahub-environment-[environment_code].conf file for each environment that requires unique properties.
	6.	If you do not need unique environment variables, delete the datahub-environment[environment_code].conf file.

### Verify the logback.xml file

	1.	Open the config folder.
	2.	Verify that the logback.xml file is inside the config folder.
	3.	DO NOT overwrite the <appender name=STDOUT> section of the logback.xml file.  This section is required if you want to access Data Hub logs in Kibana.

### Add Optional Pre-complied Extensions

Pre-compiled extensions are extensions such as Marketplace extensions.  These extensions are added to the lib folder. 

	1.	Open the config folder.
	2.	Open lib folder.
	3.	Add the JAR files and Java libraries that support the pre-compiled extensions. 
	4.	If you are not using pre-compiled extensions, delete the lib folder.

### Create the encryption key

	1.	Make sure that you have openSSL installed on your local machine.
	2.	Open a terminal window and run the following command to generate a 128-bit AES key.
          openssl enc -aes-128-ecb -k secret -P -md sha1
	3.	Verify that you see a result that includes values for “salt” and “key”
	4.	Copy the string that displays after “key=“.  Do not include “key=“.
	5.	Paste the string into a new text file.
	6.	Save the file with the name “encryption-key.txt”.
	7.	Move the file to the config folder.

### Add an SSL Certificate for Secure Communication between Data Hub and Third-Party Systems

	1.	Open the config folder.
	2.	Create a folder named “trusted-certificates”.
	3.	Copy your x509 certificate to the trusted-certificates folder.  
	4.	Verify that the file has a .cer extension and is in ASCII pem encoded format.

### Add Commerce Cloud manifest to the Commerce Cloud code repository ##To Do: Determine how to explain the manifest updates to an existing commerce manifest.

	1.	Find the manifest.json file at the root level of the sample repository. This is the Commerce Cloud manifest that includes required Data Hub properties.
	2.	In the Commerce Cloud repository root directory, replace the existing manifest.json file with this manifest.json.
	3.	Make sure that the version of Commerce Cloud identified in the first line of the manifest file is the version that you plan to use.

### Prepare to Push the Sample Repository
 
	1.	In the sample repository, verify that you have the following files in the datahub folder.
	⁃	manifest.json:  This is the manifest.json for Data Hub.
	⁃	<custom extension> folder (optional)
	⁃	config folder
	⁃	lib folder (optional)
	⁃	logback.xml
	⁃	datahub-environment.conf
	⁃	datahub-environment-[environment_code].conf (optional)
	⁃	encryption-key.txt
	⁃	trusted-certificate folder
	⁃	.cer file with x509 certificate

### Push Data Hub Configuration to Commerce Cloud Code Repository

	1.	In the Commerce Cloud root directory, push the data hub folder from your local machine to your Commerce Cloud repository.  

### Final Steps

Use the Cloud Portal to create a build and then deploy the build to an environment. The configuration you added to the Commerce Cloud repository is used to create Data Hub. After the build is deployed, you can find the Data Hub endpoint in the Environments page of the Cloud Portal.  

### More Information

Find more information on SAP Commerce Cloud and Data Hub in the SAP Commerce Cloud help at https://help.hybris.com/scc/pcd/ab9cf3c375a8407f8a5f548b8a379311.html.


