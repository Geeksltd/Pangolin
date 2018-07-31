# AssumeDate("dd-mm-yyyy"); or AssumeDate(DateTime);



This command forces the application to assume a specified date. This is useful in situations for example when you need to ensure that something expires after a period of time, like a temporary password.

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
            AssumeDate("01/07/2015");
            AssumeTime("12:00");
            Goto("/");
            Expect(What.Contains, "Email");
            Set("Email address").To("admin@gmail.com");
            Set("Password").To("test");
            Click("Login");
        }
    }
}
```

