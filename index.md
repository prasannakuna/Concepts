# Concepts

# CORS
# NPM
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
