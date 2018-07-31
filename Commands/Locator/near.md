# Near("text")



The Near command dentifies an HTML element below text matched within quotation marks. This must be used with any of the arrange or action commands.

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
            Click("New Agency");
            ExpectHeader("Agency Details");
            Near(What.Contains, "User").Check("IsActive");
            Near("Cancel").Expect("Save");
            Click("Save");
        }
    }
}
```

