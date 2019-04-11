# A Simple Real-time Emotion Analyzer.

## Introduction

Welcome back to part 2 of **Cognitive Services** module. I hope you are learning lots and enjoying it so far! 📚

In this module we will be building an emotion analyzer component that detects and responses as player's emotion changes (aka. smiling) as they watch a montage of cat videos or you know, funny stuffs. 😹

Utilizing your webcam and cognitive services, we will build a movable camera preview components with a dynamic 'hapiness' meter. As you may have guessed, if the meter filled up to 100% then the player will be prompted a **'GAME OVER'** banner. 

So you better keep a straight face!   


 [place holder for a gif demo]
 
 
 ## 1. Building a webcam component.
 
 In this section, we will first build our **MyWebcam** component to display the video feed on the screen as well as taking care of sending/retreiving API data.
 
We will use **_react-webcam_** package from **npm** to help us implement the webcam component. 

### 1.1 Install **react-webcam** package using npm 

Open powershell in the project directory and type `npm i react-webcam` to install **react-webcam** package from node.js package manager npm.

💡 **Tips:** Shift right click -> Open PowerShell window here

Read more: [react-webcam - npm](https://www.npmjs.com/package/react-webcam) 

### 1.2 Create a webcam component

Create a new JavaScript file under the **components** folder called **MyWebcam.js**.

Use `import Webcam from "react-webcam";`, and Create a class **MyWebcam.js**, which returns `<Webcam />` component. 

At the bottom don't forget to `export default MyWebcam` class component so that it is made available to use by other components.

```javascript
import React from "react";
import Webcam from "react-webcam";
 
class MyWebcam extends React.Component {
  render() {
    return <Webcam />;
  }
}

export default MyWebcam
```





