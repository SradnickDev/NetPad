# NetPadButton

The `NetPadButton` class is a networked controller component that captures and synchronizes button states between a client device and a server. It inherits from `NetPadClientController<ButtonMessage>` and implements Unity's pointer event interfaces for UI interaction.

## Configuration

**Identifier**: A unique string to identify different button instances. Use this to differentiate between multiple buttons on the same controller (e.g., "JumpButton", "FireButton").

## Core Methods

* **Reset()**: Initializes the button component reference when the script is applied to a GameObject
* **Awake()**: Ensures the button component reference is properly set up
* **IsSupported()**: Always returns true (button functionality is universally supported)
* **UpdateData(ButtonMessage message)**: Updates the ButtonMessage with current button state
* **HasChanged()**: Determines if the button state has changed since last update

## Unity UI Integration

NetPadButton implements Unity's pointer event interfaces:

* **IPointerDownHandler**: `OnPointerDown(PointerEventData eventData)`
  - Triggered when pointer/finger presses down on the button
  - Sets button state to `ButtonState.Down`
  - Immediately sends update to server

* **IPointerClickHandler**: `OnPointerClick(PointerEventData eventData)`  
  - Triggered when pointer is released on the same button (complete click)
  - Sets button state to `ButtonState.Up`
  - Sends final button state to server

* **IPointerUpHandler**: `OnPointerUp(PointerEventData eventData)`
  - Triggered when pointer is released (even if dragged outside button)
  - Resets button state to `ButtonState.None` if released outside button area
  - Ensures proper state cleanup

## Button States

- **None**: Default state, button not being interacted with
- **Down**: Button is currently pressed down
- **Up**: Button was just released (single frame state)

## Server Access

Access button states on the server side via:
```csharp
// Get specific button by identifier
var jumpButton = player.Input.GetButton("JumpButton");
if (jumpButton.IsDown)
{
    // Handle button press
}

// Or check button state directly
if (player.Input.GetButtonDown("FireButton"))
{
    // Handle button down event
}
```

## Usage Tips

- Attach to any GameObject with a Button or UI element
- Set unique identifiers for each button to distinguish them on the server
- Button state changes are sent immediately for responsive gameplay
- Works with both touch and mouse input through Unity's event system
