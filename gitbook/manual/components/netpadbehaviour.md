# NetPadBehaviour

The `NetPadBehaviour` class is a custom MonoBehaviour class that helps manage networked GameObjects and provides access to networked input for those objects. It offers additional functionality compared to the standard MonoBehaviour for handling instantiation and removal of networked GameObjects in a multiplayer context.player properties



* **IsValid**: A property indicating whether the object is correctly instantiated and connected.
* **NetPadInput**: Provides access to networked input similar to `UnityEngine.Input`.
* **NetPadPlayer**: Stores a reference to the associated `NetPadPlayer` instance.
* **OnInstantiateInternal(NetPadPlayer player)**: An internal method called after a GameObject is instantiated with `NetPadPlayer.Instantiate` and triggers the `OnInstantiate()` method.
* **OnInstantiate()**: A virtual method that can be overridden to perform custom setup after a GameObject is instantiated using `NetPadPlayer.Instantiate`.
* **OnRemove()**: A virtual method that can be overridden to handle cleanup before a GameObject and related resources are removed when the associated client disconnects.

Any script that lives on a player gameobject can be derive from NetPadBehaviour instead of Monobehaviour.

A NetPadBehaviour is only valid if the gameobject it is attached to was created through NetPadPlayer.Instantiate.

