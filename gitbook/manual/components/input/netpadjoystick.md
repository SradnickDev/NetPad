# NetPadJoystick

The `NetPadJoystick` class is a networked controller component that captures and synchronizes virtual joystick input between a client device and a server. It inherits from `NetPadClientController<JoystickMessage>` and provides analog stick functionality for mobile controllers.

## Configuration

* **Identifier**: A unique string to identify different joystick instances (e.g., "LeftStick", "RightStick")
* **Threshold**: Minimum change value for joystick input to be considered updated (optimizes network traffic)
* **JoystickBehaviour**: Reference to the UI joystick component that handles visual interaction

## Core Methods

* **IsSupported()**: Always returns true (virtual joystick functionality is universally supported)
* **UpdateData(JoystickMessage message)**: Updates the JoystickMessage with latest joystick position and magnitude
* **HasChanged()**: Determines if joystick input has changed beyond the specified threshold

## Joystick Data

The joystick provides:
- **Position**: Vector2 representing joystick direction and magnitude (-1 to 1 on each axis)
- **Magnitude**: Float value representing the distance from center (0 to 1)
- **Normalized Direction**: Unit vector representing pure direction

## JoystickBehaviour Integration

The `JoystickBehaviour` component handles the visual representation and touch interaction:
- Manages the joystick handle movement within bounds
- Converts touch input to normalized position values
- Provides visual feedback for user interaction
- Automatically returns to center when released

## Server Access

Access joystick data on the server side via:
```csharp
// Get specific joystick by identifier
var leftStick = player.Input.GetJoystick("LeftStick");
Vector2 movement = leftStick.Position;
float magnitude = leftStick.Magnitude;

// Use joystick input for player movement
if (magnitude > 0.1f) // Dead zone
{
    transform.Translate(movement * speed * Time.deltaTime);
}
```

## Performance Optimization

- **Threshold filtering**: Only sends updates when movement exceeds the threshold value
- **Dead zone support**: Prevents jitter when joystick is near center position
- **Magnitude calculation**: Provides both direction and intensity in a single value

## Usage Tips

- Set appropriate threshold values to balance responsiveness and network efficiency
- Use unique identifiers when implementing multiple joysticks
- Consider dead zones in your game logic to prevent unwanted movement
- The visual JoystickBehaviour component handles all UI interaction automatically

