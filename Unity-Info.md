Project creation and environment setup:

- Install Unity Editor
   - The minimum supported Unity version for Meta app development is 2021 LTS. I am using 2022.3.9f1
   - Download Unity Hub and install it. On the installs tab select Install editor and choose Unity version 2022.3.9f1.
- On the **Add Modules** window under **Platforms** select **Android Build Support** checkbox and then select **Android SDK &NDK Tools** and **Open JDK** checkboxes.
- Complete the installation.
- Creating a VR project in Unity
  - Open Unity Hub
  - On the projects tab, click New project. Select version 2022.3.9f1 for editor version.
- Select **3D Core template**
- Enter project name, location, and then click **Create Project**

Download Meta XR All-in-One SDK

1. Once inside the app navigate to Window > Package Manager to open the Unity Package Manager pane.

2.Go to the Unity Asset Store page and log in if needed.
https://assetstore.unity.com/packages/tools/integration/meta-xr-all-in-one-sdk-269657

3. Select Add to My Assets button.

4.Select Open in Unity to start the integration process with the Package Manager in Unity. If asked, allow Asset Store Links to be opened by Unity.

5. Wait for the Unity Package Manager window to open.

6. On the “Meta XR All-in-One SDK” pane, click Install.

7.When prompted to restart Unity, click Restart Editor.

8. Restart
![image](uploads/8a5d006f19a6de6dc48f05b534930059/image.png)


Set up Build Settings

The target platform for Meta Quest headsets is Android and the final output is an .apk file.

1) In Unity Editor, go to File > Build Settings.
In the Platform list, select Android, and select Switch Platform.

2) Switch Platform![platform](uploads/6e018c200ad3dbe226e00095635a4382/platform.png)

3) While still in the Build Settings window, focus on the Run Device list and select your Meta Quest headset. If you don’t see the headset in the list, ensure you have connected it properly and select Refresh.![buildsetting](uploads/92917ef1df056eac4e3a2307d3b17b74/buildsetting.png)

4) Run Device settings



Run Unity Project Setup Tool:

1) Navigate to Oculus > Tools > Project Setup Tool. The Unity Project Setup Tool has rules for creating a new application with Meta Quest in Unity.

2) In the checklist under the Android icon tab of the Project Setup Tool, select Fix All.![proj_setup](uploads/f9bd2b7f8346d84516ffa3541745a943/proj_setup.png)

This applies the required settings for creating Meta Quest XR apps, including setting the minimum API version, using ARM64, and installing the Oculus XR Plug-in and XR Plug-in Management package.

3) f you still see Recommended Items in the list, select Apply All.
![app_all](uploads/7e18d657c1840d71080ad522f6326cfb/app_all.png)

This optimizes project settings for Meta Quest Unity apps, including texture and graphics settings.

Add OVRCameraRig to scene:

Meta XR Core SDK contains the OVRCameraRig prefab which is a replacement to Unity’s main camera. This means you can safely delete Unity’s main camera from the Hierarchy tab.

The primary benefit of using OVRCameraRig is that it offers the OVRManager component (OVRManager.cs script). OVRManager provides the main interface to the VR hardware.

Follow this process:

1) Under Hierarchy tab, right-click Main Camera, and select Delete.

2) In the Project tab, search for Camera Rig, and drag the OVRCameraRig prefab into your scene. Alternatively, drag it in the Hierarchy tab.![cam_rig](uploads/f15151a582be9ac889c4cdd70649f195/cam_rig.png)

3) Ensure your project’s hierarchy looks like this:![hierearch](uploads/f3292eb2af9427db44ec6096db402012/hierearch.png)

4) Select OVRCameraRig in the **Hierarchy** tab.

5) With the OVRCameraRig selected in the Inspector, under the OVR Manager component, ensure your headset is selected under Target Devices.![ovrcam_rig_inspector](uploads/bb186befb40d757fcee02babeb7d85a1/ovrcam_rig_inspector.png)


Build and Run project on Headset:
1) Go to **File** > **Build Settings** and, under **Scenes**, select **Add Open Scenes**. This should list your open scene.![buildnRun](uploads/207640c3643d86e13a2bd29caf7819e1/buildnRun.png)

Select Build And Run and choose a name for your .apk file, for example, HelloWorld.apk.
Put on your Meta Quest to experience your Hello World app.
Note: For faster iteration times, you can use Meta Quest Link which helps you test your Unity projects without building your project. For details, read Use Meta Quest Link for App Development.


Additional troubleshooting steps

Error message Execution failed for task ':launcher:packageRelease'. A failure occurred while executing com.android.build.gradle.internal.tasks.Workers$ActionFacade...

You might have conflicts with a prior Android Studio installation on your computer. To resolve this, try deleting or renaming the debug.keystore and debug.keystore.lock files in your \Users\<username>\.android folder. Restart Unity, and build your project again.

For additional troubleshooting, read the Troubleshooting guide.


**META XR SIMULATOR:**

The Meta XR Simulator provides a lightweight XR runtime that runs on your development machine for rapid development and testing of XR applications. The Simulator is meant to be a drop-in replacement for the Mobile and PC XR runtimes following the same XR API specification. This allows the application to run in Unity’s Play mode or Unreal’s Preview mode without modification. The Simulator has a predefined input mapping schema and a user interface that provides information of how the runtime is compositing the final view, simulating input, and other features.

Prerequisites

-Your Unity project should be properly set up to run on Meta Quest devices. If you are starting from scratch, feel free to refer to the steps in Build Your First VR App.

-Install Meta XR Simulator

1) On the menu, go to **Oculus** > **Download XR Simulator**. The NPM download page displays in your browser.
Click the cloud icon to download the latest tarball. It takes a few minutes for the latest com.meta.xr.simulator*.tgz to download fully.
On the menu, go to **Window** > Package **Manager**.
Click the **+** sign, and then select **Install package from tarball**.... Unity installs the tarball.
Close the **Package Manager** window.


**Start Meta XR Simulator**

Once you have imported the Meta XR Simulator, you must activate it. On the menu bar, go to **Oculus** > **Meta XR Simulator** > **Activate** to activate the simulator. There will be a log message titled **Meta XR Simulator is activated** indicating that the activation is successful.
![SIM_LOG](uploads/bc113ef90aaec70819ad249eee9dc64c/SIM_LOG.png)

Then, you can run your Unity application by clicking the Play button. The Debug Window of Meta XR Simulator will open. You can drag the panels to arrange them for your convenience.
![sim](uploads/44ff277f4c04e54151ee13193cb3be0d/sim.png)

Get Started with Hands Setup

Note
The recommended way to integrate hand tracking for Unity developers is to use the Interaction SDK, which provides standardized interactions and gestures. Building custom interactions without the SDK can be a significant challenge and makes it difficult to get approved in the store.

Apps render hands in the same manner as any other input device. Start by setting up the camera, select hands as the input device, and add hands prefab to render hands in the default form. The following sections describe basic setup:

Set Up Camera
Create a new scene or open an existing one from your project.
On the Project tab, search for OVRCameraRig, and then drag it in the scene. Skip this step if OVRCameraRig already exists in the scene.
On the Hierarchy tab, select OVRCameraRig to open the Inspector tab.
On the Inspector tab, go to OVR Manager > Tracking, and then in the Tracking Origin Type list, select Floor Level.
Select Hands as Input
On the Hierarchy tab, select OVRCameraRig to open the Inspector tab. Skip this step if you are continuing from the Set Up Camera section mentioned above.
On the Inspector tab, go to OVR Manager > Quest Features, and then in the Hand Tracking Support list, select Controllers and Hands. Select Hands Only option to use hands as the input modality without any controllers.

When you select controllers and hands or hands only option, Meta Quest automatically adds<uses-permission android:name="com.oculus.permission.HAND_TRACKING" /> and <uses-feature android:name="oculus.software.handtracking" android:required="false" /> elements in the AndroidManifest.xml file. When the app supports controllers and hands, android:required is set to false, which means that the app prefers to use hands if present, but the app continues to function with controllers in the absence of hands. When the app supports hands only, android:required is set to true. Oculus adds both of these tags automatically and there is no manual update required in the Android Manifest file.

In the Hand Tracking Version list, leave selection as Default to use the latest version of hand tracking (Hands 1.0 is now deprecated. Selecting 1.0 or 2.0 will force your app to Hands 2.0, potentially preventing automatic upgrades to future major version releases)
Add Hand Prefab
On the Hierarchy tab, expand OVRCameraRig > TrackingSpace to add hand prefabs under the left and right hand anchors.
On the Project tab, search for *OVRHandPrefab, and then drag it under each hand anchor on the **Hierarchy tab.
On the Hierarchy tab, under RightHandAnchor, select OVRHandPrefab, and then on the Inspector tab, under OVR Hand, OVR Skeleton, and OVR Mesh, change the hand type to right hand. There’s no action needed for the left-hand prefab as the hand type is set to the left hand automatically.
On the Hierarchy tab, select both the OVR Hand prefabs, and then on the Inspector tab, make sure OVR Skeleton, OVR Mesh, and OVR Mesh Renderer checkboxes are selected to render hands in the app.
At this point, the app is able to render hands as an input device. To test hands, put on the headset, go to Settings > Device > Hands & Controllers, and turn on Hand Tracking. Leave the Auto Switch Between Hands And Controllers selected to let you use hands when you put controllers down. From Unity, build and run the app in the headset. After the app launches in the headset, put the controllers down, bring forward your hands that act as input devices in the app.

Update Root Pose and Root Scale
To generate and render the animated 3D model of hands, OVR Mesh Renderer combines data returned by OVR Skeleton and OVR Mesh. OVR Skeleton returns bind pose, bone hierarchy, and capsule collider data. OVR Mesh loads a specified 3D asset from the Oculus runtime and exposes it as a Unity Engine mesh. We have preconfigured the recommended settings and have explained them in detail.

On the Hierarchy tab, expand OVRCameraRig > TrackingSpace, and then under LeftHandAnchor and RightHandAnchor, select both the OVRHandPrefab prefabs.
When the OVRHandPrefab is parented to the left- and right-hand anchors under OVRCameraRig, leave the Update Root Pose checkbox unchecked so that the hand anchors can correctly position the hands in the tracking space. If it is placed independently of OVRCameraRig, select the checkbox to ensure that not only the fingers and bones, but the actual root of the hand is correctly updated.
To get an estimation of the user’s hand size via uniform scale against the reference hand model, make sure the Update Root Scale checkbox is selected. By default, the reference hand model is scaled to 100% (1.0). By enabling scaling, the hand model size is scaled either up or down based on the user’s actual hand size. The hand scale may change at any time, and we recommend that you should scale the hand for rendering and interaction at runtime. If you prefer to use the default reference hand size, clear the selection from the checkbox.
Add Physics Capsules
The physics capsules represent the volume of the bones in the hand that is used to trigger interactions with physical objects and generate collision events with other rigid bodies in the physics system.

On the Hierarchy tab, expand OVRCameraRig > TrackingSpace, and then select the OVR Hand prefab that you want to use for physics interaction.
On the Inspector tab, under OVR Skeleton, select the Enable Physics Capsules checkbox.
Repeat steps 1 and 2 for the other hand prefab.
Customize Display
Default hand models are skinned. A skinned mesh renderer surfaces properties that define how the model is rendered in the scene. Make sure the Skinned Mesh Renderer checkbox is selected. There are three broad categories that you can define to customize the hand model:

Materials define how hands appear in the app. Depending on the shader, configure the material that suits your content. For example, select either metallic or specular workflow, set the rendering mode, define the base color, or adjust the smoothness. For more information about materials, go to Creating and Using Materials guide in the Unity documentation.
Lighting specifies if and how the mesh renderer will cast and receive shadows.
Probes contains properties that set how the renderer receives light from the Light Probe system.
To define the skinned mesh renderer properties, do the following:

On the Hierarchy tab, expand OVRCameraRig > TrackingSpace, and then select the OVR Hand prefab from any one hand anchor.
On the Inspector tab, do the following:
Make sure the Skinned Mesh Renderer checkbox is selected.
Under Materials, enter the number of materials you want to use, and drag the material in the list of materials. By default, the size is set to one and the first element is always Element 0.
Under Lighting, in the Cast Shadows list, select how the renderer should cast shadows when a suitable light shines on it, and then select the Receive Shadows checkbox to let the mesh display any shadows that are cast upon it.
Under Probes, in the Light Probes list, select how the renderer should use interpolated Light Probes. By default, the renderer uses one interpolated light probe.
Repeat steps 1 and 2 for the other OVR Hand prefab.
To use a customized mesh, map your custom skeleton that is driven by our skeleton. For more information on sample usage, refer to the HandTest_Custom scene, which uses the OVRCustomHandPrefab_L and OVRCustomHandPrefab_R prefabs, as well as the OVRCustomSkeleton.cs script.

To enable wireframe skeleton rendering that renders bones with wireframe lines and assists with visual debugging, select the OVR Skeleton Renderer checkbox.

