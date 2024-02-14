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

# Server App

## What should you know?

It is recommended that you have taken CS 761 (Programming Language Concepts & Features) before working on this segment of the project. CS 735, CS 712, and CS 720 are also good to have taken. If you have experience writing async code in JavaScript, that will also be helpful. Rust, in many ways, is quite similar to Scala, but with more C-like syntax. The server makes use of functional programming features, pattern matching, and some other [advanced type features](https://doc.rust-lang.org/book/ch19-03-advanced-traits.html).

Confused by the language? Take a look at the [Rust Handbook](https://doc.rust-lang.org/book/).

## First-time Setup

The following steps should get you a working development environment quickly.

1. Clone the server repository
   - Run `git clone git@gitlab.cs.unh.edu:mobile-vr-lab/vr-lab-server.git vr-lab-server`
2. Install tools needed for the development environment
   - [Visual Studio Code](https://code.visualstudio.com/)
      - If you are using a Linux distribution, install VS code through your package manager.
   - An OCI-compliant container runtime of your choice (Docker, Podman, etc...)
3. Set up your development environment
   - Open the Git repository folder in VS code.
   - Use the Dockerfile in the repository to set up a [Dev Container](https://code.visualstudio.com/docs/devcontainers/containers).
   - The dev container will set up Rust and required system libraries for you.
   - If you would rather not use a dev container, then you will need to install Rust.
      - Install [rustup](https://rustup.rs/)
      - Run `rustup install stable` to install the current stable Rust toolchain on your system.
4. Install VS code plugins
   - Make sure your VS code window is running inside your development container or desired development environment.
   - Install the [rust-analyzer extension](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer).
5. Run `RUST_LOG=debug cargo run` in the terminal. It should build and run successfully if your environment is set up properly.

### Remarks

VS Code is recommended, but not required. You may also use the JetBrains IDE for Rust, [Rust Rover](https://www.jetbrains.com/rust/). This was not used in the development of this project, but if you prefer JetBrains IDEs, then give it a try and add to this documentation.

## The Test Client

The server has a dummy test client for local development purposes.
It is located in the `test_client` directory inside the repository.

As you add new features, you may need to send different dummy responses based on the message coming in.
There is a `match` statement in the sender thread which you will need to modify in order to do this.
Aside from that, it should just work. Note that it always connects to `127.0.0.1:15300`.

## Notes

When developing, make sure you always run this in the terminal:

```
export RUST_LOG=debug
export RUST_BACKTRACE=1
```

This tells the logging framework (env_logger) to print all log messages, and the Rust default panic handler to print the stack trace for you in the case of an unwind. Note that the stack traces are very convoluted because we make use of the [tokio asynchronous runtime](https://tokio.rs/) in this project.

## Beware

Make sure you are not mixing OS sync types (from `std::sync`) and the async-aware sync types (from `tokio::sync`). Doing so will definitely introduce very hard to debug deadlocking bugs. If you pull in new libraries, you also must make sure that these are not using any locks (like `std::sync::Mutex`) from the standard library.

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