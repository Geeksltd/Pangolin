# BelowButton("text")



This command searches below a HTML button with the text matched within quotation marks. Use this with any of the action (Set, Click etc) or find (Above, Near, Below etc) commands.

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
            BelowButton("Clients").Click(The.Left, "New Client");
            WaitToSeeHeader(That.Contains, "NEW CLIENT");
            BelowButton("Save").Expect("Cancel");
            Click("Cancel");
        }
    }
}
```

