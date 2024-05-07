# Challenges

## Week 1 :  Understanding and Implementing IoT Concepts

### Step 1: Setting Up Node-RED

1. Install Node-RED on your system. You can follow the official installation guide [Setup Instructions](../../setup/README_SETUP.md).
2. Once Node-RED is installed, launch it by running the command `node-red` in your terminal.

### Step 2: Connecting to the Database

1. Install the necessary database nodes in Node-RED. You can do this by navigating to the "Manage palette" option in the Node-RED menu and searching for the appropriate nodes `node-red-node-mysql`
or run the following command in your Node-RED user directory - typically ~/.node-red

        npm i node-red-node-mysql

2. Configure the mysql nodes with the connection details of your database (e.g., host, port, username, password).

        Host : 127.0.0.1
        Port : 3306
        User : root
        pass : 123

### Step 3: Integrating ESP32 as a Subscriber

1. Flash your ESP32 device with the appropriate firmware that supports MQTT communication. You can find example firmware and instructions on the official ESP32 documentation [here](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/).
2. Write a MQTT subscriber script for your ESP32 device. This script should connect to the MQTT broker running on your network and subscribe to the appropriate topics for receiving data.
3. Deploy the subscriber script to your ESP32 device and ensure it is connected to the network.

### Step 4: Configuring Node-RED Flows

1. In Node-RED, create flows that handle the communication between the database, MQTT broker, and ESP32 subscriber.
2. Use MQTT nodes to send and receive messages between Node-RED and the ESP32 subscriber.
3. Use database nodes to insert or retrieve data from the database based on the received MQTT messages.
4. Test the flows to ensure data exchange is working correctly between Node-RED, the database, and the ESP32 subscriber.