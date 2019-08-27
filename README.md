# tasker
Another async to sync library. Run a callback when all tasks are completed.

### Usage

```javascript
// Require the package
const Task = require('tasker').Task;

// Create a new task
var task = new Task();

// Start some tasks using callbacks/promises
someTasks.forEach(task => {
  // Tell the task we added another task
  task.tasks++;
  
  task.start().then(result, err => {
    console.log("Fulfilled task promise);
    
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
  console.log("All the tasks were completed!");
}
```
