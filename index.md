# Concepts

## CORS
## NPM
    - npm init -> this will create package.json file which contains a metadata for all the node modules to be installed
    - npm install -> will download all the node modules specified in package.json
    - npm install <package name> -> this will install a package locally for the specified project in which this command has run
    - npm install <package name> --save -> this will save the package as dependency in package.json and download the module aswell
    - npm install <package name> --save-dev -> this will save the package as dev dependency in package.json and download the module aswell
    - npm install <package name> -g -> this will install a package globally
    - npm uninstall <package name> -> this will uninstall a package locally but it will not remove dependency from package.json
    - npm uninstall <package name> --save -> this will uninstall a package locally and will remove dependency from package.json
    - npm uninstall <package name> --save-dev -> this will uninstall a package locally and  remove dev dependency from package.json
    - npm list depth 0-> will list all the packages installed in tree structure and you can also specify depth
    - npm prune -> will remove all the extraneous packages installed meaning which are installed locally but not mentioned in package.json
    - package.json contains "moment" : "4.5.1" -> here 4 represents major version number, 5 minor version number, 1 patch version number.
    - patch version number changes when there are any bug fixes, minor version number changes when there is a new feature addition and will not break current features, major version changes when there are new features which break current features
    - npx will bea coming as part of npm@5.2.0 it is a nodejs binary executor,
        1. Running a project-local bin :  
            can run local binaries without specifying it in $PATH
            eg: without npx: ./node_modules/.bin/serverless create  --template aws-node.js
                with npx: npx serverless create  --template aws-node.js
        2. One-off invocation without local installation:
            can execute uninstalled binaries of node modules
            eg: $ npm rm webpack
            $ npx webpack -- ...
            $ cat package.json
            ...webpack not in "devDependencies"...
        3. Run Command string with specific version
            eg: npx -p node@8 npm run build, this will consider node 8 version
        there are more [ ](https://www.npmjs.com/package/npx#shell-auto-fallback)

### javascript
## Objects
1. ### Accessing 
        1. const myObject = {1:"Hello", secondWord: "world"}
            myObject.1 would return error and myObject[1] will return "Hello"
            myObject.secondWord will return "world"
        2. const myObject = {1:"Hello", secondWord: "world"}
           const myVariable = "secondWord"
           myObject.myVariable returns undefined, myObject[myVariable] will return "world"
2. ### Passing a primitive is pass by value and passing an object is pass by reference 
### pass by value
        function changeToEight(n) {
            n = 8; // whatever n was, it is now 8... but only in this function!
        }
        let n = 7;
        changeToEight(n);
        console.log(n); // 7
        
### pass by reference
        let originalObject = {
        favoriteColor: 'red'
        };
        function setToBlue(object) {
            object.favoriteColor = 'blue';
        }
        setToBlue(originalObject);
        originalObject.favoriteColor;// 'blue'
    This rule applies while creating a new copy of orginal object by saying const copy Object = originalObject
3. delete operator directly mutates the object.
4. A function property of an object is called a method, "How the function is invoked determines the value of this inside the function"
5. Only declaring variables with the var keyword will add them to the window object. If you declare a variable outside of a function with either let or const, it will not be added as a property to the window object.
6. Global Functions are Methods on window

## functions
1. In JavaScript, functions are first-class functions. 
    Be stored in variables
    Be returned from a function.
    Be passed as arguments into another function.   
2. A function that takes other functions as arguments (and/or returns a function, as we learned in the previous section) is known as a higher-order function.
3. A function that is passed as an argument into another function is called a callback function.
4. forEach() doesn't return anything, while map() returns a new array with the values that are returned from the function
5. Array's filter() method is similar to the map() method:
    It is called on an array
    It takes a function as an argument
    It returns a new array
    The difference is that the function passed to filter() is used as a test, and only items in the array that pass the test are included in the new array


### Spring boot
## definition: 
    it is a tool for creation of production level spring based applications
    Spring - application framework for enterprise java applications
             programming and configuring model - write a simple class and annotate as service then all the things are handled
             infrastructure support - connect to database directly
## annotations
    @springbootapplication - this is added to main class for spring to identify this application belongs 
    @component for enabling of autowiring
    @autowired will inject the dependency
    @postmapping
    @jsonproperty - will let you customize you model properties while sending to client 
## configuring database
    just add jpa specific configuration in pom.xml or build.gradle 
    after that choose a database you want to use go to the maven repository search for that database you will be seeing some dependency configuration there you go copy that and paste the same in pom.xml
    <!-- https://mvnrepository.com/artifact/org.postgresql/postgresql -->
    <dependency>
        <groupId>org.postgresql</groupId>
        <artifactId>postgresql</artifactId>
        <version>42.2.16</version>
    </dependency>

    annotations used for database configuaration are
        @Repository  for Dao class which extends crudrepository<entityclass, primarykey>
        @Entity for the resource class like customer, employee - javax.persistence jpa package
        @Id for the primary key in entity class eg: customerID
        @GeneratedValue for generating ids/ primarykeys
        @EnableJpaRepositories for main class to enable jpa actions
## JPA





### docker

docker commands
    docker rm $(docker ps -a -q -f status=exited) to remove all the exited containers

    docker build -t prasanna555/catnip . for building an user image -t takes image name followed by location where docker file is located
    

Terminology:
Images - The blueprints of our application which form the basis of containers. In the demo above, we used the docker pull command to download the busybox image.
Containers - Created from Docker images and run the actual application. We create a container using docker run which we did using the busybox image that we downloaded. A list of running containers can be seen using the docker ps command.
Docker Daemon - The background service running on the host that manages building, running and distributing Docker containers. The daemon is the process that runs in the operating system which clients talk to.
Docker Client - The command line tool that allows the user to interact with the daemon. More generally, there can be other forms of clients too - such as Kitematic which provide a GUI to the users.
Docker Hub - A registry of Docker images. You can think of the registry as a directory of all available Docker images. If required, one can host their own Docker registries and can use them for pulling images.

An important distinction to be aware of when it comes to images is the difference between base and child images.

Base images are images that have no parent image, usually images with an OS like ubuntu, busybox or debian.

Child images are images that build on base images and add additional functionality.

Then there are official and user images, which can be both base and child images.

Official images are images that are officially maintained and supported by the folks at Docker. These are typically one word long. In the list of images above, the python, ubuntu, busybox and hello-world images are official images.

User images are images created and shared by users like you and me. They build on base images and add additional functionality. Typically, these are formatted as user/image-name.
