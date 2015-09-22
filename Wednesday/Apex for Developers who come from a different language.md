## Apex for Developers who come from a different language.
@dannyallegrezza


The biggest things that we need to realize is that there are Governor Limits inside of SFDC.

- They are there for a reason, because salesforce is a multi-tenant architecutre
- The limits enforce efficient code upfront
- Most common limits for developers are:
- DML Statements 
- SOQL Queries Issued
- SOQL Records Retrieved
- The limits are constantly increasing (sometimes removed). 

## Limits Class
- Access governor limit specifici information
- Two methods versions for each limit
- .getDMLStatemenths() and getLimitDMLStatements()

```
system.debug('DML Statements Issued - ' + Limits.getDMLStatemenths());

```

When do limits start and end? 
A: The Execution Context
- user clicking on a button
- executing anonymous apex
- then the end of the transaction
- Static variables persist 

Savepoints offer transaction control options. These are nice because you can add a savepoint, which are good for exceptions or business logic.

Savepoints can rollback 
DML 
Emails
Calls to @future methods

Example

```
You could set up an empty account

```

## DML vs Database Class
###DML
- insert 
- update
- upsert
- delete
- undelete
- merge

###Database class
- Offers partial record processing
- offers ConvertLead method
- Returns result object array. This is a great option if you need more detailed reasoning as to why your code insert failed.

```
// Showed example of inserting a list of Accounts being inserted with Database.insert. The big benefit 
```

##Triggers
###Always try to use the declarative FIRST. This means WORKFLOW or PROCESS BUILDER
- There should only be ONE trigger per object
- NO logic inside of the trigger
- Bulkify
- Defend against recursion with static variables (have heard multiple opinions on this)
- Utilize trigger handler model

```#java
trigger TaskTrigger on Task (after insert, before update){

	private static boolean firstRun = true;
	TaskTriggerHandler handler = new TaskTriggerHandler();
	
	try {
		if (firstRun){
			firstRun = false;
			handler.execute(); //This is firing from the [OBJECTNAME]TriggerHandler class
		}
	} catch (Exception e){
		system.debug(e.getMessage());
	}
}
```

He created a public abstract class Triggerhandler() (base class)

- Creates a model in which the trigger follows a defined order for firing.
- Next, he inherits with a [OBJECTNAME]TriggerHandler class which inherits from TriggerHandler.
- Inside of the [OBJECTNAME]TriggerHandler he overrides the functions

##Bulkification
Non-Bulkified Trigger: Just grabbing 1 record at a time. I don't think we have this happening anywhere.. or that I have ever done this. 

Bulkified

// Setup a list of your object

```
for (whatever A in trigger:new){
//do stuff
}
```

Non-bulkified DML
Again, in this example he just shows a for loop where he is looping through contacts in a collection, and then doing a DML state. So this is violating the "No DML in a loop" code.

## Asynchronous
###Future Method
- for long running methods to avoid delaying an apex transaction
- callouts to external Web services
- to segregate DML operations and bypass mixed save DML errors

```
@future (callout=true)
public static void doCalloutFromFuture(){
//do callout stuff
}
```

#### Queueable Apex
- To start a long running operation and to get a job ID for it (AsyncApexJob)
- to pass complex types to a job
- to chain jobs

## Batch Apex
- Good if you have long running jobs with large data volumes
- Iterates over data volumes in batches
- Allows for larger query results
- Always try to tailor your WHERE clause in your query, that way you can limit your results

## Scheduled Apex
- Schedule an apex class to run on a specific schedule
- Popular in conjunction with batch apex


## Unit Testing
- As we know, 75% code coverage requirement
- Assert expected behavior
- No data cleanup necessary

### Type of test to create:
- single action
- bulk action
- positive
- negative
- restricted user - system.runAs(user)

###Test.startTest() and Test.stopTest()
- What these methods are good for is that they help sandbox a governor limit set with any code you run in between these two lines.
- This is good if we need to setup a bunch of DML/SOQL before hand to get the test data mocked up. 
- ```test.stopTest()``` will make sure all asynch code is finished before you do your asserts.
- ```@TestVisible annotation``` If you have a private method, you can test the method as if it was public.

