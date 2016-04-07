## cfn-runner

This is a node.js utility for synchronously running CREATE, UPDATE, or DELETE on CloudFormation stacks.

**Usage**

```
// Require the module
var CFNRunner = require('cfn-runner');

// Instantiate the runner.  The arguments are (region, templateFile, envFile)
// envFile should be a text file containing:
//   AWS_ACCESS_KEY_ID=XXXXXXXXXXXXXXXXXXXXX
//   AWS_SECRET_ACCESS_KEY=XXXXXXXXXXXXXXXXXXXXX
// If the envFile argument is omitted then the runner will look for the AWS credential variables in the environment (process.env);
var runner = new CFNRunner('us-east-1', '/a/cfn/template.json', '/a/file/containing/aws/credentials.txt');

// Declare a callback function
var callback = function(err) {
  if(err) {
    console.log(err);
  }
  else {
    console.log('success');
  }
};

// Create or update the stack.
runner.deployStack(callback);

// Delete the stack
runner.deleteStack(callback);
```
