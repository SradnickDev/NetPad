# NetPadGyroscope

The `NetPadGyroscope` class is a networked controller component that captures and synchronizes gyroscope data between a client device and a server. It inherits from `NetPadClientController` and uses `GyroscopeMessage` for data transfer.



* **Identifier**: A unique string to identify different instances.
* **Threshold**: Minimum change for gyroscope data to be considered updated.
* **IsSupported()**: Checks if the device supports gyroscope functionality.
* **UpdateData(GyroscopeMessage message)**: Updates the `GyroscopeMessage` with the latest gyroscope data.
* **HasChanged()**: Determines if any gyroscope data has changed beyond the specified threshold.

`NetPadGyroscope` efficiently utilizes network resources and ensures accurate synchronization of device gyroscope information in networked games or applications.

\
