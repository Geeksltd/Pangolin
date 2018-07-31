# BelowField("text")



This command searches below a HTML field with text contained within quotation marks. It is to be used with any of the action (Set, Click etc) or find (Above, Near, Below etc) commands.

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
            Run<AdminUser>();
            Click("Log out");
            Set("Email address").To("admin@gmail.com");
            BelowField("Email address").Expect("Password");
            Set("Password").To("test");
            BelowField("Password").Above(What.Contains, "Forgot password?").Click("Login");
            WaitForNewPage();
            Expect(What.Contains, "Welcome,");
        }
    }
}
```

