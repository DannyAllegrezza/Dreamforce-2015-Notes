## Defensive Apex Programming

Developers: We understand the full life cycle..

- Requirements 
- Design
- Code
- Test/QA/Document
- MAINTENANCE!! (50% of the cost of software)

##Maintenance: 
- Bug Fixes
- New OS Version/browser
- Platform Changes
- *Regression testing of changes by Developers*
- Critical Features

How does Force.com Life-cycle look?

Almost identical, but has **Metadata changes that change the behavior of the code.**

##Traditional Applications
Your app sits on top of a Platform

vs.

Apex Applications:

Apex and other declarative metadata changes sit on top of a Platform

We are not silo'd. We live in the same world as declarative development. 

Changes to metadata can easily break our code. Changes to code can easily break a process. That is just the way it is, it's part of developing on top of the Force.com platform.

##This is where Defensive Apex Programming codes into play.

Making a future call - the wrong way

```java
public void CallFuture1(){
	vulnerableFutureCall();
}

@future
public static void vulnerableFutureCall()
{
	//Do Something;
}
```


### Using a custom setting the wrong way

Boolean enabled = ConfigSetttings__c.getInstance('default').Applicaiton_Enabled__c;
- Guaranteed null reference exception on:
- Uninitialized orgs/sandboxes
- Unit tests have to run SeeAllData true
- SeeAllData false tests on methods that don't initialize setting
- SeeAllData false tests on managed package tests that can't initialize setting.

## better way:

has a private static ConfigSettings__c testConfig:

```java
public static ConfigSettings__c getConfig() method.
[
	if(Test.isRunningTest() && testConfig! = null) return testConfig;
	ConfigSettings__c result = ConfigSettings__c.getInstance('default');
	if(result == null)
	{
		result = new ConfigSettings__c(name='default',Application_Enabled__c = false);
	}
	
	if(Test.isRunningTest()) testConfig = result;
	return result;
]
```

Then ...

```
Boolean enabled = ConfigurationClass.getConfig().Application_Enabled__c;
```

The value of the old map value is the value from the beginning from the Context.

##Updating Records - Watch for Concurrency Errors

Instead of just doing ```update listOfRecords```, think about concurrency errors.


###OR

```java
// Create a list <Database.SaveResult> dmlResults = Database.Update(listOfRecords, false);

// loop and check for concurrency
```

Continuous Integration - In Traditional Software Dev

[JENKINS (the CI tool)] -> Build -> [SOFTWARE REPOSITORY] <----- Developers code

Jenkins can monitor a repository.. deploy to an org, send warnings, etc.


### In salesforce land

[JENKINS (the CI tool)] -> Build -> [ORG ] <----- Developers code

In Salesforce, we can run Unit Tests, and then look at the results on the org itself. 

- A lot of Orgs don't have real Unit Tests
- WE NEED TO CHECK AND ASSERT THE FUNCTIONALITY OF OUR ORG!!
- THE INVESTMENT IN UNIT TESTS PAYS OFF MANY TIMES MORE THAN THE LIFE OF THE SOFTWARE

##Is there a solution for this? 
CI App 

http://AdvancedApex.com/TestTracker

Free private managed package
Open Source

No UI, no config really, basically, when it sees a Unit Test that fails that was passing, it will send out an email. It's a workflow, so you can do anything you want (send a task, email, etc.).

https://get.pluralsight.com/free-weekly-course.html

