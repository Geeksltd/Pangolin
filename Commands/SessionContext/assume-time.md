# AssumeTime("hh:mm") or AssumeTime(TimeSpan)



This command forces applications to assume a specified time. This could be a past or future time.

e.g.

```C#
using Pangolin;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace TestUITests
{
    [TestClass]
    public class Adminuser : UITest
    {
        [TestMethod]
        public override void RunTest()
        {
            Logout();
            AssumeDate("01/07/2018");
            AssumeTime("12:00");
            Goto("/");
            Set("Email address").To("admin@gmail.com");
            Set("Password").To("test");
            Click("Login");
        }
    }
}
```

