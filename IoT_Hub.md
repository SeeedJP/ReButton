# Getting started with Azure IoT Hub
---
Legal Disclaimer  
This page was provided just to provide a convenience for users. Seeed is not responsible for any errors or omissions, or for the results obtained from the use of this information. All information in this page is provided "as is", with no guarantee of completeness, accuracy, timeliness or of the results obtained from the use of this information.

---

You can learn about "Azure IoT Hub" at [here](https://docs.microsoft.com/en-us/azure/iot-hub/about-iot-hub), and pricing could be found [here](https://azure.microsoft.com/en-us/pricing/details/iot-hub/).

  ![](img/just_login.png)

When you just get sign in to Azure portal, you will see the dashboard. To find "IoT Hub", click "All services".

  ![](img/no_hub.png)

So, you will see this picture. Click "Create IoT Hub" to create new one.

  ![](img/create_hub.png)

Please choose suitable `subscription` and `region`. `Resource Group` could be empty, so please create and choose one. And name your IoT Hub and click `Next: Size and scale`.

  ![](img/create_hub2.png)

On scale, I choose `F1: Free tier` since I just want to try seeing how the ReButton and Azure IoT Hub works. There are limitation on free tier but it could be enough for trial. Click `Review + create` button.

So that you can review your choice. If it is correct, click `Create` button.

Deployment of IoT Hub may take a few minutes.

  ![](img/deployment_complete.png)

After getting deployment complete, click the name of `Resource`.

  ![](img/resource.png)

And then, choose `IoT Device`

  ![](img/add_device.png)

 and click `Add` button.
 
  ![](img/create_a_device.png)

To add a device, put `Device ID` and click `Save` button.

  ![](img/added.png)

Added. To grab the `Connection string`, click the device ID.

  ![](img/device_details.png)

You can see keys and connection strings. You will use `Connection string (primary key)`, so click the copy button for that.


# To confirm ReButton works with IoT HUB

I used [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/) to receive messages sent to IoT HUB from ReButton. You can find install manual on [here](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli).

After getting Azure CLI installed, please login.  
```
$ az login
```  
So your default web browser will be launched and let you sign in.

And then, install [Azure IoT extension for Azure CLI](https://github.com/Azure/azure-iot-cli-extension) by doing like this.
```
$ az extension add --name azure-cli-iot-ext
```  

Let's try to list IoT Hub.  
```
$ az iot hub list
```  


Too see help,  
```
$ az iot hub monitor-events --help
```  

To monitor messages from `ReButton` to IoT Hub, please do like this.  
```
$ az iot hub monitor-events -n [IoTHub Name] --properties anno sys --timeout 0
```
