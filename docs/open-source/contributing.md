## Contributing

Create a branch, work on your features, and when ready merge it with the master branch.

Make sure your respect the [Coding Conventions](#coding-conventions).

Include at least one integration test that assures the component always behaves as expected. Also, include at least one test that shows how the component can be used programmatically.

Add javadoc documentation where applicable.

## Compiling

Run `mvn package` to compile the projects you will need. You shouldn't have to define build paths in Eclipse.

To get up and running, you will also need the following:
* Java, version 11 or later.

Additionally, you may need the following if you use them in your experiments:
* [liblpsolve55j](http://lpsolve.sourceforge.net/5.5/Java/README.html) (for Mac, see [here](https://gist.github.com/san81/15843df713054852f748)) to be added to java.library.path, for the Mapping Selection transducer (project `mappingselection-orm`)


## Coding Conventions

Before committing and pushing your code, please format it using Eclipse's Source -> Format. Allow lines to overflow.

Code should not contain warnings. For known warnings, please use @SuppressWarnings.

The code is separated into two parts, production, and test code, as follows:

* **Production code**. It is placed under `src/main` and it is not meant to be modified in order to run experiments.

* **Test code**. It is placed under `src/test` and contains:
    * *Integration tests*. These tests contain `IntegrationTest` in their class names. Success means component behaviour is as expected. Failure means the component behaviour is broken.
    * *Your tests*. These are placed in separate test classes. Only commit the tests you believe will be useful to other developers in terms of demonstrating component behaviour or intended use.

All other files are placed under:

* `src/main/resources` for the production and the test code.

The root folder of the project only contains `pom.xml`, and documentation about the project.

Transducer code is placed in packages under `com.tdvf.transducer.X`, where `X` is the name of the transducer.

All other project code is placed in packages under `com.tdvf.X`, where `X` is the name of the project.
