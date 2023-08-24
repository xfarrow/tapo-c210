# How to connect to a NVR

Tested on: Tapo C210

## 1. Capabilities
This camera is capable of transmitting its stream on the RTSP protocol on two channels: one at resolution 640x360 and another one at resolution 1920x1080 (despite this model
has a 2K lens, the 2K stream is accessible through the official app only).
It supports the `ONVIF` standard.

## 2. Prerequisites
We need to create RTSP credentials. Using the official app we have to go to `Settings -> Advanced Settings -> Camera account`. We have to choose a `username` and a `password`

## 3.1. Simple RTSP stream:
High quality stream: `rtsp://username:password@IP_Address:554/stream1`

Low quality stream: `rtsp://username:password@IP_Address:554/stream2`

## 3.2. ONVIF
`http://IP_Address:2020/onvif/device_service`
and specify `username` and `password` when prompted to.