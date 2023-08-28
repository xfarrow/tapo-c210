# Secret APIs
Tapo cameras provide non-documented APIs we can use to control the camera (like using its official app). I did not do anything, 
I am writing this document while looking at the code of the awesome project [pytapo](https://github.com/JurajNyiri/pytapo), which seems it does not have a documentation on
the usage of the APIs yet.

## Preface
The APIs are accessed via `HTTP` requests.

## Headers
There are the headers `pytapo` uses, probably not all of them are necessary:
```
> Host: [camera ip]
> Content-Type: application/json; charset=UTF-8
> User-Agent: Tapo CameraClient Android
> Accept: application/json
> Accept-Encoding: gzip, deflate
> Connection: close
> requestByApp: true
```

You must use these headers for each call.

## Error codes
    "-40401": "Invalid stok value",
    "-40210": "Function not supported",
    "-64303": "Action cannot be done while camera is in patrol mode.",
    "-64324": "Privacy mode is ON, not able to execute",
    "-64302": "Preset ID not found",
    "-64321": "Preset ID was deleted so no longer exists",
    "-40106": "Parameter to get/do does not exist",
    "-40105": "Method does not exist",
    "-40101": "Parameter to set does not exist",
    "-40209": "Invalid login credentials",
    "-64304": "Maximum Pan/Tilt range reached",
    "-71103": "User ID is not authorized",

## Get token
To use the camera's functionalities, we need to get a token first (also called stok).

Create a `POST` request to `https://ip_of_your_camera`
with this `JSON` body

```
{
	"method": "login",
	"params" : {
		"hashed" : true,
		"password" : "MD5_UPPERCASE_HASH_OF_YOUR_TPLINK_ACCOUNT",
		"username" : "admin"
	}
}
```
You must provide the value `admin` for `username`, and the MD5 hash of your Tp-Link account's password as the value of `password`. You will get a token named `stok`.

## Move the camera's motors
Create a `POST` request to `https://ip_of_your_camera/stok=(your_stok)/ds`
with this `JSON` body
```
{
	"method": "do", 
	"motor": {
		"movestep": {
			"direction": "(direction_value)"
		}
	}
}
```
`direction` can be one of these values

direction | description
-------|:-----------
0 | It will move horizontally to 0°
90 | It will move vertically to the uppermost point
180 | It will move horizontally to 360° (yes)
270 | Il will move vertically to the bottommost point
