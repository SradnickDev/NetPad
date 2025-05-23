# NetPadAccelerometer

The `NetPadAccelerometer` class is a networked controller component that captures and synchronizes accelerometer data between a client device and a server. It inherits from `NetPadClientController` and uses `AccelerometerMessage` for data transfer.



* **Identifier**: A unique string to identify and separate different instances.
* **Threshold**: Minimum change for accelerometer data to be considered updated.
* **IsSupported()**: Checks if the device supports accelerometer functionality.
* **UpdateData(AccelerometerMessage message)**: Updates the `AccelerometerMessage` with the latest accelerometer data.
* **HasChanged()**: Determines if accelerometer data has changed beyond the specified threshold.

\
`NetPadAccelerometer` ensures efficient use of network resources and accurate synchronization of device accelerometer information in networked games or applications.
