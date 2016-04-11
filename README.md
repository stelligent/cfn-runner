## cfn-runner

This is a node.js utility for synchronously running CREATE, UPDATE, or DELETE on CloudFormation stacks.

**Usage**

```
// Require the module
var CFNRunner = require('cfn-runner');

// Instantiate the runner.  The arguments are (region, templateFile, credentials)
// credentials should be an object like:
// {'accessKeyId': XXXXXXX, 'secretAccessKey': XXXXXX, 'region': 'us-east-1'}
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
