# async2sync
Another async to sync library. Run a callback when all tasks are completed.

### Usage

```javascript
// Require the package
const Task = require('async2sync').Task;

// Create a new task
var task = new Task();

// Start some jobs using callbacks/promises
someJobs.forEach(aJob => {
  // Tell the task we added another job
  task.tasks++;
  
  aJob.start().then(result, err => {
    console.log("Fulfilled job promise");
    
    // Tell the task that one was completed
    task.tick();
  });
});

// Tell the task what to do when all the tasks are done
task.callback = doSomething;

// If you want you can override task.call with a method for how you would like the callback called or how tasks should be counted

// Wait for the task then do something
task.wait();

function doSomething() {
  console.log("All the jobs were completed!");
}
```
