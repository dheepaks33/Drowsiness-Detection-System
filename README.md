# Drowsiness Detection System using IBM Watson IoT
This repository contains Python code for a drowsiness detection system that uses computer vision techniques to monitor a person's eyes and detect signs of drowsiness. When drowsiness is detected, an alert is sent to the IBM Watson Internet of Things (IoT) platform, and an alarm sound is played.

## Prerequisites
Before running the code, make sure you have the following libraries and components installed:

- OpenCV
- dlib
- NumPy
- IBM Watson IoT Python SDK (ibmiotf)
- pygame
  
- You can install these dependencies using `pip`

## Setup IBM Watson IoT
Sign up for an IBM Watson IoT Platform account if you don't already have one.

Create a new device type and register a device. Note down the organization, device type, device ID, authentication method (token), and authentication token.

Replace the following variables in the code with your IBM Watson IoT credentials:

`organization`
`deviceType`
`deviceId`
`authMethod`
`authToken`

## Running the Code
1. Download the pre-trained shape predictor model from the dlib website and save it as "shape_predictor_68_face_landmarks.dat" in the same directory as the code.

2. Make sure you have an MP3 file containing the alarm sound (e.g., "oversimplified-alarm-clock-113180.mp3") in the same directory.

3. Run the code

4. The code will open your webcam feed and start monitoring for drowsiness. When drowsiness is detected, an alert will be sent to the IBM Watson IoT platform, and the alarm sound will play.

## How it Works
The code uses OpenCV to capture video frames from your webcam.

It employs dlib to detect faces in the video frames.

For each detected face, it uses facial landmarks to locate the eyes.

The Eye Aspect Ratio (EAR) is calculated based on the positions of eye landmarks. When the EAR falls below a certain threshold, it indicates drowsiness.

If drowsiness is detected for a specified number of consecutive frames (EYE_AR_CONSEC_FRAMES), an alert is sent to the IBM Watson IoT platform.

An alarm sound is played to alert the individual when drowsiness is detected.

The code continuously updates the EAR and displays it on the video feed for monitoring.

## Configuration
You can adjust the `EYE_AR_THRESH` and `EYE_AR_CONSEC_FRAMES` constants to change the sensitivity of drowsiness detection.

Replace the alarm sound with your own MP3 file for a custom alarm.
<br> <hr> <br>

# JSON

# Table of Contents
- Prerequisites
- Getting Started
- Node-RED Flow Overview
- IBM Watson IoT Integration
- Status Monitoring
- Usage
- Customization

## Prerequisites
Before you begin, ensure you have the following prerequisites in place:

Node-RED: Make sure you have Node-RED installed and running on your system. You can install it following the instructions on the official Node-RED website.

IBM Watson IoT Account: You need an IBM Watson IoT Platform account. If you don't have one, you can sign up for an account on the IBM Watson IoT Platform.

## Getting Started
To set up and run this IBM Watson IoT status monitoring system:

Clone or download this repository to your local machine.

Import the Node-RED flow configuration by following these steps:

a. Launch Node-RED by running the command node-red in your terminal.

b. Access the Node-RED editor by opening a web browser and navigating to http://localhost:1880 (or the appropriate URL if you've configured Node-RED differently).

c. Import the flow configuration by clicking the menu icon in the top-right corner of the Node-RED editor and selecting "Import > Clipboard."

d. Paste the JSON configuration provided in the original file into the clipboard. This will import the flows into Node-RED.

e. Deploy the flows by clicking the "Deploy" button in the Node-RED editor.

Configure the IBM Watson IoT node in Node-RED with your IBM Watson IoT credentials, including the apiKey and deviceId.

Access the Node-RED dashboard by opening a web browser and navigating to http://localhost:1880/ui (or the appropriate URL if you've configured Node-RED differently).

You should now see the status monitoring dashboard, which will display real-time updates from your IoT device.

## Node-RED Flow Overview
The Node-RED flow consists of several components for integrating with IBM Watson IoT and displaying device status updates on a web-based dashboard.

IBM Watson IoT Integration
IBM IoT In Node: This node is responsible for receiving events from the IBM Watson IoT platform. It subscribes to all events (allDevices and allEvents are set to true) for a specific device type and device ID.

Debug Node (debug 2): This node is used for debugging and displays the received payload from IBM Watson IoT.

Function Node (Message Status): This node processes the received payload and generates a status message. Depending on the payload value (0 or non-zero), it determines the status and sends it to the dashboard for display.

## Status Monitoring
UI Text Node: This node is part of the Node-RED dashboard and displays the status message generated by the function node. It updates in real-time based on the received status updates from the IoT device.
Usage
Start your IoT device and ensure it's connected to the IBM Watson IoT platform.

Deploy the Node-RED flow by clicking the "Deploy" button in the Node-RED editor.

Access the Node-RED dashboard by opening a web browser and navigating to http://localhost:1880/ui.

You should see the dashboard displaying the current status of your IoT device. The status will change based on the messages received from the device via the IBM Watson IoT platform.

## Customization
You can customize this monitoring system according to your needs:

Modify the IBM Watson IoT node settings to connect to your specific device and event types.

Customize the status message generation logic in the "Message Status" function node to match your device's status codes and meanings.

Customize the Node-RED dashboard appearance and layout to better suit your preferences.


## License
This project is licensed under the `MIT License` - see the [LICENSE](LICENSE) file for details.
