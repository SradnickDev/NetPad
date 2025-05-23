# Background - Player Properties

Follow this step-by-step guide to create the given script:

Step 1: Create a new script

* In your Unity project, right-click in the 'Assets' panel and select 'Create' > 'C# Script'. Name the script 'Background'.

Step 2: Open the script in an editor

* Double-click the 'Background' script in the 'Assets' panel to open it in your preferred code editor.

Step 3: Add namespaces

*   At the top of the script, replace the existing 'using' statements with the following:

    ```csharp
    using NetPad.Attributes;
    using NetPad.Client;
    using RollABall.Common;
    using UnityEngine;
    using UnityEngine.UI;
    ```

Step 4: Define the class and inherit from MonoBehaviour

*   Replace the 'MonoBehaviour' inheritance in the class definition to match the given script:

    ```csharp
    public class Background : MonoBehaviour
    {
    }
    ```

Step 5: Add serialized fields and GetComponent attributes

*   Within the 'Background' class, add the following serialized fields and GetComponent attributes:

    ```csharp
    [SerializeField, FindObjectOfType] private NetPadClient Client;
    [SerializeField, GetComponent] private Image BackgroundImage;
    ```

Step 6: Implement the Start method

*   Add a private Start method to subscribe to the client's PropertyChanged event:

    ```csharp
    private void Start()
    {
        Client.Properties.PropertyChanged += OnPropertyChanged;
    }
    ```

Step 7: Implement the OnPropertyChanged method

*   Add the OnPropertyChanged method to handle property changes and update the background color:

    ```csharp
    private void OnPropertyChanged(string key, object newValue, object oldValue)
    {
        if (NetPadConstants.Property.PlayerColor == key)
        {
            BackgroundImage.color = (Color)newValue;
        }
    }
    ```

Step 8: Save and return to Unity

* Save the 'Background' script in your code editor and return to the Unity editor. The script will automatically compile and be ready for use.

The background color will change based on the player's color property received from the NetPad client.
