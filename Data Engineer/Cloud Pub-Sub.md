___

- Real-time message service between independent devices.
- When an event is successfully represented as a message, it is pub/sub duty to inform the services that need to act on this message.
- Example there is graphic poster website, which work as follows
	- first you will order a poster
	- that poster will send to packaging service
	- after packaging it will be sent to the courier service
	On each step you will receive a step complete message on your account.
	Now, there are some issues with it.
	- What if a service fails
	- What if we introduce a new service in it.
	- To test one service is working correctly, we have to test all the others.
![[Pasted image 20240604111635.png]]
- To solve these problems, we can use cloud pub/sub.
	- Now order service will send a message to pub/sub
	- from where packaging and notification service can receive the message through pushed or pull.
	- After doing packaging , service will message back to pub/sub m from where it will be sent to courier and notification service.
	- And as the end courier service will send it msg to pub/sub, and from there to notification service.
	If a service failed it will store the messages upto 7 days.
![[Pasted image 20240604113207.png]]