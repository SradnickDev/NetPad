# Build

#### Build Pipeline Setup Guide

Follow these step-by-step instructions to properly set up your Build Pipeline:

1. Right-click on your RollABall folder, then choose 'Create > NetPad > BuildPipeline'. This will create the BuildPipeline ScriptableObject.
2. The upper section contains build information for the game itself:&#x20;
   1. Click on the small '+' sign to add a slot for a scene.&#x20;
   2. Add the previously created Game scene to the empty slot.&#x20;
   3. Set BuildTarget to "Standalone Windows 64".
3. The lower section contains build information for the Controller:&#x20;
   1. At the bottom of the inspector, click on the small '+' sign to add a slot for a scene.&#x20;
   2. Add the previously created Game scene to the empty slot.&#x20;
   3. Set BuildTarget to "Android", ensuring that you have all required modules installed.
4. All default settings should be set, and no further changes are needed.
5. Click on 'Build Controller & Game' to begin the build process. This will build the Controller first, followed by the Game.



<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption><p>complete setup</p></figcaption></figure>
