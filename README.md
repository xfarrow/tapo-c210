# Tapo camera
IP Cameras are a nightmare for our privacy. For this reason I am reverse engineering a Tp-Link Tapo C210's firmware and its relative app in order to prevent them from sending any data to untrusted servers.
There are better resources than mine: see https://github.com/nervous-inhuman/tplink-tapo-c200-re and https://drmnsamoliu.github.io/. 

In particular, I will focus on 
* the reverse engineering of the app in order to be able to use the camera without a Tp-Link account;
* the reverse engineering of the firmware to strip off the portions of code sending the video stream to their servers.

## How these cameras were designed to work
1. You download a proprietary app (Tp-Link Tapo) and create an account without which the camera can not work;
2. You use said app to instruct the camera to use a specified Wi-Fi AP;
3. The camera sends the video stream not end-to-end encrypted to servers we have no control over;
4. You have the possibility to update the camera's firmware through its app. This expands the attack surface for a hacker or from the company itself to push a malicious update.

## What we can do
As of today, we have:
* Libre NVR solutions (iSpy, ZoneMinder, ...);
* A collection of open source software to control these cameras through [undocumented APIs](https://github.com/xfarrow/tapo-camera/tree/main/secret-apis), see [my collection](https://github.com/stars/xfarrow/lists/tapo-cameras).

Nonethless, you still need the proprietary app and a Tp-Link account the first time you boot the camera up and NVRs will not stop the camera from sending the video stream to their servers without using a firewall.

This repository aims to resolve these issues.
