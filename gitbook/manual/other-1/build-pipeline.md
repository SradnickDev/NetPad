# Build Pipeline

A custom ScriptableObject-based build pipeline specifically designed to streamline the dual-target build process for NetPad applications. The build pipeline automates building both the game (server) and controller (client) in a single operation.

## Features

### Dual-Target Building
- **Game Build Settings**: Configure standalone game executable
  - Build target (e.g., StandaloneWindows64)
  - Scene list for game builds
  - Destination path for game executable
  - Development build options
- **Controller Build Settings**: Configure Android controller APK
  - Build target (Android)
  - Scene list for controller builds  
  - Destination path for APK output
  - Development build options

### Automation Features
- **Automatic APK Copy**: Copies built controller APK to StreamingAssets folder for web distribution
- **Sequential Building**: Builds controller first, then game (or vice versa)
- **Destination Cleanup**: Option to clear destination folders before building
- **Scene Execution**: Option to run the first game scene after successful build

## Configuration

### Build Settings Structure
```csharp
[Serializable]
public class BuildSettings
{
    public BuildTarget BuildTarget;
    public List<string> Scenes;
    public string DestinationPath;
    public bool DevelopmentBuild;
    public bool ConnectProfiler;
    public bool ScriptDebugging;
    public bool ClearDestinationFolderBeforeBuild;
}
```

### Pipeline Settings
- **GameBuildSettings**: Configuration for standalone game builds
- **ControllerBuildSettings**: Configuration for Android controller builds
- **RunSceneAfterBuild**: Whether to launch first scene after building
- **CopyController**: Whether to copy APK to StreamingAssets

## Usage

### Creating Build Pipeline
1. Right-click in Project window
2. Navigate to `Create > NetPad > Build Pipeline`
3. Configure build settings for both targets
4. Set appropriate scenes and destination paths

### Build Process
1. Configure Game section:
   - Add game scenes
   - Set build target (e.g., StandaloneWindows64)
   - Set destination path
2. Configure Controller section:
   - Add controller scenes
   - Set build target to Android
   - Set APK destination path
3. Click "Build Controller & Game" to start automated build

## Development Workflow Benefits

- **Faster Iterations**: Single-click building of both targets
- **Consistent Output**: Standardized build process reduces errors
- **Web Distribution Ready**: Automatic APK copying for web server distribution
- **Development Optimization**: Built-in support for development builds and profiling
- **Scene Testing**: Option to immediately test builds after completion

The build pipeline significantly reduces manual build processes and increases development productivity by handling the complex dual-target nature of NetPad applications automatically.
