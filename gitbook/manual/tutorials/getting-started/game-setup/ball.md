# Ball

#### Script

Follow this step-by-step guide to create the given script:

Step 1: Create a new script

* In your Unity project, right-click in the 'Assets/RollABall/Common/Scripts' panel and select 'Create' > 'C# Script'. Name the script 'Ball'.

Step 2: Open the script in an editor

* Double-click the 'Ball' script in the 'Assets' panel to open it in your preferred code editor.

Step 3: Add namespaces

*   At the top of the script, replace the existing 'using' statements with the following:

    ```csharp
    using NetPad;
    using NetPad.Attributes;
    using RollABall.Common;
    using UnityEngine;
    using Random = UnityEngine.Random;
    ```

Step 4: Define the class and namespace and inherit from NetPadBehaviour

*   Replace the 'MonoBehaviour' inheritance with 'NetPadBehaviour' in the class definition:

    ```csharp
    namespace RollABall.Game
    {
        public class Ball : NetPadBehaviour
        {
        }
    }
    ```

Step 5: Add serialized fields and GetComponent attributes

*   Within the 'Ball' class, add the following serialized fields and GetComponent attributes:

    ```csharp
    [SerializeField, GetComponent] private Rigidbody Rigidbody;
    [SerializeField] private float Speed = 5f;
    [SerializeField, GetComponent(inChildren: true)] private MeshRenderer MeshRenderer;
    ```

Step 6: Override the OnInstantiate method

* Inside the 'Ball' class, override the OnInstantiate method and add the following code to set the random color for the player and the MeshRenderer:
* 'OnInstantiate' is called on NetPadBehaviour's when properly instantiated
* Properties, is a key value cache an can be used to sync values between game and controller

```csharp
public override void OnInstantiate()
{
    var rndColor = Random.ColorHSV();
    NetPadPlayer.Properties.SetPlayerColor(rndColor);
    MeshRenderer.material.color = rndColor;
}
```

Step 7: Create the FixedUpdate method

*   Add a private FixedUpdate method to handle the movement of the ball:

    ```csharp
    private void FixedUpdate()
    {
        Move();
    }
    ```

Step 8: Create the Move method

*   Implement the Move method to read the acceleration input from NetPadInput and apply force to the Rigidbody:

    ```csharp
    private void Move()
    {
        var direction = NetPadInput.GetAcceleration();
        if (direction == Vector2.zero)
        {
            return;
        }

        Rigidbody.AddForce(new Vector3(direction.x, 0, direction.y) * Speed, ForceMode.Acceleration);
    }
    ```

Step 9: Save and return to Unity

* Save the 'Ball' script in your code editor and return to the Unity editor. The script will automatically compile and be ready for use.

#### Prefab

* Create a Sphere inside a scene
* Add the Rigidbody component&#x20;
* Drag and drop the Ball script on to it.
* Rename the Sphere GameObject to 'Ball'.
* Drag and drop the the Ball GameObject into the Folder 'Assets/RollABall/Game/Prefabs
