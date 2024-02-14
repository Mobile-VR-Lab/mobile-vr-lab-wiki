This project is composed of three applications, each of which has their own code repository and unique setup.

---

# Android App Setup

1. Clone code repository
   - Go to the [GitLab Repository](https://gitlab.cs.unh.edu/mobile-vr-lab/android-app)
   - Copy clone link
   - Run `git clone <link>` in a terminal at the parent folder you want the repository to live in
2. Install Android Studio
   - [External instructions](https://developer.android.com/studio/install)
   - This is the best IDE for Android Mobile App development
   - Versions Hedgehog and Giraffe have both been tested on and work fine
3. Open Project in Android Studio
   - Let dependencies get index (this may take a few minutes)
4. Build and run app on an Android device emulator (built into IDE)
   - We have been using an emulator for a Pixel C Tablet that is running Android 14 "Tiramisu" (API level 34)

### To Run The App's Test Server

The test server lives under the subfolder `test_server` on the android app repository. This is a simple webserver with Express on NodeJS that prints out HTTP requests it receives (even non-mapped endpoints for debugging purposes).

- Install `NPM` and `NodeJS`
  - [External instructions](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
- Navigate to `test_server` folder in terminal
- Run with `node index.js`
  - The program will wait for requests to arrive
  - This can be tested using the `cURL` commands located in the `readme.md` file in the same folder

---

# Server App Setup

TODO

---

# Unity Setup

### Getting Started

1. **Download [Unity Editor](https://unity.com/unity-hub)** (2022 or later) 
  
2. **Download your C# IDE of choice**
   - We recommend [Rider](https://www.jetbrains.com/rider/download)  
  
3. **Create a [GitHub](https://github.com/) account, if needed.**
   
4. **Clone the repository**:
   - <pre><code>git clone https://github.com/cjanosdev/Mobile-VR-Lab.git</code></pre>
  
5. **Open the project in Unity**
   - Click on 'Add project from disk', and navigate to the cloned project directory.
   - Install dependencies.
     - When you open the project, Unity should automatically download any needed packed specified in the `packages/manifest.json` file.
  

### Project Structure

- **Assets:** This directory contains all of the scripts, materials, models, scenes, and other third-party assets like Oculus VR support and TextMesh Pro. 
  - **Scenes:** Located within the Assets directory, this folder holds the Unity scene files which contain things like objects, models, lighting, cameras, and other UI elements. 
  - **Scripts:** Also within the Assets directory, this contains the C# scripts that control the project's behavior.
    
- **Packages**: This contains project dependencies managed by Unity's Package Manager. The manifest.json file within this directory lists all the package dependencies for the project.
   
- **ProjectSettings:** This directory stores configuration settings for the Unity project.