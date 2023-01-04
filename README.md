# VideoToMP3 Converter using RabbitMQ

The purpose of this project is to practice event driven architecture.

The scenario is:
1. Client sends an API request to API gateway and authenticates matching credentials with AuthDB
2. Client uploads a video file
3. File gets uploaded to MongoDB using grifs, triggers a message with the topic "video"
4. Consumer *"Converter"* receives the message from RabbitMQ exchange using topic routes to start processing the conversion of the video
5. *"Converter"* publishes an event that the video conversion is done and ready to be downloaded to RabbitMQ
6. *"Notification"* service receives the message and sends a notification to the client with the ID that can be used to download the MP3 File
7. User authenticates again and uses ID received in the notification to download the MP3 version of the video uploaded.

![Architeture image description](https://github.com/cesarfda/System_design_Project1_RabbitMq/blob/master/System_Design_videoToMp3.png?raw=true)
