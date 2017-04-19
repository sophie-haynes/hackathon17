# Hackathon Project 2017
## Integrating ASL input with Amazon Echo
:octocat:
### Concept
In 24 hours, we planned to create a service that allowed speech impaired individuals to use the voice command service in the amazon echo. 

----

### Requirements
* Leap Motion
* FireBase (please don't use ours, it's already riddled with errors ;) )

### Current Status
* Hand pose data has been added to Firebase
* Querying the firebase db was slow [see issue] so we manually export JSON and it sits in the html (DON'T JUDGE US)
* When a pose is sent to be identified, we extract the finger position coordinates (these are 3D) from the sent pose and compare it against each one in the JSON data. The group with the overall most similar details is returned.

### Next Steps
* Improve matching algorithm
* Increase dataset
* Migrate to MongoDB
* Apply machine learning and idenfity patterns in the data
* Word Detection 
* Intergrate with Alexa (or other services like google assistant)   

### Notable Projects
* [Sign Language Tutor using Leap Motion](https://github.com/ssaamm/sign-language-tutor)
* [Sign Language Interpretor with Robotic Hand](https://github.com/eYSIP-2016/eYSIP-2016-Sign-Language-Interpreter-Leap-Motion-Sensor-)


---

### Understanding JSON Output
The Leap Motion exports a huge amount of information. Here we'll briefly explain the important parts we identified (this is in no way complete or absolute, just a helpful :+1:).
The highest level of the JSON object looks like this (sub arrays have been removed for readability).
```json
"-KhnsCmzuImXz_8tlQV5" : {
 "currentFrameRate" : 87.0047,
 "hands" : [],
 "id" : 977156,
 "interactionBox" : {},
 "name" : "A",
 "pointables" : [],
 "r" : [],
 "s" : 1.00985,
 "t" : [],
 "timestamp" : 2196635669386
 },
```
For our project we focused on the `pointables` section as this refers to finger co-ordinates. This section is divided into five blocks, each with the same parameters. These are the values for each finger. [LeapMotion provide helpful docs on finger data here](https://developer.leapmotion.com/documentation/javascript/api/Leap.Finger.html).
```json
{
"bases" : [ [ [ 0.494996, 0.866749, 0.0610307 ], [ -0.772661, 0.406955, 0.487219 ], [ 0.39746, -0.288327, 0.871145 ] ], [ [ 0.354423, 0.913279, -0.200763 ], [ -0.677792, 0.39882, 0.61769 ], [ 0.644191, -0.0828476, 0.760364 ] ], [ [ 0.354423, 0.913279, -0.200763 ], [ -0.933402, 0.358412, -0.0173744 ], [ 0.0560882, 0.19355, 0.979486 ] ], [ [ 0.354423, 0.913279, -0.200763 ], [ -0.528821, 0.0186943, -0.848528 ], [ -0.77119, 0.406905, 0.489587 ] ] ],
"btipPosition" : [ -44.2664, 161.707, -15.9561 ],
"carpPosition" : [ -28.4845, 173.515, 65.6216 ],
"dipPosition" : [ -62.0464, 171.088, -4.6685 ],
"direction" : [ -0.0560882, -0.19355, -0.979486 ],
"extended" : false,
"handId" : 307,
"id" : 3070,
"length" : 51.341,
"mcpPosition" : [ -28.4845, 173.515, 65.6216 ],
"pipPosition" : [ -60.1625, 177.589, 28.2308 ],
"stabilizedTipPosition" : [ -51.303, 158.005, -14.4419 ],
"timeVisible" : 6.71262,
"tipPosition" : [ -48.5165, 164.188, -13.6215 ],
"tipVelocity" : [ -2.11233, 1.25636, 4.04031 ],
"tool" : false,
"touchDistance" : 0.10323,
"touchZone" : "hovering",
"type" : 0,
"width" : 19.9487
}
```
### Understanding our JavaScript
We'll get round to explaining it... Have this while you wait! :octocat:
