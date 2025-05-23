# NetPad Constants

NetPad Constants provide a simple, organized way to manage predefined string constants for different input types like buttons, joysticks, gestures, and properties.

## Implementation

The constants are implemented as simple string constants within static classes:

```csharp
public class NetPadPropertyConstants : NetPadConstants
{
    public const string NickName = "NickName";
}

public class NetPadGestureConstants : NetPadConstants
{
    public const string LeftSwipe = "LeftSwipe";
    public const string RightSwipe = "RightSwipe";
    public const string DownSwipe = "DownSwipe";
    public const string UpSwipe = "UpSwipe";
    public const string Circle = "Circle";
}
```

## Available Constant Classes

- **NetPadPropertyConstants** - Predefined property names for player synchronization
- **NetPadButtonConstants** - Button identifiers (base class for custom constants)
- **NetPadJoystickConstants** - Joystick identifiers (base class for custom constants)
- **NetPadDpadConstants** - DPad identifiers (base class for custom constants)
- **NetPadGyroscopeConstants** - Gyroscope identifiers (base class for custom constants)
- **NetPadAcceleratorConstants** - Accelerometer identifiers (base class for custom constants)
- **NetPadLayoutConstants** - Layout identifiers (base class for custom constants)
- **NetPadGestureConstants** - Predefined gesture names

## Usage

Use these constants to maintain consistency across your project when identifying input components:

```csharp
// Using gesture constants
if (gestureEventData.Name == NetPadGestureConstants.LeftSwipe)
{
    // Handle left swipe
}

// Using property constants
player.SetProperty(NetPadPropertyConstants.NickName, "Player1");
```

This approach ensures type safety and prevents string typos while keeping the implementation simple and lightweight.
