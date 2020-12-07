## Amazon Connect Telemedicine

Amazon Connect is an omnichannel cloud contact center. You can create personalized experiences for your customers using omnichannel communications. For example, you can dynamically oﬀer chat and voice contact, based on such factors as customer preference and estimated wait times. Agents, meanwhile, conveniently handle all customers from just one interface.

Amazon Connect is an open platform that you can integrate with other enterprise applications, such as Salesforce. In addition, you can take advantage of the AWS ecosystem to innovate new experiences for your customers.

The following diagram shows these key characteristics of Amazon Connect.

## Telemedicine Solutions

To recreate this telemedicine solution, the following steps are required:
-	Set hours of operations
-	Create queue
-	Import Queue Flow
-	Import Contact Flow
	- Rapid Response (Call)
	- Quick Connection (Chat)
- Create a Routing Profile
-	Configure Users
-	Claim a Phone Number

Adding chat to your website is possible with a few easy steps. This solutions spins up an Amazon API Gateway endpoint that triggers an AWS Lambda function. This Lambda function invokes the Amazon Connect Service StartChatContact API and returns the result from that call. Once you have the StartChatContact API you can either pass that response to the prebuilt widget to get a quick implementation going or you can build your own customer chat experience by using the Amazon Connect Chat JS library.

https://github.com/amazon-connect/amazon-connect-chat-ui-examples/tree/master/cloudformationTemplates/startChatContactAPI

## Set hours of operations

The ﬁrst thing you need to do when you set up a queue is to specify the hours of operation. The hours may be referenced in contact ﬂows

To set the hours of operation for a queue
1.	Choose Routing, Hours of operation.
2.	To create a template, choose Add new hours and enter a name Tele-medicine Hours and description Tele-medicine Hours of Operation
3.	For Time zone, select a value.
4.	For Add new, set new hours, for this example create Sunday to Saturday from 09:00 AM to 05:00 PM.
5.	Choose Save.

## Create a Queue

1.	Choose Routing, Queues, Add new queue.
2.	Add the appropriate information about your queue and choose Add new queue, in this case addition then next information
	- Name: Medicine
	- Description: Tele-Medicine Queue
	- Hours of Operations: Tele-medicine Hours
3.	Click Add new queue. The queue is automatically active.

For continue configure and import Contact Flow and Queue Flow please select file ## AmazonConnect_Telemedicine_Solution 

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

