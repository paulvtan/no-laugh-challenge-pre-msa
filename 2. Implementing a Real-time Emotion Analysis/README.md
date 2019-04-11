# A Simple Real-time Emotion Analyzer.

## Introduction

Welcome back to part 2 of **Cognitive Services** module. I hope you are learning lots and enjoying it so far! 📚

In this module we will be building an emotion analyzer component that detects and responses as player's emotion changes (aka. smiling) as they watch a montage of cat videos or you know, funny stuffs. 😹

Utilizing your webcam and cognitive services, we will build a movable camera preview components with a dynamic 'hapiness' meter. As you may have guessed, if the meter filled up to 100% then the player will be prompted a **'GAME OVER'** banner. 

So you better keep a straight face!   


 [place holder for a gif demo]
 
 
## 1. Building a webcam component. 📷
 
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

<details><summary>View Code 🖱️</summary>


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

</details>



### 1.3 MyWebcam quick test 🔧

Let's test our newly defined component. In **App.js** import the component, and add it to a return statement in render function of the **App** class. 

Runs `npm start` from PowerShell to see the changes.

💡 **Tips:** Comment out part 1 components being return for now to easily test development of part 2. Use `Ctrl + K + F` simultaneously to comment out a section of code. Use `Ctrl + K + U` to uncomment. 

<details><summary><b>View Code 🖱️<b></summary>
<p>

```javascript
import MyWebcam from './components/MyWebcam'

class App extends Component {

...

    render() {
        return (<div>
            {/* <Title title={'No-Laugh Challenge'} />
            <AddVideo onAddVideo={(addedPost) => {
                this.addVideo(addedPost)
            }}/>
            <div className = "video-wrapper">
                <Displayer posts={this.state.posts} />
            </div> */}
            
            <MyWebcam />
            
        </div>
        )
    }
}
```

</p>
</details>


You should be able see the webcam in effect!

### 1.4 Adjusting the camera 

Next we will adjust the camera using the props value below. 

Here we use **setRef** to reference the `<Webcam />` component and assigning it to this.webcam variable, which allow us to later on invoke a function on webcam component.

We also defined a **videoConstraints** constant which define settings for our device's webcam.

Pass in both props as well as width and height into `<Webcam />` components .

Try experimenting with width and height props to see how they affect the size of the video element.

💡 **Tips:**  `Ctrl + A` to highlight all code then `Ctrl + K + F` to automatically format the indentation!

<details><summary><b>View Code 🖱️<b></summary>
<p>

```javascript
import React from "react";
import Webcam from "react-webcam";

class MyWebcam extends React.Component {

    setRef = webcam => {
        this.webcam = webcam;
    };


    render() {

        const videoConstraints = {
            width: 750,
            height: 500,
            facingMode: "user"
        };

        return (
            <Webcam
                audio={false}
                height={1000}
                width={750}
                ref={this.setRef}
                screenshotFormat="image/jpeg"
                videoConstraints={videoConstraints}
            />
        );
    }
}

export default MyWebcam

```

</p>
</details>

### 1.5 Capturing images from webcam

Let's create a method that will continuously take photos every 2 seconds (We will increase this rate later). 

Define a constructor for **MyWebcam** class with two properties `this.timerId`, which will allow us to reference and call clearInterval() to stop taking photos later, `this.isCapturing` is a simple boolean flag that will us to stop updating the UI with API data that arrives after we have stopped the timer.

Next, create **startCapturing** that execute a function to start the capturing process. Here we use `setInterval()` method to invoke `this.webcam.getScreenshot()` every 2 seconds which returns a base64 encoded string of the image. 

Finally add a 'Start Game!' button under the **Webcam** component, add a button with onClick attribute to fires `startCapturing` into taking photos every 2 seconds.

Run the app, open developer console `F12` and start the game, you should see the base64 encoded string representation of the image being logged.

💡 **Tips:** If you copy & paste the encoded image into the URL of chrome, you can render the image taken! 

<details><summary><b>View Code 🖱️<b></summary>
<p>

```javascript

class MyWebcam extends React.Component {
    constructor(props) {
        super(props);
        this.timerId = null;
        this.isCapturing = false;
    }

...

    startCapturing = () => {
        this.isCapturing = true;
        this.timerId = setInterval(() => {
            const image = this.webcam.getScreenshot();
            console.log(image);
        }, 2000);
    }
    
    render() {
    
...

        return (
            <div>
                <div>
                <Webcam
                    audio={false}
                    height={1000}
                    width={750}
                    ref={this.setRef}
                    screenshotFormat="image/jpeg"
                    videoConstraints={videoConstraints}
                />
                </div>
                <button variant="primary" onClick={this.startCapturing}>Start Game!</button>
            </div>
        );
    }
} 
    
   
```


</p>
</details>

## 2. Fetching emotion data from Cognitive Services Face API.

We will construct a function to send off an image and fetch a JSON response from the Microsoft Cognitive Services API. 

==============================================
<details><summary><b>View Code 🖱️<b></summary>
<p>

```javascript
```


</p>
</details>


