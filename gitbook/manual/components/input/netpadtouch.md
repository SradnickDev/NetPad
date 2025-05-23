# NetPadTouch

The `NetPadTouch` class is a networked controller component that captures and synchronizes multi-touch input between a client device and a server. It inherits from `NetPadClientController<TouchMessage>` and provides comprehensive touch tracking capabilities.

## Configuration

**TouchArea**: Optional RectTransform defining the area in which touch input will be recognized and synced to the server/game. When configured, provides `IsInsideTouchArea` information for each touch.

## Core Methods

* **IsSupported()**: Checks if the device supports touch input using `Input.touchSupported`
* **UpdateData(TouchMessage message)**: Updates the TouchMessage with latest touch data from `Input.touches`
* **HasChanged()**: Always returns true for custom touch change detection
* **OnUpdate()**: Called when touch count or phase changes (immediate updates)
* **OnTick()**: Called when any touch position changes (position tracking)

## Touch Data Provided

Each touch in the synchronized data includes:
- **Position**: Absolute screen coordinates
- **Delta**: Movement since previous update
- **ScreenRelative**: Normalized coordinates (0-1 based on screen size)
- **ScreenRelativeDelta**: Normalized movement delta
- **FingerId**: Unique identifier for tracking multiple touches
- **Phase**: Current TouchPhase (Began, Moved, Stationary, Ended, Canceled)
- **TapCount**: Number of taps detected
- **IsInsideTouchArea**: Whether touch is within configured TouchArea (if set)
- **TouchAreaSize**: Size of the configured TouchArea (if set)

## Performance Optimization

NetPadTouch uses intelligent change detection:
- **Touch Count Changes**: Immediate updates when fingers are added/removed
- **Phase Changes**: Immediate updates when any touch phase changes
- **Position Changes**: Frequent updates only when touch positions move
- **Finger Tracking**: Maintains previous touch data to calculate accurate deltas

## Server Access

Access touch data on the server side via:
```csharp
// Get all current touches
var touches = player.Input.Touches;
int touchCount = player.Input.TouchCount;

// Process each touch
foreach (var touch in touches)
{
    if (touch.Phase == TouchPhase.Began)
    {
        // Handle new touch
    }
}
```

This component efficiently utilizes network resources by sending updates only when meaningful changes occur, ensuring accurate synchronization of multi-touch input in networked games.
