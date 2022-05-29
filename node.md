# Express/Node introduction

 Node was initially released, for Linux only, in 2009. The NPM package manager was released in 2010, and native Windows support was added in 2012. 
 Express was initially released in November 2010 and is currently on version 4.17.3 of the API (with 5.0 in "beta"). 

## introduction to Node : 

- what is node ? 

is an open-source, cross-platform runtime environment that allows developers to create all kinds of server-side tools and applications in JavaScript.

##### - why we need it ? 

  here is some benifits :
.You can use Node.js to create a simple web server using the Node HTTP package. 

.it is designed to optimize throughput and scalability in web applications and is a good solution for many common web-development problems .

.Code is written in "plain old JavaScript", which means that less time is spent dealing with "context shift" between languages 

.It is available on Microsoft Windows, macOS, Linux, Solaris, FreeBSD, OpenBSD, WebOS, and NonStop OS. Furthermore

.It has a very active third party ecosystem and developer community, with lots of people who are willing to help

we can run  the server bu  entring this comman ex : "node server.js" / "nodmone"

 **example creates a web server that listens for any kind of HTTP request on the URL http://127.0.0.1:8000/** : 

  ![](../sqlscreenshots/ex.PNG)

  ## introduction to Express : 

  Express is the most popular Node web framework, and is the underlying library for a number of other popular Node web frameworks . 

  why to use it ? : 
  ##### - provides mechanisms to : 

.Write handlers for requests with different HTTP verbs at different URL paths (routes).

.Integrate with "view" rendering engines in order to generate responses by inserting data into templates.

.Set common web application settings like the port to use for connecting, and the location of templates that are used for rendering the response.

.Add additional request processing "middleware" at any point within the request handling pipeline.

## what is npm :
.npm (originally short for Node Package Manager), is a package manager for the JavaScript programming language maintained by npm, Inc.
.npm is the default package manager for the JavaScript runtime environment Node.js.
.It consists of a command line client, also called npm, and an online database of public and paid-for private packages, called the npm registry. 
.npm can manage packages that are local dependencies of a particular project, as well as globally-installed JavaScript tools
### ex: npm install / npm start / npm test 

## what is TDD : 
Test Driven Development (TDD) is software development approach in which test cases are developed to specify and validate what the code will do. In simple terms, test cases for each functionality are created and tested first and if the test fails then the new code is written in order to pass the test and making code simple and bug-free.

.The simple concept of TDD is to write and correct the failed tests before writing new code (before development).


## what is CI/CD : 

#### CI :  "Continuous Integration" is the practice of automating the integration of code changes from multiple developers into a single codebase. It is a software development practice where the developers commit their work frequently into the central code repository (Github or Stash). Then there are automated tools that build the newly committed code and do a code review, etc as required upon integration.

#### CD : Continuous Delivery is carried out after Continuous Integration to make sure that we can release new changes to our customers quickly in an error-free way. This includes running integration and regression tests in the staging area (similar to the production environment) so that the final release is not broken in production. It ensures to automate the release process so that we have a release-ready product at all times and we can deploy our application at any point in time. 


[main page](../README.md)

