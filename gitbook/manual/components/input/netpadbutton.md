# NetPadButton

The `NetPadButton` class is a networked controller component that captures and synchronizes button states between a client device and a server. It inherits from `NetPadClientController` and implements `IPointerDownHandler`, `IPointerClickHandler`, and `IPointerUpHandler` to handle button interactions. The class uses `ButtonMessage` for data transfer.



**Identifier**: A unique string to identify different instances of the button.

* **Reset**(): Initializes the button component reference when the script is applied to a GameObject.
* **Awake**(): Initializes the button component reference when the script awakes.
* **IsSupported**(): Checks if the button functionality is supported on the device.
* **UpdateData**(ButtonMessage message): Updates the ButtonMessage with the latest button state data.
* **HasChanged**(): Determines if the button state has changed.

Unity Callbacks:

* `OnPointerDown(PointerEventData eventData)`: Triggered when the pointer is pressed down on the button. Sets the button state to `Down` and updates the data.
* `OnPointerClick(PointerEventData eventData)`: Triggered when the pointer is released on the same button. Sets the button state to `Up` and updates the data.
* `OnPointerUp(PointerEventData eventData)`: Triggered when the pointer is released. Resets the button state to `None` if the pointer was released outside the button.

`NetPadButton` efficiently utilizes network resources and ensures accurate synchronization of button states in networked games or applications. The class also provides methods to handle button interactions and update button states accordingly.
