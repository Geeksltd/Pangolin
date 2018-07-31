# Above("text")



The Above command will find page elements above the text contained in quotation marks. Use
this in conjunction with a command that performs an action or expects something on a page.

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
            Above("Password").Set("Email address").To("admin@gmail.com");
            Set("Password").To("pass");
            Above(What.Contains, "Forgot password?").Click("Login");
            WaitToSee(What.Contains, "Invalid username and/or password. Please try again.");
            Click("OK");
            Set("Password").To("test");
            Above(What.Contains, "Forgot password?").Click("Login");
            WaitForNewPage();
            Expect(What.Contains, "Welcome,");
        }
    }
}
```

