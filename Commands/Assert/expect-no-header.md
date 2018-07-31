# ExpectNoHeader("text")



This command searches the current page in focus to ensure that a HTML header with the text contained in
quotation marks is not found. The "ExpectNo" prefixed commands are commonly used to test scenarios where we are testing a failure scenario or if the business logic dictates that something should be unavailable to users in certain real world scenarios.

e.g.

```C#
using Pangolin;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace TestUITests
{
    [TestClass]
    public class Test : UITest
    {
        [TestMethod]
        public override void RunTest()
        {
            LoginAs<AdminUser>();
            Click("Candidates");
            ExpectNoRow(That.Contains, "New Candidate");
            Click("Search");
            ExpectRow(That.Contains, "Candidate");
            Click("New Candidate");
            WaitForNewPage();
            ExpectHeader(That.Contains, "CANDIDATE DETAILS");
            Click("Cancel");
            WaitForNewPage();
            ExpectNoHeader(That.Contains, "CANDIDATE DETAILS");
        }
    }
}
```

