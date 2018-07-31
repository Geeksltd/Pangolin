# NearHeader("text")



This command finds a HTML header with text matched within quotation marks. Use this command with an arrange (e.g. Above, Below etc) or an action (e.g. Set, Click etc) command.

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
            ExpectHeader(What.Contains, "Agency Detail");
            Set("Name").To("Edited");            
            NearHeader(What.Contains, "Agency Detail").ExpectButton("Save");            
            NearHeader(What.Contains, "Agency Detail").ClickButton("Save");
            WaitForNewPage();
            AtRow(1).Expect(What.Contains, "Edited");
        }
    }
}
```

