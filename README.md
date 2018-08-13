# Memcached DDOS Attack

A memcached distributed denial-of-service (DDoS) attack is a type of cyber attack in which an attacker attempts to overload a targeted victim with Internet traffic. The attacker spoofs requests to a vulnerable UDP memcached* server, which then floods a targeted victim with Internet traffic, potentially overwhelming the victim’s resources. While the target’s Internet infrastructure is overloaded, new requests cannot be processed and regular traffic is unable to access the Internet resource, resulting in denial-of-service.

Memcached amplification can be thought of in the context of a malicious teenager calling a restaurant and saying "I’ll have one of everything, please call me back and tell me my whole order." When the restaurant asks for a callback number, the number given is the targeted victim’s phone number. The target then receives a call from the restaurant with a lot of information that they didn’t request.

This method of amplification attack is possible because memcached servers have the option to operate using the UDP protocol. UDP is a network protocol that allows for the sending of data without first getting what’s known as a handshake, which is a network process where both sides agree to the communication. UDP is utilized because the targeted host is never consulted on whether or not they’re willing to receive the data, allowing for a massive amount of data to be sent to the target without their prior consent.

A memcached attack occurs in 4 steps:

    1. An attacker implants a large payload* of data on an exposed memcached server.
    2. Next the attacker spoofs an HTTP GET request with the IP address of the targeted victim.
    3. The vulnerable memcached server that receives the request, which is trying to be helpful by responding, sends a large   response to the target.
    4. The targeted server or its surrounding infrastructure is unable to process the large amount of data sent from the memcached server, resulting in overload and denial-of-service to legitimate requests.


## Getting Started

The steps to set up the environement. 

### Prerequisites

1. Shodan : It is a search engine that lets the user find specific types of computers (webcams, routers, servers, etc.) connected to the internet using a variety of filters. Some have also described it as a search engine of service banners, which are metadata that the server sends back to the client. 

2. Wireshark : It is a free and open source packet analyzer. It is used for network troubleshooting, analysis, software and communications protocol development, and education.

### Installing

You need Python 3.x installed.
```
apt-get install python3
```
A tool named wireshark will also be needed to capture the UDP pacckets.
Install wireshark on Ubuntu systems using the following commands.

Step 1: Add the stable official PPA. To do this, go to terminal by pressing Ctrl+Alt+T and run:

```
sudo add-apt-repository ppa:wireshark-dev/stable
```

Step 2: Update the repository:

```
sudo apt-get update
```

Step 3: Install wireshark 2.0:

```
sudo apt-get install wireshark
```

Step 4: Run wireshark:

```
sudo wireshark
```

If you get a error couldn't run /usr/bin/dumpcap in child process: Permission Denied. go to the terminal again and run:

```
sudo dpkg-reconfigure wireshark-common
```
You also require to have Scapy and Shodan modules installed

```
pip install scapy
```

```
pip install shodan
```

## Running the attack

```
python memcrashed.py
```

### Observations

The following results were observed on running the attack.
![alt text](https://github.com/chichra/Special-Topics-in-Information-Theory/blob/master/1.png)
![alt text](https://github.com/chichra/Special-Topics-in-Information-Theory/blob/master/2.png)
![alt text](https://github.com/chichra/Special-Topics-in-Information-Theory/blob/master/wireshark.png)
