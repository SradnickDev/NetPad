# Multi-Touch + Gestures

NetPad provides comprehensive multi-touch support and gesture recognition for creating intuitive mobile controller experiences.

## Touch Input System

### NetPadTouch Component

The `NetPadTouch` component captures and synchronizes multi-touch input between client and server:

- **TouchArea**: Optional RectTransform defining the touch-sensitive area
- **Multi-touch Support**: Tracks multiple fingers simultaneously by finger ID
- **Screen Coordinates**: Provides both absolute and screen-relative coordinates
- **Delta Tracking**: Calculates movement deltas between updates
- **Tap Count**: Supports tap counting for gesture detection

### Touch Data Properties

Each touch provides:
- **Position**: Absolute screen position
- **Delta**: Movement since last update
- **ScreenRelative**: Normalized coordinates (0-1)
- **ScreenRelativeDelta**: Normalized movement delta
- **FingerId**: Unique identifier for tracking
- **Phase**: TouchPhase (Began, Moved, Stationary, Ended, Canceled)
- **TapCount**: Number of taps detected
- **IsInsideTouchArea**: Whether touch is within defined TouchArea

## Gesture Recognition System

### GestureRecognition Component

The `GestureRecognition` component manages gesture detection and provides two categories of gestures:

#### Single-Touch Gestures
- **SwipeGesture**: Directional swipes with configurable minimum distance
- **DoubleTapGesture**: Double-tap detection with time and distance thresholds

#### Multi-Touch Gestures
- **PinchGesture**: Pinch-to-zoom with scale factors and velocity
- **RotateGesture**: Two-finger rotation with angle tracking

### Gesture States

All gestures follow a state machine:
- **Possible**: Ready to detect gesture
- **Began**: Gesture started
- **Updated**: Gesture continuing (multi-touch only)
- **Ended**: Gesture completed
- **Failed**: Gesture recognition failed

## Implementation Guide

### Basic Touch Setup

1. Add `NetPadTouch` component to your controller scene
2. Optionally configure TouchArea for UI boundaries
3. Access touch data on server via `NetPadInput.Touches`

```csharp
// Server-side touch access
foreach (var touch in player.Input.Touches)
{
    if (touch.Phase == TouchPhase.Began)
    {
        Debug.Log($"Touch began at {touch.Position}");
    }
}
```

### Gesture Recognition Setup

1. Add `NetPadGesture` component to controller scene
2. Add `GestureRecognition` component for advanced gestures
3. Configure gesture parameters (thresholds, distances, timing)
4. Listen for gesture events on server side

```csharp
// Server-side gesture handling
player.Input.GestureRecognized += OnGestureRecognized;

void OnGestureRecognized(GestureEventData gestureData)
{
    if (gestureData is SwipeGestureEventData swipeData)
    {
        Debug.Log($"Swipe detected: {swipeData.Direction}");
    }
    else if (gestureData is PinchGestureEventData pinchData)
    {
        Debug.Log($"Pinch scale: {pinchData.CurrentScaleFactor}");
    }
}
```

## Gesture Event Data

### SwipeGestureEventData
- **StartPosition**: Where swipe began
- **EndPosition**: Where swipe ended
- **Direction**: SwipeDirection (Left, Right, Up, Down)
- **Duration**: Time taken for swipe
- **Velocity**: Speed of swipe movement

### DoubleTapGestureEventData
- Basic gesture event (position available from touch data)

### PinchGestureEventData
- **DeltaVector**: Change in centroid position
- **Delta**: Distance change since last update
- **Velocity**: Speed of pinch movement
- **CumulativeScaleFactor**: Total scale since gesture start
- **CurrentScaleFactor**: Current scale factor
- **Centroid**: Center point between fingers
- **Angle**: Angle between touch points

### RotateGestureEventData
- **AngleDelta**: Rotation change since last update
- **TotalRotation**: Total rotation since gesture start
- **Centroid**: Center point of rotation
- **RotationVelocity**: Speed of rotation in degrees/second

## Configuration Options

### Gesture Parameters
- **MinSwipeDistance**: Minimum distance for swipe detection (default: 100f)
- **MaxTimeBetweenTaps**: Double-tap time threshold (default: 0.5f)
- **MaxDistanceBetweenTaps**: Double-tap distance threshold (default: 50f)
- **NoiseFilterThreshold**: Rotation noise filtering (default: 0.5f)

### Performance Optimization

NetPad optimizes network traffic through:
- **Threshold-based updates**: Only send changes above configured thresholds
- **Frequency separation**: OnUpdate() for immediate changes, OnTick() for position updates
- **Delta compression**: Send only movement changes, not absolute positions
- **Touch area filtering**: Limit updates to relevant UI areas