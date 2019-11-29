# flutter_chatBot
Chatbot to tell facts about Flutter.
Joseph Moshood
FlutterDevs
ChatBot in Flutter using DialogFlow
Aditya Syal
Aditya Syal
Nov 28 · 6 min read


So, it’s been a while since Flutter is out there and its upsurge these days is phenomenal. The unparalleled performance of the framework is one of the reasons for its fondness among App developers other than the fact that it helps build cross-platform apps.

Today, I am going to tell you how to build a ChatBot in Flutter using the Dialog Flow development suite. So, first let's see the points that I am going to cover in this article:

Brief about Dialogflow
Setup and Understand the console
Train your Agent
Integrate Dialogflow in Flutter App
Let's move on with the first part where we should know about Dialogflow which is the building block of the ChatBot.

What is Dialogflow?
Dialogflow is a development suite that incorporates Google’s machine learning expertise to build end-to-end,deploy-everywhere interfaces for websites, mobile applications, and IoT devices.

Build natural and rich conversational experiences

Give users new ways to interact with your product by building engaging voice and text-based conversational interfaces, such as voice apps and chatbots, powered by AI. Connect with users on your website, mobile app, the Google Assistant, Amazon Alexa, Facebook Messenger, and other popular platforms and devices.

Advantages of Dialogflow:
Powered by Google’s Machine learning
Built on Google’s Infrastructure
Optimized for Google Assistant
To know more about Dialogflow please refer to their video,


Setup and Understand Dialogflow console:
Moving on, Lets head over to the Dialogflow website by clicking on the https://dialogflow.com/.


Click on the Go to Console at the top right corner of the website.
Login using the Google account.

Create your first agent. Give it a name, set the time zone and your default language for the agent.

After clicking on Create , you’ll get the console with all the features that you can implement in your Agent.
Understanding the basic console:

Two things which are the base of an Agent you just created.

Intents
Entities
7`

Intents:
An intent categorizes an end-user intention for one conversation turn. For each agent, you can define many intents, where your combined intents can handle a complete conversation. When an end-user writes or says something, Dialogflow matches the end-user expression to the best intent in your agent. and based on that intent a response is provided by the agent to the end-user.

Intents are mappings between a user’s queries and actions fulfilled by your software.

There are two default Intents provided by the Dialogflow, namely:

Default Fallback Intent: These types of intents are used when the user’s input expression doesn’t match the Intent defined for the Agent.

Default Welcome Intent: These types of intents are used when the end-user starts the conversation.

Entities:
Each intent has a parameter and each intent parameter has a type, called the entity type, which dictates exactly how data from an end-user expression is extracted.

Dialogflow provides predefined system entities. For example, there are system entities for matching dates, times, colors, email addresses, and so on. You can also create your own developer entities for matching custom data. For example, you could define a product entity that can match the types of products available for purchase with an Online store agent.

Entities are objects your app or device takes action on.

Train your Agent:
Now, that you have basic knowledge about the Dialogflow console, all that you’ll need to build a basic Agent we can now move forward to train our agent with test cases.

Create the Intents based on your requirement
Add the training phrases to the Intents
Add the response phrases for those training phrases
Add the Action and Parameters if required for that Intent
Add the Events which will trigger the Intent on the basis of the event occurrence irrespective of the training phrases, if any.
Add the context to the Intent.

Training Phrases for the Intent

Response Phrases for the Intent
Once you create an Intent then you can go on creating different intents for different queries. As of now, Dialogflow allows you to create 780 Intents and after that, you need to update the machine learning algorithm manually which you can do by following the steps:

Click on the gear icon for your agent.
Click the ML Settings tab.
Click Train.

Once you have trained your Agent, now you’re ready to integrate your Agent to your Flutter app and before heading over to Flutter, you have to download a JSON file from the console which helps your App to connect to the Agent you’ve just created. To do that follow these steps:

Open the Google Cloud Console.
Select your Project.
From the Navigation drawer click on API's & Services

Choose Credentials from the options.

From the Credentials window, Select Service account key from the dropdown menu.

Next, select the Dialogflow integration option from the Service Account dropdown menu and select JSON from the radio button below that.

That’s it, you’ll have a JSON file downloaded which you’ll need in the next steps.

Integrate Dialogflow in Flutter App
Now, that you have your agent ready and trained you’re all set to integrate it into your Flutter app.

First, add the dependency to your pubspec.yaml file. Please make sure to the latest version, check here.
dependencies:   
flutter_dialogflow: ^0.1.3
Create a folder in your project with the name assets and move the JSON file that you’ve downloaded from the Google Cloud Console into it.
Open the pubspec.yaml file and add,
flutter:

  uses-material-design: true
  assets:
    - assets/[name_of_your_json_file].json
Now, I won’t show the whole code for the chat app here for that I will attach the link to the GitHub repo so feel free to look into it for the code but here I’ll let you know the part where you setup the code for Dialogflow in the app.

AuthGoogle authGoogle = await AuthGoogle(fileJson: "assets/[your_json_file_name].json").build(); 
Dialogflow dialogFlow =
Dialogflow(authGoogle: authGoogle, language: Language.english);
AIResponse response = await dialogFlow.detectIntent(query);
Note: use the same filename as mentioned in the pubspec.yaml file.

That’s all you’ll need to get your Agent to respond to your questions. The response will have your Agent responses based on your query.

Now, you’re good to go to make your first chatbot in Flutter using Dialogflow. This is the basic example of ChatBot just to give you an idea about how to start it.

Click the GitHub link below to find the source code of the ChatBot. Also, keep in mind not to directly clone the project and run it, it won’t work as I have removed my JSON credentials. All you need to do is replace the JSON file with your JSON obtained from the Google Cloud Console.

Aditsyal/flutter_chatbot
