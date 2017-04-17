# hackathon17
### Integrating ASL input with Amazon Echo
🐟🐟🐟🐟🐟🐟🐟🐟🐟🐟🐟🐟🐟🐟🐟🐟🐟🐟🐟🐟
### Concept
In the following 24 hours, we plan to create a service that allows speech impaired individuals to use the voice command service in the amazon echo. 

----

### Requirements
* Leap Motion
* FireBase (please don't use ours, it's already riddled with errors ;) )

### Current Status
* Hand pose data has been added to Firebase
* Querying the firebase db was slow [see issue] so we manually export JSON and it sits in the html (DON'T JUDGE US)
* When a pose is sent to be identified, we extract the finger position coordinates (these are 3D) from the sent pose and compare it against each one in the JSON data. The group with the overall most similar details is returned.

## Next Steps
* Improve matching algorithm
* Increase dataset
* Migrate to MongoDB
* Apply machine learning and idenfity patterns in the data
* Word Detection 
* Intergrate with Alexa (or other services like google assistant)   

## Notable Projects
* https://github.com/eYSIP-2016/eYSIP-2016-Sign-Language-Interpreter-Leap-Motion-Sensor-
* https://github.com/ssaamm/sign-language-tutor
