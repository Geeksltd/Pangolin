## Example: Selenium

Create new Unit Test project, add Nuget Packages Selenium.WebDriver and Selenium.WebDriver.ChromeDriver. If you want to run Selenium along with other browsers, instead of Chrome driver, install the right Nuget package.
The best practice of writing Selenium Unit Tests is that to initialize Selenium driver in TestInitialize method and dispose it from TestCleanup.

See example template.



```C#
using Pangolin;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace TestUITests
{
    [TestClass]
    public class SeleniumUnitTest
    {
        IWebDriver driver;
        
        [TestInitialize]
        public void TestInitialize()
        {
            driver = new ChromeDriver();
            driver.Manage().Window.Maximize();
        }

        [TestCleanup]
        public void TestCleanup()
        {
            driver.Dispose();
        }

        [TestMethod]
        public void SeleniumTestMethod()
        {
            driver.Url = "http://www.google.com";
            driver.FindElement(By.XPath("//input[@title='Search']")).SendKeys("Geeks");
            driver.SwitchTo().ActiveElement().SendKeys(Keys.Enter);
        }
    }
}

```



It's clear in TestInitialize method, ChromeDriver is created and is launched in Maximize mode. In this example we tend to google Geeks company. So first redirect browser to "http://www.google.com", type "Geeks" and press Search button. 

We are able to write Unit Test logic in SeleniumTestMethod method, So first redirect to Google website, find search text box by XPath command and set it to Geeks. Selenium runs the commands on the browser page and return IWebElement. Finally click on search button by pressing Enter key.

It's best practice to dispose Chrome driver in order to prevent creating a instance of chromedriver.exe per each test case, so in TestCleanup we dipose chrome driver.

Selenium has rich commands for selecting elements on the page, here is a good website for learning Selenium commands

https://www.toolsqa.com/selenium-c-sharp/