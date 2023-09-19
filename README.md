# C210 Tapo camera
<p align="center">
<img src="/img/tapo_c210.jpg" height="300" width="300">
</p>
IP Cameras are a nightmare for our privacy. For this reason I am reverse engineering a Tp-Link Tapo C210's firmware and its relative app in order to prevent them from sending any data to untrusted servers.

There are some better resources than mine: see https://github.com/nervous-inhuman/tplink-tapo-c200-re and https://drmnsamoliu.github.io/, but use those resources mindfully, as they are about Tapo C200, whereas this repository focuses on the C210. Despite being esthetically equivalent and having a similar name, their hardware is completely different. The C200 is based on a MIPS microprocessor, whereas the C210 is based on the ARM-based MStar SSC335 chipset.

In particular, I will focus on 

* the reverse engineering of the app in order to be able to use the camera without a Tp-Link account;
* <del style="text-decoration: line-through;"> the reverse engineering of the firmware to strip off the portions of code sending the video stream to their servers, or better self-compile a clean firmware.</del> **Good news** you can install [OpenIPC](https://openipc.org/) ([here for our hardware-specific version](https://openipc.org/cameras/vendors/sigmastar/socs/ssc335), with memory chip NOR 8M) and [linux-chenxing](https://github.com/linux-chenxing), so we do not need any reverse engineering, at most we need to contribute to these projects.

## How these cameras were designed to work
1. You download a proprietary app (Tp-Link Tapo) and create an account without which the camera can not work;
2. You use said app to instruct the camera to use a specified Wi-Fi AP;
3. The camera sends the video stream not end-to-end encrypted to servers we have no control over;
4. You have the possibility to update the camera's firmware through its app. This expands the attack surface for a hacker or from the company itself to push a malicious update.

## What we can do
As of today, we have:
* Libre NVR solutions (iSpy, ZoneMinder, ...);
* A collection of open source software to control these cameras through [undocumented APIs](https://github.com/xfarrow/tapo-camera/tree/main/secret-apis), see [my collection](https://github.com/stars/xfarrow/lists/tapo-cameras).

Nonethless, if you use these solutions only, you still need the proprietary app and a Tp-Link account the first time you boot the camera up and NVRs will not stop the camera from sending the video stream to their servers without using a firewall.

* Installing [OpenIPC](https://openipc.org/) or [linux-chenxing](https://github.com/linux-chenxing)

## Disclaimer
The author(s) of this document are not affiliated to TpLink, Tapo, or any company. The instructions present here are not meant to be followed, but rather, they're used to demonstrate what these cameras are capable of. No warranty is provided if you follow these instructions. Remember that any unauthorized modification can result in unrecoverable malfunctioning, a void warranty, and infringement of law, especially if meant to compromise a 3rd person.
