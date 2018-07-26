# WaitForNewPage();



This command is used when the execution of the next command is delayed until the new page has loaded.

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
            
            Click("Configurations");
            WaitToSee("API Users");
            Click("API Users");
            WaitToSeeHeader(That.Contains, "API USERS");
            Click("New API User");            
            WaitToSee(What.Contains, "API USER DETAILS");
            
            Set("Name").To("API");
            Set("Email address").To("api@yahoo.com");
            Click("Save");
            WaitForNewPage();
            AtRow(That.Contains, "API").Column(That.Contains, "Clients").Expect("1");
        }
    }
}
```

