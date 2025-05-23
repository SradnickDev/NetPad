# LayoutListener

The `LayoutListener` class is a MonoBehaviour that listens for layout changes in a Unity application. It allows you to define a list of layout callbacks that will be triggered when a layout change message is received.

Properties:

* `LayoutCallbacks`: A public list of `LayoutCallback` objects. Each `LayoutCallback` consists of a layout name and a UnityEvent to be invoked when the corresponding layout change is detected.

Fields:

* `Client`: A serialized field referencing the `NetPadClient` object. The script uses this reference to subscribe and unsubscribe from layout change messages.

Methods:

* `OnEnable()`: Called when the script is enabled. Subscribes the `OnReceive` method to the `LayoutMessage` event in the `NetPadClient`'s message processor.
* `OnDisable()`: Called when the script is disabled. Unsubscribes the `OnReceive` method from the `LayoutMessage` event in the `NetPadClient`'s message processor.
* `OnReceive(LayoutMessage message)`: Called when a `LayoutMessage` is received. Invokes the `ChangeLayout` method with the identifier of the new layout.
* `ChangeLayout(string layoutName)`: Takes a layout name as a parameter and iterates through the `LayoutCallbacks` list to find a matching layout name. If found, it invokes the associated UnityEvent.

The `LayoutListener` class makes it easy to manage layout changes in a Unity application by reacting to layout change messages and triggering the appropriate UnityEvents. This can be useful in various scenarios, such as adapting the user interface to different input devices or screen orientations.

\


<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>
