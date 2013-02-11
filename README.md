Using Web Workers with RequireJS
=====================

This is a simple plugin that allows you to declare a dependency on a web worker script using requireJS with a simple syntax. See here for [primer on Web Workers](https://developer.mozilla.org/en-US/docs/DOM/Using_web_workers).

```javascript
    define(["worker!my-web-worker"], function(worker) {
		worker.onmessage = function (event) {
			alert("I got me a message!");
		};
	});
```

The plugin will return an initilized `Worker` object which will resolve the given module ID with the currenlty configured requireJS configuration (no need to hardcode script paths just for web workers).

If Worker is not defined (IE < 10), the plugin will load a [fake Worker implementation](http://code.google.com/p/fakeworker-js/) so that your scripts can utilize the same Worker API whether the browser supports it or not.

See the example for more details. NOTE: you need to run the example page from a server (e.g. localhost) rather than the file:// protocol for web workers to work. The run-server.bat file will spin up an IIS Express instance if you are on windows.