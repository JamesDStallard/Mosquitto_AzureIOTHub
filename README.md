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


When you copy the cert, remember to strip out the unwanted characters: " \r \n. You may need a text editor capable of viewing the data in binary format. I used SapienPrimal Script, but I believe Notepad++ can also do it. If you fail to do this, the cert will be invalid.
Use these commands to verify the cert (Cygwin or *nix CLI):
openssl x509 -in DigiCert.pem -text
openssl x509 -in Baltimore.pem -text

