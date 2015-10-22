title: "Running Grunt tasks programmatically"
date: 2015-10-20 21:12:04
tags:
---

Running grunt tasks programmatically is extremely simple but it's not obvious how to go about it at first. The key is the fact that the Gruntfile.js is just an ordinary javascript file which exports a module. Therefore to load the Gruntfile all you need to do is require it and pass it grunt as the argument.

```js
var grunt = require("grunt");
require("Gruntfile.js")(grunt);
```

You can then invoke any grunt task from that file using grunt.tasks(tasks, options, callback). Where tasks is an array of tasks you want to run, options is a map of options (these correspond to the options available via the grunt cli), and callback is a standard node callback.

```js
grunt.tasks(["build"], {}, function(err){
	console.log(err || "Success");
});
```

![Grunt - The Javascript Task Runner](/css/images/grunt.png "Grunt")