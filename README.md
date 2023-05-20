# Mosquitto with Flask

## Setup
Install this command using the following command for arch linux:
```bash
yay -S mosquitto
```
and if your using ubuntu:
```bash
sudo apt-add-repository ppa:mosquitto-dev/mosquitto-ppa
sudo apt-update
sudo apt-get install mosquitto mosquitto-clients
```
enable and run the mosquitto
```bash
sudo systemctl enable mosquitto.service
sudo systemctl start mosquitto.service
```
## Mosquitto Clients
Now we will get into how to subscribe and publish messages using command line tools.

Enter in the command prompt as follows to subscribe to the topic ‘sensors/altimeter/1

```bash
mosquitto_sub -V mqttv311 -t sensors/altimeter/1 -d
```

-V determines the mqtt version we are using, here we use 3.1.1. Then the topic comes after the -t. -d means debug mode, so we can view what happens under the hood.

Here we have used our localhost. If we want to use any other server we can do it by me including -h followed by the IP address or name of the server.

The output is as follows:
![Output Picture](./Docs/mqtt-command-output.png)

using this command we publish new message and then we can see the results in the output.
```bash
mosquitto_pub -V mqttv311 -t sensors/altimeter/1 -m "100 feet" -d
```
The difference from subscribing is instead of mosquitto_sub we have used mosquitto_pub and we have an additional -m to denote the message.

The output will be as follows:
![Output](./Docs/mqtt-sub-out-2.png)

## Subscribe and publish using python
Paho-mqtt-python is a Python implementation of MQTT and we will use python to subscribe and publish messages.
for installing paho:
```bash
pip3 install paho-mqtt==1.3.1
```







## Resources
https://medium.com/@ashiqgiga07/mqtt-with-python-part-1-a38e64308c76

