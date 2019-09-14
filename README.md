# Node.js Interview Questions and Answers
| No. | Questions |
| --- | --------- |
|   | **Basic** |
|1  | [What is Node.js?](#what-is-nodejs) |
|2  | [Benefits of Node.js?](#benefits-of-nodejs) |
|3  | [Limitations?](#Limitations)|
|4  | [What is npm?](#what-is-npm)|
|5  | [Explain Node.js process modal?](#Explain-Nodejs-process-modal)|
|6  | [Primitive types?](#Primitive-types)|
|7  | [Core modules?](#Core-modules)|
|8  | [module.exports and exports?](#moduleexports-and-exports)|
|9  | [Difference between ~ and ^ in package.json?](#Difference-between-version-specificity)|
|   | [?](#)|
|   | [?](#)|
|   | [?](#)|
|   | [?](#)|
|   | [?](#)|
|   | [?](#)|


## Basic

   * Developer- Ryan Dahl 
   * Year- 2009
1. ### What is Node.js?
    * It is not a javascript library.
    * It is not framework.
    * It is not a programming language.
    * JavaScript / ECMAScript is the language specification.
    * It is a runtime.
    * It is a javascript runtime environment builtin on v8 engine.
    * It comes with runtime environment on which javascript code be interpreted and executed outside a browser.
    * Because of this runtime nodejs env ,now javascript can be executed on server side as well.
    * Blocking method execute synchronously and non blocking execute asynchronously.
    
2. ### Benefits of Node.js?
   * **Easy scalibility** - easily scale the application in both horizontal and vertical direction
   * **Single threaded, Speed and High performance**- it is non blocking i/o operation. v8 engine compile java script code directly into machine code.
   * **Advantage of caching**- it has a facility of caching single module. The first request gets cache into the application memory for any module.
   * **Light weight and Efficient** - it is non blocking, event driven i/o. it is asynchronous.
  
3. ### Limitations
   * Not good for CPU intensive task. Because it takes time to process a request, thereby blocks the single thread.
   
4. ### What is npm?
   npm- Node Package Manager
   - It is node module repository
   - CLI for Installing/Updating/Uninstalling packages, version and dependency management.
  
5. ### Explain Node.js process modal?
   #### Traditional web server modal
   - It has thread pool.
   - Whenever a request comes, available thread from the thread pool take the complete responsibility until the response send back.Then gets free and become availabe in thread pool for next request.
   - Request has to wait if any thread is not available.
   #### Node.js process model
   - Node.js runs in a single process.
   - Application code runs in a single thread.
   - All the requests will be handled by the single thread.
   - All I/O, long running job will be performed asynchronously.
   - Single thread does not need to wait to complete the request.It's free to take next request. When asynchronous I/O works completes, then it processes the request further and sends back the response.
   - An event loop is constantly watching for the events to be raised for an asynchronous job and executing callback function when the job completes.
   - Nodejs uses libev for the event loop.
   - Internally it is c++ thread pool to server asynchronous I/O.

6. ### Primitive types
   - String
   - Number
   - Boolean
   - Undefined
   - Null
   - RegExp
   - everything else is object in nodejs

7. ### Core modules
   - EventEmitter
   - FS
   - Net
   - Stream
   - Global Object

8. ### module.exports and exports
   - It is a special object which is included in every js file in nodejs application by default.
   - module is a variable that represents current module.
   - export is an object that will be exposed as a module.
   - so whatever is assign to module.exports or exports, will be exposed as module.
  
    reference - https://www.tutorialsteacher.com/nodejs/nodejs-module-exports

9. ### Difference between version specificity
    - ~version "Approximately equivalent to version"
    - ^version "Compatible with version"
    - version Must match version exactly
    - >version Must be greater than version
    - >=version etc
    - <version
    - <=version
    - 1.2.x 1.2.0, 1.2.1, etc., but not 1.3.0
    - http://sometarballurl (this may be the URL of a tarball which will be downloaded and installed locally
    - * Matches any version
    - latest Obtains latest release

10. ### Event Loop
    - The event loop is what allows Node.js to perform non-blocking I/O operations.
    - When Node.js starts, it initializes the event loop, processes the provided input script which may make async API calls, schedule timers, or call process.nextTick(), then begins processing the event loop.
    - Each phase has a FIFO queue of callbacks to execute. 
    - when the event loop enters a given phase, it will perform any operations specific to that phase, then execute callbacks in that phase's queue until the queue has been exhausted or the maximum number of callbacks has executed. When the queue has been exhausted or the callback limit is reached, the event loop will move to the next phase, and so on.
    - ### Phases Overview
    - timers: this phase executes callbacks scheduled by setTimeout() and setInterval().
    - pending callbacks: executes I/O callbacks deferred to the next loop iteration.
    - idle, prepare: only used internally.
    - poll: retrieve new I/O events; execute I/O related callbacks (almost all with the exception of close callbacks, the ones scheduled by timers, and setImmediate()); node will block here when appropriate.
    - check: setImmediate() callbacks are invoked here.
    - close callbacks: some close callbacks, e.g. socket.on('close', ...).
    Between each run of the event loop, Node.js checks if it is waiting for any asynchronous I/O or timers and shuts down cleanly if there are not any.
11. a  