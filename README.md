# Amazon Connect Telemedicine

Amazon Connect is an omnichannel cloud contact center. You can create personalized experiences for your customers using omnichannel communications. For example, you can dynamically oﬀer chat and voice contact, based on such factors as customer preference and estimated wait times. Agents, meanwhile, conveniently handle all customers from just one interface.

Amazon Connect is an open platform that you can integrate with other enterprise applications, such as Salesforce. In addition, you can take advantage of the AWS ecosystem to innovate new experiences for your customers.

The following diagram shows these key characteristics of Amazon Connect.

![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Amazon%20Connect.png?raw=true)


# Telemedicine Solutions

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

![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Hours%20of%20Operation.png?raw=true)


## Create a Queue

1.	Choose Routing, Queues, Add new queue.
2.	Add the appropriate information about your queue and choose Add new queue, in this case addition then next information
	- Name: Medicine
	- Description: Tele-Medicine Queue
	- Hours of Operations: Tele-medicine Hours
3.	Click Add new queue. The queue is automatically active.

![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Queue.png?raw=true)


## Import the Queue Flow

1.	Choose Routing, Contact Flows
2.	Click combo box Create Contact Flow and select Create Customer Queue Flow
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Contact%20Flow%20-%20Create.png?raw=true)

3.	Click combo box save, Import flow (beta)
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Contact%20Flow%20-%20Import.png?raw=true)

4.	Select file Tele-medicine Queue, find this file into Tele-medicine Solutions folder and click Import
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Queue%20Flow%20-%20Import%20Select.png?raw=true)

5.	When you import the flow, you see the next screen
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Queue%20Flow%20-%20Imported.png?raw=true)

6.	Please save and publish the Queue Flow.


## Import the Contact Flow
### Rapid Response (Call)
1.	Choose Routing, Contact Flows and Create Contact Flow 
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Contact%20Flow%20-%20Create.png?raw=true) 

2.	Click combo box save, Import flow (beta)
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Contact%20Flow%20-%20Import.png?raw=true)

3.	Select file Tele-medicine Flow, find this file into Tele-medicine Solutions folder and click Import
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Contact%20Flow%20-%20Import%20Select.png?raw=true)

4.	When you import the flow, you see the next screen
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Contact%20Flow%20-%20Imported.png?raw=true) 

5.	Please save and publish the Contact Flow.

### Quick Connection (Chat)
1.	Choose Routing, Contact Flows and Create Contact Flow 
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Chat%20-%20Create.png?raw=true)
 
2.	Click combo box save, Import flow (beta)
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Chat%20-%20Import.png?raw=true)

3.	Select file Tele-medicine Chat, find this file into Tele-medicine Solutions folder and click Import
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Chat%20-%20Import%20Select.png?raw=true)

4.	When you import the flow, you see the next screen
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Chat%20-%20Imported.png?raw=true)

5.	Please save and publish the Contact Flow
When you finish import all Queue and Contact flow you see in the Routing -> Contact flow you see 3 flow
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Validation%20Imported.png?raw=true)

 
## Create a routing profile
While queues are a 'waiting area' for contacts, a routing proﬁle links queues to agents. When you create a routing proﬁle, you specify which queues will be in it. You can also specify whether one queue should be prioritized over another.

Each agent is assigned to one routing proﬁle.

To create a routing proﬁle
1.	Choose Users, Routing proﬁles, Add new proﬁle.
2.	Enter or choose the following information:
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Routing%20Profile.png?raw=true)

3.	Under Routing proﬁle queues, enter the following information and click add queue
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Routing%20Profile%20-%20Save.png?raw=true)

4.	Under Default outbound Queue
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Routing%20Profile%20-%20Outbound.png?raw=true)

5.	Choose Add new proﬁle.

 
## Configure Users
You can add medics and conﬁgure them with permissions that are appropriate to their roles (for example, agents or managers). 

### Add a user individually
1.	Log in to the Amazon Connect console with an Admin account, or an account assigned to a security proﬁle that has permissions to create users.
2.	Choose Users, User management.
3.	Choose Add new users.
4.	Choose Create and set up a new user and then choose Next.
5.	Enter the name, email address, and password for the user.
6.	Choose a routing proﬁle Tele-medicine Profile and a security proﬁle Agent
7.	Choose Save. 
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Users.png?raw=true)
 

### Add users in bulk
Use these steps to add several users from an Excel spreadsheet (.csv)
1.	Log in to the Amazon Connect console with an Admin account, or an account assigned to a security proﬁle that has permissions to create users.
2.	Choose Users, User management.
3.	Choose Add new users.
4.	Choose Upload my users from a template (csv) and then choose Next.
5.	Choose Download template.
6.	Add your users to the template and upload it to Amazon Connect.


## Claim a Phone Number
In this step, you set up a phone number so that you can experiment with Amazon Connect.
1.	On the navigation menu, choose Routing, Phone numbers.
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Claim%20-%20Phone%20Number.png?raw=true)

2.	On the right side of the page, choose Claim a number.
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Manage%20-%20Phone%20Number.png?raw=true)

3.	Select the DID (Direct Inward Dialing) or Toll free tab. Use the drop-down arrow to choose your country/ region. When numbers are returned, choose one.
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Claim%20-%20Tool%20Free%20Number.png?raw=true)

4.	In the Description box, type this note: This the number for Tele-medicine Solutions.
5.	In the Contact Flow/IVR select Tele-medicine Flow and chose Save
![alt text](https://github.com/aws-samples/amazon-connect-telemedicine-sample/blob/main/Images/Claim%20-%20Save%20Number.png?raw=true)


Congratulations! You set up your instance and claimed a phone number. Please call and validate functionality 


## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

