# ExpectUrl("url")



Note: Don't use this unless you absolutely have to.

This command confirms that the URL specified in quotation marks is the current page that Sanity has in focus. Use this command when verifying or validating that an intended URL redirection occurs as a result of some other action you performed within Pangolin.

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
            ExpectLink("Software Development");
            RightOfLink("Software Development").ExpectLink(That.Contains, "Geeks");
            Click("Software Development");
            ExpectUrl("http://www.geeks.ltd.uk");
        }
    }
}
```

