# NetPadJoystick

The NetPadJoystick class is a networked controller component that captures and synchronizes joystick input between a client device and a server. It inherits from NetPadClientController and uses JoystickMessage for data transfer.



* **Identifier**: A unique string to identify different instances.&#x20;
* **Threshold**: Minimum change for joystick input to be considered updated.&#x20;
* **JoystickBehaviour**: A reference to the joystick input handling component.&#x20;
* **IsSupported()**: Always returns true, indicating that joystick functionality is supported. -&#x20;
* **UpdateData(JoystickMessage message)**: Updates the JoystickMessage with the latest joystick input.&#x20;
* **HasChanged()**: Determines if any joystick input has changed beyond the specified threshold

