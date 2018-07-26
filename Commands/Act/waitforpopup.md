# WaitForPopup();



The WaitForPopup command is used when the execution of the next command is delayed until the pop up has loaded.

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
            Click("Users");
            WaitForPopup();
            ExpectHeader(That.Contains, "CLIENT");
            Set("New client").To("user");
            Click("Save");
        }
    }
}
```

