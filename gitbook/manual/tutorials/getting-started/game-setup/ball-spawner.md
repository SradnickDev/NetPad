# Ball Spawner

Follow this step-by-step guide to create the given script:

Step 1: Create a new script

* In your Unity project, right-click in the 'Assets/RollABall/Game/Scripts' panel and select 'Create' > 'C# Script'. Name the script 'BallSpawner'.

Step 2: Open the script in an editor

* Double-click the 'BallSpawner' script in the 'Assets' panel to open it in your preferred code editor.

Step 3: Add namespaces

*   At the top of the script, replace the existing 'using' statements with the following:

    ```csharp
    using System.Collections.Generic;
    using NetPad.Attributes;
    using NetPad.Server;
    using UnityEngine;
    ```

Step 4: Define the class and inherit from MonoBehaviour

*   Replace the 'MonoBehaviour' inheritance in the class definition to match the given script:

    ```csharp
    namespace RollABall.Game
    {
        public class BallSpawner : MonoBehaviour
        {
        }
    }
    ```

Step 5: Add serialized fields and FindObjectOfType attributes

*   Within the 'BallSpawner' class, add the following serialized fields and FindObjectOfType attributes:

    ```csharp
    [SerializeField, FindObjectOfType] private NetPadServer Server;
    [SerializeField, FindObjectOfType] private Ball BallPrefab;
    ```

Step 6: Create a dictionary for storing balls

*   Add a private dictionary for storing the instantiated ball objects:

    ```csharp
    private Dictionary<NetPadPlayer, Ball> m_balls = new Dictionary<NetPadPlayer, Ball>();
    ```

Step 7: Add the Start method

*   Implement the Start method to subscribe to the server's events:

    ```csharp
    private void Start()
    {
        Server.PlayerConnected += OnPlayerConnected;
        Server.PlayerDisconnected += OnPlayerDisconnected;
    }
    ```

Step 8: Implement OnPlayerConnected method

*   Add the OnPlayerConnected method to handle player connections and spawn a ball for the connected player:

    ```csharp
    private void OnPlayerConnected(NetPadPlayer netPadPlayer)
    {
        SpawnBall(netPadPlayer);
    }
    ```

Step 9: Implement SpawnBall method

* Add the SpawnBall method to instantiate a ball for the connected player
*   make sure to use 'NetPadPlayer.Instantiate' to properly instantiate and initialize NetPadBehaviour

    ```csharp
    private void SpawnBall(NetPadPlayer netPadPlayer)
    {
        var ball = NetPadPlayer.Instantiate(BallPrefab, Vector3.zero, Quaternion.identity, netPadPlayer);
        m_balls[netPadPlayer] = ball;
    }
    ```

Step 10: Implement OnPlayerDisconnected method

*   Add the OnPlayerDisconnected method to handle player disconnections and destroy the associated ball:

    ```csharp
    private void OnPlayerDisconnected(NetPadPlayer netPadPlayer)
    {
        DestroyBall(netPadPlayer);
    }
    ```

Step 11: Implement DestroyBall method

*   Add the DestroyBall method to remove the ball from the dictionary and destroy its GameObject:

    ```csharp
    private void DestroyBall(NetPadPlayer netPadPlayer)
    {
        if (m_balls.TryGetValue(netPadPlayer, out var ball))
        {
            Destroy(ball.gameObject);
            m_balls.Remove(netPadPlayer);
        }
    }
    ```

Step 12: Save and return to Unity

* Save the 'BallSpawner' script in your code editor and return to the Unity editor. The script will automatically compile and be ready for use.
