# Expect("text")



Searches the current page or pop-up window for the text after the command. The first argument can be That.Equals or That.Contains. Each has a purpose for narrowing the search.

The expect command should only be used when 'ExpectButton()', 'ExpectField()', 'ExpectHeader()' or 'ExpectRow()' are not applicable. It is also good practice that it should be the last command to appear in every test.

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
            Expect(That.Contains, "CLIENTS");
            AtRow(That.Contains, "client1").Click("Edit");
            ExpectText(That.Contains, "Client Details");
            Expect(That.Contains, "Bank Shared");
            ExpectHeader(That.Contains, "Banks Shared with me");
            Set("Name").To("client2");
            Click("Save");
            WaitForNewPage();
            Expect(That.Contains, "Bank Shared");
        }
    }
}
```

