# AboveField("text")



The AboveField command finds an element above a field labelled with text contained within quotation marks. Once it is found you need to perform some sort of action or assertion.

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
            AboveField("Password").Expect("Email address");
            Set("Email address").To("admin@gmail.com");
            AboveButton("Login").Set("Password").To("test");
            Above(What.Contains, "Forgot password?").Click("Login");
            WaitForNewPage();
            Expect(What.Contains, "Welcome,");
        }
    }
}
```

