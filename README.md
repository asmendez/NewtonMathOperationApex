# NewtonMathOperationApex

This is a simple coding challenge project that use aunyks/newwton-api to update the Math Operations custom object in a salesforce org instance.

Reference to the API: https://github.com/aunyks/newton-api

# The Math Operation Custom Object

If you want to use these Apex classes in your org you will need to create the custom object with the following ccriteria:

- API Name: Math_Operation__c
 - Fields:
	 - Expression__c Text(100) Required
	 - Operation_Type__c Picklist Required
	 - Math_Operation_Result__c Text(200)
 - Operation types:
	 - abs
	 - arccos
	 - arcsin
	 - arctan
	 - area
	 - cos
	 - derive
	 - factor
	 - integrate
	 - log
	 - simplify
	 - sin
	 - tan
	 - tangent
	 - zeroes

# The Newton Maths App

In your Salesforce organization you must create the Math Operations tab for the Math Operation custom object. Then you can create a new App that will include that tab. The app for the purpose of this demo is called Newton Maths.

For the purpose of this demo you should create at least one Math Operation record. You must consider the Newton APIquirement for Expressions: 

# How to execute the Apex class

Once you have all the classes imported to your organization in the developer console go ahead and follow these steps:
 1. Click in Debug > Open Execute Anonymous Windows
 2. Write the following code and click Execute (you can select Open log if you want and click in Only Debug later)

// Get the 5 newest MathOpperation

Math_Operation__c[] newMathOperations = [SELECT Id, Expression__c, Operation_Type__c FROM Math_Operation__c ORDER BY CreatedDate DESC LIMIT 5]; 

// Call the Apex class method 

NewtonApp_NewtonMathsIntegrationService.setMathOperationResultForLastFiveOperations(newMathOperations);


3. Navigate to the Newton Maths app
4. Click in the Math Operations tab
5. Select on of the Recently viewed records
6. You can see that the Result field has now the value provided by the Newton Api
