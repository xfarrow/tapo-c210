# Tapo camera
IP Cameras are a nightmare for our privacy. For this reason I am reverse engineering a Tp-Link Tapo C210's firmware and its relative app in order to prevent them from sending any data to untrusted servers.

## How these cameras were designed to work
1. You download a proprietary app (Tp-Link Tapo) and create an account without which the camera can not work;
2. You use said app to instruct the camera to use a specified Wi-Fi AP;
3. The camera sends the video stream not end-to-end encrypted to servers we have no control over;
4. You have the possibility to update the camera's firmware through its app. This expands the attack surface for a hacker or from the company itself to push a malicious update.

## What we can do
As of today, we have libre NVR solutions we can use in place of the proprietary app, but you still need it the first time you boot the camera up and NVRs will not stop the camera from sending the video to their servers without using a firewall.

This repository aims to resolve these issues.

## What we know so far
### Tapo C200
* It runs a Linux kernel (3.10);

### Tapo C210
* It uses a Linux Kernel (4.9.84)

## Download
There's nothing yet.
