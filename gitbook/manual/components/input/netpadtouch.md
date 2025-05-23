# NetPadTouch

The `NetPadTouch` class is a networked controller component that captures and synchronizes touch input between a client device and a server. It inherits from `NetPadClientController` and uses `TouchMessage` for data transfer.

**TouchArea**: A RectTransform defining the area in which touch input will be recognized and synced to the server/game.

* **IsSupported()**: Checks if the device supports touch input.
* **UpdateData(TouchMessage message):** Updates the TouchMessage with the latest touch input.
* **HasChanged():** Always returns true, indicating that touch input is considered changed.
* **OnUpdate():** Called during the update cycle if the client is connected and touch input has changed.
* **OnTick()**: Called during the tick cycle if any touch position has changed.

NetPadTouch efficiently utilizes network resources and ensures accurate synchronization of device touch information in networked games or applications. The class also provides helper methods to validate touch capacity, detect touch phase changes, and retrieve previous touch data for a given finger ID.
