# ExpectNoRow("text")



This command searches the current page in focus to ensure a HTML table row with the text contained in
quotation marks is not found. The "ExpectNo" prefixed commands are commonly used to test scenarios where the business logic dictates that something should be unavailable to users in certain test cases.

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
            LoginAs<Adminuser>();
            Click("Agencies");
            AtRow(That.Contains, "Working Group").Click("Edit");
            Set("Name").To("Unchanged");
            Click("Cancel");
            ExpectHeader(That.Contains, "AGENCIES");
            ExpectRow(That.Contains, "Working Group");
            AtRow(That.Contains, "Working Group").Click("Edit");
            Set("Name").To("Edited");
            Click("Save");
            WaitForNewPage();
            ExpectRow(That.Contains, "Edited");
            ExpectNoRow(That.Contains, "Working Group");
        }
    }
}
```

