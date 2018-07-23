# Running and debugging a test in Visual Studio

Visual Studio includes the unit testing, When you build the test project, the tests appear in Test Explorer. If Test Explorer is not visible, choose Test on the Visual Studio menu, from the Windows submenu click Test Explorer.

As you run, write, and rerun your tests, Test Explorer displays the results in default groups of Failed Tests, Passed Tests, Skipped Tests and Not Run Tests.

To run or debug the unit test from the Test Explorer right click on the unit test, there are two choices “Run Selected Tests” to run the unit test and “Debug Selected Tests” to debug the unit test. Also there is an option to run all the unit tests, “Run All”. 

Default WebDriver is a normal Chrome. When the Headless is enabled, Unit test will be run without showing the Chrome browser, to enable this feature and hide chrome while the unit test is running, open App.config and set 	Headless key to true.