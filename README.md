## How To Install The IoT Kit

For this guide, you will need to place some things in the home directory of the logged in user, which we will be assuming is pi. Keep in mind that you must have sudo privileges to complete this installation.

### To Install Informix:

You need the Informix Dynamic Server for Arm, which you can find at the following link. Please ensure you use this ARM6 copy of Informix, as ARM7 is not yet fully supported.  
 [http://www14.software.ibm.com/webapp/download/preconfig.jsp?id=2013-10-02+10%3A49%3A20.723369R&S_TACT=&S_CMP=](http://www14.software.ibm.com/webapp/download/preconfig.jsp?id=2013-10-02+10%3A49%3A20.723369R&S_TACT=&S_CMP=)  
 Enter your ID and password, then select the version of Informix you'd like to download. Fill out the information, select I agree, and it will take you to the download page. Once your download has completed, create /home/pi/iot-gateway-kit-depend , and place the Informix tar file in that directory.

### To Install Components From GitHub:

Switch to the directory containing iot-gateway-kit-depend (in this example, /home/pi ) and download the Iot Kit components from GitHub via the following command:

git clone [https://github.com/IBM-IoT/iot-gateway-kit](https://github.com/IBM-IoT/iot-gateway-kit)

Then run the iot_install script found in the top level of the repository. The script will configure Informix and other utilities, and install Node.js. It will also install Node-RED and related components of the Iot Kit to the Informix home directory, which by default is /home/informix . After installation, the Node-RED server will be up and running. You can access Node-RED by opening your browser and typing 127.0.0.1:1880 in the address bar.

### Using The Sensor Tag:

To interact with sensor tag devices, you'll need to run sudo ./start.ble , located in /home/informix/node-red/run/iot by default. Here's an example of what the sensor tag output will look like when it's connected: {"id":"b827ebad4da3.bc6a29ab5c75","tstamp":"2015-05-05 18:45:36.00000","json_data":{"myName":"TI Sensor Tag","accelX":3,"accelY":-0.4375,"accelZ":4.125}}

### After A Reboot:

To start the services up again after rebooting your machine (or stopping them for some other reason), run sudo service iot start , and then run sudo ./start.ble  again.
