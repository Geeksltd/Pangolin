# ExpectNoButton("text")



This command searches the current page to ensure no HTML buttons are found with the text contained in
quotation marks on them. These "ExpectNo" prefixed commands are commonly used to test scenarios where the application's business logic dictates that something should be unavailable to users. For example if someone selects on an online passport application that they have no children, all parts of the online form related to children should be hidden.

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
            ExpectRow(That.Contains, "Working Group");
            Click("Working Group");
            Click("Details");
            ExpectHeader(That.Contains, "AGENCY DETAILS");
            Click("Edit");
            Set("Name").To("not changed");
            Click("Cancel");
            WaitForNewPage();
            ExpectNoButton(That.Contains, "Cancel");
            ExpectNoButton(That.Contains, "Save");
            AtLabel(That.Contains, "Name").Expect(What.Contains, "Working Group");
        }
    }
}
```

