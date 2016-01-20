## Rotten Tomatoes
In this exercise you will get started with a simple node application. The application will read from two files; one JSON file and one XML-file.

The files contains famous movie titles and some metadata about those movies. You are supposed to write an application that reads the data from the files and calculates the average rating of the movies. The data in the json-file stems from [IMDB](http://www.imdb.com/) whereas the xml-file stems from [Rotten Tomatoes](http://www.rottentomatoes.com/). One average is calculated for the Imdb data and one average for the Rotten tomatoes data. (The focus of this exercise is promises and callbacks, not calculating stuff)

Lets get started!

### Getting started guide
Before you begin, make sure you have an laboratory environment set up according to your course specification.

1. Start out by creating a package.json identifying your project. (Tip: `npm init`).
2. Create an app.js file in the root directory. (`touch app.js`)
3. Create an directory called "lib". (`mkdir lib`)
4. Create an directory in the lib-folder called "movies" (`mkdir lib/movies`)
5. Create an file called movieParser.js  in the lib directory (`touch lib/movieParser.js`)
6. Export a function from the movieParser.js and require it in app.js. Add `console.log("Hello World");` to the function in movieParser. Call the function from app.js and run the application using `node app.js`. If the console greets you with "Hello World" you are good to go. Otherwise, debug!
7. Copy the [json-file](movies.json) and the [xml-file](movies.xml) into the folder `./lib/movies`
8. Find an npm-package that can convert xml to javascript objects. ([xml2js](https://www.npmjs.com/package/xml2js))
9. Add the package to your project. (`npm install xml2js --save`)

Now you are good to go.

In this exercise the main goal is to train your skills in handling callbacks and promises. The recommended path to follow is, therefore:
1. Solve the exercise using the fs-module (`var fs = require("fs");`) to read the content of the files and the module xml2js to convert the XML-content to js.
2. Wrap the fs-callback-interface behind a promise-module. I.e. create a module called `fs-promise.js` with functions returning promises. Make use of `Promise.all()` to be able to read the xml- and json-files in parallel.
3. Search the [npm library](https://www.npmjs.com/search?q=fs+promise) and discover that some one else already made a [promise wrapper](https://www.npmjs.com/package/fs-promise). Remove your fs-promise.js and use `fs-promise`instead. (`npm install fs-promise --save`)
4. Use the flow control module `co`(`npm install co --save`) together with generator functions and promises for an even slicker program flow.

#### Example use and output:
```shell
vagrant@precise32:/vagrant$ node app.js
Avarage rating IMDB: 9.08
Avarage rating Rotten Tomatoes: 94.8 %
```

### Bonus exercise
Using the built in time measurement tool `console.time("What I am measuring");` and corresponding `console.timeEnd("What I am measuring");` you can measure the execution time of parts of your code. Use that to analyze which parts of your code are the bottlenecks. How could that be avoided?
