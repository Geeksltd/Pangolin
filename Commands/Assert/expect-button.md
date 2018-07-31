# ExpectButton("text")



This command searches the current page for an HTML button with the text matched in quotation marks on it. This command is used when verifying or validating that an intended button appears as a result of some other action you performed within Pangolin.

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
            WaitForNewPage();
            Click("Clients");
            WaitForNewPage();
            ExpectButton(That.Contains, "New Client");            
            Click("New Client");
            WaitForNewPage();
            Set("Name").To("client1");
            Choose("Public");
            UnCheck("Inactive");
            ExpectButton(That.Contains, "Save");  
            Click("Save");
            WaitToSee(What.Contains, "Are you sure?");
            ExpectButton(That.Contains, "Cancel");
            Click("OK");
            WaitToSee(What.Contains, "CLIENT USER DETAILS");
        }
    }
}
```

