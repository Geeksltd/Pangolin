# ExpectRow("text")



This command searches the current page for a row in a list (or table) with the text contained in quotation marks in it. Use this command when verifying or validating that an intended table row appears as a result of some other action you performed within Pangolin.

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
            Click("Clients");
            WaitForNewPage();
            ExpectHeader(That.Contains, "CLIENTS");
            Click("New Client");
            WaitForNewPage();
            ExpectHeader(That.Contains, "CLIENT DETAILS");
            Set("Name").To("New Client");
            UnCheck("Inactive");
            Click("Save");
            WaitForNewPage();
            ExpectRow(That.Contains, "New Client");
        }
    }
}
```

