This project is composed of three applications, each of which has their own code repository and unique setup.

---
# Android App Setup
1. Clone code repository
   - Go to the [GitLab Repository](https://gitlab.cs.unh.edu/mobile-vr-lab/android-app)
   - Copy clone link
   - Run `git clone <link>` in a terminal at the parent folder you want the repository to live in
1. Install Android Studio
   - [External instructions](https://developer.android.com/studio/install)
   - This is the best IDE for Android Mobile App development
   - Versions Hedgehog and Giraffe have both been tested on and work fine
1. Open Project in Android Studio
   - Let dependencies get index (this may take a few minutes)
2. Build and run app on an Android device emulator (built into IDE)
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
# Unity App Setup
TODO

