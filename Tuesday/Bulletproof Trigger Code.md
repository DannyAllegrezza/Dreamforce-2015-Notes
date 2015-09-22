## Bulletproof Trigger Code

Avoiding the pain points:
1. Don't write a trigger. 
2. Avoid DML
3. Write Great Unit Tests

- Design for testability.
- Use asserts
- Always test in Bulk. 
- Test the happy path (test the bare minimum). 
- Don't test if the trigger handler is disabled.
- Test error and exception conditions
- Try to cover all logical branches

Create a base class; always test in bulk.

Remove DML from unit tests

Cover all logic
//cover test with null values for Name, Account number
// test with blank values for Name, accountNumber
// test with long values
// test where description doesn't change
// etc. 

