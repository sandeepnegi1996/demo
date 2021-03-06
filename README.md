## Demo - demonstrates an application and tests

This is an application used by [Coveros](https://www.coveros.com/) to demonstrate a multitude of good
software practices.  

#### Dependencies:

[Oracle Java Development Kit](https://www.oracle.com/technetwork/java/javase/downloads/index.html)

#### Quick Start:

* Clone or download this repo.  (if you download, unzip the file to a directory.)
* On the command line in the top directory of this repo, run _gradlew apprun_
* Visit the application at http://localhost:8080/demo


###### Optional Dependencies - needed for API testing and Selenium testing.
* [Python](https://www.python.org/downloads/)
* [Chromedriver](http://chromedriver.chromium.org/downloads)
* [Chrome internet browser](https://www.google.com/chrome/)

---

#### Java installation notes

To install: download the development kit, make note of the installation directory.  Add that directory 
to your path.  For example, on Windows, press the Windows button, type "env" to edit the environment
variables for your account.  Under _user variables_ click New and add:

*  Variable name: JAVA_HOME
*  Variable value: C:\Program Files\Java\jdk-11.0.5   _replace this with the correct path_

Click OK.
Click the PATH user variable and click edit, and then click New, and add a new line for Java
as follows:

    %JAVA_HOME%\bin
    
Test this out by opening a command terminal, for example run the program called "cmd", and run this:
    
    javac -version
    
You should get something similar to the following:

    C:\Users\byron>javac -version
    javac 11.0.5
    
Now you are ready!


#### Chromedriver notes
make sure that the Chromedriver executable is installed in one of the directories that is 
on your path.  To see your path, type the following in a command line: 

on Windows:

    echo %PATH%  
    
On Mac/Linux:

    echo $PATH
    
#### Python notes
To run API tests and Selenium tests, an easy way to handle its 
dependencies is to use *pipenv*.  To get this installed, first download
[get-pip.py](https://bootstrap.pypa.io/get-pip.py), and run the following on the command line:

    python get-pip.py
    
Then,

    pip install pipenv
   
And in the demo directory,
    
    pipenv install   
   
#### To build and run tests:
On the command line, run the following:

On Mac/Linux

    ./gradlew check

On Windows

    gradlew check

#### To run the web application:
On the command line, run the following:

On Mac/Linux

    ./gradlew apprun

On Windows

    gradlew apprun
    
Then, head to http://localhost:8080/demo    
    

#### To run API and UI tests:
Note: The app has to be already running for these tests to pass, and you _need_
to have installed Python and Chromedriver.

On the command line, run the following:

On Mac/Linux

    ./gradlew runAllTests

On Windows

    gradlew runAllTests    
    
#### Interesting links when the system is up:
* http://localhost:8080/demo - the main application
* http://localhost:8080/demo/console - the database viewer - use URL of jdbc:h2:mem:training and no user or password

#### Summary of relevant Gradle commands
* gradlew apprun - runs the application
* gradlew check - runs all tests possible with only dependency being Java 8.  No need for app to be running.
* gradlew runAllTests - runs the whole set of tests**  
* gradlew clean - cleans build products and installs pre-push hook. (see the file in this directory, pre-push)
* gradlew runBehaveTests - runs the UI tests**
* gradlew runApiTests - runs the API tests**
* gradlew generateCucumberReport - runs cucumber and creates a nice-looking HTML report
* gradlew pitest - runs mutation testing (see http://pitest.org/)
* gradlew dependencyCheckAnalyze - analyzes security reports for the dependencies of 
  this project.  See https://www.owasp.org/index.php/OWASP_Dependency_Check
* gradlew sonarqube - runs static analysis using SonarQube.  Sonarqube must be running - check http://localhost:9000
* gradlew fastIntegrationTest - runs the database integration tests
* gradlew startH2Console - Starts a console to examine the H2 database file.  (user and
  password are empty, URL to use is jdbc:h2:./build/db/training)
* gradlew <task 1>...<task N> taskTree - a utility that will show the task tree for a particular task



  ** Requires the app to be running 
     (usually in another terminal) and all optional dependencies installed.

#### Summary:
 
Demo consists of a simple web application and tests.  Its goal is to provide 
an environment suitable for demonstration and practice in valuable development
techniques.  Some of the techniques exemplified are:
* Unit tests in TDD style using [Junit](https://junit.org/junit5/) as a driver and [Mockito](https://site.mockito.org/) for mocks, with coverage reports.
* BDD-style tests using gherkin
  * [Cucumber](https://docs.cucumber.io/) tests, with reports
  * [Behave](https://behave.readthedocs.io/en/latest/) UI tests that use [Selenium](https://www.selenium.dev/) web driver.
* Integration tests that test the database
* Database versioning, with [Flyway](https://flywaydb.org/)
* Uses [H2 database](https://www.h2database.com/html/main.html) to simplify operation
* Security analysis using [DependencyCheck](https://www.owasp.org/index.php/OWASP_Dependency_Check)
* Uses [Gretty](https://github.com/gretty-gradle-plugin/gretty) which allows us to hot swap Java code at runtime.

Its essential goals:
* Just works, any platform.
* As simple as possible
* Minimal system requirements
* Fast and easy to install and to run
* High test coverage
* Multiple business domains
* Easy to maintain and improve
* Well documented
* High performance
* Illustrates maximum number of techniques
* Easy to get up to speed
    
#### The whole shebang - a CI/CD pipeline

Details on building out a CI/CD pipeline are found in the "docs/ci_and_cd" directory.
For example, to set it all up on a [local Windows box](https://raw.githubusercontent.com/7ep/demo/master/docs/ci_and_cd/ci_and_cd_for_localhost.txt) 

###### Features of the pipeline:
* Instructions for setting up virtual machines (with VirtualBox).
* A fully functioning demonstration CI/CD pipeline using Jenkins.
* Incorporates static analysis using SonarQube
* UI tests running on Chrome


---

##Screenshots:
![Cucumber report](https://c2.staticflickr.com/8/7881/33202009728_00134731ac_o.png)
![Feature file](https://c2.staticflickr.com/8/7811/47077017811_ef51957ea5_b.jpg)
![Jenkins pipeline](https://c2.staticflickr.com/8/7889/33202009658_11422b7f20_b.jpg)
![Webapp](https://c2.staticflickr.com/8/7916/47077017561_f190c6f88e_o.png)
![Zap attach proxy](https://c2.staticflickr.com/8/7905/33202009438_8f367e20ec_o.png)
![SonarQube analysis](https://c2.staticflickr.com/8/7823/33202009548_e678128200_b.jpg)
![Running performance tests](https://c2.staticflickr.com/8/7854/47077017751_7e045f68dd_b.jpg)
