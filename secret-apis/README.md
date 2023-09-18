# Secret APIs
Tapo cameras provide undocumented APIs we can use to control them (simulating the use of their official app).
You can download my [Insomnia](https://insomnia.rest/) API collection [at this link](https://github.com/xfarrow/tapo-camera/blob/main/secret-apis/TapoCameraAPIs.yaml). The collection is not complete yet.

I am writing this collection also by giving a look at the code of the awesome project [pytapo](https://github.com/JurajNyiri/pytapo).

## Getting a Stok
Each API call is in the form `https://{cameraa_ip}/stok={stok}/ds`, hence you need your camera's IP and a token, called stok. You can obtain the stok by calling `GetStok`. Keep in mind that this token expires every `x` minutes (I did not test the actual expiration time yet).

## Error codes
```
    -40401: Invalid stok value
    -40210: Function not supported
    -64303: Action cannot be done while camera is in patrol mode.
    -64324: Privacy mode is ON, not able to execute
    -64302: Preset ID not found
    -64321: Preset ID was deleted so no longer exists
    -40106: Parameter to get/do does not exist
    -40105: Method does not exist
    -40101: Parameter to set does not exist
    -40209: Invalid login credentials
    -64304: Maximum Pan/Tilt range reached
    -71103: User ID is not authorized
```

## More
The APIs provide more pieces of information than the official app. For example the camera somehow geotagged itself (I never gave the permission to the app to use location services, probably the camera is using public IP's location to determine its position). This is not clearly shown to the end user, and carries privacy and security implications. This further proves the necessity to create libre solutions for these cameras.
