# rtimer
Persistent timer with set and clear

## Install

	npm install rtimer

## Usage

rtimer has two instance methods `set` and `clear`.
 - `set` restart the timeout
 - `clear` clear the current timeout, timeout can be restarted again after clear
 - `callback` property contains the callback method
 - `delay` property contains the timeout delay

## Example

```js
var rtimer = require('rtimer');

var start_time = +new Date();

// create new timeout with 1000ms delay
var timeout = rtimer(function() {
	// this will be triggered after 1500ms
	// because of the reset
	var t = (+new Date() - start_time);
	console.log('time ' + t + ' ms');

	// change timeout delay and callback
	timeout.delay = 500;
	timeout.callback = function() {
		console.log('Hello World!');
	};
	// reset timeout
	timeout.set();
}, 1000);

// reset timeout after 500ms
setTimeout(function() {
	timeout.set();
}, 500);

```
