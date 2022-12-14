# Mosquitto_AzureIOTHub
James D. Stallard 2022
Sample connection code for Mosquitto to Azure IOT Hub using MQTT/TLS

Adapted from:
https://techcommunity.microsoft.com/t5/internet-of-things-blog/mosquitto-client-tools-and-azure-iot-hub-the-beginning-of/ba-p/2824717

Which cites:
https://github.com/Azure-Samples/IoTMQTTSample/tree/master/src/Mosquitto_pub

This was done with Windows 10, but everything should work just the same with *nix

# Essential
Install Mosquitto: https://mosquitto.org/

Sign up for Azure: https://portal.azure.com/

Download the Root CA cert: https://raw.githubusercontent.com/Azure/azure-iot-sdk-c/master/certs/certs.c

# Optional
Install Cygwin so you can verify your downloaded certs on Windows: https://www.cygwin.com/

# Certs
You will need one or other of the "Baltimore CyberTrust Root" or "DigiCert Global Root G2" certs. This is because Microsoft are changing over their Root CA and from around Feb2023 the Baltimore cert will no longer work.


When you copy the cert, remember to strip out the unwanted characters: " \r \n. You may need a text editor capable of viewing the data in binary format. I used Sapien PrimalScript, but I believe Notepad++ can also do it. If you fail to do this, the cert will be invalid.
Use these commands to verify the cert (Cygwin or *nix CLI):
openssl x509 -in DigiCert.pem -text
openssl x509 -in Baltimore.pem -text

# Steps
1. Setup your Azure environment: AzureCLICommands.txt
2. Download your certificate, refer Certs or use the files here
3. Verify your certficate, refer Certs
4. Install Mosquitto
5. Run the monitor command in the AZ CLI Cloud Shell from AzureCLICommands.txt
6. Modify the command in Mosquitto_pub to replace the SAS Token, names and devices I used with those you chose in step 1, and the path to the binaries and the certificate
7. If it worked, then you will see a message in the AZ CLI monitor

The Shared Access Signature Token will expire (default is 1hr) so although not a suitable long term method of authentication is fine for this demo



