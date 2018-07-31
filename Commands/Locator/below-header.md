# BelowHeader("text")



This command searches below a HTML header with text contained within quotation marks. Use this in
conjunction with any of the action (Set, Click etc) or find (Above, Near, Below etc) commands.

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
            BelowHeader(That.Contains, "Welcome : ").Expect("Admin");
            Click(That.Contains, "New Candidate");            
            ExpectHeader(That.Contains, "New Candidate");
            BelowHeader(That.Contains, "New Candidate").Set("Name").To("Candidate1");
            Click("Save");
        }
    }
}
```

