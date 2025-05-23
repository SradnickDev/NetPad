# NetPadDPad

The `NetPadDPad` class is a networked controller component that captures and synchronizes D-pad input between a client device and a server. It inherits from `NetPadClientController` and uses `DPadMessage` for data transfer.



* **Identifier**: A unique string to identify different instances.&#x20;
* **MultipleDirection**: A boolean flag to allow or disallow multiple simultaneous directions (e.g., right and down).
* **IsSupported()**: Always returns true, indicating that D-pad functionality is supported.
* Set(DPadButton button): Adds a D-pad button to the internal list if it is not already present and if the list has fewer than 4 buttons.
* UpdateData(DPadMessage message): Updates the DPadMessage with the latest D-pad input.
* HasChanged(): Determines if any D-pad input has changed.
* OnButtonDown(DPadButton button) and OnButtonUp(DPadButton button): Event handlers for button press and release events.



`NetPadDPad` efficiently utilizes network resources and ensures accurate synchronization of device D-pad information in networked games or applications.
