## Script XML File Documentation:

The Script file is an XML file that can be loaded into the instructor app, and contains all the data that will be displayed for the scenes on the app. This is where the “script” that the instructor can read off of comes from.

### Example XML Script File:

```xml
<vrExperience title="my vr experience">
   <scene title="my title 1" id="1">
       my script here 1
   </scene>
   <scene title="my title 2" id="2">
       my script here 2
   </scene>
   <scene title="my title 3" id="3">
       my script here 3.
       this is an <action id="5" type="highlight">action</action>
       what a paragraph.
   </scene>
</vrExperience>
```

#### VR Experience
The **script file** must contain the `<vrExperience>` tag, which will then contain 0 or more `<scene>` tags, which can contain **raw text** along with `<action>` tags. The `<vrExperience>` tag can contain a **title** property to display on screen. 

#### Scene
Each `<scene>` should have its own **title** and **id** properties, the id of which will be used to correspond with a scene in the Unity app. 

#### Action
Each `<action>` should have its own **id** and **type** properties, the id of which will correspond to an object in the Unity scene and the type of which will determine what will occur when the action is clicked.