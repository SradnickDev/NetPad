# Buildpipeline

The BuildPipeline class is a ScriptableObject that automates and manages the building process of a Unity game or application and its controller. It provides separate build settings for the game and controller, keeps a log of build processes, and allows for post-build actions like copying the controller to StreamingAssets and running the game scene.

* Holds separate build settings for the game and controller
* Stores logs for build processes, including messages, timestamps, and log types
* Runs the game scene after the build process if specified
* Copies the controller to StreamingAssets upon a successful build if specified
* Provides methods for building the game, controller, or both together
* Automatically switches the build target back to the original platform after the build is complete
