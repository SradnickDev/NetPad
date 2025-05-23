# NetPadBehaviour

The `NetPadBehaviour` class is a custom MonoBehaviour that provides convenient access to NetPad's input system and player management. It serves as a base class for scripts that need to interact with mobile controller input and player-specific data.

## Core Properties

* **IsValid**: Boolean property indicating whether the object is correctly instantiated and connected to a NetPadPlayer
* **NetPadInput**: Direct access to the networked input system, equivalent to `NetPadPlayer.Input`
* **NetPadPlayer**: Reference to the associated NetPadPlayer instance that owns this GameObject

## Lifecycle Methods

* **OnInstantiateInternal(NetPadPlayer player)**: Internal method called automatically after GameObject instantiation via `NetPadPlayer.Instantiate`
* **OnInstantiate()**: Virtual method for custom initialization logic after proper NetPad instantiation
* **OnRemove()**: Virtual method for cleanup logic before GameObject removal when client disconnects

## Usage Pattern

### Deriving from NetPadBehaviour
```csharp
public class PlayerController : NetPadBehaviour
{
    public override void OnInstantiate()
    {
        // Custom setup after NetPad instantiation
        Debug.Log($"Player {NetPadPlayer.PlayerId} connected");
    }
    
    private void Update()
    {
        if (!IsValid) return;
        
        // Access input directly through NetPadInput
        var joystick = NetPadInput.GetJoystick("MovementStick");
        if (joystick.Magnitude > 0.1f)
        {
            transform.Translate(joystick.Position * speed * Time.deltaTime);
        }
        
        // Check button input
        if (NetPadInput.GetButtonDown("JumpButton"))
        {
            Jump();
        }
    }
    
    public override void OnRemove()
    {
        // Cleanup before player disconnection
        SavePlayerData();
    }
}
```

## Instantiation Requirement

**Important**: NetPadBehaviour components are only valid when the GameObject is created through `NetPadPlayer.Instantiate()`. Objects created through standard Unity instantiation methods will have `IsValid = false`.

### Proper Instantiation
```csharp
// Server-side player instantiation
void OnPlayerConnected(NetPadPlayer player)
{
    var playerObject = player.Instantiate(playerPrefab, spawnPosition, Quaternion.identity);
    // NetPadBehaviour components on playerObject will now be valid
}
```

## Benefits Over MonoBehaviour

- **Automatic Input Access**: No need to manually find or reference NetPadInput
- **Player Context**: Direct access to the owning NetPadPlayer
- **Lifecycle Management**: Built-in hooks for instantiation and removal
- **Validation**: `IsValid` property ensures proper setup before using NetPad features

## Best Practices

- Always check `IsValid` before accessing NetPad-specific functionality
- Use `OnInstantiate()` for setup that requires NetPad context
- Implement `OnRemove()` for graceful cleanup on player disconnection
- Prefer NetPadBehaviour over MonoBehaviour for player-specific scripts

