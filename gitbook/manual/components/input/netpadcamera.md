# NetPadCamera

The `NetPadCamera` class is a networked controller component that captures and synchronizes camera data between a client device and a server. It inherits from `NetPadClientController` and uses `CameraMessage` for data transfer.



* **CameraOrientation**: Enum to select either the front or back camera.&#x20;
* **Resolution**: A Vector2Int representing the desired camera resolution.&#x20;
* **Quality**: An integer value representing the image quality (0 to 100).&#x20;
* **TextureFormat**: The format of the texture used for the camera image.
* **Start**(): Initializes the camera, sets the background texture, and starts the camera.
* **IsSupported**(): Checks if the device supports camera functionality.
* **FindCameraDevice**(): Searches for and initializes the appropriate camera device based on the specified CameraOrientation.
* **HasChanged**(): Determines if the camera data has changed.
* **TakeSnapshot**(): Captures a snapshot from the camera, encodes it to JPEG format, and sets the m\_hasChanged flag.
* **UpdateData(CameraMessage message)**: Updates the CameraMessage with the latest camera data.

`NetPadCamera` efficiently utilizes network resources and ensures accurate synchronization of device camera information in networked games or applications. The class also provides methods to initialize the camera and take snapshots.
